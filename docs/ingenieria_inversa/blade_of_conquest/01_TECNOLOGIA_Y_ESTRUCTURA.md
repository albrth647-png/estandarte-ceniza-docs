# 01 · TECNOLOGÍA Y ESTRUCTURA — Cómo está construido Blade of Conquest

> Este dossier documenta la estructura técnica del APK original con un objetivo práctico:
> saber **cómo se hace cada cosa** para reconstruirla en Valcoria «pero mucho mejor».
> Regla: se extrae conocimiento de diseño, nunca assets ni código copiado.

## 1. Inventario del APK (v1.0.2, 36,79 MB)

```
blade_of_conquest_1.0.2.apk  (38.577.920 bytes)
├─ AndroidManifest.xml        actividad: com.wmstudio.games.boc.AppActivity (glue Cocos2d-x)
├─ classes.dex (3,6 MB)       SOLO glue: org.cocos2dx.lib + AdMob + Umeng + Firebase + enhances
├─ lib/armeabi/libcocos2dcpp.so (27,6 MB)   ← EL JUEGO ENTERO (C++, ARM32)
├─ resources.arsc (184 KB)    iconos/strings android
└─ assets/                    ← BASE DE DATOS + CONTENIDO
   ├─ datas/                  19 XML con TODAS las tablas de juego
   ├─ game_maps/              25 TMX (mundo 5×5 + mapa de prueba) + tilesets + .tsx
   ├─ Scenes/                 17 .csb CocoStudio (UI de pantallas)
   ├─ ImageRes/               atlas UI (.plist + .png) por pantalla
   ├─ RoleModels/             modelos de unidades (sprites animados por frames)
   ├─ battle_bgs/             fondos de batalla
   ├─ char_faces/             retratos (uf_*.png)
   ├─ ps_effects/             efectos de partículas
   ├─ sounds/                 audio
   ├─ fonts/ + fnt*.png       fuentes bitmap numéricas
   ├─ Rc.plist / Rc_cn.plist  textos de recursos EN/中文
   └─ Default/, misc
```

## 2. Arquitectura de runtime (deducida de símbolos y carga)

```
AppActivity (Java, glue)
  └─ libcocos2dcpp.so
      ├─ cocos2d-x 3.x (render, acciones, UI, CocosDenshion, extensions)
      ├─ CocoStudio CSLoader (lee Scenes/*.csb)
      ├─ tinyxml2 (parsea datas/*.dat y TMX)
      ├─ Recast/Detour (dtNavMesh, dtNavMeshQuery) — pathfinding de batalla
      ├─ poly2tri + ClipperLib (triangulación/clipping de geometría)
      ├─ Box2D (btConvexHull* aparece; física auxiliar)
      ├─ MOTOR PROPIO "AE" (AppEngine?): escenas, UI, diálogo, economía, plataforma
      └─ JUEGO "SG" (Strategy Game?): datos, legiones, batalla, reinos, sitios
```

Los prefijos del binario delatan dos capas propias:
- **AE\*** = framework de aplicación (escenas genéricas, cajas de UI, plataforma, utilidades,
  presupuesto, inventario, tienda…). Ej: `AEPlayerData`, `AESandTableScene`, `AEGameShared`.
- **SG\*** = dominio del juego (unidades, legiones, generales, reinos, sitios, batalla).
  Ej: `SGUnitsData`, `SGLegion`, `SGGeneral`, `SGKingdom`, `SGMapSiteObj`, `SGBattleScene`.

## 3. La base de datos: `assets/datas/*.dat` (XML en claro)

| Archivo | Contenido | Registros | Campos clave |
|---|---|---|---|
| `units.dat` | Tropas reclutables | 23 | `base_stat`, `growth`, `pre_unit`, `hire_price`, `up_price`, `drops`, `exp` |
| `skills.dat` | Habilidades/magias del héroe | 32 | `pre_skill`, `sp_cost[5]`, `val1..val5[5]`, `mp[5]`, `cd_time`, `global_cd` |
| `chars.dat` | Personajes (héroe incl.) | — | `base_str/agi/int`, `growth_str/agi/int`, `def_level`, `def_money`, `def_honor` |
| `tlt.dat` | Talentos (árbol pasivo) | — | `code`, `type`, `depend` |
| `pl.dat` | Objetos/equipo | — | `type`, `sub_t`, `equip_part`, `weapon_t`, `requires`, `f_val`, `sell_p` |
| `sl.dat` | Tienda + IAP | — | `store_id`, `item_id`, `category`, `price`, `ms_pid`, `google_pid`, `ios_pid` |
| `map_objs.dat` | Ciudades/aldeas/castillos | — | `mo_type`, `def_prosp/max_prosp`, `def_defence/max_defence`, `tower_slot`, `grocer`, `trade`, `blacksmith`, `belong` |
| `sitespos.dat` | Posición (x,y) de cada sitio | — | `id`, `pos` |
| `mmi.dat` | Meta del mapa mundial | 1 | `map_col=5`, `map_row=5`, `cell_width/height=1600`, `cells=world_0_0..world_4_4` |
| `mash1.dat` | Grafo de caminos del mundo | nodos | `link_node` con `x, y, links` |
| `ed.dat` | Bandas enemigas errantes | 34 | `rs_time`, `map_pos`, `move_mode`, `guard_radius`, `min/max_level`, `army_list`, `drops` |
| `init_datas.dat` | Estado político inicial | 6+ reinos | `king`, `chars` (con lealtad `id:valor`), `sites` (`sitio,chars`) |
| `kd.dat` | Nombres de reinos | — | `kd_id`, `kd_name` |
| `formation.dat` | Formaciones de batalla | — | `fmt_id`, `cmd_pos`, `pts` |
| `md.dat` | Metadatos de modelos | — | `model_file`, `body_radius`, `body_height`, `att_range`, `att_acts` |
| `mu.dat` | Animaciones por modelo | — | `act_name` (sr/rr…), `act_prefix`, `total_frames`, `frame_delay` |
| `gdl.dat` | Botín global por nivel | — | `s_lv`, `e_lv`, `prop`, `dl` |
| `eft.dat` | Efectos visuales | — | `eft_prefix`, `total_frames`, `frame_delay` |
| `tips.dat` | Consejos al jugador | — | `info` |

