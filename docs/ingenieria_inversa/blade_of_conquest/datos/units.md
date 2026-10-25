
> **Nota de preservación (2026-10-25):** estas tablas se generaron parseando los XML
> `assets/datas/*.dat` y `game_maps/*.tmx` del APK de Blade of Conquest v1.0.2
> (com.wmstudio.games.boc, desarrollador 田坤/Kevin_Tien86, juego abandonado retirado de
> Google Play en 2020). Se publican como material de análisis y referencia de diseño para
> el proyecto Valcoria: son tablas de datos y cifras reformateadas, no assets del juego.
> El APK original y la descompilación completa de Ghidra (5.750 funciones en `findings/decomp/`)
> se conservan en el espacio local del proyecto (`/home/z/my-project/rea/blade_of_conquest/`).
# UNIDADES/TROPAS — tabla completa

Fuente: `assets/datas/units.dat` (XML en claro). 
Entidades: `unit` ×23


## `unit` — 23 registros

### unit #1

| campo | valor |
|---|---|
| unit_id | 1 |
| unit_name | Farmer |
| unit_name_cn | 农兵 |
| model | 3 |
| u_face | uf_farmer1.png |
| main_class | 2 |
| weapon | 0 |
| skills |  |
| pre_unit | 0 |
| unit_level | 0 |
| max_level | 10 |
| r_level | 0 |
| hire_price | 10 |
| up_price | 1 |
| att_int | 2.8 |
| ratt_int | 0 |
| ratt_eff | eft_arraw1_ |
| base_stat | mhp,260\|atk,40\|def,4\|cri,30\|mvspd,50\|atspd,10 |
| growth | mhp,400\|atk,100\|def,40\|cri,100\|mvspd,50\|atspd,40 |
| drops | 100.0:1,1,3,0,0;100.0:10,1,2,0,0 |
| exp | 60 |

### unit #2

| campo | valor |
|---|---|
| unit_id | 10 |
| unit_name | Swordsman |
| unit_name_cn | 剑士 |
| model | 10 |
| u_face | uf_footman1.png |
| main_class | 2 |
| weapon | 0 |
| skills |  |
| pre_unit | 1 |
| unit_level | 1 |
| max_level | 15 |
| r_level | 5 |
| hire_price | 80 |
| up_price | 40 |
| att_int | 2.5 |
| ratt_int | 0 |
| ratt_eff | eft_arraw1_ |
| base_stat | mhp,280\|atk,42\|def,6\|cri,50\|mvspd,50\|atspd,20 |
| growth | mhp,500\|atk,110\|def,50\|cri,150\|mvspd,50\|atspd,50 |
| drops | 100.0:1,5,10,0,0;100.0:10,2,4,0,0 |
| exp | 100 |

### unit #3

| campo | valor |
|---|---|
| unit_id | 11 |
| unit_name | Senior Swordsman |
| unit_name_cn | 资深剑士 |
| model | 11 |
| u_face | uf_footman2.png |
| main_class | 2 |
| weapon | 0 |
| skills |  |
| pre_unit | 10 |
| unit_level | 2 |
| max_level | 25 |
| r_level | 15 |
| hire_price | 160 |
| up_price | 80 |
| att_int | 2.5 |
| ratt_int | 0 |
| ratt_eff | eft_arraw1_ |
| base_stat | mhp,320\|atk,45\|def,8\|cri,60\|mvspd,55\|atspd,30 |
| growth | mhp,550\|atk,120\|def,55\|cri,150\|mvspd,50\|atspd,50 |
| drops | 100.0:1,10,20,0,0;100.0:11,2,4,0,0 |
| exp | 140 |

### unit #4

| campo | valor |
|---|---|
| unit_id | 12 |
| unit_name | Elite Swordsman |
| unit_name_cn | 精锐剑士 |
| model | 12 |
| u_face | uf_footman3.png |
| main_class | 2 |
| weapon | 0 |
| skills |  |
| pre_unit | 11 |
| unit_level | 3 |
| max_level | 35 |
| r_level | 25 |
| hire_price | 320 |
| up_price | 160 |
| att_int | 2.5 |
| ratt_int | 0 |
| ratt_eff | eft_arraw1_ |
| base_stat | mhp,360\|atk,50\|def,10\|cri,70\|mvspd,60\|atspd,35 |
| growth | mhp,600\|atk,130\|def,60\|cri,150\|mvspd,50\|atspd,50 |
| drops | 100.0:1,20,30,0,0;100.0:12,2,4,0,0;1.0:5 |
| exp | 180 |

