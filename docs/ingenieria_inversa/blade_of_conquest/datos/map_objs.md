
> **Nota de preservación (2026-10-25):** estas tablas se generaron parseando los XML
> `assets/datas/*.dat` y `game_maps/*.tmx` del APK de Blade of Conquest v1.0.2
> (com.wmstudio.games.boc, desarrollador 田坤/Kevin_Tien86, juego abandonado retirado de
> Google Play en 2020). Se publican como material de análisis y referencia de diseño para
> el proyecto Valcoria: son tablas de datos y cifras reformateadas, no assets del juego.
> El APK original y la descompilación completa de Ghidra (5.750 funciones en `findings/decomp/`)
> se conservan en el espacio local del proyecto (`/home/z/my-project/rea/blade_of_conquest/`).
# OBJETOS DEL MAPA (ciudades, aldeas, castillos)

Fuente: `assets/datas/map_objs.dat` (XML en claro). 
Entidades: `map_obj` ×88


## `map_obj` — 88 registros

### map_obj #1

| campo | valor |
|---|---|
| mo_id | 1 |
| mo_type | 1 |
| name | St Sith |
| name_cn | 圣西斯 |
| def_prosp | 1400 |
| max_prosp | 5000 |
| def_defence | 1000 |
| max_defence | 2000 |
| tower_slot | 3 |
| grocer | 100.0:14,20,20,0,0;100.0:14,20,20,0,0;50.0:14,20,20,0,0;50.0:14,20,20,0,0;50.0:14,20,20,0,0 |
| trade | 100.0:2001,5,10,0,0;100.0:2002,3,6,0,0;100.0:2011,3,6,0,0;100.0:2013,2,8,0,0 |
| blacksmith |  |
| belong |  |

### map_obj #2

| campo | valor |
|---|---|
| mo_id | 2 |
| mo_type | 1 |
| name | Lorraine |
| name_cn | 洛林 |
| def_prosp | 1600 |
| max_prosp | 5000 |
| def_defence | 1200 |
| max_defence | 2000 |
| tower_slot | 3 |
| grocer |  |
| trade | 100.0:2004,3,8,0,0;100.0:2005,2,6,0,0;100.0:2007,1,4,0,0;100.0:2008,1,3,0,0;50.0:2014,1,3,0,0;50.0:2015,1,3,0,0;50.0:2016,1,3,0,0 |
| blacksmith |  |
| belong |  |

### map_obj #3

| campo | valor |
|---|---|
| mo_id | 3 |
| mo_type | 1 |
| name | Luske |
| name_cn | 卢斯克 |
| def_prosp | 1250 |
| max_prosp | 5000 |
| def_defence | 1100 |
| max_defence | 2000 |
| tower_slot | 3 |
| grocer |  |
| trade | 100.0:2002,3,8,0,0;100.0:2004,2,6,0,0;100.0:2006,1,4,0,0;100.0:2010,1,3,0,0;50.0:2009,1,3,0,0;50.0:2015,1,3,0,0;50.0:2015,1,3,0,0;50.0:2016,1,3,0,0 |
| blacksmith |  |
| belong |  |

### map_obj #4

| campo | valor |
|---|---|
| mo_id | 4 |
| mo_type | 1 |
| name | Bain City |
| name_cn | 贝恩城 |
| def_prosp | 1450 |
| max_prosp | 5000 |
| def_defence | 1200 |
| max_defence | 2000 |
| tower_slot | 3 |
| grocer |  |
| trade | 100.0:2001,3,8,0,0;100.0:2003,2,6,0,0;100.0:2008,1,4,0,0;100.0:2011,1,3,0,0;50.0:2012,1,3,0,0;50.0:2017,1,3,0,0;50.0:2016,1,3,0,0;50.0:2018,1,3,0,0 |
| blacksmith |  |
| belong |  |

### map_obj #5

| campo | valor |
|---|---|
| mo_id | 5 |
| mo_type | 1 |
| name | Baham |
| name_cn | 巴哈姆 |
| def_prosp | 1360 |
| max_prosp | 5000 |
| def_defence | 1000 |
| max_defence | 2000 |
| tower_slot | 3 |
| grocer |  |
| trade | 100.0:2004,3,8,0,0;100.0:2006,2,6,0,0;100.0:2007,1,4,0,0;100.0:2013,1,3,0,0;50.0:2014,1,3,0,0;50.0:2016,1,3,0,0;50.0:2009,1,3,0,0;50.0:2019,1,3,0,0 |
| blacksmith |  |
| belong |  |

### map_obj #6

| campo | valor |
|---|---|
| mo_id | 6 |
| mo_type | 1 |
| name | Lille |
| name_cn | 里尔 |
| def_prosp | 1500 |
| max_prosp | 5000 |
| def_defence | 1000 |
| max_defence | 2000 |
| tower_slot | 3 |
| grocer | 100.0:14,20,20,0,0;100.0:14,20,20,0,0;50.0:14,20,20,0,0;50.0:14,20,20,0,0;50.0:14,20,20,0,0 |
| trade | 100.0:2001,3,8,0,0;100.0:2003,2,6,0,0;100.0:2006,1,4,0,0;100.0:2008,1,3,0,0;50.0:2012,1,3,0,0;50.0:2014,1,3,0,0;50.0:2015,1,3,0,0;50.0:2018,1,3,0,0 |
| blacksmith | 30.0:906,1,1,1,60;30.0:907,1,1,1,60 |
| belong |  |

### map_obj #7

