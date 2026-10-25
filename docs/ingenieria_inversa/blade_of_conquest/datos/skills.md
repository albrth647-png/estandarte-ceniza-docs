
> **Nota de preservación (2026-10-25):** estas tablas se generaron parseando los XML
> `assets/datas/*.dat` y `game_maps/*.tmx` del APK de Blade of Conquest v1.0.2
> (com.wmstudio.games.boc, desarrollador 田坤/Kevin_Tien86, juego abandonado retirado de
> Google Play en 2020). Se publican como material de análisis y referencia de diseño para
> el proyecto Valcoria: son tablas de datos y cifras reformateadas, no assets del juego.
> El APK original y la descompilación completa de Ghidra (5.750 funciones en `findings/decomp/`)
> se conservan en el espacio local del proyecto (`/home/z/my-project/rea/blade_of_conquest/`).
# HABILIDADES/MAGIAS — tabla completa

Fuente: `assets/datas/skills.dat` (XML en claro). 
Entidades: `skill` ×32


## `skill` — 32 registros

### skill #1

| campo | valor |
|---|---|
| sk_code | 101 |
| sk_type | 1 |
| sk_class | 0 |
| tgt_type | 1 |
| max_level | 5 |
| pre_skill | 0 |
| pre_skill_lv | 0 |
| csp_require | 0 |
| sp_cost | 1,1,1,1,1 |
| limit_lv | 1,2,3,4,5 |
| val1 | 20,30,40,50,60 |
| val2 | 30,35,40,45,50 |
| val3 | 40,40,50,50,60 |
| val4 | 0,0,0,0,0 |
| val5 | 0,0,0,0,0 |
| mp | 10,12,14,16,18 |
| cd_time | 10,10,10,10,10 |
| global_cd | 3 |
| sk_icon | icon_skill_0.png |
| sk_name | Fierce Blow |
| sk_name_cn | 重击 |
| sk_info | Launching a fierce blow to your target is likely to cause vertigo effect |
| sk_info_cn | 向你的目标发起猛烈的一击，有几率造成眩晕效果 |

### skill #2

| campo | valor |
|---|---|
| sk_code | 102 |
| sk_type | 0 |
| sk_class | 0 |
| tgt_type | 0 |
| max_level | 5 |
| pre_skill | 0 |
| pre_skill_lv | 0 |
| csp_require | 0 |
| sp_cost | 1,1,1,1,1 |
| limit_lv | 1,2,3,4,5 |
| val1 | 2,4,6,8,10 |
| val2 | 1,2,3,4,5 |
| val3 | 0,0,0,0,0 |
| val4 | 0,0,0,0,0 |
| val5 | 0,0,0,0,0 |
| mp | 0,0,0,0,0 |
| cd_time | 10,10,10,10,10 |
| global_cd | 3 |
| sk_icon | icon_skill_1.png |
| sk_name | Strong |
| sk_name_cn | 强健 |
| sk_info | Physical strength increased %%%d,Melee attack force increased %%%d |
| sk_info_cn | 体力增加%%%d，近战攻击力增加%%%d |

### skill #3

| campo | valor |
|---|---|
| sk_code | 103 |
| sk_type | 1 |
| sk_class | 0 |
| tgt_type | 6 |
| max_level | 5 |
| pre_skill | 101 |
| pre_skill_lv | 1 |
| csp_require | 5 |
| sp_cost | 1,1,1,1,1 |
| limit_lv | 1,2,3,4,5 |
| val1 | 20,25,30,35,40 |
| val2 | 400,420,440,460,480 |
| val3 | 1,2,3,4,5 |
| val4 | 0,0,0,0,0 |
| val5 | 0,0,0,0,0 |
| mp | 15,15,18,18,20 |
| cd_time | 15,15,15,15,15 |
| global_cd | 3 |
| sk_icon | icon_skill_2.png |
| sk_name | Whirlwind |
| sk_name_cn | 旋风斩 |
| sk_info | Give out a whirlwind attack and and explode sword power to damage the enemy ahead. |
| sk_info_cn | 发出旋风般的攻击并形成剑气对前方敌人造成伤害 |

### skill #4