### unit #5

| campo | valor |
|---|---|
| unit_id | 13 |
| unit_name | Royal Warriors |
| unit_name_cn | 皇家勇士 |
| model | 13 |
| u_face | uf_footman4.png |
| main_class | 2 |
| weapon | 0 |
| skills |  |
| pre_unit | 12 |
| unit_level | 4 |
| max_level | 40 |
| r_level | 35 |
| hire_price | 480 |
| up_price | 240 |
| att_int | 2.5 |
| ratt_int | 0 |
| ratt_eff | eft_arraw1_ |
| base_stat | mhp,400\|atk,55\|def,13\|cri,80\|mvspd,65\|atspd,40 |
| growth | mhp,650\|atk,140\|def,70\|cri,150\|mvspd,50\|atspd,50 |
| drops | 100.0:1,30,40,0,0;100.0:13,2,4,0,0;1.0:5 |
| exp | 220 |

### unit #6

| campo | valor |
|---|---|
| unit_id | 20 |
| unit_name | Pikeman |
| unit_name_cn | 长枪兵 |
| model | 20 |
| u_face | uf_spearman1.png |
| main_class | 2 |
| weapon | 3 |
| skills |  |
| pre_unit | 1 |
| unit_level | 1 |
| max_level | 15 |
| r_level | 5 |
| hire_price | 80 |
| up_price | 40 |
| att_int | 2.8 |
| ratt_int | 0 |
| ratt_eff | eft_arraw1_ |
| base_stat | mhp,280\|atk,50\|def,3\|cri,50\|mvspd,50\|atspd,20 |
| growth | mhp,500\|atk,130\|def,40\|cri,150\|mvspd,50\|atspd,50 |
| drops | 100.0:1,5,10,0,0;100.0:10,2,4,0,0 |
| exp | 100 |

### unit #7

| campo | valor |
|---|---|
| unit_id | 21 |
| unit_name | Senior Pikeman |
| unit_name_cn | 资深长枪兵 |
| model | 21 |
| u_face | uf_spearman2.png |
| main_class | 2 |
| weapon | 3 |
| skills |  |
| pre_unit | 20 |
| unit_level | 2 |
| max_level | 25 |
| r_level | 15 |
| hire_price | 160 |
| up_price | 80 |
| att_int | 2.8 |
| ratt_int | 0 |
| ratt_eff | eft_arraw1_ |
| base_stat | mhp,300\|atk,55\|def,5\|cri,60\|mvspd,55\|atspd,25 |
| growth | mhp,550\|atk,140\|def,40\|cri,150\|mvspd,50\|atspd,50 |
| drops | 100.0:1,10,20,0,0;100.0:11,2,4,0,0 |
| exp | 140 |

### unit #8

| campo | valor |
|---|---|
| unit_id | 22 |
| unit_name | Elite Pikeman |
| unit_name_cn | 精锐长枪兵 |
| model | 22 |
| u_face | uf_spearman3.png |
| main_class | 2 |
| weapon | 3 |
| skills |  |
| pre_unit | 21 |
| unit_level | 3 |
| max_level | 35 |
| r_level | 25 |
| hire_price | 320 |
| up_price | 160 |
| att_int | 2.8 |
| ratt_int | 0 |
| ratt_eff | eft_arraw1_ |
| base_stat | mhp,320\|atk,60\|def,7\|cri,70\|mvspd,60\|atspd,30 |
| growth | mhp,600\|atk,150\|def,40\|cri,150\|mvspd,50\|atspd,50 |
| drops | 100.0:1,20,30,0,0;100.0:12,2,4,0,0;1.0:5 |
| exp | 180 |

### unit #9

| campo | valor |
|---|---|
| unit_id | 23 |
| unit_name | Royal Guard |
| unit_name_cn | 皇家卫士 |
| model | 23 |
| u_face | uf_spearman4.png |
| main_class | 2 |
| weapon | 3 |
| skills |  |
| pre_unit | 22 |
| unit_level | 4 |
| max_level | 40 |
| r_level | 35 |
| hire_price | 480 |
| up_price | 240 |
| att_int | 2.8 |
| ratt_int | 0 |
| ratt_eff | eft_arraw1_ |
| base_stat | mhp,340\|atk,65\|def,10\|cri,80\|mvspd,65\|atspd,35 |
| growth | mhp,600\|atk,160\|def,40\|cri,150\|mvspd,50\|atspd,50 |
| drops | 100.0:1,30,40,0,0;100.0:10,1,5,0,0;1.0:5 |
| exp | 220 |

