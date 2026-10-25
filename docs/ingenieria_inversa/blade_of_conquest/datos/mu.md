
> **Nota de preservación (2026-10-25):** estas tablas se generaron parseando los XML
> `assets/datas/*.dat` y `game_maps/*.tmx` del APK de Blade of Conquest v1.0.2
> (com.wmstudio.games.boc, desarrollador 田坤/Kevin_Tien86, juego abandonado retirado de
> Google Play en 2020). Se publican como material de análisis y referencia de diseño para
> el proyecto Valcoria: son tablas de datos y cifras reformateadas, no assets del juego.
> El APK original y la descompilación completa de Ghidra (5.750 funciones en `findings/decomp/`)
> se conservan en el espacio local del proyecto (`/home/z/my-project/rea/blade_of_conquest/`).
# ANIMACIONES DE MODELOS

Fuente: `assets/datas/mu.dat` (XML en claro). 
Entidades: `model_info` ×3, `act` ×6


## `model_info` — 3 registros

| model_id | model_radx | model_rady | model_ap |
|---|---|---|---|
| 1 | 15 | 5 | 0.5,0.1 |
| 2 | 15 | 5 | 0.5,0.1 |
| 3 | 15 | 5 | 0.5,0.1 |

## `act` — 6 registros

| act_name | act_prefix | color_layer | total_frames | frame_delay |
|---|---|---|---|---|
| sr | army1_sr_ | 1 | 5 | 0.15 |
| rr | army1_rr_ | 1 | 6 | 0.1 |
| sr | footman1_sr_ | 0 | 4 | 0.15 |
| rr | footman1_rr_ | 0 | 4 | 0.16 |
| sr | caravan1_sr_ | 1 | 1 | 0.15 |
| rr | caravan1_rr_ | 1 | 6 | 0.1 |