| campo | valor |
|---|---|
| sk_code | 104 |
| sk_type | 2 |
| sk_class | 0 |
| tgt_type | 0 |
| max_level | 5 |
| pre_skill | 103 |
| pre_skill_lv | 1 |
| csp_require | 10 |
| sp_cost | 1,1,1,1,1 |
| limit_lv | 1,2,3,4,5 |
| val1 | 30,35,40,45,50 |
| val2 | 10,15,20,25,30 |
| val3 | 12,14,16,18,20 |
| val4 | 0,0,0,0,0 |
| val5 | 0,0,0,0,0 |
| mp | 16,18,20,22,25 |
| cd_time | 30,35,40,45,50 |
| global_cd | 3 |
| sk_icon | icon_skill_3.png |
| sk_name | Battle Roar |
| sk_name_cn | 战斗咆哮 |
| sk_info | Increase your attack speed and damage in short time |
| sk_info_cn | 短期内大幅提高你的攻击速度及伤害 |

### skill #5

| campo | valor |
|---|---|
| sk_code | 105 |
| sk_type | 0 |
| sk_class | 0 |
| tgt_type | 0 |
| max_level | 5 |
| pre_skill | 103 |
| pre_skill_lv | 1 |
| csp_require | 10 |
| sp_cost | 1,1,1,1,1 |
| limit_lv | 1,2,3,4,5 |
| val1 | 20,40,60,80,100 |
| val2 | 0,0,0,0,0 |
| val3 | 0,0,0,0,0 |
| val4 | 0,0,0,0,0 |
| val5 | 0,0,0,0,0 |
| mp | 0,0,0,0,0 |
| cd_time | 10,10,10,10,10 |
| global_cd | 3 |
| sk_icon | icon_skill_4.png |
| sk_name | Block |
| sk_name_cn | 格挡 |
| sk_info | Increase your block value by %d |
| sk_info_cn | 使你的格挡值提高%d |

### skill #6

| campo | valor |
|---|---|
| sk_code | 106 |
| sk_type | 0 |
| sk_class | 0 |
| tgt_type | 0 |
| max_level | 5 |
| pre_skill | 104 |
| pre_skill_lv | 1 |
| csp_require | 15 |
| sp_cost | 1,1,1,1,1 |
| limit_lv | 1,2,3,4,5 |
| val1 | 50,75,100,125,150 |
| val2 | 30,35,40,45,50 |
| val3 | 0,0,0,0,0 |
| val4 | 0,0,0,0,0 |
| val5 | 0,0,0,0,0 |
| mp | 0,0,0,0,0 |
| cd_time | 10,10,10,10,10 |
| global_cd | 3 |
| sk_icon | icon_skill_5.png |
| sk_name | Bloodthirsty |
| sk_name_cn | 嗜血 |
| sk_info | Melee attacks have a chance to restore life |
| sk_info_cn | 近战攻击时有一定几率回复生命 |

### skill #7

| campo | valor |
|---|---|
| sk_code | 107 |
| sk_type | 2 |
| sk_class | 0 |
| tgt_type | 0 |
| max_level | 5 |
| pre_skill | 105 |
| pre_skill_lv | 1 |
| csp_require | 15 |
| sp_cost | 1,1,1,1,1 |
| limit_lv | 1,2,3,4,5 |
| val1 | 50,55,60,65,70 |
| val2 | 10,12,14,16,18 |
| val3 | 0,0,0,0,0 |
| val4 | 0,0,0,0,0 |
| val5 | 0,0,0,0,0 |
| mp | 20,24,28,32,36 |
| cd_time | 40,40,40,40,40 |
| global_cd | 3 |
| sk_icon | icon_skill_6.png |
| sk_name | Shield Walls |
| sk_name_cn | 盾墙 |
| sk_info | All damage received within a certain time is reduced by %%%d |
| sk_info_cn | 一定时间内受到的所有伤害降低%%%d |

### skill #8

