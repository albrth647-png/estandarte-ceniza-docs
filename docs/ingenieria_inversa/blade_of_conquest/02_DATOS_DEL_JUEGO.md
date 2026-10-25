# 02 · Datos del juego — inventario, cifrado y contenido legible — BoC v1.1.1

> Dossier de extracción de datos. Complementa a `01_ARQUITECTURA_DEL_APK.md` con lo aprendido
> al INTENTAR descifrar la base de datos y lo que de hecho ya es legible.

---

## 1. El hallazgo clave: el juego NUNCA lee los ZIP cifrados

Verificado de dos formas independientes sobre `libMyGame.so`:

1. **Escaneo completo de llamadas** (BL/BLX ARM + Thumb-2, 148.546 + 71.241 instrucciones de
   llamada decodificadas con mapeo de segmentos ELF correcto): **cero llamadas** a
   `AEZipUtility::unzipOpenFile`, `unzipFile`, `unzipFileToMemory`, `unzipTagFileToMemory` ni
   `unzOpenCurrentFilePassword`.
2. **Constantes ZipCrypto ausentes**: `0x12345678` y `0x08088405` (inicialización de claves del
   cifrado ZIP) no aparecen en ningún byte del binario — el minizip embebido fue compilado
   **sin soporte de criptografía**.

Consecuencia: los 18 ZIP con contraseña de `assets/datas/` son **restos del empaquetado del
desarrollador** (Kevin Tien los creaba en PC con `AEZipUtility::addFileToZip` y los subía con
la clave puesta; en el móvil nunca se abren). Por eso el ataque de diccionario contra la
contraseña era una calle sin salida: **la contraseña no existe en el binario**.

## 2. Los 5 ficheros que el juego SÍ lee

Referencias de cadena encontradas en `.rodata`:

| Fichero | Referencia en binario | Estado |
|---|---|---|
| `datas/mmi.dat` | `@0x00ae1589` (junto a claves `mp_id`, `mtype`) | ✅ XML plano — metadatos del mapa mundial |
| `datas/sitespos.dat` | (cargado vía `mmi.dat` §`site_pos_file`) | ✅ XML plano — posiciones de sitios |
| `datas/mesh1.dat` / `mesh2.dat` | (cargados vía `mmi.dat` §`mesh_file`) | ✅ ASCII — mallas de terreno |
| `datas/tips.dat` | `@0x00ada2b8` | ✅ XML plano — consejos EN/CN |
| `datas/sw.dat` | `@0x00ada7d7` (junto a `words_count=%d`) | ✅ texto GBK — **filtro de palabras censuradas** |
| `datas/pdl.dat` | `@0x00add7cc` (junto a `txt_pdl_thanks`) | ✅ XML plano — créditos |
| `datas/tmp_datas.dat` | `@0x00ada8b1` (junto a `1.2.8`, `r+b`, `%02x`) | ⚠️ blob de alta entropía — ver §4 |

## 3. `sw.dat` no es contenido de juego: es el filtro de censura

Decodificado como GBK: lista de **nombres políticos y personas reales** (毛泽东, 周恩来,
孙中山, 邓小平…) — el filtro que impide usar nombres sensibles al crear el héroe (requisito de
las tiendas chinas de 2016). Interesante para el dossier histórico; **sin valor de diseño**.

## 4. `tmp_datas.dat` — la pista del «caché temporal»

- 118.904 bytes de alta entropía (sin cabecera PK/zlib).
- El binario lo abre con modo **`r+b`** (lectura/escritura) y hay un `%02x` y una versión
  `1.2.8` en las cadenas contiguas — patrón de *caché binario que el juego genera y relee*.
- Hipótesis de trabajo: es un **caché** que el juego reconstruye; el contenido real (unidades,
  habilidades, economía) está **compilado dentro de `libMyGame.so`** (coherente con las cifras
  del .rodata: 568 KB de constantes + 202 KB de `.data.rel.ro`).
- Desencriptar los ZIP es por tanto **importante pero no urgente**: la data viva está en el
  binario y se extrae por descompilación (dossier 04).

