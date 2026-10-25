# 02 · MAPA MUNDIAL — Cómo está hecho el continente de Atmora

> Dossier 02 de la anatomía de Blade of Conquest. Aquí se documenta **cómo se construye
> el mapa del juego** (geografía, sitios, caminos, viajes) con su implementación original
> y la decisión de diseño equivalente para Valcoria.

## 1. La idea en una frase

El mundo es **una cuadrícula de sectores de tiles + un grafo de caminos + una tabla de
sitios**: la vista estratégica ("mesa de arena", `AESandTableScene`) recorre esa
composición y mueve las huestes por el grafo; nada de terreno continuo ni streaming.

## 2. La cuadrícula de sectores (`mmi.dat`)

```xml
<map_info>
  <map_col>5</map_col>          <!-- 5 columnas -->
  <map_row>5</map_row>          <!-- 5 filas -->
  <cell_width>1600</cell_width> <!-- cada sector: 1600 px -->
  <cell_height>1600</cell_height>
  <mash_file>datas/mash1.dat</mash_file>
  <cells>world_0_0,world_0_1,…;world_1_0,…;…</cells>  <!-- 25 archivos TMX -->
</map_info>
```

- El continente completo = **25 sectores `world_col_row.tmx`** (Tiled XML, el formato
  estándar de editor de mapas), cada uno 1600×1600 px de tiles.
- `game_maps/` incluye además `test.tmx` (mapa de batalla de pruebas) y los tilesets
  (`bg_tiles.tsx`, `fg_tiles1.tsx`, `fg_tiles2.tsx` con sus PNG).
- El mundo se renderiza por sectores: solo el sector visible y sus vecinos están "vivos".

## 3. El grafo de caminos (`mash1.dat`)

```xml
<link_node>
  <x>933</x><y>943</y>
  <links>841,940;1134,1152;1102,769</links>  <!-- coordenadas de los nodos vecinos -->
</link_node>
```

- **209 nodos** (`link_node`) con aristas como pares de coordenadas.
- Es el esqueleto de los viajes: las huestes no andan campo a través, se mueven de nodo
  a nodo por caminos; los sitios (poblados) cuelgan de nodos del grafo.
- Clase nativa relacionada: `SGMergeMap` (33 métodos) — compone/gestiona la malla del
  mundo; `AEFindPath` resuelve rutas sobre esa malla (`updateMapTransform`, `markOnMap`).

## 4. Los sitios (`sitespos.dat` + `map_objs.dat`)

- `sitespos.dat`: coordenada (x,y) de cada sitio en el mundo — **88 sitios**.
- `map_objs.dat`: propiedades de cada sitio (ver dossier 03). Clases nativas:
  `SGMapSiteObj` (39 métodos: `createMapSite`, `setMapPos`, …), `AEGameShared::getMapSite`.

## 5. Los reinos que viven en el mapa (`init_datas.dat` + `kd.dat`)

```xml
<kingdom>
  <id>2</id> <king>105</king>
  <chars>105,118:100,119:100,120:95,…</chars>   <!-- id:lealtad -->
  <sites>5,105,118,119|6,120,121|9,122,128|53,123|…</sites>  <!-- sitio,guarnición -->
</kingdom>
```

- Cada reino declara su **rey** (id de personaje), sus **vasallos con lealtad inicial**
  (0–100) y qué **sitios ocupa con qué guarnición** al comenzar la partida.
- `kd.dat` nombra los reinos. El jugador empieza en el reino 1 (Casadoria, el caído).
- La lealtad por personaje (`119:100`) es la semilla del juego político: vasallos que
  pueden ser reclutados o traidos — el antecedente directo del sistema de "capitanes con
  memoria" de Valcoria.

## 6. Cómo viaja el jugador (flujo deducido)

1. Vista de mundo: el jugador pulsa un destino → `AEFindPath` calcula la ruta sobre la
   malla (grafo de caminos).
2. La hueste (`SGLegion`) se desplaza nodo a nodo; el mundo renderiza el sector actual
   (tiles TMX) y transiciona al siguiente.
3. Encuentros: al cruzarse con bandas (`ed.dat`) o llegar a un sitio hostil → transición
   a batalla (`AEBattlePrepare` → `SGBattleScene`).
4. Al llegar a un sitio propio/amigo → escena de ciudad (`AECityScene`).

## 7. Decisión para Valcoria — el mismo esqueleto, mucho mejor

| Aspecto | BoC (2017) | Valcoria (lo que haremos) |
|---|---|---|
| Estructura del mundo | 25 TMX de 1600 px + grafo de 209 nodos | Igual de sencillo por dentro: **mapa por sectores** renderizado en WebGL a alta resolución, con niebla de guerra, clima por sector y nombres en el mapa |
| Navegación | grafo estático en XML | grafo de caminos **con pesos vivos** (estación del año, peligro por sector, escoltas) y rutas calculadas en el cliente |
| Sitios | 88 sitios, coordenada plana | misma tabla de sitios + **logos/vistas por sitio**, aldea→castillo jerarquizada (`belong`) conservada |
| Reinos | init XML con lealtades | mismo arranque declarativo + **memoria de capitanes** (Némesis propio) |
| Experiencia visual | tiles 2D planos, cámara libre | paralaje, iluminación día/noche, transiciones de sector suaves, minimapa interactivo |
| Datos | XML `.dat` privados | **JSON versionados** en `datos/` con validador — filosofía ya fijada en la documentación de Valcoria |

> Detalle importante: el "nível de construcción estilo Age of Empires" del pitch original
> NO existe en BoC (0 menciones en el repo). Lo más cercano son las **torres de defensa**
> (huecos de torre por ciudad, dossier 03). Valcoria decide: o se adoptan las torres como
> "construcción ligera de defensa", o se diseña una capa de construcción propia —
> decisión del dueño (ver `../fase_B_tabla_decisiones.md`).