| campo | valor |
|---|---|
| mo_id | 7 |
| mo_type | 1 |
| name | Winster |
| name_cn | 温斯特 |
| def_prosp | 1200 |
| max_prosp | 5000 |
| def_defence | 1100 |
| max_defence | 2000 |
| tower_slot | 3 |
| grocer |  |
| trade | 100.0:2002,3,8,0,0;100.0:2005,2,6,0,0;100.0:2003,1,4,0,0;100.0:2013,1,3,0,0;50.0:2014,1,3,0,0;50.0:2015,1,3,0,0;50.0:2017,1,3,0,0;50.0:2019,1,3,0,0 |
| blacksmith | 60.0:203,1,1,1,60;60.0:403,1,1,1,60 |
| belong |  |

### map_obj #8

| campo | valor |
|---|---|
| mo_id | 8 |
| mo_type | 1 |
| name | Elbetal |
| name_cn | 埃尔贝托 |
| def_prosp | 1450 |
| max_prosp | 5000 |
| def_defence | 1300 |
| max_defence | 2000 |
| tower_slot | 3 |
| grocer | 100.0:14,20,20,0,0;100.0:14,20,20,0,0;50.0:14,20,20,0,0;50.0:14,20,20,0,0;50.0:14,20,20,0,0 |
| trade | 100.0:2004,3,8,0,0;100.0:2007,2,6,0,0;100.0:2008,1,4,0,0;100.0:2009,1,3,0,0;50.0:2012,1,3,0,0;50.0:2016,1,3,0,0;30.0:2017,1,3,0,0;50.0:2018,1,3,0,0 |
| blacksmith | 70.0:104,1,1,1,60;70.0:105,1,1,1,60;30.0:1008,1,1,1,60;30.0:1009,1,1,1,60;30.0:1107,1,1,1,60 |
| belong |  |

### map_obj #9

| campo | valor |
|---|---|
| mo_id | 9 |
| mo_type | 1 |
| name | Otis |
| name_cn | 奥提斯 |
| def_prosp | 1300 |
| max_prosp | 5000 |
| def_defence | 1200 |
| max_defence | 2000 |
| tower_slot | 3 |
| grocer | 100.0:10,20,20,0,0;100.0:10,20,20,0,0;100.0:10,20,20,0,0;100.0:5;100.0:100,1,1,50,100,50.0\|101,1,1,50,100,50.0 |
| trade | 100.0:2002,3,8,0,0;100.0:2005,2,6,0,0;100.0:2006,1,4,0,0;100.0:2007,1,3,0,0;50.0:2012,1,3,0,0;50.0:2016,1,3,0,0;20.0:2017,1,3,0,0;30.0:2019,1,3,0,0 |
| blacksmith | 30.0:604,1,1,1,60;30.0:704,1,1,1,60 |
| belong |  |

### map_obj #10

| campo | valor |
|---|---|
| mo_id | 50 |
| mo_type | 2 |
| name | Tisch |
| name_cn | 提斯克 |
| def_prosp | 820 |
| max_prosp | 2000 |
| def_defence | 800 |
| max_defence | 1200 |
| tower_slot | 2 |
| grocer |  |
| trade |  |
| blacksmith |  |
| belong |  |

### map_obj #11

| campo | valor |
|---|---|
| mo_id | 51 |
| mo_type | 2 |
| name | Katz Castle |
| name_cn | 卡兹堡 |
| def_prosp | 840 |
| max_prosp | 2000 |
| def_defence | 800 |
| max_defence | 1200 |
| tower_slot | 2 |
| grocer |  |
| trade |  |
| blacksmith |  |
| belong |  |

### map_obj #12

| campo | valor |
|---|---|
| mo_id | 52 |
| mo_type | 2 |
| name | Soren Castle |
| name_cn | 索伦堡 |
| def_prosp | 780 |
| max_prosp | 2000 |
| def_defence | 800 |
| max_defence | 1200 |
| tower_slot | 2 |
| grocer |  |
| trade |  |
| blacksmith |  |
| belong |  |

### map_obj #13

| campo | valor |
|---|---|
| mo_id | 53 |
| mo_type | 2 |
| name | Ward Castle |
| name_cn | 沃德 |
| def_prosp | 690 |
| max_prosp | 2000 |
| def_defence | 800 |
| max_defence | 1200 |
| tower_slot | 2 |
| grocer |  |
| trade |  |
| blacksmith |  |
| belong |  |

### map_obj #14

| campo | valor |
|---|---|
| mo_id | 54 |
| mo_type | 2 |
| name | Brent Castle |
| name_cn | 布伦特 |
| def_prosp | 720 |
| max_prosp | 2000 |
| def_defence | 800 |
| max_defence | 1200 |
| tower_slot | 2 |
| grocer |  |
| trade |  |
| blacksmith |  |
| belong |  |

### map_obj #15

| campo | valor |
|---|---|
| mo_id | 55 |
| mo_type | 2 |
| name | Thunder Castle |
| name_cn | 雷霆堡 |
| def_prosp | 680 |
| max_prosp | 2000 |
| def_defence | 800 |
| max_defence | 1200 |
| tower_slot | 2 |
| grocer |  |
| trade |  |
| blacksmith |  |
| belong |  |

### map_obj #16

| campo | valor |
|---|---|
| mo_id | 56 |
| mo_type | 2 |
| name | Frannie Castle |
| name_cn | 法兰伦 |
| def_prosp | 840 |
| max_prosp | 2000 |
| def_defence | 800 |
| max_defence | 1200 |
| tower_slot | 2 |
| grocer |  |
| trade |  |
| blacksmith |  |
| belong |  |

### map_obj #17

