
> **Nota de preservación (2026-10-25):** estas tablas se generaron parseando los XML
> `assets/datas/*.dat` y `game_maps/*.tmx` del APK de Blade of Conquest v1.0.2
> (com.wmstudio.games.boc, desarrollador 田坤/Kevin_Tien86, juego abandonado retirado de
> Google Play en 2020). Se publican como material de análisis y referencia de diseño para
> el proyecto Valcoria: son tablas de datos y cifras reformateadas, no assets del juego.
> El APK original y la descompilación completa de Ghidra (5.750 funciones en `findings/decomp/`)
> se conservan en el espacio local del proyecto (`/home/z/my-project/rea/blade_of_conquest/`).
# TALENTOS (árbol)

Fuente: `assets/datas/tlt.dat` (XML en claro). 
Entidades: `talent` ×17


## `talent` — 17 registros

### talent #1

| campo | valor |
|---|---|
| code | t_atk |
| type | 0 |
| depend | 0 |
| tlt_name | Combat Skill |
| tlt_name_cn | 搏击 |
| tlt_info | Add %5 melee physical attack power per point |
| tlt_info_cn | 每点增加%5近战物理攻击力 |

### talent #2

| campo | valor |
|---|---|
| code | t_sht |
| type | 0 |
| depend | 1 |
| tlt_name | Archery |
| tlt_name_cn | 箭术 |
| tlt_info | Add %5 remote physical attack power per point |
| tlt_info_cn | 每点增加%5远程物理攻击力 |

### talent #3

| campo | valor |
|---|---|
| code | t_def |
| type | 0 |
| depend | 0 |
| tlt_name | Tough Body |
| tlt_name_cn | 钢筋铁骨 |
| tlt_info | Add 10 HP per point |
| tlt_info_cn | 每点增加10点生命值 |

### talent #4

| campo | valor |
|---|---|
| code | t_mat |
| type | 0 |
| depend | 2 |
| tlt_name | Magic Power |
| tlt_name_cn | 魔法能量 |
| tlt_info | Add %5 magic attack power per point |
| tlt_info_cn | 每点增加%5魔法攻击力 |

### talent #5

| campo | valor |
|---|---|
| code | t_mag |
| type | 0 |
| depend | 2 |
| tlt_name | Mana Affinity |
| tlt_name_cn | 魔力亲和 |
| tlt_info | Add 2 points of mana value and 2 mana recovery speed per point |
| tlt_info_cn | 每点增加2点魔力值和2点魔力回复速度 |

### talent #6

| campo | valor |
|---|---|
| code | t_rid |
| type | 0 |
| depend | 1 |
| tlt_name | Ride Skill |
| tlt_name_cn | 骑术 |
| tlt_info | Be able to use more advanced mounts |
| tlt_info_cn | 能够使用更高级的坐骑 |

### talent #7

| campo | valor |
|---|---|
| code | t_cmd |
| type | 0 |
| depend | 2 |
| tlt_name | Control |
| tlt_name_cn | 统御 |
| tlt_info | Increase all properties of the soldiers under your command by %2 per point |
| tlt_info_cn | 每点提升麾下士兵%2所有属性 |

### talent #8

| campo | valor |
|---|---|
| code | t_spk |
| type | 0 |
| depend | 2 |
| tlt_name | Eloquence |
| tlt_name_cn | 口才 |
| tlt_info | Each point improves the probability of persuading others by %5 |
| tlt_info_cn | 每点提高说服别人的概率%5 |

### talent #9

| campo | valor |
|---|---|
| code | t_tch |
| type | 0 |
| depend | 0 |
| tlt_name | Coach |
| tlt_name_cn | 教练 |
| tlt_info | Each point increases the speed your troops gaining experience and increases the effectiveness of daily training |
| tlt_info_cn | 每点提升你的部队获得经验的速度，提升每日训练的效果 |

### talent #10

| campo | valor |
|---|---|
| code | t_lead |
| type | 1 |
| depend | 2 |
| tlt_name | Leadership |
| tlt_name_cn | 领导 |
| tlt_info | Every points increase the maximum size of the troop |
| tlt_info_cn | 每点提升最大部队规模 |

### talent #11

| campo | valor |
|---|---|
| code | t_heal |
| type | 1 |
| depend | 2 |
| tlt_name | Medicine |
| tlt_name_cn | 医术 |
| tlt_info | Each point reduces the soldiers’ death probability by %2,and increases the health recovery power of the troop by %5 |
| tlt_info_cn | 每点降低士兵的死亡概率%2，增加部队生命恢复力%5 |

### talent #12

| campo | valor |
|---|---|
| code | t_rob |
| type | 1 |
| depend | 0 |
| tlt_name | Plunder |
| tlt_name_cn | 掠夺 |
| tlt_info | Each point increases the probability of obtaining trophies and the speed of implementing predatory commands by %5 |
| tlt_info_cn | 每点提升获得战利品的概率，执行掠夺命令的速度提升%5 |

### talent #13

| campo | valor |
|---|---|
| code | t_mng |
| type | 1 |
| depend | 2 |
| tlt_name | Logistics |
| tlt_name_cn | 后勤 |
| tlt_info | Adds 3 storage rooms per point |
| tlt_info_cn | 每点提升3个的物品空间 |

### talent #14

| campo | valor |
|---|---|
| code | t_egn |
| type | 1 |
| depend | 2 |
| tlt_name | Engineering |
| tlt_name_cn | 工程 |
| tlt_info | Each point reduce the preparation time and improve the urban construction speed |
| tlt_info_cn | 每点减少攻城准备时间，提高城镇建设速度 |

### talent #15

| campo | valor |
|---|---|
| code | t_cap |
| type | 1 |
| depend | 0 |
| tlt_name | Capture |
| tlt_name_cn | 俘虏 |
| tlt_info | Each point improves the probability of capturing the opponents by %2,and increase the number of captives you can carry by 3 |
| tlt_info_cn | 每点提高俘获对方的概率%2，可多携带3名俘虏 |

### talent #16

| campo | valor |
|---|---|
| code | t_gud |
| type | 2 |
| depend | 1 |
| tlt_name | Guide |
| tlt_name_cn | 向导 |
| tlt_info | Each point increases the movement speed of the troop on Big Map by %10 |
| tlt_info_cn | 每点提升部队在大地图的移动速度%10 |

### talent #17

| campo | valor |
|---|---|
| code | t_trd |
| type | 2 |
| depend | 2 |
| tlt_name | Commerce |
| tlt_name_cn | 商业 |
| tlt_info | Each point reduces the buying price by %1,and increases the selling price by %1 |
| tlt_info_cn | 每点降低%1买入物品的价格，提高%1出售物品的价格 |

