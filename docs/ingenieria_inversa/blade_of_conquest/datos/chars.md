
> **Nota de preservación (2026-10-25):** estas tablas se generaron parseando los XML
> `assets/datas/*.dat` y `game_maps/*.tmx` del APK de Blade of Conquest v1.0.2
> (com.wmstudio.games.boc, desarrollador 田坤/Kevin_Tien86, juego abandonado retirado de
> Google Play en 2020). Se publican como material de análisis y referencia de diseño para
> el proyecto Valcoria: son tablas de datos y cifras reformateadas, no assets del juego.
> El APK original y la descompilación completa de Ghidra (5.750 funciones en `findings/decomp/`)
> se conservan en el espacio local del proyecto (`/home/z/my-project/rea/blade_of_conquest/`).
# PERSONAJES (NPC/compañeros) — tabla completa

Fuente: `assets/datas/chars.dat` (XML en claro). 
Entidades: `char` ×75


## `char` — 75 registros

### char #1

| campo | valor |
|---|---|
| char_id | 101 |
| char_type | 0 |
| char_name | Chuck |
| char_name_cn | 查克 |
| face | 2 |
| weapon | 2 |
| base_str | 13 |
| base_agi | 4 |
| base_int | 8 |
| growth_str | 0.5 |
| growth_agi | 0.15 |
| growth_int | 0.35 |
| def_level | 1 |
| def_money | 800 |
| def_honor | 11 |
| def_exploit | 0 |
| skills | 301,302,303,304,305,306,307,308 |
| talent | t_rid,3\|t_cmd,8\|t_heal,3\|t_lead,1\|t_spk,1\|t_mng,4\|t_egn,3\|t_cap,4\|t_tac,1\|t_trd,5\|t_tch,3 |
| def_equip | 300,20\|700,10\|900\|0\|0\|0 |
| home_city | 0 |
| show_prop | 100 |

### char #2

| campo | valor |
|---|---|
| char_id | 102 |
| char_type | 0 |
| char_name | Archduck Williams |
| char_name_cn | 威廉姆公爵 |
| face | 3 |
| weapon | 1 |
| base_str | 11 |
| base_agi | 10 |
| base_int | 5 |
| growth_str | 0.4578 |
| growth_agi | 0.423574 |
| growth_int | 0.208626 |
| def_level | 20 |
| def_money | 5000 |
| def_honor | 6 |
| def_exploit | 0 |
| skills | 101,102,103,104,105,106,107 |
| talent | t_rid,3\|t_atk,4\|t_def,3\|t_lead,2\|t_spk,2\|t_rob,2\|t_mng,3\|t_egn,1\|t_cap,4\|t_tac,3\|t_trd,3\|t_tch,3 |
| def_equip | 203,20\|704,10\|903\|0\|0\|0 |
| home_city | 0 |
| show_prop | 100 |

### char #3

| campo | valor |
|---|---|
| char_id | 103 |
| char_type | 0 |
| char_name | King Harrison |
| char_name_cn | 哈里森国王 |
| face | 4 |
| weapon | 0 |
| base_str | 5 |
| base_agi | 3 |
| base_int | 10 |
| growth_str | 0.2128 |
| growth_agi | 0.125856 |
| growth_int | 0.421344 |
| def_level | 24 |
| def_money | 5000 |
| def_honor | 5 |
| def_exploit | 0 |
| skills | 301,302,303,304 |
| talent | t_rid,3\|t_cmd,7\|t_heal,4\|t_mng,5\|t_egn,5\|t_tac,5\|t_trd,4\|t_tch,3 |
| def_equip | 103,20\|703,10\|906\|0\|0\|0 |
| home_city | 0 |
| show_prop | 100 |

### char #4

| campo | valor |
|---|---|
| char_id | 104 |
| char_type | 0 |
| char_name | King Titus |
| char_name_cn | 泰特斯国王 |
| face | 5 |
| weapon | 1 |
| base_str | 8 |
| base_agi | 3 |
| base_int | 9 |
| growth_str | 0.3528 |
| growth_agi | 0.116928 |
| growth_int | 0.370272 |
| def_level | 26 |
| def_money | 6000 |
| def_honor | 6 |
| def_exploit | 0 |
| skills | 301,302,303,304,305 |
| talent | t_rid,3\|t_cmd,5\|t_heal,3\|t_lead,4\|t_cap,1\|t_tac,3\|t_trd,3\|t_tch,3 |
| def_equip | 204,20\|704,10\|906\|0\|0\|0 |
| home_city | 0 |
| show_prop | 100 |

### char #5

| campo | valor |
|---|---|
| char_id | 105 |
| char_type | 0 |
| char_name | King Belloc |
| char_name_cn | 贝洛克国王 |
| face | 6 |
| weapon | 1 |
| base_str | 7 |
| base_agi | 3 |
| base_int | 11 |
| growth_str | 0.2992 |
| growth_agi | 0.121968 |
| growth_int | 0.458832 |
| def_level | 25 |
| def_money | 9000 |
| def_honor | 10 |
| def_exploit | 0 |
| skills | 301,302,303,304,305 |
| talent | t_rid,3\|t_cmd,6\|t_heal,8\|t_lead,1\|t_spk,2\|t_rob,5\|t_mng,3\|t_egn,2\|t_cap,1\|t_tac,5\|t_trd,1\|t_tch,3 |
| def_equip | 204,20\|703,10\|906\|0\|0\|0 |
| home_city | 0 |
| show_prop | 100 |

### char #6

| campo | valor |
|---|---|
| char_id | 106 |
| char_type | 0 |
| char_name | Archduke Adams |
| char_name_cn | 亚当斯公爵 |
| face | 7 |
| weapon | 0 |
| base_str | 15 |
| base_agi | 5 |
| base_int | 5 |
| growth_str | 0.624 |
| growth_agi | 0.22464 |
| growth_int | 0.19136 |
| def_level | 24 |
| def_money | 4700 |
| def_honor | 0 |
| def_exploit | 0 |
| skills | 101,102,103,104,105,106,107 |
| talent | t_rid,3\|t_atk,6\|t_def,4\|t_lead,3\|t_rob,2\|t_mng,1\|t_egn,5\|t_cap,3\|t_trd,5\|t_tch,3 |
| def_equip | 105,20\|702,10\|906\|0\|0\|0 |
| home_city | 0 |
| show_prop | 100 |

### char #7

| campo | valor |
|---|---|
| char_id | 107 |
| char_type | 0 |
| char_name | Pater |
| char_name_cn | 佩特 |
| face | 8 |
| weapon | 3 |
| base_str | 10 |
| base_agi | 5 |
| base_int | 5 |
| growth_str | 0.4264 |
| growth_agi | 0.204672 |
| growth_int | 0.188928 |
| def_level | 8 |
| def_money | 800 |
| def_honor | -2 |
| def_exploit | 1200 |
| skills | 101,102,103,104,105 |
| talent | t_rid,3\|t_atk,6\|t_def,9\|t_lead,4\|t_spk,2\|t_rob,1\|t_mng,3\|t_egn,1\|t_cap,2\|t_tac,4\|t_trd,4\|t_tch,3 |
| def_equip | 400,20\|700,10\|900\|0\|0\|0 |
| home_city | 0 |
| show_prop | 100 |

### char #8

| campo | valor |
|---|---|
| char_id | 108 |
| char_type | 0 |
| char_name | Kennan |
| char_name_cn | 凯南 |
| face | 9 |
| weapon | 2 |
| base_str | 21 |
| base_agi | 5 |
| base_int | 2 |
| growth_str | 0.8436 |
| growth_agi | 0.201552 |
| growth_int | 0.094848 |
| def_level | 4 |
| def_money | 800 |
| def_honor | 7 |
| def_exploit | 880 |
| skills | 101,102,103,104,105,106,107,108 |
| talent | t_rid,3\|t_atk,9\|t_def,5\|t_lead,3\|t_spk,1\|t_mng,5\|t_egn,1\|t_tac,1\|t_trd,4\|t_tch,3 |
| def_equip | 300,20\|700,10\|900\|0\|0\|0 |
| home_city | 0 |
| show_prop | 100 |

### char #9