| campo | valor |
|---|---|
| mo_id | 57 |
| mo_type | 2 |
| name | Jacques Castle |
| name_cn | 亚克堡垒 |
| def_prosp | 780 |
| max_prosp | 2000 |
| def_defence | 800 |
| max_defence | 1200 |
| tower_slot | 2 |
| grocer |  |
| trade |  |
| blacksmith |  |
| belong |  |

### map_obj #18

| campo | valor |
|---|---|
| mo_id | 58 |
| mo_type | 2 |
| name | Dunca Castle |
| name_cn | 敦克堡 |
| def_prosp | 900 |
| max_prosp | 2000 |
| def_defence | 800 |
| max_defence | 1200 |
| tower_slot | 2 |
| grocer |  |
| trade |  |
| blacksmith | 100.0:101,1,1,1,60;100.0:102,1,1,1,60;100.0:200,1,1,1,60;100.0:300,1,1,1,60;100.0:400,1,1,1,60;100.0:500,1,1,1,60;100.0:600,1,1,1,60 |
| belong |  |

### map_obj #19

| campo | valor |
|---|---|
| mo_id | 59 |
| mo_type | 2 |
| name | Maas Castle |
| name_cn | 马斯堡 |
| def_prosp | 850 |
| max_prosp | 2000 |
| def_defence | 800 |
| max_defence | 1200 |
| tower_slot | 2 |
| grocer |  |
| trade |  |
| blacksmith |  |
| belong |  |

### map_obj #20

| campo | valor |
|---|---|
| mo_id | 60 |
| mo_type | 2 |
| name | Valtara Castle |
| name_cn | 瓦特拉 |
| def_prosp | 840 |
| max_prosp | 2000 |
| def_defence | 800 |
| max_defence | 1200 |
| tower_slot | 2 |
| grocer |  |
| trade |  |
| blacksmith |  |
| belong |  |

### map_obj #21

| campo | valor |
|---|---|
| mo_id | 61 |
| mo_type | 2 |
| name | Behlen Castle |
| name_cn | 贝伦堡 |
| def_prosp | 690 |
| max_prosp | 2000 |
| def_defence | 800 |
| max_defence | 1200 |
| tower_slot | 2 |
| grocer |  |
| trade |  |
| blacksmith |  |
| belong |  |

### map_obj #22

| campo | valor |
|---|---|
| mo_id | 62 |
| mo_type | 2 |
| name | Derek Castle |
| name_cn | 德雷克 |
| def_prosp | 780 |
| max_prosp | 2000 |
| def_defence | 800 |
| max_defence | 1200 |
| tower_slot | 2 |
| grocer |  |
| trade |  |
| blacksmith |  |
| belong |  |

### map_obj #23

| campo | valor |
|---|---|
| mo_id | 63 |
| mo_type | 2 |
| name | Aerio Castle |
| name_cn | 艾比奥 |
| def_prosp | 750 |
| max_prosp | 2000 |
| def_defence | 800 |
| max_defence | 1200 |
| tower_slot | 2 |
| grocer |  |
| trade |  |
| blacksmith |  |
| belong |  |

### map_obj #24

| campo | valor |
|---|---|
| mo_id | 64 |
| mo_type | 2 |
| name | Armitage |
| name_cn | 亚姆力特 |
| def_prosp | 860 |
| max_prosp | 2000 |
| def_defence | 800 |
| max_defence | 1200 |
| tower_slot | 2 |
| grocer |  |
| trade |  |
| blacksmith |  |
| belong |  |

### map_obj #25

| campo | valor |
|---|---|
| mo_id | 65 |
| mo_type | 2 |
| name | Whitestone |
| name_cn | 白石城 |
| def_prosp | 850 |
| max_prosp | 2000 |
| def_defence | 800 |
| max_defence | 1200 |
| tower_slot | 2 |
| grocer |  |
| trade |  |
| blacksmith |  |
| belong |  |

### map_obj #26

| campo | valor |
|---|---|
| mo_id | 66 |
| mo_type | 2 |
| name | Highcastle |
| name_cn | 高地城 |
| def_prosp | 740 |
| max_prosp | 2000 |
| def_defence | 800 |
| max_defence | 1200 |
| tower_slot | 2 |
| grocer |  |
| trade |  |
| blacksmith |  |
| belong |  |

### map_obj #27

| campo | valor |
|---|---|
| mo_id | 67 |
| mo_type | 2 |
| name | Watcher Castle |
| name_cn | 守望堡 |
| def_prosp | 900 |
| max_prosp | 2000 |
| def_defence | 800 |
| max_defence | 1200 |
| tower_slot | 2 |
| grocer |  |
| trade |  |
| blacksmith |  |
| belong |  |

### map_obj #28

| campo | valor |
|---|---|
| mo_id | 101 |
| mo_type | 3 |
| name | Edessa Village |
| name_cn | 埃德萨村 |
| def_prosp | 320 |
| max_prosp | 800 |
| def_defence | 80 |
| max_defence | 200 |
| tower_slot |  |
| grocer |  |
| trade |  |
| blacksmith |  |
| belong | 50 |

### map_obj #29

| campo | valor |
|---|---|
| mo_id | 102 |
| mo_type | 3 |
| name | Zora Village |
| name_cn | 朱诺村 |
| def_prosp | 430 |
| max_prosp | 800 |
| def_defence | 80 |
| max_defence | 200 |
| tower_slot |  |
| grocer |  |
| trade |  |
| blacksmith |  |
| belong | 6 |

### map_obj #30

| campo | valor |
|---|---|
| mo_id | 103 |
| mo_type | 3 |
| name | Agate Village |
| name_cn | 阿盖特村 |
| def_prosp | 280 |
| max_prosp | 800 |
| def_defence | 80 |
| max_defence | 200 |
| tower_slot |  |
| grocer |  |
| trade |  |
| blacksmith |  |
| belong | 6 |

