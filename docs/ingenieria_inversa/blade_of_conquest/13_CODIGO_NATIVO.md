# 11 · CÓDIGO NATIVO — Fórmulas y sistemas extraídos con Ghidra

> Dossier 11. Resultados de la descompilación del `libcocos2dcpp.so` (Ghidra 12.2, ARM32).
> Se exportaron **5.750 funciones de 23 clases de juego** a C (copia local en
> `rea/blade_of_conquest/findings/decomp/`). Aquí queda el conocimiento destilado:
> las fórmulas y el diseño interno que alimentarán la reconstrucción de Valcoria.

## 1. Fórmula de daño (decodificada de `AEPlayerData::getAutoFightDamage`)

El daño de un golpe en BoC (auto-batalla; el mismo esqueleto usa el combate directo):

```
ENTRADAS:  A = atacante (stats), B = defensor
  atk_efectivo   = A.atk + A.atk_nivel × 1.2            (0x1c + 0x20×1.2)
  def_neta       = max(B.def − A.penetración, 0)        (0x3c − 0x38, suelo 0)

1) BLOQUEO:   si tirada(getPropRatio(B.bloqueo − A.antibloqueo)) → daño = 0
2) dañobruto  = atk_efectivo − 2 × def_neta
3) CRÍTICO:   si tirada(getPropRatio(A.cri)) → dañobruto ×= 1 + random(0.00–0.50)
4) SUELO:     dañobruto = max(dañobruto, 0.25 × atk_efectivo)     (nunca bajo el 25 %)
5) VARIANZA:  dañobruto ×= random(0.90–1.10)                      (±10 %)
```

Con `getPropRatio(v) = v/100` (los valores `cri:30–120` son porcentajes directos) y
`getRandomBool(p)` como tirada Bernoulli. Constantes confirmadas en el binario:
`1.2` (0x3f99999a), `0.25` (0x3e800000), `0.9–1.1` (0x5a/0x6e sobre 100.0 = 0x42c80000).

**Lectura de diseño**: el bloqueo que anula (no mitiga) hace del escudo una lotería
decisiva; el piso del 25 % garantiza que nunca hay golpes "de papel"; la defensa resta
el doble que el ataque suma → la armadura domina hasta que aparece penetración.

## 2. Experiencia y niveles de tropa

- `SGUnitsData::getLevelUpExp` — la EXP necesaria por nivel vive junto a los datos de la
  unidad (`units.dat`: campo `exp` = EXP que otorga al morir; la curva de subida la
  interpola `SGUnitInfoData`).
- Subida: `stat = base_stat + growth × nivel` (ver dossier 04), techo `max_level`.

## 3. El guardado (decodificado de `AEPlayerData::SavePlayerData`)

Formato: **almacén clave-valor plano** sobre `AEGameDataManager` (envoltorio de
`UserDefault` de Cocos), con `setIntegerForKey / setDoubleForKey / setStringForKey /
setBoolForKey` + listas serializadas aparte. Claves reales visibles en el binario:

| Grupo | Claves |
|---|---|
| Jugador | `player_name`, `player_level`, `player_color`, `player_debts`, `sg_unused_sp`, `sg_played_days` |
| Selección | `cur_char_id`, `cur_warband_id` |
| Listas | `char_list`, `char_info(s)`, `char_state`, `legions`, `fmt_id`, `item_id`, `unit_id`, `position_x/y` |
| Mundo | `kingdom_rl` (lealtades de reino), estado de sitios |
| Meta | `save_count` (contador de ranuras usadas) |

Hallazgos de diseño:
- **`player_debts` existía ya en BoC**: el juego original llevaba deudas del jugador —
  Valcoria hereda la idea y la convierte en pilar narrativo (la Deuda, canon propio).
- La partida es un "saco de escalares + blobs de lista": simple, frágil, sin versionado.
- Carga con `PreloadPlayerData(slot, info)` que alimenta las estadísticas del selector
  (`AESelectGameScene::fillFileStatisticNums`).
- Guardado por escena viva: `onCtlCmdsPanelSaveGame` en `AESandTableScene` y `AECityScene`.

**Para Valcoria**: contrato `SAVE_VERSION=1` con esquema completo y validación (ya escrito
en `docs/produccion/02_GUARDADO_Y_DATOS.md`) — se conserva la granularidad clave-valor
pero con estructura versionada, y la Crónica viaja dentro del save.

