
> **Nota de preservación (2026-10-25):** estas tablas se generaron parseando los XML
> `assets/datas/*.dat` y `game_maps/*.tmx` del APK de Blade of Conquest v1.0.2
> (com.wmstudio.games.boc, desarrollador 田坤/Kevin_Tien86, juego abandonado retirado de
> Google Play en 2020). Se publican como material de análisis y referencia de diseño para
> el proyecto Valcoria: son tablas de datos y cifras reformateadas, no assets del juego.
> El APK original y la descompilación completa de Ghidra (5.750 funciones en `findings/decomp/`)
> se conservan en el espacio local del proyecto (`/home/z/my-project/rea/blade_of_conquest/`).
# MODELOS 3D (rango de ataque, radios)

Fuente: `assets/datas/md.dat` (XML en claro). 
Entidades: `model_info` ×25


## `model_info` — 25 registros

### model_info #1

| campo | valor |
|---|---|
| model_id | 1 |
| model_name | general1 |
| model_file | HeroWalk1 |
| body_radius | 40 |
| body_height | 120 |
| att_range | 40 |
| skins |  |
| att_acts | att_1,att_2 |

### model_info #2

| campo | valor |
|---|---|
| model_id | 2 |
| model_name | general2 |
| model_file | HeroRide1 |
| body_radius | 45 |
| body_height | 140 |
| att_range | 50 |
| skins |  |
| att_acts | att_1,att_2 |

### model_info #3

| campo | valor |
|---|---|
| model_id | 3 |
| model_name | farmer |
| model_file | SwordMan2 |
| body_radius | 25 |
| body_height | 100 |
| att_range | 30 |
| skins | weapon,md_farmer1_pitchfork_0.png;lleg,md_farmer1_lleg_0.png;rleg,md_farmer1_rleg_0.png;larm,md_farmer1_larm_0.png;body_d,md_farmer1_dbody_0.png;body_u,md_farmer1_ubody_0.png;h_color,md_swordman2_ubody_c.png;head,md_farmer1_head_0.png;blink,md_farmer1_head_1.png;color,md_farmer1_head_c.png;rarm,md_farmer1_rarm_0.png;weapon,md_farmer1_pitchfork_0.png |
| att_acts | att_1,att_2 |

### model_info #4

| campo | valor |
|---|---|
| model_id | 10 |
| model_name | sword man 1 |
| model_file | SwordMan2 |
| body_radius | 25 |
| body_height | 100 |
| att_range | 30 |
| skins | weapon,md_swordman1_sword_0.png;lleg,md_swordman1_lleg_0.png;rleg,md_swordman1_rleg_0.png;larm,md_swordman1_larm_0.png;body_d,md_swordman1_dbody_0.png;body_u,md_swordman1_ubody_0.png;h_color,md_swordman1_ubody_c.png;head,md_swordman1_head_0.png;blink,md_swordman1_head_1.png;color,md_swordman1_head_c.png;rarm,md_swordman1_rarm_0.png;weapon,md_swordman1_pitchfork_0.png |
| att_acts | att_1,att_2 |

### model_info #5

| campo | valor |
|---|---|
| model_id | 11 |
| model_name | sword man 2 |
| model_file | SwordMan2 |
| body_radius | 25 |
| body_height | 100 |
| att_range | 30 |
| skins | weapon,md_swordman2_sword_0.png;lleg,md_swordman2_lleg_0.png;rleg,md_swordman2_rleg_0.png;larm,md_swordman2_larm_0.png;body_d,md_swordman2_dbody_0.png;body_u,md_swordman2_ubody_0.png;h_color,md_swordman2_ubody_c.png;head,md_swordman2_head_0.png;blink,md_swordman2_head_1.png;color,md_swordman2_head_c.png;rarm,md_swordman2_rarm_0.png;weapon,md_swordman2_pitchfork_0.png |
| att_acts | att_1,att_2 |

### model_info #6

| campo | valor |
|---|---|
| model_id | 12 |
| model_name | sword man 3 |
| model_file | SwordMan2 |
| body_radius | 25 |
| body_height | 100 |
| att_range | 30 |
| skins | weapon,md_swordman3_sword_0.png;lleg,md_swordman3_lleg_0.png;rleg,md_swordman3_rleg_0.png;larm,md_swordman3_larm_0.png;body_d,md_swordman3_dbody_0.png;body_u,md_swordman3_ubody_0.png;h_color,md_swordman3_ubody_c.png;head,md_swordman3_head_0.png;blink,md_swordman3_head_1.png;color,md_swordman3_head_c.png;rarm,md_swordman3_rarm_0.png;weapon,md_swordman3_pitchfork_0.png |
| att_acts | att_1,att_2 |