**Lección de diseño para Valcoria:** separar el 100 % del contenido en tablas de datos
versionadas, legibles y editables — exactamente la filosofía que ya exige la documentación
de Valcoria (fichas en `docs/` con cifras canónicas). BoC lo hace a su manera: una tabla
XML por dominio, ids numéricos cruzados (unidad → modelo → animaciones → efectos), y
todos los valores de balance visibles. Valcoria lo llevará a JSON con validación.

## 4. Formato de las tablas (convenciones observadas)

- **Estadísticas compactas**: `base_stat` = `mhp,260|atk,40|def,4|cri,30|mvspd,50|atspd,10`
  (pares clave,valor separados por `|`); `growth` misma forma = cuánto suma por nivel.
- **Probabilidades**: prefijo porcentual + payload separado por comas:
  `drops` = `100.0:1,20,40,0,0;100.0:10,5,10,0,0;5.0:5`
  → "100 % de veces: item 1, cantidad 20–40…; 5 %: item 5…" (tablas de loot y de comercio
  usan la misma gramática: `grocer`, `trade` en `map_objs.dat`).
- **Árboles por referencia simple**: `pre_unit` (unidad previa), `pre_skill`+`pre_skill_lv`
  (prerrequisito de habilidad), `depend` (talentos), `belong` (reino propietario).
- **Bilingüe de serie**: todo nombre/descripción existe en `*` y `*_cn`.

## 5. El mapa mundial: TMX + malla de caminos

- `mmi.dat` define la cuadrícula: **5 columnas × 5 filas, celdas de 1600×1600 px**,
  archivos `world_col_row.tmx` y malla de caminos en `datas/mash1.dat`.
- Cada `world_X_Y.tmx` (Tiled XML) trae capas de tiles (fondo/foreground con sus `.tsx`)
  y grupos de objetos.
- `mash1.dat` es el **grafo de navegación estratégica**: nodos `link_node{x,y,links}`
  que conectan poblados — el "mapa de rutas" por el que viajan las huestes.
- `sitespos.dat` da la coordenada (x,y) de cada sitio (ciudad/aldea/castillo) dentro de
  esa cuadrícula; `map_objs.dat` sus propiedades; `init_datas.dat` quién lo posee al empezar.

**Lección para Valcoria:** el mundo es *una cuadrícula de sectores + un grafo de caminos +
una tabla de sitios*. Ni terreno continuo ni streaming: lo que en móvil de 2017 era una
limitación es hoy una decisión de diseño elegante (renderizado por sectores, minimapa
natural, Partidas guardadas pequeñas).

## 6. Guardado (lo visible sin Ghidra)

- `UserDefault.xml` — el guardado ligero de Cocos (preferencias).
- Símbolos: `AECityScene::onCtlCmdsPanelSaveGame`, `AESandTableScene::onCtlCmdsPanelSaveGame`
  → el guardado se dispara desde el panel de comandos en las dos escenas "vivas"
  (mapa mundial y ciudad). `save_count` como contador de partidas.
- Strings de UI: `cm_alert_savegame`, `cm_msg_savegame`, `txt_sys_savegame.png`.

## 7. Monetización y analítica (para saber qué NO revivir tal cual)

- Tienda IAP con SKUs multiplataforma (`ms_pid`, `google_pid`, `ios_pid`) en `sl.dat`
  con categorías y precios; AdMob interstitial (`AdMobInterHelper`), Umeng analytics,
  Firebase, "enhance gameservice". Detección de trampas (changelog v1.1.1: "fixes BUG
  for cheating detection").
- Para Valcoria: nada de IAP ni anuncios en la demo; conservar solo la estructura
  de tienda local (comercio de juego) y la telemetría local opcional.

## 8. Versiones conocidas del juego

| Versión | Tamaño | Fuente | Notas |
|---|---|---|---|
| 1.0.2 (2017-05) | 36,79 MB | apk.gold (esta análisis) | base completa del esqueleto |
| 1.0.5 (2017-05) | — | apk.gold / uptodown | parche menor |
| 1.1.1 (2018-02) | 53,35 MB | uptodown (protegida con Turnstile) | última; +contenido, anti-cheat |

La v1.0.2 contiene ya todos los sistemas; la 1.1.1 añade contenido y arreglos.