### map_obj #31

| campo | valor |
|---|---|
| mo_id | 104 |
| mo_type | 3 |
| name | Liz Village |
| name_cn | 莉斯村 |
| def_prosp | 440 |
| max_prosp | 800 |
| def_defence | 80 |
| max_defence | 200 |
| tower_slot |  |
| grocer |  |
| trade |  |
| blacksmith |  |
| belong | 9 |

### map_obj #32

| campo | valor |
|---|---|
| mo_id | 105 |
| mo_type | 3 |
| name | Roland Village |
| name_cn | 卢伦村 |
| def_prosp | 530 |
| max_prosp | 800 |
| def_defence | 80 |
| max_defence | 200 |
| tower_slot |  |
| grocer |  |
| trade |  |
| blacksmith |  |
| belong | 9 |

### map_obj #33

| campo | valor |
|---|---|
| mo_id | 106 |
| mo_type | 3 |
| name | Balme Village |
| name_cn | 巴姆村 |
| def_prosp | 430 |
| max_prosp | 800 |
| def_defence | 80 |
| max_defence | 200 |
| tower_slot |  |
| grocer |  |
| trade |  |
| blacksmith |  |
| belong | 2 |

### map_obj #34

| campo | valor |
|---|---|
| mo_id | 107 |
| mo_type | 3 |
| name | Korb Village |
| name_cn | 科布村 |
| def_prosp | 390 |
| max_prosp | 800 |
| def_defence | 80 |
| max_defence | 200 |
| tower_slot |  |
| grocer |  |
| trade |  |
| blacksmith |  |
| belong | 2 |

### map_obj #35

| campo | valor |
|---|---|
| mo_id | 108 |
| mo_type | 3 |
| name | Palau Village |
| name_cn | 帕劳村 |
| def_prosp | 450 |
| max_prosp | 800 |
| def_defence | 80 |
| max_defence | 200 |
| tower_slot |  |
| grocer |  |
| trade |  |
| blacksmith |  |
| belong | 51 |

### map_obj #36

| campo | valor |
|---|---|
| mo_id | 109 |
| mo_type | 3 |
| name | Bangor Village |
| name_cn | 班格尔村 |
| def_prosp | 360 |
| max_prosp | 800 |
| def_defence | 80 |
| max_defence | 200 |
| tower_slot |  |
| grocer |  |
| trade |  |
| blacksmith |  |
| belong | 52 |

### map_obj #37

| campo | valor |
|---|---|
| mo_id | 110 |
| mo_type | 3 |
| name | Roca Village |
| name_cn | 罗卡村 |
| def_prosp | 540 |
| max_prosp | 800 |
| def_defence | 80 |
| max_defence | 200 |
| tower_slot |  |
| grocer |  |
| trade |  |
| blacksmith |  |
| belong | 53 |

### map_obj #38

| campo | valor |
|---|---|
| mo_id | 111 |
| mo_type | 3 |
| name | Polesia Village |
| name_cn | 波力西村 |
| def_prosp | 430 |
| max_prosp | 800 |
| def_defence | 80 |
| max_defence | 200 |
| tower_slot |  |
| grocer |  |
| trade |  |
| blacksmith |  |
| belong | 55 |

### map_obj #39

| campo | valor |
|---|---|
| mo_id | 112 |
| mo_type | 3 |
| name | Darling Village |
| name_cn | 达林村 |
| def_prosp | 390 |
| max_prosp | 800 |
| def_defence | 80 |
| max_defence | 200 |
| tower_slot |  |
| grocer |  |
| trade |  |
| blacksmith |  |
| belong | 5 |

### map_obj #40

| campo | valor |
|---|---|
| mo_id | 113 |
| mo_type | 3 |
| name | Skole Village |
| name_cn | 斯科尔村 |
| def_prosp | 550 |
| max_prosp | 800 |
| def_defence | 80 |
| max_defence | 200 |
| tower_slot |  |
| grocer |  |
| trade |  |
| blacksmith |  |
| belong | 56 |

### map_obj #41

| campo | valor |
|---|---|
| mo_id | 114 |
| mo_type | 3 |
| name | Nagot Village |
| name_cn | 纳哥村 |
| def_prosp | 420 |
| max_prosp | 800 |
| def_defence | 80 |
| max_defence | 200 |
| tower_slot |  |
| grocer |  |
| trade |  |
| blacksmith |  |
| belong | 57 |

### map_obj #42

| campo | valor |
|---|---|
| mo_id | 115 |
| mo_type | 3 |
| name | Hoener Village |
| name_cn | 霍纳村 |
| def_prosp | 480 |
| max_prosp | 800 |
| def_defence | 80 |
| max_defence | 200 |
| tower_slot |  |
| grocer |  |
| trade |  |
| blacksmith |  |
| belong | 58 |

### map_obj #43

| campo | valor |
|---|---|
| mo_id | 116 |
| mo_type | 3 |
| name | Niederl Village |
| name_cn | 尼德尔村 |
| def_prosp | 600 |
| max_prosp | 800 |
| def_defence | 80 |
| max_defence | 200 |
| tower_slot |  |
| grocer |  |
| trade |  |
| blacksmith |  |
| belong | 3 |

### map_obj #44

| campo | valor |
|---|---|
| mo_id | 117 |
| mo_type | 3 |
| name | Vigos Village |
| name_cn | 维戈西村 |
| def_prosp | 480 |
| max_prosp | 800 |
| def_defence | 80 |
| max_defence | 200 |
| tower_slot |  |
| grocer |  |
| trade |  |
| blacksmith |  |
| belong | 3 |

### map_obj #45