### unit #10

| campo | valor |
|---|---|
| unit_id | 30 |
| unit_name | Trainee Archer |
| unit_name_cn | 见习射手 |
| model | 30 |
| u_face | uf_archerman1.png |
| main_class | 4 |
| weapon | 5 |
| skills |  |
| pre_unit | 1 |
| unit_level | 1 |
| max_level | 15 |
| r_level | 5 |
| hire_price | 100 |
| up_price | 50 |
| att_int | 2.5 |
| ratt_int | 4.0 |
| ratt_eff | eft_arraw1_ |
| base_stat | mhp,260\|atk,22\|ratk,35\|def,3\|cri,50\|mvspd,50\|atspd,20\|stspd,20\|strag,600\|stdev,20 |
| growth | mhp,400\|atk,80\|ratk,65\|def,30\|cri,200\|mvspd,50\|atspd,50\|stspd,80\|strag,500\|stdev,100 |
| drops | 100.0:1,5,10,0,0;100.0:10,2,4,0,0 |
| exp | 120 |

### unit #11

| campo | valor |
|---|---|
| unit_id | 31 |
| unit_name | Archer |
| unit_name_cn | 弓箭手 |
| model | 31 |
| u_face | uf_archerman2.png |
| main_class | 4 |
| weapon | 5 |
| skills |  |
| pre_unit | 30 |
| unit_level | 2 |
| max_level | 25 |
| r_level | 15 |
| hire_price | 180 |
| up_price | 90 |
| att_int | 2.5 |
| ratt_int | 4.0 |
| ratt_eff | eft_arraw1_ |
| base_stat | mhp,280\|atk,26\|ratk,40\|def,5\|cri,60\|mvspd,55\|atspd,30\|stspd,22\|strag,650\|stdev,35 |
| growth | mhp,450\|atk,90\|ratk,70\|def,30\|cri,200\|mvspd,50\|atspd,50\|stspd,90\|strag,500\|stdev,100 |
| drops | 100.0:1,10,20,0,0;100.0:11,2,4,0,0 |
| exp | 160 |

### unit #12

| campo | valor |
|---|---|
| unit_id | 32 |
| unit_name | Sniper |
| unit_name_cn | 狙击手 |
| model | 32 |
| u_face | uf_archerman3.png |
| main_class | 4 |
| weapon | 5 |
| skills |  |
| pre_unit | 31 |
| unit_level | 3 |
| max_level | 35 |
| r_level | 25 |
| hire_price | 320 |
| up_price | 180 |
| att_int | 2.5 |
| ratt_int | 4.0 |
| ratt_eff | eft_arraw1_ |
| base_stat | mhp,300\|atk,30\|ratk,45\|def,7\|cri,70\|mvspd,60\|atspd,40\|stspd,24\|strag,700\|stdev,50 |
| growth | mhp,500\|atk,100\|ratk,75\|def,30\|cri,200\|mvspd,50\|atspd,50\|stspd,100\|strag,500\|stdev,100 |
| drops | 100.0:1,20,30,0,0;100.0:12,2,4,0,0;1.0:5 |
| exp | 200 |

### unit #13

| campo | valor |
|---|---|
| unit_id | 33 |
| unit_name | Marksman |
| unit_name_cn | 神射手 |
| model | 33 |
| u_face | uf_archerman4.png |
| main_class | 4 |
| weapon | 5 |
| skills |  |
| pre_unit | 32 |
| unit_level | 4 |
| max_level | 40 |
| r_level | 35 |
| hire_price | 480 |
| up_price | 220 |
| att_int | 2.5 |
| ratt_int | 4.0 |
| ratt_eff | eft_arraw1_ |
| base_stat | mhp,320\|atk,35\|ratk,50\|def,9\|cri,80\|mvspd,65\|atspd,50\|stspd,26\|strag,750\|stdev,50 |
| growth | mhp,550\|atk,110\|ratk,80\|def,30\|cri,200\|mvspd,50\|atspd,50\|stspd,110\|strag,500\|stdev,100 |
| drops | 100.0:1,30,40,0,0;100.0:10,1,5,0,0;1.0:5 |
| exp | 240 |

### unit #14