| campo | valor |
|---|---|
| char_id | 109 |
| char_type | 0 |
| char_name | Scripps |
| char_name_cn | 斯克利普斯 |
| face | 10 |
| weapon | 0 |
| base_str | 7 |
| base_agi | 2 |
| base_int | 7 |
| growth_str | 0.2982 |
| growth_agi | 0.098832 |
| growth_int | 0.312968 |
| def_level | 3 |
| def_money | 800 |
| def_honor | 8 |
| def_exploit | 860 |
| skills | 301,302,303,304 |
| talent | t_rid,3\|t_cmd,3\|t_heal,8\|t_lead,1\|t_spk,2\|t_rob,5\|t_mng,2\|t_cap,2\|t_trd,4\|t_tch,3 |
| def_equip | 100,20\|700,10\|900\|0\|0\|0 |
| home_city | 0 |
| show_prop | 100 |

### char #10

| campo | valor |
|---|---|
| char_id | 110 |
| char_type | 0 |
| char_name | Clive |
| char_name_cn | 克莱夫 |
| face | 11 |
| weapon | 0 |
| base_str | 11 |
| base_agi | 4 |
| base_int | 2 |
| growth_str | 0.469 |
| growth_agi | 0.15477 |
| growth_int | 0.07623 |
| def_level | 2 |
| def_money | 800 |
| def_honor | -20 |
| def_exploit | 740 |
| skills | 101,102,103,104 |
| talent | t_rid,3\|t_atk,8\|t_def,8\|t_lead,2\|t_rob,5\|t_egn,4\|t_tac,3\|t_trd,3\|t_tch,3 |
| def_equip | 100,20\|700,10\|900\|0\|0\|0 |
| home_city | 0 |
| show_prop | 100 |

### char #11

| campo | valor |
|---|---|
| char_id | 111 |
| char_type | 0 |
| char_name | Daniel |
| char_name_cn | 丹尼尔 |
| face | 12 |
| weapon | 1 |
| base_str | 11 |
| base_agi | 3 |
| base_int | 13 |
| growth_str | 0.4662 |
| growth_agi | 0.12876 |
| growth_int | 0.51504 |
| def_level | 1 |
| def_money | 800 |
| def_honor | 16 |
| def_exploit | 0 |
| skills | 301,302,303,304,305,306,307 |
| talent | t_rid,3\|t_cmd,8\|t_heal,9\|t_lead,3\|t_spk,2\|t_rob,2\|t_mng,2\|t_egn,1\|t_cap,3\|t_tac,3\|t_trd,3\|t_tch,3 |
| def_equip | 200,20\|700,10\|900\|0\|0\|0 |
| home_city | 0 |
| show_prop | 100 |

### char #12

| campo | valor |
|---|---|
| char_id | 112 |
| char_type | 0 |
| char_name | Flynn |
| char_name_cn | 弗林 |
| face | 13 |
| weapon | 3 |
| base_str | 11 |
| base_agi | 6 |
| base_int | 5 |
| growth_str | 0.4732 |
| growth_agi | 0.24024 |
| growth_int | 0.19656 |
| def_level | 15 |
| def_money | 1200 |
| def_honor | 5 |
| def_exploit | 900 |
| skills | 101,102,103,104,105,106 |
| talent | t_rid,3\|t_atk,9\|t_def,5\|t_rob,4\|t_mng,3\|t_cap,1\|t_tac,3\|t_trd,3\|t_tch,3 |
| def_equip | 302,20\|701,10\|906\|1003\|0\|801 |
| home_city | 0 |
| show_prop | 100 |

### char #13

| campo | valor |
|---|---|
| char_id | 113 |
| char_type | 0 |
| char_name | Giles |
| char_name_cn | 贾尔斯 |
| face | 14 |
| weapon | 3 |
| base_str | 11 |
| base_agi | 6 |
| base_int | 4 |
| growth_str | 0.4472 |
| growth_agi | 0.251808 |
| growth_int | 0.160992 |
| def_level | 5 |
| def_money | 800 |
| def_honor | 11 |
| def_exploit | 0 |
| skills | 101,102,103,104,105 |
| talent | t_rid,3\|t_atk,8\|t_def,8\|t_lead,1\|t_spk,2\|t_rob,2\|t_mng,2\|t_egn,1\|t_cap,4\|t_tac,1\|t_trd,5\|t_tch,3 |
| def_equip | 400,20\|700,10\|900\|0\|0\|0 |
| home_city | 0 |
| show_prop | 100 |

### char #14

| campo | valor |
|---|---|
| char_id | 114 |
| char_type | 0 |
| char_name | Cook |
| char_name_cn | 库克 |
| face | 15 |
| weapon | 5 |
| base_str | 7 |
| base_agi | 15 |
| base_int | 3 |
| growth_str | 0.27876 |
| growth_agi | 0.606 |
| growth_int | 0.12524 |
| def_level | 1 |
| def_money | 800 |
| def_honor | -9 |
| def_exploit | 0 |
| skills | 401,402,403,404,405,406 |
| talent | t_rid,3\|t_sht,5\|t_gud,9\|t_lead,3\|t_spk,1\|t_rob,1\|t_egn,1\|t_cap,1\|t_tac,5\|t_trd,2\|t_tch,3 |
| def_equip | 600,20\|0\|900\|0\|0\|0 |
| home_city | 0 |
| show_prop | 100 |

### char #15

| campo | valor |
|---|---|
| char_id | 115 |
| char_type | 0 |
| char_name | Marion |
| char_name_cn | 马里恩 |
| face | 16 |
| weapon | 0 |
| base_str | 11 |
| base_agi | 7 |
| base_int | 4 |
| growth_str | 0.455 |
| growth_agi | 0.3094 |
| growth_int | 0.1456 |
| def_level | 1 |
| def_money | 800 |
| def_honor | 10 |
| def_exploit | 0 |
| skills | 101,102,103,104,105,106 |
| talent | t_rid,3\|t_atk,9\|t_def,8\|t_lead,1\|t_spk,2\|t_rob,1\|t_mng,1\|t_egn,2\|t_cap,3\|t_tac,5\|t_trd,5\|t_tch,3 |
| def_equip | 100,20\|700,10\|900\|0\|0\|0 |
| home_city | 0 |
| show_prop | 100 |

### char #16

| campo | valor |
|---|---|
| char_id | 116 |
| char_type | 0 |
| char_name | Warren |
| char_name_cn | 瓦伦 |
| face | 17 |
| weapon | 4 |
| base_str | 9 |
| base_agi | 4 |
| base_int | 15 |
| growth_str | 0.368184 |
| growth_agi | 0.165416 |
| growth_int | 0.6264 |
| def_level | 3 |
| def_money | 800 |
| def_honor | -4 |
| def_exploit | 0 |
| skills | 201,202,203,204,205,206,207,208 |
| talent | t_rid,3\|t_mat,5\|t_mag,9\|t_lead,4\|t_spk,2\|t_rob,5\|t_mng,4\|t_egn,4\|t_cap,4\|t_tac,5\|t_tch,3 |
| def_equip | 500,20\|700,10\|900\|0\|0\|0 |
| home_city | 0 |
| show_prop | 100 |

### char #17

| campo | valor |
|---|---|
| char_id | 117 |
| char_type | 0 |
| char_name | David |
| char_name_cn | 戴维 |
| face | 18 |
| weapon | 1 |
| base_str | 7 |
| base_agi | 3 |
| base_int | 9 |
| growth_str | 0.294354 |
| growth_agi | 0.132246 |
| growth_int | 0.3634 |
| def_level | 5 |
| def_money | 800 |
| def_honor | -18 |
| def_exploit | 0 |
| skills | 201,202,203,204,205 |
| talent | t_rid,3\|t_mat,4\|t_mag,9\|t_spk,1\|t_mng,5\|t_egn,3\|t_tac,5\|t_tch,3 |
| def_equip | 500,20\|700,10\|900\|0\|0\|0 |
| home_city | 0 |
| show_prop | 100 |

### char #18

| campo | valor |
|---|---|
| char_id | 118 |
| char_type | 0 |
| char_name | Clemens |
| char_name_cn | 克里曼斯 |
| face | 19 |
| weapon | 0 |
| base_str | 8 |
| base_agi | 5 |
| base_int | 4 |
| growth_str | 0.329 |
| growth_agi | 0.18921 |
| growth_int | 0.18179 |
| def_level | 10 |
| def_money | 800 |
| def_honor | -16 |
| def_exploit | 870 |
| skills | 101,102,103,104 |
| talent | t_rid,3\|t_atk,9\|t_def,9\|t_lead,1\|t_spk,2\|t_rob,1\|t_mng,3\|t_egn,3\|t_tac,2\|t_trd,1\|t_tch,3 |
| def_equip | 100,20\|700,10\|900\|0\|0\|0 |
| home_city | 0 |
| show_prop | 100 |