### model_info #7

| campo | valor |
|---|---|
| model_id | 13 |
| model_name | sword man 4 |
| model_file | SwordMan2 |
| body_radius | 25 |
| body_height | 100 |
| att_range | 30 |
| skins | weapon,md_swordman4_sword_0.png;lleg,md_swordman4_lleg_0.png;rleg,md_swordman4_rleg_0.png;larm,md_swordman4_larm_0.png;body_d,md_swordman4_dbody_0.png;body_u,md_swordman4_ubody_0.png;h_color,md_swordman4_ubody_c.png;head,md_swordman4_head_0.png;blink,md_swordman4_head_1.png;color,md_swordman4_head_c.png;rarm,md_swordman4_rarm_0.png;weapon,md_swordman4_pitchfork_0.png |
| att_acts | att_1,att_2 |

### model_info #8

| campo | valor |
|---|---|
| model_id | 20 |
| model_name | spearman1 |
| model_file | SwordMan2 |
| body_radius | 25 |
| body_height | 100 |
| att_range | 50 |
| skins | weapon,md_swordman1_spear_0.png;lleg,md_swordman1_lleg_0.png;rleg,md_swordman1_rleg_0.png;larm,md_swordman1_larm_0.png;body_d,md_swordman1_dbody_0.png;body_u,md_swordman1_ubody_0.png;h_color,md_swordman1_ubody_c.png;head,md_swordman1_head_0.png;blink,md_swordman1_head_1.png;color,md_swordman1_head_c.png;rarm,md_swordman1_rarm_0.png;weapon,md_swordman1_pitchfork_0.png |
| att_acts | att_2 |

### model_info #9

| campo | valor |
|---|---|
| model_id | 21 |
| model_name | spearman2 |
| model_file | SwordMan2 |
| body_radius | 25 |
| body_height | 100 |
| att_range | 30 |
| skins | weapon,md_swordman2_spear_0.png;lleg,md_swordman2_lleg_0.png;rleg,md_swordman2_rleg_0.png;larm,md_swordman2_larm_0.png;body_d,md_swordman2_dbody_0.png;body_u,md_swordman2_ubody_0.png;h_color,md_swordman2_ubody_c.png;head,md_swordman2_head_0.png;blink,md_swordman2_head_1.png;color,md_swordman2_head_c.png;rarm,md_swordman2_rarm_0.png;weapon,md_swordman2_pitchfork_0.png |
| att_acts | att_2 |

### model_info #10

| campo | valor |
|---|---|
| model_id | 22 |
| model_name | spearman3 |
| model_file | SwordMan2 |
| body_radius | 25 |
| body_height | 100 |
| att_range | 50 |
| skins | weapon,md_swordman3_spear_0.png;lleg,md_swordman3_lleg_0.png;rleg,md_swordman3_rleg_0.png;larm,md_swordman3_larm_0.png;body_d,md_swordman3_dbody_0.png;body_u,md_swordman3_ubody_0.png;h_color,md_swordman3_ubody_c.png;head,md_swordman3_head_0.png;blink,md_swordman3_head_1.png;color,md_swordman3_head_c.png;rarm,md_swordman3_rarm_0.png;weapon,md_swordman3_pitchfork_0.png |
| att_acts | att_2 |

### model_info #11

| campo | valor |
|---|---|
| model_id | 23 |
| model_name | spearman4 |
| model_file | SwordMan2 |
| body_radius | 25 |
| body_height | 100 |
| att_range | 50 |
| skins | weapon,md_swordman4_spear_0.png;lleg,md_swordman4_lleg_0.png;rleg,md_swordman4_rleg_0.png;larm,md_swordman4_larm_0.png;body_d,md_swordman4_dbody_0.png;body_u,md_swordman4_ubody_0.png;h_color,md_swordman4_ubody_c.png;head,md_swordman4_head_0.png;blink,md_swordman4_head_1.png;color,md_swordman4_head_c.png;rarm,md_swordman4_rarm_0.png;weapon,md_swordman4_pitchfork_0.png |
| att_acts | att_2 |

### model_info #12

| campo | valor |
|---|---|
| model_id | 30 |
| model_name | archer1 |
| model_file | ArcherMan1 |
| body_radius | 25 |
| body_height | 100 |
| att_range | 30 |
| skins | bow,md_archerman1_bow_0.png;body_u,md_archerman1_bodyup_0.png;body_d,md_archerman1_bodydown_0.png;head,md_archerman1_head_0.png;blink,md_archerman1_head_1.png;color,md_archerman1_head_c.png;larm,md_archerman1_larm_0.png;lleg,md_archerman1_lleg_0.png;rarm,md_archerman1_rarm_0.png;rleg,md_archerman1_rleg_0.png |
| att_acts | att |