| campo | valor |
|---|---|
| unit_id | 40 |
| unit_name | Light Cavalry |
| unit_name_cn | 轻骑兵 |
| model | 40 |
| u_face | uf_calvary_sword_1.png |
| main_class | 3 |
| weapon | 3 |
| skills |  |
| pre_unit | 10 |
| unit_level | 2 |
| max_level | 25 |
| r_level | 15 |
| hire_price | 240 |
| up_price | 120 |
| att_int | 2.5 |
| ratt_int | 0 |
| ratt_eff | eft_arraw1_ |
| base_stat | mhp,500\|atk,50\|def,8\|cri,50\|mvspd,90\|atspd,20 |
| growth | mhp,600\|atk,110\|def,40\|cri,200\|mvspd,50\|atspd,50 |
| drops | 100.0:1,10,20,0,0;100.0:11,2,4,0,0 |
| exp | 140 |

### unit #15

| campo | valor |
|---|---|
| unit_id | 41 |
| unit_name | Elite Cavalry |
| unit_name_cn | 精锐骑兵 |
| model | 41 |
| u_face | uf_calvary_sword_2.png |
| main_class | 3 |
| weapon | 3 |
| skills |  |
| pre_unit | 40 |
| unit_level | 3 |
| max_level | 35 |
| r_level | 25 |
| hire_price | 400 |
| up_price | 200 |
| att_int | 2.5 |
| ratt_int | 0 |
| ratt_eff | eft_arraw1_ |
| base_stat | mhp,650\|atk,60\|def,11\|cri,70\|mvspd,85\|atspd,30 |
| growth | mhp,650\|atk,120\|def,50\|cri,200\|mvspd,50\|atspd,50 |
| drops | 100.0:1,20,30,0,0;100.0:12,2,4,0,0;1.0:5 |
| exp | 200 |

### unit #16

| campo | valor |
|---|---|
| unit_id | 42 |
| unit_name | Royal Cavalry |
| unit_name_cn | 皇家剑骑士 |
| model | 42 |
| u_face | uf_calvary_sword_3.png |
| main_class | 3 |
| weapon | 3 |
| skills |  |
| pre_unit | 41 |
| unit_level | 4 |
| max_level | 40 |
| r_level | 35 |
| hire_price | 600 |
| up_price | 300 |
| att_int | 2.5 |
| ratt_int | 0 |
| ratt_eff | eft_arraw1_ |
| base_stat | mhp,700\|atk,70\|def,15\|cri,100\|mvspd,80\|atspd,40 |
| growth | mhp,700\|atk,130\|def,60\|cri,200\|mvspd,50\|atspd,50 |
| drops | 100.0:1,30,40,0,0;100.0:13,2,4,0,0;1.0:5 |
| exp | 240 |

### unit #17

| campo | valor |
|---|---|
| unit_id | 50 |
| unit_name | Lance Cavalry |
| unit_name_cn | 轻骑枪兵 |
| model | 50 |
| u_face | uf_calvary_spear_1.png |
| main_class | 3 |
| weapon | 3 |
| skills |  |
| pre_unit | 20 |
| unit_level | 2 |
| max_level | 25 |
| r_level | 15 |
| hire_price | 240 |
| up_price | 120 |
| att_int | 2.8 |
| ratt_int | 0 |
| ratt_eff | eft_arraw1_ |
| base_stat | mhp,420\|atk,60\|def,5\|cri,60\|mvspd,90\|atspd,20 |
| growth | mhp,500\|atk,120\|def,40\|cri,200\|mvspd,50\|atspd,50 |
| drops | 100.0:1,10,20,0,0;100.0:11,2,4,0,0 |
| exp | 140 |

### unit #18

| campo | valor |
|---|---|
| unit_id | 51 |
| unit_name | Elite Lance Cavalry |
| unit_name_cn | 精锐骑枪兵 |
| model | 51 |
| u_face | uf_calvary_spear_2.png |
| main_class | 3 |
| weapon | 3 |
| skills |  |
| pre_unit | 50 |
| unit_level | 3 |
| max_level | 35 |
| r_level | 25 |
| hire_price | 400 |
| up_price | 200 |
| att_int | 2.8 |
| ratt_int | 0 |
| ratt_eff | eft_arraw1_ |
| base_stat | mhp,500\|atk,70\|def,8\|cri,90\|mvspd,85\|atspd,30 |
| growth | mhp,550\|atk,130\|def,40\|cri,200\|mvspd,50\|atspd,50 |
| drops | 100.0:1,20,30,0,0;100.0:12,2,4,0,0;1.0:5 |
| exp | 200 |

### unit #19

