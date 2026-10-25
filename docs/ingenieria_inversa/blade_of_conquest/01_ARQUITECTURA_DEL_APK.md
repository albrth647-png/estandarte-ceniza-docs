# 01 · Arquitectura del APK y datos legibles — Blade of Conquest v1.1.1

> Extracción estática completa del paquete. Todo lo observado aquí se verificó sobre los
> ficheros reales del APK (hash en `00_RESUMEN_DEL_BLANCO.md` §1). Los volcados crudos viven en
> `rea_targets/boc_unpacked/` (fuera del repo).

---

## 1. Mapa del paquete

```
Blade-Of-Conquest-1.1.1.apk  (55.940.905 bytes)
├─ AndroidManifest.xml        arranque, permisos (8), paquete com.wmstudio.games.boc
├─ classes.dex                1 solo dex; SOLO bootstrap de Cocos2d-x (sin lógica de juego)
├─ lib/armeabi/libMyGame.so   TODA la lógica del juego (C++ nativo, ARM32)
├─ res/ + resources.arsc      iconos y strings de sistema Android
└─ assets/  (52 MB, 501 ficheros)  ← el juego de verdad está aquí
```

**Conclusión arquitectónica:** BoC es un juego 100 % nativo C++ sobre Cocos2d-x. El DEX no
contiene juego. Esto significa que para Valcoria (web/TS) no hay lógica Java que portar: la
lógica vive en el binario (Ghidra) y en los datos (`assets/`).

## 2. Inventario de `assets/` por tipo

| Tipo | Cantidad | Qué es |
|---|---|---|
| `.png` | 307 | Arte de unidades, UI, iconos, fondos |
| `.mp3` | 64 | Audio (música y efectos) |
| `.tmx` | 41 (+2 `.tsx`) | **Mapas Tiled XML** — el mundo y los campos de batalla |
| `.csb` | 31 | **Escenas Cocos Studio 2.1.0.0** — layouts de toda la UI |
| `.plist` | 25 | Atlas de sprites + tablas de textos (`Rc.plist` EN, `Rc_cn.plist` CN) |
| `.dat` | 24 | **Base de datos del juego** (ZIPs con contraseña) + 6 ficheros legibles |
| `.ttf` | 3 | Fuentes |
| `.so` | 2 | Librerías embebidas adicionales (ARM + x86, stripped) |

## 3. La base de datos del juego (`assets/datas/`)

24 ficheros `.dat`. **18 son ZIP con contraseña** (cada uno contiene un `.dat` interior
descomprimido). 6 son legibles directamente:

| Fichero | Tipo | Contenido observado |
|---|---|---|
| `mmi.dat` | XML | **Metadatos del mapa mundial**: rejilla 5×5 celdas, cada celda 1600×1600 px con sub-rejilla 50×50; ficheros `world_X_Y.tmx`; `mesh_file` y `site_pos_file` por mapa |
| `sitespos.dat` / `sitespos2.dat` | XML/texto | **Posiciones de los sitios del mundo**: `<id>` + `<pos>x,y` (ids observados: 1, 65, 105, 108, 129, 201, 282…) |
| `tips.dat` | XML | Consejos de juego EN/CN — **confirman mecánicas**: moral alta = más daño; lanza tiene bonus vs caballería; picas cargan con bonus en el primer golpe |
| `pdl.dat` | XML | Créditos: Kevin Tien (planificación+programación+arte+pruebas) |
| `sw.dat` | Texto GBK | Tabla larga de textos CN separados por comas (125 KB) |
| `mesh1.dat` / `mesh2.dat` | Texto ASCII | Mallas de terreno del mundo (25 y 26 KB) |

### Los 18 ZIP cifrados (contenido tras descifrar)