| campo | valor |
|---|---|
| mo_id | 118 |
| mo_type | 3 |
| name | Arshad Village |
| name_cn | 阿萨村 |
| def_prosp | 390 |
| max_prosp | 800 |
| def_defence | 80 |
| max_defence | 200 |
| tower_slot |  |
| grocer |  |
| trade |  |
| blacksmith |  |
| belong | 59 |

### map_obj #46

| campo | valor |
|---|---|
| mo_id | 119 |
| mo_type | 3 |
| name | Korbin Village |
| name_cn | 科宾村 |
| def_prosp | 360 |
| max_prosp | 800 |
| def_defence | 80 |
| max_defence | 200 |
| tower_slot |  |
| grocer |  |
| trade |  |
| blacksmith |  |
| belong | 54 |

### map_obj #47

| campo | valor |
|---|---|
| mo_id | 120 |
| mo_type | 3 |
| name | Dakor Village |
| name_cn | 达哥尔村 |
| def_prosp | 370 |
| max_prosp | 800 |
| def_defence | 80 |
| max_defence | 200 |
| tower_slot |  |
| grocer |  |
| trade |  |
| blacksmith |  |
| belong | 5 |

### map_obj #48

| campo | valor |
|---|---|
| mo_id | 121 |
| mo_type | 3 |
| name | Jerraca Village |
| name_cn | 杰拉卡村 |
| def_prosp | 440 |
| max_prosp | 800 |
| def_defence | 80 |
| max_defence | 200 |
| tower_slot |  |
| grocer |  |
| trade |  |
| blacksmith |  |
| belong | 60 |

### map_obj #49

| campo | valor |
|---|---|
| mo_id | 122 |
| mo_type | 3 |
| name | Bhutto Village |
| name_cn | 布多村 |
| def_prosp | 360 |
| max_prosp | 800 |
| def_defence | 80 |
| max_defence | 200 |
| tower_slot |  |
| grocer |  |
| trade |  |
| blacksmith |  |
| belong | 8 |

### map_obj #50

| campo | valor |
|---|---|
| mo_id | 123 |
| mo_type | 3 |
| name | Becca Village |
| name_cn | 贝卡村 |
| def_prosp | 290 |
| max_prosp | 800 |
| def_defence | 80 |
| max_defence | 200 |
| tower_slot |  |
| grocer |  |
| trade |  |
| blacksmith |  |
| belong | 8 |

### map_obj #51

| campo | valor |
|---|---|
| mo_id | 124 |
| mo_type | 3 |
| name | Garcia Village |
| name_cn | 加西亚村 |
| def_prosp | 450 |
| max_prosp | 800 |
| def_defence | 80 |
| max_defence | 200 |
| tower_slot |  |
| grocer |  |
| trade |  |
| blacksmith |  |
| belong | 1 |

### map_obj #52

| campo | valor |
|---|---|
| mo_id | 125 |
| mo_type | 3 |
| name | Cahill Village |
| name_cn | 卡希尔村 |
| def_prosp | 390 |
| max_prosp | 800 |
| def_defence | 80 |
| max_defence | 200 |
| tower_slot |  |
| grocer |  |
| trade |  |
| blacksmith |  |
| belong | 1 |

### map_obj #53

| campo | valor |
|---|---|
| mo_id | 126 |
| mo_type | 3 |
| name | Tumyan Village |
| name_cn | 图米扬村 |
| def_prosp | 340 |
| max_prosp | 800 |
| def_defence | 80 |
| max_defence | 200 |
| tower_slot |  |
| grocer |  |
| trade |  |
| blacksmith |  |
| belong | 61 |

### map_obj #54

| campo | valor |
|---|---|
| mo_id | 127 |
| mo_type | 3 |
| name | Eicher Village |
| name_cn | 艾希奥村 |
| def_prosp | 430 |
| max_prosp | 800 |
| def_defence | 80 |
| max_defence | 200 |
| tower_slot |  |
| grocer |  |
| trade |  |
| blacksmith |  |
| belong | 62 |

### map_obj #55

| campo | valor |
|---|---|
| mo_id | 128 |
| mo_type | 3 |
| name | Bronn Village |
| name_cn | 波隆村 |
| def_prosp | 540 |
| max_prosp | 800 |
| def_defence | 80 |
| max_defence | 200 |
| tower_slot |  |
| grocer |  |
| trade |  |
| blacksmith |  |
| belong | 4 |

### map_obj #56

| campo | valor |
|---|---|
| mo_id | 129 |
| mo_type | 3 |
| name | Kirk Village |
| name_cn | 柯克村 |
| def_prosp | 510 |
| max_prosp | 800 |
| def_defence | 80 |
| max_defence | 200 |
| tower_slot |  |
| grocer |  |
| trade |  |
| blacksmith |  |
| belong | 4 |

### map_obj #57

| campo | valor |
|---|---|
| mo_id | 130 |
| mo_type | 3 |
| name | Carol Village |
| name_cn | 嘉卢村 |
| def_prosp | 390 |
| max_prosp | 800 |
| def_defence | 80 |
| max_defence | 200 |
| tower_slot |  |
| grocer |  |
| trade |  |
| blacksmith |  |
| belong | 64 |

### map_obj #58

| campo | valor |
|---|---|
| mo_id | 131 |
| mo_type | 3 |
| name | Fabian Village |
| name_cn | 法宾村 |
| def_prosp | 430 |
| max_prosp | 800 |
| def_defence | 80 |
| max_defence | 200 |
| tower_slot |  |
| grocer |  |
| trade |  |
| blacksmith |  |
| belong | 65 |

### map_obj #59