### char #19

| campo | valor |
|---|---|
| char_id | 119 |
| char_type | 0 |
| char_name | Edward |
| char_name_cn | 爱德华 |
| face | 20 |
| weapon | 5 |
| base_str | 5 |
| base_agi | 17 |
| base_int | 3 |
| growth_str | 0.201159 |
| growth_agi | 0.7107 |
| growth_int | 0.118141 |
| def_level | 5 |
| def_money | 800 |
| def_honor | 17 |
| def_exploit | 680 |
| skills | 401,402,403,404,405,406,407 |
| talent | t_rid,3\|t_sht,4\|t_gud,5\|t_lead,5\|t_spk,2\|t_rob,4\|t_mng,2\|t_egn,1\|t_cap,1\|t_trd,4\|t_tch,3 |
| def_equip | 600,20\|0\|900\|0\|0\|0 |
| home_city | 0 |
| show_prop | 100 |

### char #20

| campo | valor |
|---|---|
| char_id | 120 |
| char_type | 0 |
| char_name | Nelson |
| char_name_cn | 纳尔森 |
| face | 21 |
| weapon | 2 |
| base_str | 11 |
| base_agi | 4 |
| base_int | 12 |
| growth_str | 0.4428 |
| growth_agi | 0.165672 |
| growth_int | 0.471528 |
| def_level | 1 |
| def_money | 800 |
| def_honor | 17 |
| def_exploit | 750 |
| skills | 301,302,303,304,305,306,307 |
| talent | t_rid,3\|t_cmd,6\|t_heal,8\|t_lead,5\|t_spk,1\|t_rob,4\|t_mng,5\|t_egn,1\|t_cap,3\|t_tac,3\|t_trd,2\|t_tch,3 |
| def_equip | 300,20\|700,10\|900\|0\|0\|0 |
| home_city | 0 |
| show_prop | 100 |

### char #21

| campo | valor |
|---|---|
| char_id | 121 |
| char_type | 0 |
| char_name | Warren |
| char_name_cn | 瓦伦 |
| face | 22 |
| weapon | 1 |
| base_str | 18 |
| base_agi | 5 |
| base_int | 4 |
| growth_str | 0.7215 |
| growth_agi | 0.21756 |
| growth_int | 0.17094 |
| def_level | 11 |
| def_money | 800 |
| def_honor | -12 |
| def_exploit | 640 |
| skills | 101,102,103,104,105,106,107 |
| talent | t_rid,3\|t_atk,3\|t_def,5\|t_lead,5\|t_spk,2\|t_mng,3\|t_egn,1\|t_cap,4\|t_tac,3\|t_trd,3\|t_tch,3 |
| def_equip | 200,20\|700,10\|900\|0\|0\|0 |
| home_city | 0 |
| show_prop | 100 |

### char #22

| campo | valor |
|---|---|
| char_id | 122 |
| char_type | 0 |
| char_name | Duncan |
| char_name_cn | 邓肯 |
| face | 23 |
| weapon | 1 |
| base_str | 13 |
| base_agi | 5 |
| base_int | 3 |
| growth_str | 0.5632 |
| growth_agi | 0.20592 |
| growth_int | 0.11088 |
| def_level | 13 |
| def_money | 800 |
| def_honor | -19 |
| def_exploit | 0 |
| skills | 101,102,103,104,105 |
| talent | t_rid,3\|t_atk,8\|t_def,6\|t_lead,3\|t_spk,1\|t_rob,4\|t_mng,1\|t_cap,2\|t_trd,1\|t_tch,3 |
| def_equip | 200,20\|700,10\|900\|0\|0\|0 |
| home_city | 0 |
| show_prop | 100 |

### char #23

| campo | valor |
|---|---|
| char_id | 123 |
| char_type | 0 |
| char_name | Hood |
| char_name_cn | 胡德 |
| face | 24 |
| weapon | 3 |
| base_str | 15 |
| base_agi | 4 |
| base_int | 4 |
| growth_str | 0.6204 |
| growth_agi | 0.172584 |
| growth_int | 0.147016 |
| def_level | 1 |
| def_money | 800 |
| def_honor | -18 |
| def_exploit | 480 |
| skills | 101,102,103,104,105,106 |
| talent | t_rid,3\|t_atk,5\|t_def,5\|t_lead,5\|t_mng,5\|t_egn,2\|t_cap,2\|t_tac,1\|t_trd,5\|t_tch,3 |
| def_equip | 400,20\|700,10\|900\|0\|0\|0 |
| home_city | 0 |
| show_prop | 100 |

### char #24

| campo | valor |
|---|---|
| char_id | 124 |
| char_type | 0 |
| char_name | Campbell |
| char_name_cn | 坎贝尔 |
| face | 25 |
| weapon | 0 |
| base_str | 7 |
| base_agi | 2 |
| base_int | 9 |
| growth_str | 0.2774 |
| growth_agi | 0.095046 |
| growth_int | 0.357554 |
| def_level | 1 |
| def_money | 800 |
| def_honor | 0 |
| def_exploit | 0 |
| skills | 301,302,303,304 |
| talent | t_rid,3\|t_cmd,9\|t_heal,7\|t_lead,3\|t_spk,1\|t_rob,1\|t_egn,4\|t_cap,3\|t_tac,4\|t_trd,1\|t_tch,3 |
| def_equip | 100,20\|700,10\|900\|0\|0\|0 |
| home_city | 0 |
| show_prop | 100 |

### char #25

| campo | valor |
|---|---|
| char_id | 125 |
| char_type | 0 |
| char_name | Dale |
| char_name_cn | 达勒 |
| face | 26 |
| weapon | 4 |
| base_str | 4 |
| base_agi | 4 |
| base_int | 20 |
| growth_str | 0.17595 |
| growth_agi | 0.16905 |
| growth_int | 0.8049999 |
| def_level | 1 |
| def_money | 800 |
| def_honor | 8 |
| def_exploit | 690 |
| skills | 201,202,203,204,205,206,207,208 |
| talent | t_rid,3\|t_mat,7\|t_mag,7\|t_lead,5\|t_rob,4\|t_mng,5\|t_egn,2\|t_cap,1\|t_trd,3\|t_tch,3 |
| def_equip | 500,20\|700,10\|900\|0\|0\|0 |
| home_city | 0 |
| show_prop | 100 |

### char #26

| campo | valor |
|---|---|
| char_id | 126 |
| char_type | 0 |
| char_name | O'Connor |
| char_name_cn | 奥康纳 |
| face | 27 |
| weapon | 2 |
| base_str | 13 |
| base_agi | 9 |
| base_int | 4 |
| growth_str | 0.5355 |
| growth_agi | 0.34986 |
| growth_int | 0.16464 |
| def_level | 13 |
| def_money | 800 |
| def_honor | -15 |
| def_exploit | 0 |
| skills | 101,102,103,104,105,106,107 |
| talent | t_rid,3\|t_atk,8\|t_def,9\|t_spk,1\|t_rob,4\|t_mng,3\|t_egn,1\|t_cap,1\|t_tac,4\|t_tch,3 |
| def_equip | 300,20\|700,10\|900\|0\|0\|0 |
| home_city | 0 |
| show_prop | 100 |

### char #27

| campo | valor |
|---|---|
| char_id | 127 |
| char_type | 0 |
| char_name | Cumberland |
| char_name_cn | 坎伯兰 |
| face | 28 |
| weapon | 1 |
| base_str | 10 |
| base_agi | 8 |
| base_int | 5 |
| growth_str | 0.4048 |
| growth_agi | 0.319424 |
| growth_int | 0.195776 |
| def_level | 9 |
| def_money | 800 |
| def_honor | 2 |
| def_exploit | 0 |
| skills | 101,102,103,104,105,106 |
| talent | t_rid,3\|t_atk,6\|t_def,8\|t_lead,2\|t_spk,2\|t_rob,4\|t_mng,3\|t_egn,3\|t_tac,2\|t_trd,2\|t_tch,3 |
| def_equip | 200,20\|700,10\|900\|0\|0\|0 |
| home_city | 0 |
| show_prop | 100 |

### char #28

