
> **Nota de preservación (2026-10-25):** estas tablas se generaron parseando los XML
> `assets/datas/*.dat` y `game_maps/*.tmx` del APK de Blade of Conquest v1.0.2
> (com.wmstudio.games.boc, desarrollador 田坤/Kevin_Tien86, juego abandonado retirado de
> Google Play en 2020). Se publican como material de análisis y referencia de diseño para
> el proyecto Valcoria: son tablas de datos y cifras reformateadas, no assets del juego.
> El APK original y la descompilación completa de Ghidra (5.750 funciones en `findings/decomp/`)
> se conservan en el espacio local del proyecto (`/home/z/my-project/rea/blade_of_conquest/`).
# MAPAS — resumen de los TMX (formato Tiled)

Fuente: `assets/game_maps/*.tmx`. El mundo se divide en una cuadrícula de sectores `world_col_row.tmx`.


## test.tmx

- tamaño: ?×? tiles de ?×? px; orientación ?
- capas de tiles: ['bg1', 'road', 'fg1']
- grupos de objetos: [] (total objetos: 0)

## test_bak.tmx

- tamaño: ?×? tiles de ?×? px; orientación ?
- capas de tiles: ['bg1', 'road', 'fg1']
- grupos de objetos: [] (total objetos: 0)

## world_0_0.tmx

- tamaño: ?×? tiles de ?×? px; orientación ?
- capas de tiles: ['bg1', 'road', 'fg1']
- grupos de objetos: ['obj'] (total objetos: 3)
- primeros objetos: ['obj', 'Castle', 'village', 'Mine']

## world_0_1.tmx

- tamaño: ?×? tiles de ?×? px; orientación ?
- capas de tiles: ['bg1', 'road', 'fg1']
- grupos de objetos: ['obj'] (total objetos: 1)
- primeros objetos: ['obj', 'Castle']

## world_0_2.tmx

- tamaño: ?×? tiles de ?×? px; orientación ?
- capas de tiles: ['bg1', 'road', 'fg1']
- grupos de objetos: ['obj'] (total objetos: 2)
- primeros objetos: ['obj', 'City', 'village']

## world_0_3.tmx

- tamaño: ?×? tiles de ?×? px; orientación ?
- capas de tiles: ['bg1', 'road', 'fg1']
- grupos de objetos: ['obj'] (total objetos: 3)
- primeros objetos: ['obj', 'village', 'village', 'Monastery']

## world_0_4.tmx

- tamaño: ?×? tiles de ?×? px; orientación ?
- capas de tiles: ['bg1', 'road', 'fg1']
- grupos de objetos: ['obj'] (total objetos: 2)
- primeros objetos: ['obj', 'village', 'city']

## world_1_0.tmx

- tamaño: ?×? tiles de ?×? px; orientación ?
- capas de tiles: ['bg1', 'road', 'fg1']
- grupos de objetos: ['obj'] (total objetos: 4)
- primeros objetos: ['obj', 'village', 'City', 'village', 'Farm']

…


## world_4_2.tmx

- tamaño: ?×? tiles de ?×? px; orientación ?
- capas de tiles: ['bg1', 'road', 'fg2', 'fg1']
- grupos de objetos: ['obj'] (total objetos: 2)
- primeros objetos: ['obj', 'village', 'Mine']

## world_4_3.tmx

- tamaño: ?×? tiles de ?×? px; orientación ?
- capas de tiles: ['bg1', 'road', 'fg2', 'fg1']
- grupos de objetos: ['obj'] (total objetos: 1)
- primeros objetos: ['obj', 'Mine']

## world_4_4.tmx

- tamaño: ?×? tiles de ?×? px; orientación ?
- capas de tiles: ['bg1', 'road', 'fg2', 'fg1']
- grupos de objetos: ['obj'] (total objetos: 2)
- primeros objetos: ['obj', 'village', 'Castle']