| campo | valor |
|---|---|
| mo_id | 132 |
| mo_type | 3 |
| name | Adolph Village |
| name_cn | 阿多夫村 |
| def_prosp | 370 |
| max_prosp | 800 |
| def_defence | 80 |
| max_defence | 200 |
| tower_slot |  |
| grocer |  |
| trade |  |
| blacksmith |  |
| belong | 7 |

### map_obj #60

| campo | valor |
|---|---|
| mo_id | 133 |
| mo_type | 3 |
| name | Cecil Village |
| name_cn | 塞西村 |
| def_prosp | 430 |
| max_prosp | 800 |
| def_defence | 80 |
| max_defence | 200 |
| tower_slot |  |
| grocer |  |
| trade |  |
| blacksmith |  |
| belong | 7 |

### map_obj #61

| campo | valor |
|---|---|
| mo_id | 134 |
| mo_type | 3 |
| name | Cotys Village |
| name_cn | 科提斯村 |
| def_prosp | 390 |
| max_prosp | 800 |
| def_defence | 80 |
| max_defence | 200 |
| tower_slot |  |
| grocer |  |
| trade |  |
| blacksmith |  |
| belong | 66 |

### map_obj #62

| campo | valor |
|---|---|
| mo_id | 135 |
| mo_type | 3 |
| name | Adela Village |
| name_cn | 阿德拉村 |
| def_prosp | 340 |
| max_prosp | 800 |
| def_defence | 80 |
| max_defence | 200 |
| tower_slot |  |
| grocer |  |
| trade |  |
| blacksmith |  |
| belong | 63 |

### map_obj #63

| campo | valor |
|---|---|
| mo_id | 136 |
| mo_type | 3 |
| name | Marshall Village |
| name_cn | 马绍尔村 |
| def_prosp | 450 |
| max_prosp | 800 |
| def_defence | 80 |
| max_defence | 200 |
| tower_slot |  |
| grocer |  |
| trade |  |
| blacksmith |  |
| belong | 67 |

### map_obj #64

| campo | valor |
|---|---|
| mo_id | 201 |
| mo_type | 4 |
| name | Abbey of Saint-martin |
| name_cn | 圣马丁修道院 |
| def_prosp | 0 |
| max_prosp | 0 |
| def_defence | 0 |
| max_defence | 0 |
| tower_slot |  |
| grocer |  |
| trade |  |
| blacksmith |  |
| belong |  |

### map_obj #65

| campo | valor |
|---|---|
| mo_id | 202 |
| mo_type | 4 |
| name | Abbey of Morpheus |
| name_cn | 马菲斯修道院 |
| def_prosp | 0 |
| max_prosp | 0 |
| def_defence | 0 |
| max_defence | 0 |
| tower_slot |  |
| grocer |  |
| trade |  |
| blacksmith |  |
| belong |  |

### map_obj #66

| campo | valor |
|---|---|
| mo_id | 203 |
| mo_type | 4 |
| name | Abbey of Reddell |
| name_cn | 德雷尔修道院 |
| def_prosp | 0 |
| max_prosp | 0 |
| def_defence | 0 |
| max_defence | 0 |
| tower_slot |  |
| grocer |  |
| trade |  |
| blacksmith |  |
| belong |  |

### map_obj #67

| campo | valor |
|---|---|
| mo_id | 204 |
| mo_type | 4 |
| name | Abbey of Edmund |
| name_cn | 埃蒙修道院 |
| def_prosp | 0 |
| max_prosp | 0 |
| def_defence | 0 |
| max_defence | 0 |
| tower_slot |  |
| grocer |  |
| trade |  |
| blacksmith |  |
| belong |  |

### map_obj #68

| campo | valor |
|---|---|
| mo_id | 221 |
| mo_type | 5 |
| name | Charlie's Farm |
| name_cn | 理查农场 |
| def_prosp | 300 |
| max_prosp | 500 |
| def_defence | 100 |
| max_defence | 100 |
| tower_slot |  |
| grocer |  |
| trade |  |
| blacksmith |  |
| belong |  |

### map_obj #69

| campo | valor |
|---|---|
| mo_id | 222 |
| mo_type | 5 |
| name | Denis's Farm |
| name_cn | 丹尼斯农场 |
| def_prosp | 420 |
| max_prosp | 500 |
| def_defence | 100 |
| max_defence | 100 |
| tower_slot |  |
| grocer |  |
| trade |  |
| blacksmith |  |
| belong |  |

### map_obj #70

| campo | valor |
|---|---|
| mo_id | 223 |
| mo_type | 5 |
| name | Davis's Farm |
| name_cn | 戴维斯农场 |
| def_prosp | 390 |
| max_prosp | 500 |
| def_defence | 100 |
| max_defence | 100 |
| tower_slot |  |
| grocer |  |
| trade |  |
| blacksmith |  |
| belong |  |

### map_obj #71

| campo | valor |
|---|---|
| mo_id | 224 |
| mo_type | 5 |
| name | Baker's Farm |
| name_cn | 贝克利农场 |
| def_prosp | 490 |
| max_prosp | 500 |
| def_defence | 100 |
| max_defence | 100 |
| tower_slot |  |
| grocer |  |
| trade |  |
| blacksmith |  |
| belong |  |

### map_obj #72

| campo | valor |
|---|---|
| mo_id | 225 |
| mo_type | 5 |
| name | Frank's Farm |
| name_cn | 法兰农场 |
| def_prosp | 440 |
| max_prosp | 500 |
| def_defence | 100 |
| max_defence | 100 |
| tower_slot |  |
| grocer |  |
| trade |  |
| blacksmith |  |
| belong |  |

### map_obj #73