| campo | valor |
|---|---|
| char_id | 128 |
| char_type | 0 |
| char_name | Spencer |
| char_name_cn | 斯宾森 |
| face | 29 |
| weapon | 1 |
| base_str | 14 |
| base_agi | 5 |
| base_int | 2 |
| growth_str | 0.572 |
| growth_agi | 0.20636 |
| growth_int | 0.10164 |
| def_level | 1 |
| def_money | 800 |
| def_honor | 19 |
| def_exploit | 0 |
| skills | 101,102,103,104,105 |
| talent | t_rid,3\|t_atk,5\|t_def,8\|t_lead,5\|t_spk,2\|t_rob,2\|t_mng,1\|t_egn,2\|t_cap,5\|t_tac,5\|t_trd,3\|t_tch,3 |
| def_equip | 200,20\|700,10\|900\|0\|0\|0 |
| home_city | 0 |
| show_prop | 100 |

### char #29

| campo | valor |
|---|---|
| char_id | 129 |
| char_type | 0 |
| char_name | Cromwell |
| char_name_cn | 克伦威尔 |
| face | 30 |
| weapon | 2 |
| base_str | 7 |
| base_agi | 5 |
| base_int | 13 |
| growth_str | 0.2987 |
| growth_agi | 0.204764 |
| growth_int | 0.526536 |
| def_level | 5 |
| def_money | 800 |
| def_honor | -8 |
| def_exploit | 0 |
| skills | 301,302,303,304,305,306,307 |
| talent | t_rid,3\|t_cmd,5\|t_heal,5\|t_lead,3\|t_spk,2\|t_rob,5\|t_egn,5\|t_cap,1\|t_tac,2\|t_trd,5\|t_tch,3 |
| def_equip | 300,20\|700,10\|900\|0\|0\|0 |
| home_city | 0 |
| show_prop | 100 |

### char #30

| campo | valor |
|---|---|
| char_id | 130 |
| char_type | 0 |
| char_name | Leonard |
| char_name_cn | 莱纳德 |
| face | 31 |
| weapon | 4 |
| base_str | 3 |
| base_agi | 2 |
| base_int | 13 |
| growth_str | 0.132192 |
| growth_agi | 0.062208 |
| growth_int | 0.5256 |
| def_level | 1 |
| def_money | 800 |
| def_honor | 2 |
| def_exploit | 0 |
| skills | 201,202,203,204 |
| talent | t_rid,3\|t_mat,9\|t_mag,4\|t_lead,4\|t_spk,2\|t_rob,3\|t_mng,1\|t_egn,3\|t_tac,1\|t_trd,1\|t_tch,3 |
| def_equip | 500,20\|700,10\|900\|0\|0\|0 |
| home_city | 0 |
| show_prop | 100 |

### char #31

| campo | valor |
|---|---|
| char_id | 131 |
| char_type | 0 |
| char_name | Anderson |
| char_name_cn | 安德森 |
| face | 32 |
| weapon | 1 |
| base_str | 12 |
| base_agi | 5 |
| base_int | 3 |
| growth_str | 0.4814 |
| growth_agi | 0.223104 |
| growth_int | 0.125496 |
| def_level | 1 |
| def_money | 800 |
| def_honor | 3 |
| def_exploit | 0 |
| skills | 101,102,103,104,105 |
| talent | t_rid,3\|t_atk,3\|t_def,6\|t_lead,4\|t_spk,2\|t_mng,1\|t_egn,5\|t_cap,3\|t_tac,2\|t_trd,5\|t_tch,3 |
| def_equip | 200,20\|700,10\|900\|0\|0\|0 |
| home_city | 0 |
| show_prop | 100 |

### char #32

| campo | valor |
|---|---|
| char_id | 132 |
| char_type | 0 |
| char_name | Berkeley |
| char_name_cn | 贝克莱 |
| face | 33 |
| weapon | 4 |
| base_str | 3 |
| base_agi | 3 |
| base_int | 16 |
| growth_str | 0.1183 |
| growth_agi | 0.1183 |
| growth_int | 0.6734 |
| def_level | 1 |
| def_money | 800 |
| def_honor | -10 |
| def_exploit | 0 |
| skills | 201,202,203,204,205,206 |
| talent | t_rid,3\|t_mat,8\|t_mag,9\|t_lead,3\|t_rob,3\|t_mng,5\|t_egn,3\|t_cap,1\|t_tac,3\|t_trd,4\|t_tch,3 |
| def_equip | 500,20\|700,10\|900\|0\|0\|0 |
| home_city | 0 |
| show_prop | 100 |

### char #33

| campo | valor |
|---|---|
| char_id | 133 |
| char_type | 0 |
| char_name | Murray |
| char_name_cn | 默里 |
| face | 34 |
| weapon | 2 |
| base_str | 13 |
| base_agi | 9 |
| base_int | 4 |
| growth_str | 0.5457 |
| growth_agi | 0.361767 |
| growth_int | 0.162533 |
| def_level | 1 |
| def_money | 800 |
| def_honor | -13 |
| def_exploit | 0 |
| skills | 101,102,103,104,105,106,107 |
| talent | t_rid,3\|t_atk,8\|t_def,7\|t_lead,3\|t_mng,1\|t_cap,4\|t_tac,4\|t_trd,1\|t_tch,3 |
| def_equip | 300,20\|700,10\|900\|0\|0\|0 |
| home_city | 0 |
| show_prop | 100 |

### char #34

| campo | valor |
|---|---|
| char_id | 134 |
| char_type | 0 |
| char_name | Adams |
| char_name_cn | 亚当斯 |
| face | 35 |
| weapon | 5 |
| base_str | 5 |
| base_agi | 16 |
| base_int | 5 |
| growth_str | 0.195738 |
| growth_agi | 0.6262 |
| growth_int | 0.188062 |
| def_level | 17 |
| def_money | 800 |
| def_honor | -11 |
| def_exploit | 0 |
| skills | 401,402,403,404,405,406 |
| talent | t_rid,3\|t_sht,7\|t_gud,5\|t_lead,1\|t_spk,2\|t_mng,3\|t_egn,3\|t_tac,3\|t_trd,3\|t_tch,3 |
| def_equip | 600,20\|0\|900\|0\|0\|0 |
| home_city | 0 |
| show_prop | 100 |

### char #35

| campo | valor |
|---|---|
| char_id | 135 |
| char_type | 0 |
| char_name | Crane |
| char_name_cn | 克兰 |
| face | 36 |
| weapon | 0 |
| base_str | 13 |
| base_agi | 4 |
| base_int | 2 |
| growth_str | 0.5304 |
| growth_agi | 0.172224 |
| growth_int | 0.077376 |
| def_level | 11 |
| def_money | 800 |
| def_honor | 13 |
| def_exploit | 0 |
| skills | 101,102,103,104,105 |
| talent | t_rid,3\|t_atk,4\|t_def,5\|t_lead,2\|t_spk,2\|t_rob,5\|t_mng,5\|t_egn,4\|t_cap,5\|t_tac,3\|t_trd,5\|t_tch,3 |
| def_equip | 100,20\|700,10\|900\|0\|0\|0 |
| home_city | 0 |
| show_prop | 100 |

### char #36

| campo | valor |
|---|---|
| char_id | 136 |
| char_type | 0 |
| char_name | Bentham |
| char_name_cn | 本瑟姆 |
| face | 37 |
| weapon | 2 |
| base_str | 14 |
| base_agi | 4 |
| base_int | 3 |
| growth_str | 0.5742 |
| growth_agi | 0.153816 |
| growth_int | 0.141984 |
| def_level | 11 |
| def_money | 800 |
| def_honor | 19 |
| def_exploit | 0 |
| skills | 101,102,103,104,105 |
| talent | t_rid,3\|t_atk,9\|t_def,7\|t_lead,3\|t_spk,2\|t_rob,3\|t_mng,3\|t_egn,5\|t_cap,5\|t_tac,1\|t_trd,3\|t_tch,3 |
| def_equip | 300,20\|700,10\|900\|0\|0\|0 |
| home_city | 0 |
| show_prop | 100 |

### char #37

| campo | valor |
|---|---|
| char_id | 137 |
| char_type | 0 |
| char_name | Bloomer |
| char_name_cn | 布卢默 |
| face | 38 |
| weapon | 0 |
| base_str | 16 |
| base_agi | 6 |
| base_int | 5 |
| growth_str | 0.6649001 |
| growth_agi | 0.238056 |
| growth_int | 0.187044 |
| def_level | 13 |
| def_money | 800 |
| def_honor | -11 |
| def_exploit | 0 |
| skills | 101,102,103,104,105,106,107 |
| talent | t_rid,3\|t_atk,7\|t_def,6\|t_lead,3\|t_spk,2\|t_rob,3\|t_mng,2\|t_egn,2\|t_cap,2\|t_tac,1\|t_tch,3 |
| def_equip | 100,20\|700,10\|900\|0\|0\|0 |
| home_city | 0 |
| show_prop | 100 |