### model_info #13

| campo | valor |
|---|---|
| model_id | 31 |
| model_name | archer1 |
| model_file | ArcherMan1 |
| body_radius | 25 |
| body_height | 100 |
| att_range | 30 |
| skins | bow,md_archerman2_bow_0.png;body_u,md_archerman2_bodyup_0.png;body_d,md_archerman2_bodydown_0.png;head,md_archerman2_head_0.png;blink,md_archerman2_head_1.png;color,md_archerman2_head_c.png;larm,md_archerman2_larm_0.png;lleg,md_archerman2_lleg_0.png;rarm,md_archerman2_rarm_0.png;rleg,md_archerman2_rleg_0.png |
| att_acts | att |

### model_info #14

| campo | valor |
|---|---|
| model_id | 32 |
| model_name | archer1 |
| model_file | ArcherMan1 |
| body_radius | 25 |
| body_height | 100 |
| att_range | 30 |
| skins | bow,md_archerman3_bow_0.png;body_u,md_archerman3_bodyup_0.png;body_d,md_archerman3_bodydown_0.png;head,md_archerman3_head_0.png;blink,md_archerman3_head_1.png;color,md_archerman3_head_c.png;larm,md_archerman3_larm_0.png;lleg,md_archerman3_lleg_0.png;rarm,md_archerman3_rarm_0.png;rleg,md_archerman3_rleg_0.png |
| att_acts | att |

### model_info #15

| campo | valor |
|---|---|
| model_id | 33 |
| model_name | archer1 |
| model_file | ArcherMan1 |
| body_radius | 25 |
| body_height | 100 |
| att_range | 30 |
| skins | bow,md_archerman4_bow_0.png;body_u,md_archerman4_bodyup_0.png;body_d,md_archerman4_bodydown_0.png;head,md_archerman4_head_0.png;blink,md_archerman4_head_1.png;color,md_archerman4_head_c.png;larm,md_archerman4_larm_0.png;lleg,md_archerman4_lleg_0.png;rarm,md_archerman4_rarm_0.png;rleg,md_archerman4_rleg_0.png |
| att_acts | att |

### model_info #16

| campo | valor |
|---|---|
| model_id | 40 |
| model_name | cavalry1 |
| model_file | Calvary1 |
| body_radius | 35 |
| body_height | 120 |
| att_range | 40 |
| skins |  |
| att_acts | att_1,att_2 |

### model_info #17

| campo | valor |
|---|---|
| model_id | 41 |
| model_name | cavalry1 |
| model_file | Calvary1 |
| body_radius | 35 |
| body_height | 120 |
| att_range | 40 |
| skins | weapon,md_calvary2_sword_0.png;head,md_calvary2_head_0.png;color,md_calvary2_head_c.png;body_d,md_calvary2_dbody_0.png;body_u,md_calvary2_ubody_0.png;larm,md_calvary2_larm_0.png;rarm1,md_calvary2_rarm1_0.png;rarm2,md_calvary2_rarm2_0.png;rleg,md_calvary2_rleg_0.png;h_bleg1,md_calvary2_h_bleg1_0.png;bleg2,md_calvary2_h_bleg2_0.png;h_body,md_calvary2_h_body_0.png;h_color,md_calvary2_h_body_c_0.png;h_fleg1,md_calvary2_h_fleg1_0.png;h_fleg2,md_calvary2_h_fleg2_0.png;h_head,md_calvary2_h_head_n_0.png;h_neck,md_calvary2_h_neck_0.png;h_tail,md_calvary2_h_tail_0.png |
| att_acts | att_1,att_2 |

### model_info #18

| campo | valor |
|---|---|
| model_id | 42 |
| model_name | cavalry1 |
| model_file | Calvary1 |
| body_radius | 35 |
| body_height | 120 |
| att_range | 40 |
| skins | weapon,md_calvary3_sword_0.png;head,md_calvary3_head_0.png;color,md_calvary3_head_c.png;body_d,md_calvary3_dbody_0.png;body_u,md_calvary3_ubody_0.png;larm,md_calvary3_larm_0.png;rarm1,md_calvary3_rarm1_0.png;rarm2,md_calvary3_rarm2_0.png;rleg,md_calvary3_rleg_0.png;h_bleg1,md_calvary3_h_bleg1_0.png;bleg2,md_calvary3_h_bleg2_0.png;h_body,md_calvary3_h_body_0.png;h_color,md_calvary3_h_body_c_0.png;h_fleg1,md_calvary3_h_fleg1_0.png;h_fleg2,md_calvary3_h_fleg2_0.png;h_head,md_calvary3_h_head_n_0.png;h_neck,md_calvary3_h_neck_0.png;h_tail,md_calvary3_h_tail_0.png |
| att_acts | att_1,att_2 |