| campo | valor |
|---|---|
| mo_id | 241 |
| mo_type | 6 |
| name | Smithy |
| name_cn | 铁匠铺 |
| def_prosp | 0 |
| max_prosp | 0 |
| def_defence | 0 |
| max_defence | 0 |
| tower_slot |  |
| grocer |  |
| trade |  |
| blacksmith | 60.0:100,1,1,1,60;50.0:101,1,1,1,60;40.0:102,1,1,1,60;30.0:103,1,1,1,60;60.0:200,1,1,1,60;50.0:201,1,1,1,60;40.0:202,1,1,1,60;60.0:300,1,1,1,60;50.0:301,1,1,1,60;40.0:302,1,1,1,60;60.0:400,1,1,1,60;50.0:401,1,1,1,60;60.0:500,1,1,1,60;50.0:501,1,1,1,60;30.0:502,1,1,1,60;60.0:600,1,1,1,60;50.0:601,1,1,1,60;40.0:602,1,1,1,60;30.0:603,1,1,1,60;60.0:700,1,1,1,60;50.0:701,1,1,1,60;40.0:702,1,1,1,60;30.0:703,1,1,1,60;60.0:900,1,1,1,60;50.0:901,1,1,1,60;40.0:902,1,1,1,60;30.0:903,s1,1,1,60;30.0:904,1,1,1,60;30.0:905,1,1,1,60;60.0:1000,1,1,1,60;50.0:1001,1,1,1,60;40.0:1002,1,1,1,60;30.0:1003,1,1,1,60;30.0:1004,1,1,1,60;30.0:1005,1,1,1,60;60.0:1100,1,1,1,60;50.0:1101,1,1,1,60;30.0:1102,1,1,1,60;50.0:906,1,1,1,60;50.0:907,1,1,1,60 |
| belong |  |

### map_obj #74

| campo | valor |
|---|---|
| mo_id | 242 |
| mo_type | 6 |
| name | Smithy |
| name_cn | 铁匠铺 |
| def_prosp | 0 |
| max_prosp | 0 |
| def_defence | 0 |
| max_defence | 0 |
| tower_slot |  |
| grocer |  |
| trade |  |
| blacksmith | 60.0:100,1,1,1,60;50.0:101,1,1,1,60;40.0:102,1,1,1,60;30.0:103,1,1,1,60;60.0:200,1,1,1,60;50.0:201,1,1,1,60;40.0:202,1,1,1,60;60.0:300,1,1,1,60;50.0:301,1,1,1,60;40.0:302,1,1,1,60;60.0:400,1,1,1,60;50.0:401,1,1,1,60;60.0:500,1,1,1,60;50.0:501,1,1,1,60;30.0:502,1,1,1,60;60.0:600,1,1,1,60;50.0:601,1,1,1,60;40.0:602,1,1,1,60;30.0:603,1,1,1,60;60.0:700,1,1,1,60;50.0:701,1,1,1,60;40.0:702,1,1,1,60;30.0:703,1,1,1,60;60.0:900,1,1,1,60;50.0:901,1,1,1,60;40.0:902,1,1,1,60;30.0:903,1,1,1,60;30.0:904,1,1,1,60;30.0:905,1,1,1,60;60.0:1000,1,1,1,60;50.0:1001,1,1,1,60;40.0:1002,1,1,1,60;30.0:1003,1,1,1,60;30.0:1004,1,1,1,60;30.0:1005,1,1,1,60;60.0:1100,1,1,1,60;50.0:1101,1,1,1,60;30.0:1102,1,1,1,60;50.0:906,1,1,1,60;50.0:907,1,1,1,60 |
| belong |  |

### map_obj #75

| campo | valor |
|---|---|
| mo_id | 243 |
| mo_type | 6 |
| name | Smithy |
| name_cn | 铁匠铺 |
| def_prosp | 0 |
| max_prosp | 0 |
| def_defence | 0 |
| max_defence | 0 |
| tower_slot |  |
| grocer |  |
| trade |  |
| blacksmith | 60.0:100,1,1,1,60;50.0:101,1,1,1,60;40.0:102,1,1,1,60;30.0:103,1,1,1,60;60.0:200,1,1,1,60;50.0:201,1,1,1,60;40.0:202,1,1,1,60;60.0:300,1,1,1,60;50.0:301,1,1,1,60;40.0:302,1,1,1,60;60.0:400,1,1,1,60;50.0:401,1,1,1,60;60.0:500,1,1,1,60;50.0:501,1,1,1,60;30.0:502,1,1,1,60;60.0:600,1,1,1,60;50.0:601,1,1,1,60;40.0:602,1,1,1,60;30.0:603,1,1,1,60;60.0:700,1,1,1,60;50.0:701,1,1,1,60;40.0:702,1,1,1,60;30.0:703,1,1,1,60;60.0:900,1,1,1,60;60.0:901,1,1,1,60;60.0:902,1,1,1,60;60.0:903,1,1,1,60;60.0:904,1,1,1,60;60.0:905,1,1,1,60;60.0:1000,1,1,1,60;50.0:1001,1,1,1,60;40.0:1002,1,1,1,60;30.0:1003,1,1,1,60;30.0:1004,1,1,1,60;30.0:1005,1,1,1,60;60.0:1100,1,1,1,60;50.0:1101,1,1,1,60;30.0:1102,1,1,1,60;50.0:906,1,1,1,60;50.0:907,1,1,1,60 |
| belong |  |

### map_obj #76