| Fichero | Tamaño descomprimido | Significado probable (por nombre) |
|---|---|---|
| `chars.dat` | 63.671 B | **Personajes** (héroe, generales, reclutables) |
| `pl.dat` | 64.232 B | Plantillas/planos (probablemente items o poblaciones) |
| `map_objs.dat` | 31.468 B | **Objetos del mapa** (sitios, recursos, puntos de interés) |
| `skills.dat` | 29.757 B | **Habilidades y magias** (4 categorías, 30 habilidades según la ficha de tienda) |
| `units.dat` | 20.223 B | **Unidades militares** (20+ tipos reclutables) |
| `md.dat` | 16.529 B | Mercados/datos de comercio urbano |
| `ed.dat` | 20.066 B | Enemigos/encuentros |
| `gdl.dat` | 7.461 B | Datos globales (gold/diplomacia?) |
| `tlt.dat` | 5.833 B | Talentos (árbol del héroe) |
| `pdl.dat`(zip) | 4.556 B | niveles de población/producción |
| `tmp_datas.dat` | 118.904 B (binario) | blob cifrado/comprimido adicional |
| `mu.dat` | 1.869 B | Música/mapas de audio |
| `mmi.dat`(zip)/`sl.dat`/`kd.dat`/`mu.dat`/`eft.dat`/`formation.dat`/`init_datas.dat` | <1,5 KB c/u | formaciones, reinos, efectos, init de partida |

> El `init_datas.dat` (1.476 B) es probablemente el **estado inicial de partida** — el análogo
> directo de nuestro `SaveState` v1. Prioridad alta de descifrado.

## 4. El sistema de mapas (cómo BoC construyó su mundo abierto)

1. **Mundo = cuadrícula de celdas**: `mmi.dat` define 5×5 = 25 celdas `world_X_Y.tmx`, cada una
   50×50 tiles de 32 px (1600×1600 px), con malla de terreno en `mesh1.dat` y sitios anclados por
   `sitespos.dat`. Total del mundo: 250×250 tiles de 32 px.
2. **Mapas Tiled estándar**: los `.tmx` usan capas `fg1` comprimidas (base64+gzip) y tilesets
   externos (`fg_tiles1.tsx`, `tile_marks.tsx`) — herramientas libres (Tiled) pueden abrirlos hoy.
3. **Sitios por id**: cada pueblo/ciudad/campo es un id numérico con posición — el equivalente
   directo de las 29 «plazas» del diseño de Valcoria (aquí son cientos, repartidos en la rejilla).

## 5. Las escenas de UI (flujo completo del juego)

`Scenes/*.csb` (Cocos Studio 2.1.0.0 — binario con nodos, botones y texturas legibles por strings):

BarracksScene · BattlePrepareScene · CharactorScene · CompletedRewards · CreateFile ·
FaceGenerator · GiftBoxScene · HomeScene · InventoryScene · PartyScene (+ ~21 más).

**Flujo observable:** HomeScene (menú) → CreateFile (crear partida/slot) → FaceGenerator
(apariencia del héroe) → CharactorScene (atributos/origen) → mundo → PartyScene (ejército) →
BattlePrepareScene (despliegue antes de combate) → batalla → CompletedRewards (botín).

## 6. Mecánicas confirmadas por `tips.dat` (texto oficial del juego)

- **Moral → daño**: mantener moral alta aumenta el daño del ejército (equivalente BoC de la
  «moral de campo» de Valcoria, §5 de `batalla/01_CIFRAS.md`).
- **Lanza vs caballería**: bonus de daño de armas de asta contra unidades montadas (anti-clase).
- **Carga de picas**: bonus de sprint en el primer ataque de lanceros con pica.
- (Resto de tips: ver volcado completo cuando se descifre `datas/` y se crucen con `sw.dat`.)

## 7. Lo que Ghidra debe responder (siguiente dossier)

1. La **contraseña ZIP** (llamadores de `unzOpenCurrentFilePassword`).
2. **Fórmulas de combate**: daño, mitigación, moral, sprint — en las funciones de resolución.
3. **Economía**: ingresos urbanos, salarios, comercio (`md.dat` + funciones asociadas).
4. **IA de mapa**: qué hacen los generadores enemigos por turno/día.
5. **Guardado**: formato y clave (`init_datas.dat`, `AECrypto`).