| campo | valor |
|---|---|
| sk_code | 108 |
| sk_type | 1 |
| sk_class | 0 |
| tgt_type | 6 |
| max_level | 3 |
| pre_skill | 106\|107 |
| pre_skill_lv | 1 |
| csp_require | 20 |
| sp_cost | 1,1,1 |
| limit_lv | 30,33,36 |
| val1 | 360,360,360 |
| val2 | 20,22,24 |
| val3 | 55,60,65 |
| val4 | 30,40,50 |
| val5 | 0,0,0 |
| mp | 30,35,40 |
| cd_time | 10,10,10 |
| global_cd | 3 |
| sk_icon | icon_skill_7.png |
| sk_name | Heroic Charge |
| sk_name_cn | 无畏冲锋 |
| sk_info | Launch an assault in one direction,and cause all the enemies passing by to be hurt and unconscious |
| sk_info_cn | 向一个方向发起冲锋，并使所有经过的敌人受到伤害并昏迷 |

### skill #9

| campo | valor |
|---|---|
| sk_code | 201 |
| sk_type | 1 |
| sk_class | 1 |
| tgt_type | 6 |
| max_level | 5 |
| pre_skill | 0 |
| pre_skill_lv | 0 |
| csp_require | 0 |
| sp_cost | 1,1,1,1,1 |
| limit_lv | 1,2,3,4,5 |
| val1 | 120,140,160,180,200 |
| val2 | 45,50,55,60,65 |
| val3 | 21,23,25,27,29 |
| val4 | 0,0,0,0,0 |
| val5 | 0,0,0,0,0 |
| mp | 20,24,28,32,36 |
| cd_time | 10,10,10,10,10 |
| global_cd | 3 |
| sk_icon | icon_skill_8.png |
| sk_name | Firebolt |
| sk_name_cn | 火球 |
| sk_info | Fire a fireball to the specified direction,which explodes when hitting the target and cause damage to nearby enemies |
| sk_info_cn | 向指定方向发射一枚火球，该火球在击中目标后会爆炸并对周围敌人造成伤害 |

### skill #10

| campo | valor |
|---|---|
| sk_code | 202 |
| sk_type | 0 |
| sk_class | 1 |
| tgt_type | 0 |
| max_level | 5 |
| pre_skill | 0 |
| pre_skill_lv | 0 |
| csp_require | 0 |
| sp_cost | 1,1,1,1,1 |
| limit_lv | 1,2,3,4,5 |
| val1 | 5,10,15,20,25 |
| val2 | 0,0,0,0,0 |
| val3 | 0,0,0,0,0 |
| val4 | 0,0,0,0,0 |
| val5 | 0,0,0,0,0 |
| mp | 0,0,0,0,0 |
| cd_time | 10,10,10,10,10 |
| global_cd | 3 |
| sk_icon | icon_skill_14.png |
| sk_name | Meditation |
| sk_name_cn | 冥想 |
| sk_info | Improve magic recover speed in combat |
| sk_info_cn | 提高战斗中的魔法恢复速度 |

### skill #11

| campo | valor |
|---|---|
| sk_code | 203 |
| sk_type | 1 |
| sk_class | 1 |
| tgt_type | 6 |
| max_level | 5 |
| pre_skill | 201 |
| pre_skill_lv | 1 |
| csp_require | 5 |
| sp_cost | 1,1,1,1,1 |
| limit_lv | 1,2,3,4,5 |
| val1 | 120,140,160,180,200 |
| val2 | 50,60,70,80,90 |
| val3 | 18,20,22,24,26 |
| val4 | 35,40,45,50,55 |
| val5 | 45,55,65,75,85 |
| mp | 20,24,28,32,36 |
| cd_time | 8,8,8,8,8 |
| global_cd | 3 |
| sk_icon | icon_skill_9.png |
| sk_name | Frostbolt |
| sk_name_cn | 寒冰箭 |
| sk_info | Cast a Frostbolt to the specified direction,which will cause a deceleration effect |
| sk_info_cn | 向指定方向施放一枚寒冰箭，该寒冰箭会造成减速效果 |

### skill #12