## 4. Construcción en el sitio: torres (confirmado con strings + clases)

- Flujo de construcción de torre: `cm_site_opt_buildtower` → `cm_site_buildtower_info` →
  `cm_site_buildtower_done` / `cm_site_tower_full` (si no quedan `tower_slot`) con
  sprite `bs_arrow_tower_0.png` (torre de flechas).
- Caja de territorio: `cm_ter_opt_defence`, `cm_ter_opt_prosperity`, `cm_ter_opt_towers`
  → se **invierte** en los tres pilares del sitio.
- Única construcción del juego: torres defensivas en huecos fijos (3 ciudad / 2 castillo).

## 5. Presupuesto semanal (`AEWeeklyBudget`)

- `calculateNetIncomes(SGCharacterData*, …)` — el neto es **por personaje** (sueldos de
  la corte), con lista de líneas (`addIncomeOption`) y confirmación (`confirmBudget`).
- Colores por tipo de línea (`getIncomeColor`): ingresos verdes, gastos rojos.
- La semana avanza con el tiempo de juego (`sg_played_days`).

## 6. Mapa de clases de juego (top por tamaño, del análisis de símbolos)

| Clase | Métodos | Rol |
|---|---|---|
| `AEPlayerData` | 116 | estado del jugador + guardado/carga |
| `SGRoleObj` | 104 | entidad viva en batalla (soldado/héroe): mover, atacar, recibir |
| `SGBattleScene` | 97 | escena de batalla completa |
| `AESandTableScene` | 81 | mapa mundial (la "mesa de arena") |
| `AEGameShared` | 73 | datos compartidos y utilidades globales |
| `AECityScene` | 68 | escena de ciudad |
| `AECtlCmdsPanel` | 63 | panel de órdenes de batalla |
| `AEVictoryScene` | 57 | resultado de batalla (botín, prisioneros) |
| `SGBattleField` | 56 | el tablero táctico |
| `AEPartyScene` | 55 | administración de la hueste |
| `AEInventoryScene` | 48 | inventario/equipo |
| `SGCharacterData` | 45 | datos de personaje (NPC o héroe) |
| `SGMapUnitObj` | 42 | unidad sobre el mapa mundial |
| `AEGarrisonScene` | 42 | guarniciones |
| `AESkillBox` / `AETradeBox` / `AEPrisonBox` | 40/40/33 | cajas de UI: skills, comercio, prisioneros |
| `SGMapSiteObj` | 39 | sitio del mapa (ciudad/aldea/castillo) |
| `AEBattlePrepare` | 39 | despliegue + auto-batalla |
| `SGLegion` | 38 | legión del jugador o del enemigo |
| `SGGeneral` | 37 | el héroe en batalla |
| `SGMergeMap` | 33 | composición del mapa mundial |
| `AECreateFileScene` / `AESelectGameScene` | 32/27 | nueva partida / selector |
| `AEWeeklyBudget` | 26 | liquidación semanal |
| `AEFindPath` | 17 | rutas sobre el grafo del mundo |
| `dtNavMesh` / `dtNavMeshQuery` | 40/33 | Recast-Detour: navegación de batalla |

La lista completa demangled está en `findings/arquitectura_clases.md` (copia local);
el resumen queda aquí y en el dossier 00.

## 7. Decisión para Valcoria — fórmulas abiertas desde el día uno

1. **Daño**: adoptar la forma `atk_efectivo − 2×def` con suelo del 25 %, crítico ×1,0–1,5,
   varianza ±10 % — pero con **bloqueo que mitiga (no anula)** y penetración explícita;
   todas las constantes en `docs/batalla/01_CIFRAS.md` y validadas en demo.
2. **Guardado**: misma granularidad, con esquema versionado v1 (contrato ya escrito).
3. **Torres**: conservar como construcción ligera; el debate AoE se resuelve en fase B.
4. **Presupuesto**: neto por personaje + líneas coloreadas — idéntico en espíritu,
   explicado al jugador (ya está en `docs/sistemas/06_ECONOMIA.md`).
5. **Deudas**: la clave `player_debts` confirma que el germen de la Deuda era real en
   BoC — Valcoria lo eleva a sistema narrativo central.