### char #38

| campo | valor |
|---|---|
| char_id | 138 |
| char_type | 0 |
| char_name | Gary |
| char_name_cn | 加里 |
| face | 39 |
| weapon | 3 |
| base_str | 12 |
| base_agi | 3 |
| base_int | 3 |
| growth_str | 0.5016 |
| growth_agi | 0.14212 |
| growth_int | 0.11628 |
| def_level | 9 |
| def_money | 800 |
| def_honor | -4 |
| def_exploit | 0 |
| skills | 101,102,103,104 |
| talent | t_rid,3\|t_atk,8\|t_def,6\|t_lead,3\|t_rob,3\|t_cap,3\|t_tac,3\|t_trd,2\|t_tch,3 |
| def_equip | 400,20\|700,10\|900\|0\|0\|0 |
| home_city | 0 |
| show_prop | 100 |

### char #39

| campo | valor |
|---|---|
| char_id | 139 |
| char_type | 0 |
| char_name | Hazlitt |
| char_name_cn | 哈兹利特 |
| face | 40 |
| weapon | 4 |
| base_str | 3 |
| base_agi | 3 |
| base_int | 14 |
| growth_str | 0.12936 |
| growth_agi | 0.10584 |
| growth_int | 0.6048 |
| def_level | 8 |
| def_money | 800 |
| def_honor | -3 |
| def_exploit | 0 |
| skills | 201,202,203,204,205 |
| talent | t_rid,3\|t_mat,4\|t_mag,6\|t_spk,2\|t_rob,2\|t_mng,1\|t_egn,4\|t_cap,1\|t_tac,2\|t_tch,3 |
| def_equip | 500,20\|700,10\|900\|0\|0\|0 |
| home_city | 0 |
| show_prop | 100 |

### char #40

| campo | valor |
|---|---|
| char_id | 140 |
| char_type | 0 |
| char_name | Fergus |
| char_name_cn | 弗格斯 |
| face | 41 |
| weapon | 2 |
| base_str | 7 |
| base_agi | 4 |
| base_int | 12 |
| growth_str | 0.2852 |
| growth_agi | 0.1587 |
| growth_int | 0.4761 |
| def_level | 5 |
| def_money | 800 |
| def_honor | 2 |
| def_exploit | 0 |
| skills | 301,302,303,304,305,306 |
| talent | t_rid,3\|t_cmd,4\|t_heal,9\|t_lead,5\|t_mng,1\|t_egn,4\|t_cap,2\|t_tac,5\|t_trd,4\|t_tch,3 |
| def_equip | 300,20\|700,10\|900\|0\|0\|0 |
| home_city | 0 |
| show_prop | 100 |

### char #41

| campo | valor |
|---|---|
| char_id | 141 |
| char_type | 0 |
| char_name | Keats |
| char_name_cn | 基茨 |
| face | 42 |
| weapon | 5 |
| base_str | 4 |
| base_agi | 16 |
| base_int | 3 |
| growth_str | 0.166656 |
| growth_agi | 0.6624 |
| growth_int | 0.130944 |
| def_level | 7 |
| def_money | 800 |
| def_honor | -8 |
| def_exploit | 0 |
| skills | 401,402,403,404,405,406 |
| talent | t_rid,3\|t_sht,9\|t_gud,8\|t_lead,1\|t_rob,3\|t_egn,5\|t_cap,4\|t_tac,3\|t_trd,5\|t_tch,3 |
| def_equip | 600,20\|0\|900\|0\|0\|0 |
| home_city | 0 |
| show_prop | 100 |

### char #42

| campo | valor |
|---|---|
| char_id | 142 |
| char_type | 0 |
| char_name | Leslie |
| char_name_cn | 莱斯利 |
| face | 43 |
| weapon | 2 |
| base_str | 9 |
| base_agi | 6 |
| base_int | 5 |
| growth_str | 0.3526 |
| growth_agi | 0.247722 |
| growth_int | 0.219678 |
| def_level | 13 |
| def_money | 800 |
| def_honor | 8 |
| def_exploit | 0 |
| skills | 101,102,103,104,105 |
| talent | t_rid,3\|t_atk,4\|t_def,3\|t_lead,3\|t_rob,3\|t_mng,2\|t_egn,4\|t_cap,1\|t_trd,4\|t_tch,3 |
| def_equip | 300,20\|700,10\|900\|0\|0\|0 |
| home_city | 0 |
| show_prop | 100 |

### char #43

| campo | valor |
|---|---|
| char_id | 143 |
| char_type | 0 |
| char_name | Penn |
| char_name_cn | 佩恩 |
| face | 44 |
| weapon | 1 |
| base_str | 10 |
| base_agi | 4 |
| base_int | 12 |
| growth_str | 0.3922 |
| growth_agi | 0.160272 |
| growth_int | 0.5075279 |
| def_level | 9 |
| def_money | 800 |
| def_honor | -10 |
| def_exploit | 0 |
| skills | 301,302,303,304,305,306,307 |
| talent | t_rid,3\|t_cmd,6\|t_heal,8\|t_lead,3\|t_rob,1\|t_mng,1\|t_egn,5\|t_cap,4\|t_tac,1\|t_trd,1\|t_tch,3 |
| def_equip | 200,20\|700,10\|900\|0\|0\|0 |
| home_city | 0 |
| show_prop | 100 |

### char #44

| campo | valor |
|---|---|
| char_id | 144 |
| char_type | 0 |
| char_name | Dennis |
| char_name_cn | 丹尼斯 |
| face | 45 |
| weapon | 0 |
| base_str | 19 |
| base_agi | 4 |
| base_int | 3 |
| growth_str | 0.7776 |
| growth_agi | 0.178416 |
| growth_int | 0.123984 |
| def_level | 8 |
| def_money | 800 |
| def_honor | 19 |
| def_exploit | 0 |
| skills | 101,102,103,104,105,106,107 |
| talent | t_rid,3\|t_atk,7\|t_def,4\|t_lead,1\|t_rob,5\|t_mng,3\|t_egn,4\|t_cap,2\|t_tch,3 |
| def_equip | 100,20\|700,10\|900\|0\|0\|0 |
| home_city | 0 |
| show_prop | 100 |

### char #45

| campo | valor |
|---|---|
| char_id | 145 |
| char_type | 0 |
| char_name | Eddy |
| char_name_cn | 艾迪 |
| face | 46 |
| weapon | 2 |
| base_str | 9 |
| base_agi | 3 |
| base_int | 10 |
| growth_str | 0.3827 |
| growth_agi | 0.10146 |
| growth_int | 0.40584 |
| def_level | 12 |
| def_money | 800 |
| def_honor | 16 |
| def_exploit | 0 |
| skills | 301,302,303,304,305,306 |
| talent | t_rid,3\|t_cmd,6\|t_heal,7\|t_lead,4\|t_spk,1\|t_rob,3\|t_mng,5\|t_egn,2\|t_cap,5\|t_trd,5\|t_tch,3 |
| def_equip | 300,20\|700,10\|900\|0\|0\|0 |
| home_city | 0 |
| show_prop | 100 |

### char #46

| campo | valor |
|---|---|
| char_id | 146 |
| char_type | 0 |
| char_name | Webster |
| char_name_cn | 韦伯斯特 |
| face | 47 |
| weapon | 5 |
| base_str | 5 |
| base_agi | 10 |
| base_int | 4 |
| growth_str | 0.217152 |
| growth_agi | 0.4056 |
| growth_int | 0.157248 |
| def_level | 6 |
| def_money | 800 |
| def_honor | -19 |
| def_exploit | 0 |
| skills | 401,402,403,404,405 |
| talent | t_rid,3\|t_sht,3\|t_gud,5\|t_lead,2\|t_rob,3\|t_mng,1\|t_cap,4\|t_tac,5\|t_trd,5\|t_tch,3 |
| def_equip | 600,20\|0\|900\|0\|0\|0 |
| home_city | 0 |
| show_prop | 100 |

### char #47

| campo | valor |
|---|---|
| char_id | 147 |
| char_type | 0 |
| char_name | Henrietta |
| char_name_cn | 亨里埃塔 |
| face | 48 |
| weapon | 1 |
| base_str | 10 |
| base_agi | 5 |
| base_int | 4 |
| growth_str | 0.39 |
| growth_agi | 0.2067 |
| growth_int | 0.1833 |
| def_level | 3 |
| def_money | 800 |
| def_honor | -9 |
| def_exploit | 0 |
| skills | 101,102,103,104,105 |
| talent | t_rid,3\|t_atk,5\|t_def,3\|t_lead,1\|t_spk,2\|t_mng,1\|t_egn,5\|t_cap,3\|t_tac,4\|t_trd,4\|t_tch,3 |
| def_equip | 200,20\|700,10\|900\|0\|0\|0 |
| home_city | 0 |
| show_prop | 100 |