| campo | valor |
|---|---|
| sk_code | 204 |
| sk_type | 1 |
| sk_class | 1 |
| tgt_type | 1 |
| max_level | 5 |
| pre_skill | 203 |
| pre_skill_lv | 1 |
| csp_require | 10 |
| sp_cost | 1,1,1,1,1 |
| limit_lv | 1,2,3,4,5 |
| val1 | 3,5,7,9,11 |
| val2 | 55,65,75,85,95 |
| val3 | 12,14,16,18,20 |
| val4 | 50,100,150,200,250 |
| val5 | 0,0,0,0,0 |
| mp | 24,26,28,30,32 |
| cd_time | 10,10,10,10,10 |
| global_cd | 3 |
| sk_icon | icon_skill_10.png |
| sk_name | Chain Lighting |
| sk_name_cn | 闪电链 |
| sk_info | Release a lighting bolt to the specified enemy,and randomly damage other enemy targets which are close to this target |
| sk_info_cn | 向指定的敌人释放一道闪电，并随机伤害到离该目标相近的其他敌方目标 |

### skill #13

| campo | valor |
|---|---|
| sk_code | 205 |
| sk_type | 1 |
| sk_class | 1 |
| tgt_type | 2 |
| max_level | 5 |
| pre_skill | 203 |
| pre_skill_lv | 1 |
| csp_require | 10 |
| sp_cost | 1,1,1,1,1 |
| limit_lv | 1,2,3,4,5 |
| val1 | 3,5,7,9,11 |
| val2 | 10,14,18,22,26 |
| val3 | 25,27,29,31,33 |
| val4 | 50,60,70,80,90 |
| val5 | 0,0,0,0,0 |
| mp | 35,40,45,50,55 |
| cd_time | 20,20,20,20,20 |
| global_cd | 3 |
| sk_icon | icon_skill_11.png |
| sk_name | Fire Wall |
| sk_name_cn | 火墙 |
| sk_info | Release a firewall to a designated area,all units within this area are subject to sustained damage |
| sk_info_cn | 向一个指定区域释放一道火墙，所有位于该区域的单位都会受到持续性伤害 |

### skill #14

| campo | valor |
|---|---|
| sk_code | 206 |
| sk_type | 4 |
| sk_class | 1 |
| tgt_type | 0 |
| max_level | 5 |
| pre_skill | 204 |
| pre_skill_lv | 1 |
| csp_require | 15 |
| sp_cost | 1,1,1,1,1 |
| limit_lv | 1,2,3,4,5 |
| val1 | 3,4,5,6,7 |
| val2 | 30,40,50,60,70 |
| val3 | 60,62,64,66,68 |
| val4 | 0,0,0,0,0 |
| val5 | 0,0,0,0,0 |
| mp | 50,55,60,65,70 |
| cd_time | 60,60,60,60,60 |
| global_cd | 3 |
| sk_icon | icon_skill_12.png |
| sk_name | Summon Dead |
| sk_name_cn | 召唤亡灵 |
| sk_info | Raise the dead army to fight for you |
| sk_info_cn | 召唤出亡灵大军来为你战斗 |

### skill #15

| campo | valor |
|---|---|
| sk_code | 207 |
| sk_type | 0 |
| sk_class | 1 |
| tgt_type | 0 |
| max_level | 5 |
| pre_skill | 205 |
| pre_skill_lv | 1 |
| csp_require | 15 |
| sp_cost | 1,1,1,1,1 |
| limit_lv | 1,2,3,4,5 |
| val1 | 4,8,12,16,20 |
| val2 | 0,0,0,0,0 |
| val3 | 0,0,0,0,0 |
| val4 | 0,0,0,0,0 |
| val5 | 0,0,0,0,0 |
| mp | 0,0,0,0,0 |
| cd_time | 0,0,0,0,0 |
| global_cd | 3 |
| sk_icon | icon_skill_15.png |
| sk_name | Magic Shield |
| sk_name_cn | 魔法护盾 |
| sk_info | Absorb %%%d damage when being attacked |
| sk_info_cn | 受到攻击时可吸收%%%d的伤害 |

### skill #16