| campo | valor |
|---|---|
| mo_id | 261 |
| mo_type | 7 |
| name | Ranch |
| name_cn | 牧场 |
| def_prosp | 0 |
| max_prosp | 0 |
| def_defence | 0 |
| max_defence | 0 |
| tower_slot |  |
| grocer | 100.0:800,1,1,1,60;100.0:800,1,1,1,60;100.0:800,1,1,1,60;100.0:801,1,1,1,60;50.0:801,1,1,1,60;50.0:801,1,1,1,60;10.0:803,1,1,1,60 |
| trade |  |
| blacksmith |  |
| belong |  |

### map_obj #77

| campo | valor |
|---|---|
| mo_id | 262 |
| mo_type | 7 |
| name | Ranch |
| name_cn | 牧场 |
| def_prosp | 0 |
| max_prosp | 0 |
| def_defence | 0 |
| max_defence | 0 |
| tower_slot |  |
| grocer | 100.0:800,1,1,1,60;100.0:800,1,1,1,60;100.0:800,1,1,1,60;100.0:801,1,1,1,60;50.0:801,1,1,1,60;50.0:801,1,1,1,60;10.0:803,1,1,1,60 |
| trade |  |
| blacksmith |  |
| belong |  |

### map_obj #78

| campo | valor |
|---|---|
| mo_id | 263 |
| mo_type | 7 |
| name | Ranch |
| name_cn | 牧场 |
| def_prosp | 0 |
| max_prosp | 0 |
| def_defence | 0 |
| max_defence | 0 |
| tower_slot |  |
| grocer | 100.0:800,1,1,1,60;100.0:800,1,1,1,60;100.0:800,1,1,1,60;100.0:801,1,1,1,60;50.0:801,1,1,1,60;50.0:801,1,1,1,60;10.0:803,1,1,1,60 |
| trade |  |
| blacksmith |  |
| belong |  |

### map_obj #79

| campo | valor |
|---|---|
| mo_id | 281 |
| mo_type | 8 |
| name | Badorf Mine |
| name_cn | 贝多夫矿洞 |
| def_prosp | 660 |
| max_prosp | 800 |
| def_defence | 100 |
| max_defence | 100 |
| tower_slot |  |
| grocer |  |
| trade |  |
| blacksmith |  |
| belong |  |

### map_obj #80

| campo | valor |
|---|---|
| mo_id | 282 |
| mo_type | 8 |
| name | Hock Mine |
| name_cn | 霍克矿洞 |
| def_prosp | 620 |
| max_prosp | 800 |
| def_defence | 100 |
| max_defence | 100 |
| tower_slot |  |
| grocer |  |
| trade |  |
| blacksmith |  |
| belong |  |

### map_obj #81

| campo | valor |
|---|---|
| mo_id | 283 |
| mo_type | 8 |
| name | Warloff Mine |
| name_cn | 沃伦夫矿洞 |
| def_prosp | 530 |
| max_prosp | 800 |
| def_defence | 100 |
| max_defence | 100 |
| tower_slot |  |
| grocer |  |
| trade |  |
| blacksmith |  |
| belong |  |

### map_obj #82

| campo | valor |
|---|---|
| mo_id | 284 |
| mo_type | 8 |
| name | Feland Mine |
| name_cn | 费兰矿洞 |
| def_prosp | 650 |
| max_prosp | 800 |
| def_defence | 100 |
| max_defence | 100 |
| tower_slot |  |
| grocer |  |
| trade |  |
| blacksmith |  |
| belong |  |

### map_obj #83

| campo | valor |
|---|---|
| mo_id | 285 |
| mo_type | 8 |
| name | Vallis Mine |
| name_cn | 瓦里斯矿洞 |
| def_prosp | 560 |
| max_prosp | 800 |
| def_defence | 100 |
| max_defence | 100 |
| tower_slot |  |
| grocer |  |
| trade |  |
| blacksmith |  |
| belong |  |

### map_obj #84

| campo | valor |
|---|---|
| mo_id | 286 |
| mo_type | 8 |
| name | Grief Mine |
| name_cn | 格里夫矿洞 |
| def_prosp | 550 |
| max_prosp | 800 |
| def_defence | 100 |
| max_defence | 100 |
| tower_slot |  |
| grocer |  |
| trade |  |
| blacksmith |  |
| belong |  |

### map_obj #85

| campo | valor |
|---|---|
| mo_id | 301 |
| mo_type | 9 |
| name | Thieves' den |
| name_cn | 盗贼巢穴 |
| def_prosp | 300 |
| max_prosp | 300 |
| def_defence | 201 |
| max_defence | 100 |
| tower_slot |  |
| grocer |  |
| trade |  |
| blacksmith |  |
| belong |  |

### map_obj #86

| campo | valor |
|---|---|
| mo_id | 302 |
| mo_type | 9 |
| name | Thieves' den |
| name_cn | 盗贼巢穴 |
| def_prosp | 300 |
| max_prosp | 300 |
| def_defence | 202 |
| max_defence | 100 |
| tower_slot |  |
| grocer |  |
| trade |  |
| blacksmith |  |
| belong |  |

### map_obj #87

| campo | valor |
|---|---|
| mo_id | 303 |
| mo_type | 9 |
| name | Thieves' den |
| name_cn | 盗贼巢穴 |
| def_prosp | 300 |
| max_prosp | 300 |
| def_defence | 203 |
| max_defence | 100 |
| tower_slot |  |
| grocer |  |
| trade |  |
| blacksmith |  |
| belong |  |

### map_obj #88

| campo | valor |
|---|---|
| mo_id | 304 |
| mo_type | 9 |
| name | Thieves' den |
| name_cn | 盗贼巢穴 |
| def_prosp | 300 |
| max_prosp | 300 |
| def_defence | 204 |
| max_defence | 100 |
| tower_slot |  |
| grocer |  |
| trade |  |
| blacksmith |  |
| belong |  |