### char #48

| campo | valor |
|---|---|
| char_id | 148 |
| char_type | 0 |
| char_name | Christian |
| char_name_cn | 克里斯蒂安 |
| face | 49 |
| weapon | 1 |
| base_str | 19 |
| base_agi | 6 |
| base_int | 4 |
| growth_str | 0.7488 |
| growth_agi | 0.244296 |
| growth_int | 0.176904 |
| def_level | 3 |
| def_money | 800 |
| def_honor | 11 |
| def_exploit | 0 |
| skills | 101,102,103,104,105,106,107,108 |
| talent | t_rid,3\|t_atk,8\|t_def,7\|t_lead,5\|t_spk,1\|t_rob,5\|t_mng,3\|t_egn,3\|t_cap,3\|t_tac,2\|t_trd,5\|t_tch,3 |
| def_equip | 200,20\|700,10\|900\|0\|0\|0 |
| home_city | 0 |
| show_prop | 100 |

### char #49

| campo | valor |
|---|---|
| char_id | 149 |
| char_type | 0 |
| char_name | Eden |
| char_name_cn | 艾登 |
| face | 50 |
| weapon | 4 |
| base_str | 4 |
| base_agi | 4 |
| base_int | 16 |
| growth_str | 0.171402 |
| growth_agi | 0.151998 |
| growth_int | 0.6566001 |
| def_level | 2 |
| def_money | 800 |
| def_honor | 14 |
| def_exploit | 0 |
| skills | 201,202,203,204,205,206 |
| talent | t_rid,3\|t_mat,7\|t_mag,9\|t_lead,3\|t_spk,1\|t_rob,1\|t_mng,5\|t_egn,3\|t_cap,1\|t_tac,5\|t_trd,2\|t_tch,3 |
| def_equip | 500,20\|700,10\|900\|0\|0\|0 |
| home_city | 0 |
| show_prop | 100 |

### char #50

| campo | valor |
|---|---|
| char_id | 150 |
| char_type | 0 |
| char_name | Jonathan |
| char_name_cn | 乔纳森 |
| face | 51 |
| weapon | 4 |
| base_str | 5 |
| base_agi | 4 |
| base_int | 21 |
| growth_str | 0.2196 |
| growth_agi | 0.1404 |
| growth_int | 0.84 |
| def_level | 30 |
| def_money | 800 |
| def_honor | 3 |
| def_exploit | 0 |
| skills | 201,202,203,204,205,206,207,208 |
| talent | t_rid,3\|t_mat,7\|t_mag,8\|t_lead,4\|t_spk,2\|t_rob,5\|t_mng,2\|t_egn,5\|t_cap,3\|t_tac,3\|t_trd,2\|t_tch,3 |
| def_equip | 505,100\|705,100\|902\|1008\|1107\|802 |
| home_city | 0 |
| show_prop | 100 |

### char #51

| campo | valor |
|---|---|
| char_id | 151 |
| char_type | 0 |
| char_name | Jeffery |
| char_name_cn | 杰弗瑞 |
| face | 27 |
| weapon | 0 |
| base_str | 11 |
| base_agi | 4 |
| base_int | 12 |
| growth_str | 0.429 |
| growth_agi | 0.16775 |
| growth_int | 0.50325 |
| def_level | 1 |
| def_money | 800 |
| def_honor | 0 |
| def_exploit | 0 |
| skills | 301,302,303,304,305,306,307 |
| talent | t_rid,3\|t_cmd,7\|t_heal,4\|t_lead,1\|t_rob,1\|t_mng,1\|t_egn,2\|t_cap,5\|t_tac,5\|t_trd,1\|t_tch,3 |
| def_equip | 100,20\|700,10\|900\|0\|0\|0 |
| home_city | 0 |
| show_prop | 100 |

### char #52

| campo | valor |
|---|---|
| char_id | 152 |
| char_type | 0 |
| char_name | Garfield |
| char_name_cn | 加菲尔德 |
| face | 29 |
| weapon | 4 |
| base_str | 7 |
| base_agi | 6 |
| base_int | 13 |
| growth_str | 0.28812 |
| growth_agi | 0.22638 |
| growth_int | 0.5355 |
| def_level | 1 |
| def_money | 800 |
| def_honor | 0 |
| def_exploit | 0 |
| skills | 201,202,203,204,205,206,207 |
| talent | t_rid,3\|t_mat,4\|t_mag,5\|t_lead,5\|t_rob,3\|t_egn,1\|t_tac,2\|t_trd,1\|t_tch,3 |
| def_equip | 500,20\|700,10\|900\|0\|0\|0 |
| home_city | 0 |
| show_prop | 100 |

### char #53

| campo | valor |
|---|---|
| char_id | 153 |
| char_type | 0 |
| char_name | Francis |
| char_name_cn | 弗兰克思 |
| face | 30 |
| weapon | 5 |
| base_str | 5 |
| base_agi | 20 |
| base_int | 4 |
| growth_str | 0.1863 |
| growth_agi | 0.8049999 |
| growth_int | 0.1587 |
| def_level | 1 |
| def_money | 800 |
| def_honor | 0 |
| def_exploit | 0 |
| skills | 401,402,403,404,405,406,407,408 |
| talent | t_rid,3\|t_sht,8\|t_gud,7\|t_lead,1\|t_spk,2\|t_rob,3\|t_mng,1\|t_egn,3\|t_cap,2\|t_tac,2\|t_trd,2\|t_tch,3 |
| def_equip | 600,20\|0\|900\|0\|0\|0 |
| home_city | 0 |
| show_prop | 100 |

### char #54

| campo | valor |
|---|---|
| char_id | 154 |
| char_type | 0 |
| char_name | Cary |
| char_name_cn | 凯里 |
| face | 24 |
| weapon | 0 |
| base_str | 18 |
| base_agi | 4 |
| base_int | 2 |
| growth_str | 0.7326 |
| growth_agi | 0.16731 |
| growth_int | 0.09009 |
| def_level | 1 |
| def_money | 800 |
| def_honor | 0 |
| def_exploit | 0 |
| skills | 101,102,103,104,105,106 |
| talent | t_rid,3\|t_atk,8\|t_def,4\|t_lead,1\|t_spk,1\|t_rob,4\|t_egn,1\|t_cap,5\|t_tac,3\|t_trd,5\|t_tch,3 |
| def_equip | 100,20\|700,10\|900\|0\|0\|0 |
| home_city | 0 |
| show_prop | 100 |

### char #55

| campo | valor |
|---|---|
| char_id | 155 |
| char_type | 0 |
| char_name | Caleb |
| char_name_cn | 迦勒 |
| face | 23 |
| weapon | 2 |
| base_str | 15 |
| base_agi | 7 |
| base_int | 3 |
| growth_str | 0.612 |
| growth_agi | 0.27336 |
| growth_int | 0.13464 |
| def_level | 1 |
| def_money | 800 |
| def_honor | 0 |
| def_exploit | 0 |
| skills | 101,102,103,104,105,106,107 |
| talent | t_rid,3\|t_atk,3\|t_def,3\|t_spk,2\|t_rob,4\|t_mng,1\|t_egn,2\|t_tac,3\|t_trd,1\|t_tch,3 |
| def_equip | 300,20\|700,10\|900\|0\|0\|0 |
| home_city | 0 |
| show_prop | 100 |

### char #56

| campo | valor |
|---|---|
| char_id | 156 |
| char_type | 0 |
| char_name | Benson |
| char_name_cn | 本森 |
| face | 22 |
| weapon | 2 |
| base_str | 10 |
| base_agi | 3 |
| base_int | 9 |
| growth_str | 0.396 |
| growth_agi | 0.11592 |
| growth_int | 0.38808 |
| def_level | 1 |
| def_money | 800 |
| def_honor | 0 |
| def_exploit | 0 |
| skills | 301,302,303,304,305,306 |
| talent | t_rid,3\|t_cmd,5\|t_heal,5\|t_lead,5\|t_spk,1\|t_rob,1\|t_egn,5\|t_cap,5\|t_tac,1\|t_trd,1\|t_tch,3 |
| def_equip | 300,20\|700,10\|900\|0\|0\|0 |
| home_city | 0 |
| show_prop | 100 |

