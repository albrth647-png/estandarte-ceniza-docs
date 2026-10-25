
> **Nota de preservación (2026-10-25):** estas tablas se generaron parseando los XML
> `assets/datas/*.dat` y `game_maps/*.tmx` del APK de Blade of Conquest v1.0.2
> (com.wmstudio.games.boc, desarrollador 田坤/Kevin_Tien86, juego abandonado retirado de
> Google Play en 2020). Se publican como material de análisis y referencia de diseño para
> el proyecto Valcoria: son tablas de datos y cifras reformateadas, no assets del juego.
> El APK original y la descompilación completa de Ghidra (5.750 funciones en `findings/decomp/`)
> se conservan en el espacio local del proyecto (`/home/z/my-project/rea/blade_of_conquest/`).
# INICIALIZACIÓN DEL MUNDO (reinos, reyes, sitios)

Fuente: `assets/datas/init_datas.dat` (XML en claro). 
Entidades: `kingdom` ×6


## `kingdom` — 6 registros

### kingdom #1

| campo | valor |
|---|---|
| id | 1 |
| king | 1 |
| chars | 1,101 |
| sites |  |

### kingdom #2

| campo | valor |
|---|---|
| id | 2 |
| king | 105 |
| chars | 105,118:100,119:100,120:95,121:95,122:92,123:90,124:88,125:86,126:85,127:83,128:80 |
| sites | 5,105,118,119\|6,120,121\|9,122,128\|53,123\|54,124\|55,125\|56,126\|59,127 |

### kingdom #3

| campo | valor |
|---|---|
| id | 3 |
| king | 103 |
| chars | 103,107:100,108:100,109:98,110:95,111:92,112:90,113:88,114:85,115:83,116:80,117:75 |
| sites | 2,103,113,111\|50,107,114\|51,108,115\|52,109,116\|57,110,117\|58,112 |

### kingdom #4

| campo | valor |
|---|---|
| id | 4 |
| king | 104 |
| chars | 104,129:100,130:100,131:98,132:96,133:96,134:94,135:98,136:92,137:90,138:88,139:86,140:88,141:82 |
| sites | 4,104,136,141\|7,129,137\|8,130,138\|60,131,139\|63,132,140\|64,133\|65,134\|67,135 |

### kingdom #5

| campo | valor |
|---|---|
| id | 5 |
| king | 106 |
| chars | 106,142:100,143:96,144:94,145:90 |
| sites | 3,106,143,144\|62,142,145 |

### kingdom #6

| campo | valor |
|---|---|
| id | 6 |
| king | 102 |
| chars | 102,146:100,147:98,148:98,149:95 |
| sites | 1,102,148\|61,146,149\|66,147 |