| campo | valor |
|---|---|
| sk_code | 208 |
| sk_type | 1 |
| sk_class | 1 |
| tgt_type | 2 |
| max_level | 3 |
| pre_skill | 206\|207 |
| pre_skill_lv | 1 |
| csp_require | 20 |
| sp_cost | 1,1,1 |
| limit_lv | 30,33,36 |
| val1 | 300,400,500 |
| val2 | 80,100,120 |
| val3 | 55,60,65 |
| val4 | 35,45,55 |
| val5 | 10,12,14 |
| mp | 80,90,100 |
| cd_time | 60,60,60 |
| global_cd | 3 |
| sk_icon | icon_skill_13.png |
| sk_name | Summon The Doom |
| sk_name_cn | 末日召唤 |
| sk_info | Raise doomsday fire rain to the specified area,cause damage to all units in this area at random |
| sk_info_cn | 向指定的区域召唤出末日火雨，随机对该区域内所有的单位造成伤害 |

### skill #17

| campo | valor |
|---|---|
| sk_code | 301 |
| sk_type | 2 |
| sk_class | 2 |
| tgt_type | 4 |
| max_level | 5 |
| pre_skill | 0 |
| pre_skill_lv | 0 |
| csp_require | 0 |
| sp_cost | 1,1,1,1,1 |
| limit_lv | 1,2,3,4,5 |
| val1 | 5,10,15,20,25 |
| val2 | 5,10,15,20,25 |
| val3 | 15,16,17,18,19 |
| val4 | 20,25,30,35,40 |
| val5 | 0,0,0,0,0 |
| mp | 22,24,26,28,30 |
| cd_time | 60,60,60,60,60 |
| global_cd | 3 |
| sk_icon | icon_skill_16.png |
| sk_name | Pray |
| sk_name_cn | 祈祷 |
| sk_info | Pray to the Goddess of Light to strengthen the attack and defense power of you and your army in short time |
| sk_info_cn | 向光之女神祈祷，使你及你的军队在短时间内攻击及防御力获得强化 |

### skill #18

| campo | valor |
|---|---|
| sk_code | 302 |
| sk_type | 0 |
| sk_class | 2 |
| tgt_type | 0 |
| max_level | 5 |
| pre_skill | 0 |
| pre_skill_lv | 0 |
| csp_require | 0 |
| sp_cost | 1,1,1,1,1 |
| limit_lv | 1,2,3,4,5 |
| val1 | 2,4,6,8,10 |
| val2 | 0,0,0,0,0 |
| val3 | 0,0,0,0,0 |
| val4 | 0,0,0,0,0 |
| val5 | 0,0,0,0,0 |
| mp | 0,0,0,0,0 |
| cd_time | 10,10,10,10,10 |
| global_cd | 3 |
| sk_icon | icon_skill_21.png |
| sk_name | Perseverance |
| sk_name_cn | 坚毅 |
| sk_info | Increase defense power by %%%d |
| sk_info_cn | 防御力提高%%%d |

### skill #19

| campo | valor |
|---|---|
| sk_code | 303 |
| sk_type | 5 |
| sk_class | 2 |
| tgt_type | 3 |
| max_level | 5 |
| pre_skill | 301 |
| pre_skill_lv | 1 |
| csp_require | 5 |
| sp_cost | 1,1,1,1,1 |
| limit_lv | 1,2,3,4,5 |
| val1 | 60,80,100,120,140 |
| val2 | 0,0,0,0,0 |
| val3 | 10,10,10,10,10 |
| val4 | 0,0,0,0,0 |
| val5 | 0,0,0,0,0 |
| mp | 25,27,29,31,33 |
| cd_time | 15,14,13,12,11 |
| global_cd | 3 |
| sk_icon | icon_skill_17.png |
| sk_name | Holy Light |
| sk_name_cn | 圣光治愈 |
| sk_info | Heal yourself or a friendly unit |
| sk_info_cn | 治愈自己或者一个友方单位 |

### skill #20

| campo | valor |
|---|---|
| sk_code | 304 |
| sk_type | 0 |
| sk_class | 2 |
| tgt_type | 0 |
| max_level | 5 |
| pre_skill | 303 |
| pre_skill_lv | 1 |
| csp_require | 10 |
| sp_cost | 1,1,1,1,1 |
| limit_lv | 1,2,3,4,5 |
| val1 | 2,4,6,8,10 |
| val2 | 2,4,6,8,10 |
| val3 | 0,0,0,0,0 |
| val4 | 0,0,0,0,0 |
| val5 | 0,0,0,0,0 |
| mp | 0,0,0,0,0 |
| cd_time | 0,0,0,0,0 |
| global_cd | 3 |
| sk_icon | icon_skill_23.png |
| sk_name | Heroism |
| sk_name_cn | 英勇 |
| sk_info | Increase your attack power and attack speed |
| sk_info_cn | 使你的军队攻击力及攻击速度提高 |