### char #57

| campo | valor |
|---|---|
| char_id | 157 |
| char_type | 0 |
| char_name | Alfred |
| char_name_cn | 阿尔弗雷德 |
| face | 21 |
| weapon | 2 |
| base_str | 9 |
| base_agi | 4 |
| base_int | 10 |
| growth_str | 0.361 |
| growth_agi | 0.16492 |
| growth_int | 0.42408 |
| def_level | 1 |
| def_money | 800 |
| def_honor | 0 |
| def_exploit | 0 |
| skills | 301,302,303,304,305,306 |
| talent | t_rid,3\|t_cmd,9\|t_heal,7\|t_spk,1\|t_rob,5\|t_mng,2\|t_egn,3\|t_cap,3\|t_tac,5\|t_trd,3\|t_tch,3 |
| def_equip | 300,20\|700,10\|900\|0\|0\|0 |
| home_city | 0 |
| show_prop | 100 |

### char #58

| campo | valor |
|---|---|
| char_id | 158 |
| char_type | 0 |
| char_name | Kenny |
| char_name_cn | 肯尼 |
| face | 18 |
| weapon | 1 |
| base_str | 12 |
| base_agi | 5 |
| base_int | 4 |
| growth_str | 0.484 |
| growth_agi | 0.22176 |
| growth_int | 0.17424 |
| def_level | 1 |
| def_money | 800 |
| def_honor | 0 |
| def_exploit | 0 |
| skills | 101,102,103,104,105 |
| talent | t_rid,3\|t_atk,3\|t_def,3\|t_spk,2\|t_rob,2\|t_mng,1\|t_egn,3\|t_cap,1\|t_tac,3\|t_trd,2\|t_tch,3 |
| def_equip | 200,20\|700,10\|900\|0\|0\|0 |
| home_city | 0 |
| show_prop | 100 |

### char #59

| campo | valor |
|---|---|
| char_id | 159 |
| char_type | 0 |
| char_name | Leander |
| char_name_cn | 利安德尔 |
| face | 20 |
| weapon | 2 |
| base_str | 16 |
| base_agi | 5 |
| base_int | 4 |
| growth_str | 0.6262 |
| growth_agi | 0.203414 |
| growth_int | 0.180386 |
| def_level | 1 |
| def_money | 800 |
| def_honor | 0 |
| def_exploit | 0 |
| skills | 101,102,103,104,105,106 |
| talent | t_rid,3\|t_atk,3\|t_def,8\|t_lead,5\|t_spk,1\|t_rob,2\|t_mng,2\|t_egn,2\|t_cap,5\|t_tac,1\|t_tch,3 |
| def_equip | 300,20\|700,10\|900\|0\|0\|0 |
| home_city | 0 |
| show_prop | 100 |

### char #60

| campo | valor |
|---|---|
| char_id | 160 |
| char_type | 0 |
| char_name | Marshal |
| char_name_cn | 马歇尔 |
| face | 33 |
| weapon | 5 |
| base_str | 7 |
| base_agi | 13 |
| base_int | 4 |
| growth_str | 0.278784 |
| growth_agi | 0.5544 |
| growth_int | 0.156816 |
| def_level | 1 |
| def_money | 800 |
| def_honor | 0 |
| def_exploit | 0 |
| skills | 401,402,403,404,405,406 |
| talent | t_rid,3\|t_sht,8\|t_gud,9\|t_lead,2\|t_spk,2\|t_rob,4\|t_mng,3\|t_egn,1\|t_cap,1\|t_tac,1\|t_trd,2\|t_tch,3 |
| def_equip | 600,20\|0\|900\|0\|0\|0 |
| home_city | 0 |
| show_prop | 100 |

### char #61

| campo | valor |
|---|---|
| char_id | 161 |
| char_type | 0 |
| char_name | Nicholas |
| char_name_cn | 尼古拉斯 |
| face | 34 |
| weapon | 3 |
| base_str | 16 |
| base_agi | 3 |
| base_int | 2 |
| growth_str | 0.629 |
| growth_agi | 0.13481 |
| growth_int | 0.08619001 |
| def_level | 1 |
| def_money | 800 |
| def_honor | 0 |
| def_exploit | 0 |
| skills | 101,102,103,104,105 |
| talent | t_rid,3\|t_atk,9\|t_def,7\|t_lead,4\|t_rob,2\|t_mng,3\|t_egn,5\|t_tac,2\|t_trd,4\|t_tch,3 |
| def_equip | 400,20\|700,10\|900\|0\|0\|0 |
| home_city | 0 |
| show_prop | 100 |

### char #62

| campo | valor |
|---|---|
| char_id | 162 |
| char_type | 0 |
| char_name | Phoebe |
| char_name_cn | 菲比 |
| face | 35 |
| weapon | 2 |
| base_str | 16 |
| base_agi | 5 |
| base_int | 3 |
| growth_str | 0.6256 |
| growth_agi | 0.194304 |
| growth_int | 0.100096 |
| def_level | 1 |
| def_money | 800 |
| def_honor | 0 |
| def_exploit | 0 |
| skills | 101,102,103,104,105,106 |
| talent | t_rid,3\|t_atk,6\|t_def,7\|t_lead,2\|t_rob,2\|t_cap,1\|t_tac,3\|t_trd,5\|t_tch,3 |
| def_equip | 300,20\|700,10\|900\|0\|0\|0 |
| home_city | 0 |
| show_prop | 100 |

### char #63

| campo | valor |
|---|---|
| char_id | 163 |
| char_type | 0 |
| char_name | Randolph |
| char_name_cn | 伦道夫 |
| face | 37 |
| weapon | 2 |
| base_str | 15 |
| base_agi | 6 |
| base_int | 4 |
| growth_str | 0.612 |
| growth_agi | 0.25296 |
| growth_int | 0.15504 |
| def_level | 1 |
| def_money | 800 |
| def_honor | 0 |
| def_exploit | 0 |
| skills | 101,102,103,104,105,106,107 |
| talent | t_rid,3\|t_atk,6\|t_def,4\|t_lead,4\|t_rob,5\|t_mng,5\|t_egn,5\|t_cap,1\|t_tac,1\|t_trd,1\|t_tch,3 |
| def_equip | 300,20\|700,10\|900\|0\|0\|0 |
| home_city | 0 |
| show_prop | 100 |

### char #64

| campo | valor |
|---|---|
| char_id | 164 |
| char_type | 0 |
| char_name | Ryan |
| char_name_cn | 赖安 |
| face | 38 |
| weapon | 3 |
| base_str | 18 |
| base_agi | 4 |
| base_int | 4 |
| growth_str | 0.721 |
| growth_agi | 0.1545 |
| growth_int | 0.1545 |
| def_level | 1 |
| def_money | 800 |
| def_honor | 0 |
| def_exploit | 0 |
| skills | 101,102,103,104,105,106,107 |
| talent | t_rid,3\|t_atk,5\|t_def,3\|t_lead,5\|t_spk,1\|t_rob,2\|t_mng,3\|t_egn,5\|t_cap,4\|t_tac,2\|t_trd,4\|t_tch,3 |
| def_equip | 400,20\|700,10\|900\|0\|0\|0 |
| home_city | 0 |
| show_prop | 100 |

### char #65

| campo | valor |
|---|---|
| char_id | 165 |
| char_type | 0 |
| char_name | Stanley |
| char_name_cn | 斯坦利 |
| face | 40 |
| weapon | 3 |
| base_str | 14 |
| base_agi | 8 |
| base_int | 6 |
| growth_str | 0.5488 |
| growth_agi | 0.337008 |
| growth_int | 0.234192 |
| def_level | 1 |
| def_money | 800 |
| def_honor | 0 |
| def_exploit | 0 |
| skills | 101,102,103,104,105,106,107 |
| talent | t_rid,3\|t_atk,3\|t_def,3\|t_lead,1\|t_spk,2\|t_rob,3\|t_mng,2\|t_egn,3\|t_cap,3\|t_tac,3\|t_trd,2\|t_tch,3 |
| def_equip | 400,20\|700,10\|900\|0\|0\|0 |
| home_city | 0 |
| show_prop | 100 |

### char #66