## 5. Lo que ya sabemos del contenido por las cadenas (Rc.plist, 488 claves)

Vocabulario completo del juego agrupado por prefijo:

| Prefijo | Nº | Sistema |
|---|---|---|
| `cm_` | 234 | UI común (botones, títulos) |
| `txt_` | 76 | textos generales |
| `td_` | 54 | **encuentros en el mapa**: bandidos que piden oro (pagar/pelear/huir con éxito/fallo), bestias |
| `krl_` | 33 | unidades/roles |
| `sk_` | 16 | habilidades: **4 clases** (Combate, Magia, Divina, Disparo), activas/pasivas, rango `X/Y` |
| `talk_` | 10 | **retención de generales**: recompensar en oro / despedir; la lealtad se queja («quizá sea hora de irme») |
| `captalk_` | 10 | **cautivos**: persuadir / liberar / nada / matar; persuasión **1 intento por semana**; el ransom de un capturado llega por diplomacia |
| `dip_` | 6 | **diplomacia**: tributo, tregua, alianza, rescate de cautivo con oro |
| `slave_` | 5 | **venta de cautivos** al tratante |
| `persuade_` / `release_` | 3 | resultados de captación/liberación |
| `bs_` / `sg_` / `rs_` / `free_` / `dlorder_` / `map_` / `info_` | 37 | batalla, guardado, versión, descargas, mapa, info |

### El «árbol genealógico» de los sistemas de Valcoria

Estas cadenas demuestran que los sistemas estrella de Valcoria ya estaban **germinados** en BoC:

| BoC (2017) | Valcoria (diseño 2026) |
|---|---|
| `captalk_` persuadir/liberar/matar + rescate semanal | `sistemas/02_PRISIONEROS.md` (4 salidas) + canje |
| `talk_` recompensar/despedir a generales descontentos | `sistemas/10_LEALTAD_Y_DESERCION.md` |
| `dip_` tributo/tregua/alianza/rescate | Facciones con memoria de casa (`historia/05`) |
| `td_` bandidos y bestias en el mapa | Encargos y emboscadas (`misiones/`) |
| `WeeklyBudget` (escena) | Salarios diarios y renta (`sistemas/06_ECONOMIA.md`) |
| `TerritoryBox` (escena) | Conquista de sitios (`mundo/`) |
| Moral → daño (tips.dat) | Moral de campo (`batalla/01_CIFRAS.md` §5) |
| Lanza vs caballería (tips.dat) | Anti-clase por arma (batalla) |

## 6. Escenas de UI (22 ficheros `.csb`) — el flujo completo

HomeScene → SelectGame / CreateFile → FaceGenerator → CharactorScene → mundo →
PartyScene · BarracksScene · UpgradeUnit · InventoryScene · StoreScene · TradeScene ·
PrisonScene · TerritoryBox · TalentBox · SkillBox/SkillSelBox · WeeklyBudget · GiftBoxScene →
BattlePrepareScene → batalla → VictoryScene → CompletedRewards.

(+ `TestUI.csb` — residuo de desarrollo del propio Kevin Tien.)

## 7. Estado del descifrado de los ZIP (CERRADO — ver dossier 03)

- Contraseña NO está en el binario (verificado: 231.677 candidatos de strings del .so y del
  dex contra el ZipCrypto, 874 falsos positivos del check de cabecera, 0 reales).
- bkcrack (Biham-Kocher): **espacio agotado al 100 %** con las dos hipótesis de cabecera XML
  (con BOM y sin BOM) — claves no encontradas. El interior no es XML: son volcados binarios
  del editor PC del desarrollador.
- **Caso cerrado y documentado** (`03_ESTADO_DEL_DESCIFRADO.md`): los ZIP son residuos de
  build, el runtime nunca los lee, y la data viva está en el binario (dossier 04).


---

# Parte 2 · La base de datos en v1.0.2 — tablas XML en claro (anatomía completa)

> En la v1.0.2 (copia local del proyecto) los `datas/*.dat` **no son ZIP**: son XML en claro.
> Lo que sigue es la anatomía completa de esa base de datos, extraída y tabulada (ver `datos/`).

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