### skill #21

| campo | valor |
|---|---|
| sk_code | 305 |
| sk_type | 0 |
| sk_class | 2 |
| tgt_type | 0 |
| max_level | 5 |
| pre_skill | 303 |
| pre_skill_lv | 1 |
| csp_require | 10 |
| sp_cost | 1,1,1,1,1 |
| limit_lv | 1,2,3,4,5 |
| val1 | 2,4,6,8,10 |
| val2 | 5,10,15,20,25 |
| val3 | 0,0,0,0,0 |
| val4 | 0,0,0,0,0 |
| val5 | 0,0,0,0,0 |
| mp | 0,0,0,0,0 |
| cd_time | 0,0,0,0,0 |
| global_cd | 3 |
| sk_icon | icon_skill_22.png |
| sk_name | Faith |
| sk_name_cn | 信仰 |
| sk_info | Increase your army’s defense power by %%%d,and magic resistance by %d |
| sk_info_cn | 使你的军队防御力提高%%%d，魔法抗性提高%d |

### skill #22

| campo | valor |
|---|---|
| sk_code | 306 |
| sk_type | 2 |
| sk_class | 2 |
| tgt_type | 4 |
| max_level | 5 |
| pre_skill | 304 |
| pre_skill_lv | 1 |
| csp_require | 15 |
| sp_cost | 1,1,1,1,1 |
| limit_lv | 1,2,3,4,5 |
| val1 | 20,24,28,32,36 |
| val2 | 20,25,30,35,40 |
| val3 | 20,22,24,26,28 |
| val4 | 30,35,40,45,50 |
| val5 | 0,0,0,0,0 |
| mp | 35,37,39,41,43 |
| cd_time | 60,60,60,60,60 |
| global_cd | 3 |
| sk_icon | icon_skill_18.png |
| sk_name | Blessing |
| sk_name_cn | 女神赐福 |
| sk_info | To enable you and your army to gain the Goddess Blessing and increase your attack and move speed |
| sk_info_cn | 使你及你的军队获得女神的赐福，短时间内攻击及移动速度提高 |

### skill #23

| campo | valor |
|---|---|
| sk_code | 307 |
| sk_type | 5 |
| sk_class | 2 |
| tgt_type | 7 |
| max_level | 5 |
| pre_skill | 305 |
| pre_skill_lv | 1 |
| csp_require | 15 |
| sp_cost | 1,1,1,1,1 |
| limit_lv | 1,2,3,4,5 |
| val1 | 10,15,20,25,30 |
| val2 | 160,190,220,250,280 |
| val3 | 35,37,39,41,43 |
| val4 | 3,4,5,6,7 |
| val5 | 0,0,0,0,0 |
| mp | 45,50,55,60,65 |
| cd_time | 60,60,60,60,60 |
| global_cd | 3 |
| sk_icon | icon_skill_19.png |
| sk_name | Light Shines |
| sk_name_cn | 圣光照耀 |
| sk_info | Create a zone covered by Holy Light shines and heal the friendly units in this zone continually |
| sk_info_cn | 创造一片圣光笼罩的区域，并持续的治愈该区域内的友方单位 |

### skill #24

| campo | valor |
|---|---|
| sk_code | 308 |
| sk_type | 6 |
| sk_class | 2 |
| tgt_type | 4 |
| max_level | 3 |
| pre_skill | 306\|307 |
| pre_skill_lv | 1 |
| csp_require | 20 |
| sp_cost | 1,1,1 |
| limit_lv | 30,33,36 |
| val1 | 5,7,9 |
| val2 | 45,50,55 |
| val3 | 30,35,40 |
| val4 | 0,0,0 |
| val5 | 0,0,0 |
| mp | 60,70,80 |
| cd_time | 90,90,90 |
| global_cd | 3 |
| sk_icon | icon_skill_20.png |
| sk_name | Resurrection |
| sk_name_cn | 复活术 |
| sk_info | Summon the power of the Goddess of Light to restore the friendly units who lost combat strength on the battlefield. |
| sk_info_cn | 召唤出光之女神的力量使战场上失去战斗力的友方单位重获新生 |