| campo | valor |
|---|---|
| unit_id | 52 |
| unit_name | Royal Lance Cavalry |
| unit_name_cn | 皇家枪骑士 |
| model | 52 |
| u_face | uf_calvary_spear_3.png |
| main_class | 3 |
| weapon | 3 |
| skills |  |
| pre_unit | 51 |
| unit_level | 4 |
| max_level | 40 |
| r_level | 35 |
| hire_price | 600 |
| up_price | 300 |
| att_int | 2.8 |
| ratt_int | 0 |
| ratt_eff | eft_arraw1_ |
| base_stat | mhp,600\|atk,80\|def,12\|cri,120\|mvspd,80\|atspd,40 |
| growth | mhp,600\|atk,140\|def,40\|cri,200\|mvspd,50\|atspd,50 |
| drops | 100.0:1,30,40,0,0;100.0:13,2,4,0,0;1.0:5 |
| exp | 240 |

### unit #20

| campo | valor |
|---|---|
| unit_id | 60 |
| unit_name | Monk |
| unit_name_cn | 修道士 |
| model | 60 |
| u_face | uf_monk1.png |
| main_class | 2 |
| weapon | 1 |
| skills |  |
| pre_unit | 0 |
| unit_level | 1 |
| max_level | 20 |
| r_level | 10 |
| hire_price | 200 |
| up_price | 100 |
| att_int | 2.8 |
| ratt_int | 0 |
| ratt_eff | eft_arraw1_ |
| base_stat | mhp,240\|mmp,80\|atk,30\|def,4\|cri,50\|mvspd,50\|atspd,20\|sdr,3 |
| growth | mhp,500\|mmp,200\|atk,100\|def,50\|cri,100\|mvspd,50\|atspd,50\|sdr,10 |
| drops | 100.0:1,5,10,0,0;100.0:11,2,4,0,0 |
| exp | 160 |

### unit #21

| campo | valor |
|---|---|
| unit_id | 61 |
| unit_name | Crusader |
| unit_name_cn | 圣教兵 |
| model | 61 |
| u_face | uf_monk2.png |
| main_class | 2 |
| weapon | 1 |
| skills |  |
| pre_unit | 60 |
| unit_level | 2 |
| max_level | 30 |
| r_level | 20 |
| hire_price | 600 |
| up_price | 600 |
| att_int | 2.8 |
| ratt_int | 0 |
| ratt_eff | eft_arraw1_ |
| base_stat | mhp,280\|mmp,100\|atk,35\|def,6\|cri,80\|mvspd,55\|atspd,25\|sdr,4 |
| growth | mhp,500\|mmp,200\|atk,100\|def,50\|cri,100\|mvspd,50\|atspd,50\|sdr,10 |
| drops | 100.0:1,15,25,0,0;100.0:12,2,4,0,0;1.0:5 |
| exp | 200 |

### unit #22

| campo | valor |
|---|---|
| unit_id | 62 |
| unit_name | Holy Warrior |
| unit_name_cn | 圣战士 |
| model | 62 |
| u_face | uf_monk3.png |
| main_class | 2 |
| weapon | 1 |
| skills |  |
| pre_unit | 61 |
| unit_level | 3 |
| max_level | 40 |
| r_level | 30 |
| hire_price | 1000 |
| up_price | 1000 |
| att_int | 2.8 |
| ratt_int | 0 |
| ratt_eff | eft_arraw1_ |
| base_stat | mhp,320\|mmp,120\|atk,40\|def,8\|cri,100\|mvspd,60\|atspd,30\|sdr,5 |
| growth | mhp,500\|mmp,200\|atk,100\|def,50\|cri,100\|mvspd,50\|atspd,50\|sdr,10 |
| drops | 100.0:1,20,40,0,0;100.0:13,2,4,0,0;2.0:5 |
| exp | 240 |

### unit #23

| campo | valor |
|---|---|
| unit_id | 101 |
| unit_name | Skeleton Soldior |
| unit_name_cn | 骷髅士兵 |
| model | 101 |
| u_face | uf_skull1.png |
| main_class | 2 |
| weapon | 0 |
| skills |  |
| pre_unit | 0 |
| unit_level | 0 |
| max_level | 40 |
| r_level | 0 |
| hire_price | 10 |
| up_price | 1 |
| att_int | 2.6 |
| ratt_int | 0 |
| ratt_eff | eft_arraw1_ |
| base_stat | mhp,360\|atk,60\|def,5\|cri,50\|mvspd,50\|atspd,20\|mdef,20 |
| growth | mhp,800\|atk,110\|def,40\|cri,150\|mvspd,50\|atspd,50\|mdef,100 |
| drops |  |
| exp | 50 |

