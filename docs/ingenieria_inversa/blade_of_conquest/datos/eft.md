
> **Nota de preservación (2026-10-25):** estas tablas se generaron parseando los XML
> `assets/datas/*.dat` y `game_maps/*.tmx` del APK de Blade of Conquest v1.0.2
> (com.wmstudio.games.boc, desarrollador 田坤/Kevin_Tien86, juego abandonado retirado de
> Google Play en 2020). Se publican como material de análisis y referencia de diseño para
> el proyecto Valcoria: son tablas de datos y cifras reformateadas, no assets del juego.
> El APK original y la descompilación completa de Ghidra (5.750 funciones en `findings/decomp/`)
> se conservan en el espacio local del proyecto (`/home/z/my-project/rea/blade_of_conquest/`).
# EFECTOS VISUALES

Fuente: `assets/datas/eft.dat` (XML en claro). 
Entidades: `effect_info` ×16


## `effect_info` — 16 registros

| eft_prefix | eft_anchorpt | total_frames | start_index | frame_delay | allow_replay |
|---|---|---|---|---|---|
| eft_arraw1_ | 0.12,0.5 | 1 | 0 | 0.2 | 1 |
| eft_arraw_done_ | 0.12,0.5 | 1 | 0 | 0.2 | 1 |
| eft_firearrow1_ | 0,0.5 | 2 | 0 | 0.2 | 1 |
| eft_fireflame1_ | 0.5,0.25 | 4 | 0 | 0.18 | 1 |
| cm_whirlwind_efc_1_ | 0.5,0.2 | 4 | 0 | 0.15 | 1 |
| eft_charge1_ | 0.5,0.5 | 2 | 0 | 0.15 | 0 |
| eft_fireball2_ | 0.1,0.5 | 3 | 0 | 0.15 | 1 |
| eft_fire_exp1_ | 0.5,0.5 | 5 | 0 | 0.12 | 0 |
| eft_frostball2_ | 0.1,0.5 | 3 | 0 | 0.15 | 1 |
| eft_ice_exp1_ | 0.5,0.5 | 4 | 0 | 0.15 | 0 |
| eft_lightball2_ | 0.1,0.5 | 3 | 0 | 0.12 | 1 |
| eft_doomball1_ | 0.1,0.5 | 3 | 0 | 0.12 | 1 |
| eft_doomexp1_ | 0.5,0.15 | 5 | 0 | 0.12 | 0 |
| eft_snipearrow_ | 0.1,0.5 | 3 | 0 | 0.15 | 1 |
| eft_mrcarrow_ | 0.1,0.5 | 4 | 0 | 0.12 | 1 |
| eft_antimag_arrow1_ | 0.15,0.5 | 1 | 0 | 0.2 | 1 |