### skill #25

| campo | valor |
|---|---|
| sk_code | 401 |
| sk_type | 1 |
| sk_class | 3 |
| tgt_type | 1 |
| max_level | 5 |
| pre_skill | 0 |
| pre_skill_lv | 0 |
| csp_require | 0 |
| sp_cost | 1,1,1,1,1 |
| limit_lv | 1,2,3,4,5 |
| val1 | 40,50,60,70,80 |
| val2 | 300,350,400,450,500 |
| val3 | 0,0,0,0,0 |
| val4 | 0,0,0,0,0 |
| val5 | 0,0,0,0,0 |
| mp | 20,24,28,32,36 |
| cd_time | 10,10,10,10,10 |
| global_cd | 3 |
| sk_icon | icon_skill_24.png |
| sk_name | Snipe |
| sk_name_cn | 狙击 |
| sk_info | Aim at a target and give it a fatal blow |
| sk_info_cn | 瞄准一个目标并给予其致命的一击 |

### skill #26

| campo | valor |
|---|---|
| sk_code | 402 |
| sk_type | 0 |
| sk_class | 3 |
| tgt_type | 0 |
| max_level | 5 |
| pre_skill | 0 |
| pre_skill_lv | 0 |
| csp_require | 0 |
| sp_cost | 1,1,1,1,1 |
| limit_lv | 1,2,3,4,5 |
| val1 | 2,4,6,8,10 |
| val2 | 0,0,0,0,0 |
| val3 | 0,0,0,0,0 |
| val4 | 0,0,0,0,0 |
| val5 | 0,0,0,0,0 |
| mp | 0,0,0,0,0 |
| cd_time | 10,10,10,10,10 |
| global_cd | 3 |
| sk_icon | icon_skill_25.png |
| sk_name | Agile |
| sk_name_cn | 迅捷 |
| sk_info | Raise your attack and move speed by %d |
| sk_info_cn | 使你的攻击及移动速度上升%d |

### skill #27

| campo | valor |
|---|---|
| sk_code | 403 |
| sk_type | 2 |
| sk_class | 3 |
| tgt_type | 4 |
| max_level | 5 |
| pre_skill | 401 |
| pre_skill_lv | 1 |
| csp_require | 5 |
| sp_cost | 1,1,1,1,1 |
| limit_lv | 1,2,3,4,5 |
| val1 | 30,35,40,45,50 |
| val2 | 20,25,30,35,40 |
| val3 | 400,450,500,550,600 |
| val4 | 15,20,25,30,35 |
| val5 | 0,0,0,0,0 |
| mp | 30,33,36,39,42 |
| cd_time | 50,50,50,50,50 |
| global_cd | 3 |
| sk_icon | icon_skill_30.png |
| sk_name | Wind Walk |
| sk_name_cn | 疾风步 |
| sk_info | Make you extremely fast and improve your dodge rate in short time |
| sk_info_cn | 短时间使你迅捷无比，并提高闪避率 |

### skill #28

| campo | valor |
|---|---|
| sk_code | 404 |
| sk_type | 1 |
| sk_class | 3 |
| tgt_type | 1 |
| max_level | 5 |
| pre_skill | 403 |
| pre_skill_lv | 1 |
| csp_require | 10 |
| sp_cost | 1,1,1,1,1 |
| limit_lv | 1,2,3,4,5 |
| val1 | 30,40,50,60,70 |
| val2 | 5,10,15,20,25 |
| val3 | 0,0,0,0,0 |
| val4 | 0,0,0,0,0 |
| val5 | 0,0,0,0,0 |
| mp | 24,26,28,30,32 |
| cd_time | 15,15,15,15,15 |
| global_cd | 3 |
| sk_icon | icon_skill_26.png |
| sk_name | Antimagic Arrow |
| sk_name_cn | 汲灵箭 |
| sk_info | Shoot a magic arrow at an enemy hero,causing damage to it while making it lose a lot of mana |
| sk_info_cn | 向敌方英雄射出一支魔法箭，造成伤害的同时使其损失大量魔力值 |