### model_info #19

| campo | valor |
|---|---|
| model_id | 50 |
| model_name | cavalry1 |
| model_file | Calvary1 |
| body_radius | 35 |
| body_height | 120 |
| att_range | 60 |
| skins | weapon,md_calvary1_spear_0.png |
| att_acts | att_2 |

### model_info #20

| campo | valor |
|---|---|
| model_id | 51 |
| model_name | cavalry2 |
| model_file | Calvary1 |
| body_radius | 35 |
| body_height | 120 |
| att_range | 40 |
| skins | weapon,md_calvary2_spear_0.png;head,md_calvary2_head_0.png;color,md_calvary2_head_c.png;body_d,md_calvary2_dbody_0.png;body_u,md_calvary2_ubody_0.png;larm,md_calvary2_larm_0.png;rarm1,md_calvary2_rarm1_0.png;rarm2,md_calvary2_rarm2_0.png;rleg,md_calvary2_rleg_0.png;h_bleg1,md_calvary2_h_bleg1_0.png;bleg2,md_calvary2_h_bleg2_0.png;h_body,md_calvary2_h_body_0.png;h_color,md_calvary2_h_body_c_0.png;h_fleg1,md_calvary2_h_fleg1_0.png;h_fleg2,md_calvary2_h_fleg2_0.png;h_head,md_calvary2_h_head_n_0.png;h_neck,md_calvary2_h_neck_0.png;h_tail,md_calvary2_h_tail_0.png |
| att_acts | att_2 |

### model_info #21

| campo | valor |
|---|---|
| model_id | 52 |
| model_name | cavalry3 |
| model_file | Calvary1 |
| body_radius | 35 |
| body_height | 120 |
| att_range | 40 |
| skins | weapon,md_calvary3_spear_0.png;head,md_calvary3_head_0.png;color,md_calvary3_head_c.png;body_d,md_calvary3_dbody_0.png;body_u,md_calvary3_ubody_0.png;larm,md_calvary3_larm_0.png;rarm1,md_calvary3_rarm1_0.png;rarm2,md_calvary3_rarm2_0.png;rleg,md_calvary3_rleg_0.png;h_bleg1,md_calvary3_h_bleg1_0.png;bleg2,md_calvary3_h_bleg2_0.png;h_body,md_calvary3_h_body_0.png;h_color,md_calvary3_h_body_c_0.png;h_fleg1,md_calvary3_h_fleg1_0.png;h_fleg2,md_calvary3_h_fleg2_0.png;h_head,md_calvary3_h_head_n_0.png;h_neck,md_calvary3_h_neck_0.png;h_tail,md_calvary3_h_tail_0.png |
| att_acts | att_2 |

### model_info #22

| campo | valor |
|---|---|
| model_id | 60 |
| model_name | monk1 |
| model_file | Monk1 |
| body_radius | 25 |
| body_height | 100 |
| att_range | 30 |
| skins |  |
| att_acts | att_1 |

### model_info #23

| campo | valor |
|---|---|
| model_id | 61 |
| model_name | monk2 |
| model_file | Monk1 |
| body_radius | 25 |
| body_height | 100 |
| att_range | 30 |
| skins | weapon,md_monk2_weapon_0.png;body_d,md_monk2_dbody_0.png;head,md_monk2_head_0.png;blink,md_monk2_head_1.png;color,md_monk2_head_c.png;larm,md_monk2_larm_0.png;lleg,md_monk2_lleg_0.png;rarm,md_monk2_rarm_0.png;rleg,md_monk2_rleg_0.png;body_u,md_monk2_ubody_0.png |
| att_acts | att_1 |

### model_info #24

| campo | valor |
|---|---|
| model_id | 62 |
| model_name | monk3 |
| model_file | Monk1 |
| body_radius | 25 |
| body_height | 100 |
| att_range | 30 |
| skins | weapon,md_monk3_weapon_0.png;body_d,md_monk3_dbody_0.png;head,md_monk3_head_0.png;blink,md_monk3_head_1.png;color,md_monk3_head_c.png;larm,md_monk3_larm_0.png;lleg,md_monk3_lleg_0.png;rarm,md_monk3_rarm_0.png;rleg,md_monk3_rleg_0.png;body_u,md_monk3_ubody_0.png |
| att_acts | att_1 |

### model_info #25

| campo | valor |
|---|---|
| model_id | 101 |
| model_name | skeleton1 |
| model_file | Skeleton1 |
| body_radius | 25 |
| body_height | 100 |
| att_range | 30 |
| skins |  |
| att_acts | att_1,att_2 |