| campo | valor |
|---|---|
| char_id | 166 |
| char_type | 0 |
| char_name | Spike |
| char_name_cn | 斯派克 |
| face | 43 |
| weapon | 1 |
| base_str | 7 |
| base_agi | 4 |
| base_int | 10 |
| growth_str | 0.3026 |
| growth_agi | 0.164472 |
| growth_int | 0.422928 |
| def_level | 1 |
| def_money | 800 |
| def_honor | 0 |
| def_exploit | 0 |
| skills | 301,302,303,304,305,306 |
| talent | t_rid,3\|t_cmd,7\|t_heal,3\|t_lead,4\|t_spk,1\|t_rob,4\|t_mng,1\|t_egn,4\|t_cap,1\|t_tac,1\|t_trd,3\|t_tch,3 |
| def_equip | 200,20\|700,10\|900\|0\|0\|0 |
| home_city | 0 |
| show_prop | 100 |

### char #67

| campo | valor |
|---|---|
| char_id | 167 |
| char_type | 0 |
| char_name | Todd |
| char_name_cn | 托德 |
| face | 44 |
| weapon | 1 |
| base_str | 9 |
| base_agi | 4 |
| base_int | 10 |
| growth_str | 0.384 |
| growth_agi | 0.14976 |
| growth_int | 0.42624 |
| def_level | 1 |
| def_money | 800 |
| def_honor | 0 |
| def_exploit | 0 |
| skills | 301,302,303,304,305,306 |
| talent | t_rid,3\|t_cmd,6\|t_heal,4\|t_spk,2\|t_rob,2\|t_mng,2\|t_egn,5\|t_cap,4\|t_tch,3 |
| def_equip | 200,20\|700,10\|900\|0\|0\|0 |
| home_city | 0 |
| show_prop | 100 |

### char #68

| campo | valor |
|---|---|
| char_id | 168 |
| char_type | 0 |
| char_name | Thomas |
| char_name_cn | 托马斯 |
| face | 47 |
| weapon | 5 |
| base_str | 9 |
| base_agi | 11 |
| base_int | 5 |
| growth_str | 0.378624 |
| growth_agi | 0.4284 |
| growth_int | 0.212976 |
| def_level | 1 |
| def_money | 800 |
| def_honor | 0 |
| def_exploit | 0 |
| skills | 401,402,403,404,405,406,407 |
| talent | t_rid,3\|t_sht,6\|t_gud,6\|t_lead,4\|t_spk,2\|t_cap,1\|t_tac,5\|t_trd,4\|t_tch,3 |
| def_equip | 600,20\|0\|900\|0\|0\|0 |
| home_city | 0 |
| show_prop | 100 |

### char #69

| campo | valor |
|---|---|
| char_id | 169 |
| char_type | 0 |
| char_name | Vern |
| char_name_cn | 弗恩 |
| face | 49 |
| weapon | 0 |
| base_str | 10 |
| base_agi | 7 |
| base_int | 5 |
| growth_str | 0.4002 |
| growth_agi | 0.277182 |
| growth_int | 0.192618 |
| def_level | 1 |
| def_money | 800 |
| def_honor | 0 |
| def_exploit | 0 |
| skills | 101,102,103,104,105 |
| talent | t_rid,3\|t_atk,6\|t_def,6\|t_lead,4\|t_spk,1\|t_rob,3\|t_mng,5\|t_egn,5\|t_cap,4\|t_tac,1\|t_trd,3\|t_tch,3 |
| def_equip | 100,20\|700,10\|900\|0\|0\|0 |
| home_city | 0 |
| show_prop | 100 |

### char #70

| campo | valor |
|---|---|
| char_id | 170 |
| char_type | 0 |
| char_name | Warner |
| char_name_cn | 华纳 |
| face | 46 |
| weapon | 4 |
| base_str | 6 |
| base_agi | 4 |
| base_int | 18 |
| growth_str | 0.258048 |
| growth_agi | 0.145152 |
| growth_int | 0.7168 |
| def_level | 1 |
| def_money | 800 |
| def_honor | 1 |
| def_exploit | 0 |
| skills | 201,202,203,204,205,206,207 |
| talent | t_rid,3\|t_mat,4\|t_mag,4\|t_lead,5\|t_spk,2\|t_rob,2\|t_mng,5\|t_egn,5\|t_cap,1\|t_trd,5\|t_tch,3 |
| def_equip | 500,20\|700,10\|900\|0\|0\|0 |
| home_city | 0 |
| show_prop | 100 |

### char #71

| campo | valor |
|---|---|
| char_id | 800 |
| char_type | 1 |
| char_name | Captain |
| char_name_cn | 卫队长 |
| face | 52 |
| weapon | 1 |
| base_str | 6 |
| base_agi | 4 |
| base_int | 12 |
| growth_str | 0.2639 |
| growth_agi | 0.155064 |
| growth_int | 0.491036 |
| def_level | 1 |
| def_money | 800 |
| def_honor | 0 |
| def_exploit | 0 |
| skills | 301,302,303,304,305,306 |
| talent | t_rid,3\|t_cmd,3\|t_heal,9\|t_lead,3\|t_spk,1\|t_rob,1\|t_mng,1\|t_tac,2\|t_trd,1\|t_tch,3 |
| def_equip | 200,20\|700,10\|900\|0\|0\|0 |
| home_city | 0 |
| show_prop | 100 |

### char #72

| campo | valor |
|---|---|
| char_id | 801 |
| char_type | 1 |
| char_name | Caravan Leader |
| char_name_cn | 商队头领 |
| face | 53 |
| weapon | 2 |
| base_str | 5 |
| base_agi | 3 |
| base_int | 11 |
| growth_str | 0.185 |
| growth_agi | 0.111 |
| growth_int | 0.444 |
| def_level | 1 |
| def_money | 800 |
| def_honor | 0 |
| def_exploit | 0 |
| skills | 301,302,303,304 |
| talent | t_rid,3\|t_cmd,7\|t_heal,5\|t_spk,1\|t_mng,5\|t_egn,2\|t_cap,3\|t_tac,1\|t_tch,3 |
| def_equip | 300,20\|700,10\|900\|0\|0\|0 |
| home_city | 0 |
| show_prop | 100 |

### char #73

| campo | valor |
|---|---|
| char_id | 802 |
| char_type | 1 |
| char_name | Bandit Boss |
| char_name_cn | 盗贼头目 |
| face | 54 |
| weapon | 0 |
| base_str | 13 |
| base_agi | 8 |
| base_int | 4 |
| growth_str | 0.53 |
| growth_agi | 0.3149 |
| growth_int | 0.1551 |
| def_level | 1 |
| def_money | 800 |
| def_honor | -100 |
| def_exploit | 0 |
| skills | 101,102,103,104,105,106 |
| talent | t_rid,3\|t_atk,3\|t_def,5\|t_lead,3\|t_spk,1\|t_mng,5\|t_cap,2\|t_tac,4\|t_trd,5\|t_tch,3 |
| def_equip | 100,20\|700,10\|900\|0\|0\|0 |
| home_city | 0 |
| show_prop | 100 |

### char #74

| campo | valor |
|---|---|
| char_id | 803 |
| char_type | 1 |
| char_name | Bandit Leader |
| char_name_cn | 强盗首领 |
| face | 55 |
| weapon | 1 |
| base_str | 11 |
| base_agi | 6 |
| base_int | 3 |
| growth_str | 0.451 |
| growth_agi | 0.23247 |
| growth_int | 0.13653 |
| def_level | 1 |
| def_money | 800 |
| def_honor | -100 |
| def_exploit | 0 |
| skills | 101,102,103,104,105 |
| talent | t_rid,3\|t_atk,7\|t_def,9\|t_mng,5\|t_egn,2\|t_cap,1\|t_tac,3\|t_trd,5\|t_tch,3 |
| def_equip | 200,20\|700,10\|900\|0\|0\|0 |
| home_city | 0 |
| show_prop | 100 |

### char #75

| campo | valor |
|---|---|
| char_id | 900 |
| char_type | 1 |
| char_name | Slave Trader |
| char_name_cn | 奴隶贩子 |
| face | 53 |
| weapon | 2 |
| base_str | 5 |
| base_agi | 3 |
| base_int | 11 |
| growth_str | 0.185 |
| growth_agi | 0.111 |
| growth_int | 0.444 |
| def_level | 1 |
| def_money | 800 |
| def_honor | 0 |
| def_exploit | 0 |
| skills | 301,302,303,304 |
| talent | t_rid,3\|t_cmd,7\|t_heal,5\|t_spk,1\|t_mng,5\|t_egn,2\|t_cap,3\|t_tac,1\|t_tch,3 |
| def_equip | 300,20\|700,10\|900\|0\|0\|0 |
| home_city | 0 |
| show_prop | 100 |