### skill #29

| campo | valor |
|---|---|
| sk_code | 405 |
| sk_type | 0 |
| sk_class | 3 |
| tgt_type | 0 |
| max_level | 5 |
| pre_skill | 403 |
| pre_skill_lv | 1 |
| csp_require | 10 |
| sp_cost | 1,1,1,1,1 |
| limit_lv | 1,2,3,4,5 |
| val1 | 10,20,30,40,50 |
| val2 | 10,20,30,40,50 |
| val3 | 0,0,0,0,0 |
| val4 | 0,0,0,0,0 |
| val5 | 0,0,0,0,0 |
| mp | 0,0,0,0,0 |
| cd_time | 20,20,20,20,20 |
| global_cd | 3 |
| sk_icon | icon_skill_31.png |
| sk_name | Hawkeye |
| sk_name_cn | 鹰眼 |
| sk_info | Make your hit rate and shooting accuracy increased by %d, crit rate increased by %d |
| sk_info_cn | 使你的命中率及射击精确度提高%d,暴击率提高%d |

### skill #30

| campo | valor |
|---|---|
| sk_code | 406 |
| sk_type | 1 |
| sk_class | 3 |
| tgt_type | 2 |
| max_level | 5 |
| pre_skill | 404 |
| pre_skill_lv | 1 |
| csp_require | 15 |
| sp_cost | 1,1,1,1,1 |
| limit_lv | 1,2,3,4,5 |
| val1 | 15,20,25,30,35 |
| val2 | 40,50,60,70,80 |
| val3 | 200,220,240,260,280 |
| val4 | 0,0,0,0,0 |
| val5 | 0,0,0,0,0 |
| mp | 38,40,42,44,46 |
| cd_time | 30,30,30,30,30 |
| global_cd | 3 |
| sk_icon | icon_skill_27.png |
| sk_name | Arrow Rain |
| sk_name_cn | 箭雨 |
| sk_info | Summon a large number of arrows to carry out intensive blow to a region |
| sk_info_cn | 召唤大量的箭矢对一个区域进行密集打击 |

### skill #31

| campo | valor |
|---|---|
| sk_code | 407 |
| sk_type | 1 |
| sk_class | 3 |
| tgt_type | 6 |
| max_level | 5 |
| pre_skill | 405 |
| pre_skill_lv | 1 |
| csp_require | 15 |
| sp_cost | 1,1,1,1,1 |
| limit_lv | 1,2,3,4,5 |
| val1 | 20,30,40,50,60 |
| val2 | 40,50,60,70,80 |
| val3 | 40,50,60,70,80 |
| val4 | 0,0,0,0,0 |
| val5 | 0,0,0,0,0 |
| mp | 36,40,44,48,52 |
| cd_time | 30,30,30,30,30 |
| global_cd | 3 |
| sk_icon | icon_skill_28.png |
| sk_name | Miracle Arrow |
| sk_name_cn | 神赐之箭 |
| sk_info | To shoot an arrow full of energy in a given direction,which can cause damage to all passing targets |
| sk_info_cn | 向指定方向射出充满能量的一箭，能够对所有经过的目标造成伤害 |

### skill #32

| campo | valor |
|---|---|
| sk_code | 408 |
| sk_type | 1 |
| sk_class | 3 |
| tgt_type | 5 |
| max_level | 3 |
| pre_skill | 406\|407 |
| pre_skill_lv | 1 |
| csp_require | 20 |
| sp_cost | 1,1,1 |
| limit_lv | 30,33,36 |
| val1 | 10,15,20 |
| val2 | 10,14,18 |
| val3 | 0,0,0 |
| val4 | 0,0,0 |
| val5 | 0,0,0 |
| mp | 60,70,80 |
| cd_time | 60,60,60 |
| global_cd | 3 |
| sk_icon | icon_skill_29.png |
| sk_name | Thorns Growing |
| sk_name_cn | 荆棘之触 |
| sk_info | Summon a huge number of thorny tentacles to trap your enemies and cause damage |
| sk_info_cn | 召唤出大量的荆棘触须困住你的敌人并造成伤害 |

