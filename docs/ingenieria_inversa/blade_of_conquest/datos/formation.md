
> **Nota de preservación (2026-10-25):** estas tablas se generaron parseando los XML
> `assets/datas/*.dat` y `game_maps/*.tmx` del APK de Blade of Conquest v1.0.2
> (com.wmstudio.games.boc, desarrollador 田坤/Kevin_Tien86, juego abandonado retirado de
> Google Play en 2020). Se publican como material de análisis y referencia de diseño para
> el proyecto Valcoria: son tablas de datos y cifras reformateadas, no assets del juego.
> El APK original y la descompilación completa de Ghidra (5.750 funciones en `findings/decomp/`)
> se conservan en el espacio local del proyecto (`/home/z/my-project/rea/blade_of_conquest/`).
# FORMACIONES DE BATALLA

Fuente: `assets/datas/formation.dat` (XML en claro). 
Entidades: `fmt_info` ×3


## `fmt_info` — 3 registros

### fmt_info #1

| campo | valor |
|---|---|
| fmt_id | 0 |
| fmt_name | default |
| cmd_pos | 140,0 |
| pts | -40,50\|-40,-50\|-40,150\|-40,-150\|-40,250\|-40,-250\|-40,350\|-40,-350\|-40,450\|-40,-450\|40,450\|40,-450\|40,350\|40,-350\|40,250\|40,-250\|40,150\|40,-150\|40,50\|40,-50 |

### fmt_info #2

| campo | valor |
|---|---|
| fmt_id | 1 |
| fmt_name | default |
| cmd_pos | 0,0 |
| pts | -100,50\|-100,-50\|-100,150\|-100,-150\|-100,250\|-100,-250\|-100,350\|-100,-350\|-100,450\|-100,-450\|100,450\|100,-450\|100,350\|100,-350\|100,250\|100,-250\|100,150\|100,-150\|100,50\|100,-50 |

### fmt_info #3

| campo | valor |
|---|---|
| fmt_id | 2 |
| fmt_name | default |
| cmd_pos | -140,0 |
| pts | -40,50\|-40,-50\|-40,150\|-40,-150\|-40,250\|-40,-250\|-40,350\|-40,-350\|-40,450\|-40,-450\|40,450\|40,-450\|40,350\|40,-350\|40,250\|40,-250\|40,150\|40,-150\|40,50\|40,-50 |

