# 07 · BATALLA — Cómo está construido el combate en tiempo real

> Dossier 07. El motor de batalla de BoC: formaciones, campo, compañías, órdenes y el
> control del héroe. Combina lo visible en datos (`formation.dat`, `md.dat`) con el mapa
> de clases nativas (`SGBattleScene`, `SGBattleField`) — las fórmulas finas se completan
> con Ghidra (ver `11_CODIGO_NATIVO.md`).

## 1. El modelo de batalla en una frase

Dos **legiones** (`SGLegion`) despliegan sus tropas en **formaciones predefinidas**
(20 huecos en doble columna), cada soldado es una entidad con pathfinding navmesh
(`dtNavMeshQuery`) que busca su objetivo, ataca según `att_int`, y el jugador además
**controla a su héroe en tercera persona** con habilidades — todo en tiempo real,
sin turnos.

## 2. Formaciones (`formation.dat`)

```xml
<fmt_info>
  <fmt_id>0</fmt_id> <fmt_name>default</fmt_name>
  <cmd_pos>140,0</cmd_pos>          <!-- posición del mando -->
  <pts>-40,50|-40,-50|-40,150|…|40,-50</pts>  <!-- 20 huecos en 2 columnas × 10 filas -->
</fmt_info>
```

- 3 formaciones (ataque, centro, reverso según `cmd_pos` ±140/0).
- Los 20 puntos son offsets relativos al centro de la legión: milicia en las filas,
  el héroe/mando delante o al flanco.
- Clases nativas: `SGBattleField` (56 métodos — el tablero), `SGBattleScene` (97 — la
  escena completa), `AEBattlePrepare` (39 — despliegue y auto-batalla:
  `onAutoBattleTimerCountDone`), `AECtlCmdsPanel` (63 — panel de órdenes a compañías).

## 3. El cuerpo a cuerpo (lo que dicen los datos)

| Mecánica | Dato que la sustenta | Comportamiento |
|---|---|---|
| Cadencia | `att_int` (2.5–2.8 s) por unidad | cada soldado ataca cuando su temporizador vence y hay objetivo en `att_range` (`md.dat`) |
| Alcance | `att_range` por modelo (cuerpo a cuerpo vs `strag` 600–750 de arqueros) | los arqueros disparan con proyectil (`ratt_eff`: `eft_arraw1_`) |
| Movimiento | `mvspd` (50 a pie, 90 a caballo) + navmesh | avance en línea hasta contacto |
| Crítico | `cri` (30–120) | golpe crítico con probabilidad `cri` |
| Defensa | `def` (+ `mdef` mágica en enemigos) | reduce el daño entrante |
| Botín/XP | `drops`, `exp` por unidad | al morir suelta y otorga experiencia |

**Fórmula de daño finas** (multiplicadores de crit, varianza, moral): viven compiladas en
el `.so` — se documentan en `11_CODIGO_NATIVO.md` cuando Ghidra termine de decompilar
`SGBattleField`/`SGRoleObj`.

## 4. Órdenes y control (lo que hace el jugador en batalla)

- `AECtlCmdsPanel` (63 métodos): panel con órdenes de compañía (avanzar, sostener,
  retroceder, seguirme — deducible de los strings de UI y de los botones de batalla).
- Héroe: joystick virtual + habilidades (`AESkillBox`) con mana, `cd_time` y `global_cd`.
- **Auto-batalla** disponible (`AEBattlePrepare::onAutoBattleTimerCountDone`): el juego
  resuelve el choque sin control directo.
- Victoria: `AEVictoryScene` (57 métodos) con botín, prisioneros (`AEPrisonBox`) y honor.

## 5. Decisión para Valcoria — el mismo choque, mucho mejor

| Aspecto | BoC | Valcoria |
|---|---|---|
| Vista | cámara 2D/2.5D sobre el campo | **1.ª persona** (decisión de diseño del dueño) con opción de vista de mando — el "SandTable" vivo |
| Formaciones | 3 plantillas de 20 huecos | mismas plantillas JSON + editor visual; huecos según aforo canon (6+2×(n−1)) |
| Órdenes | panel fijo | panel radial con pausa táctica y voces de capitanes |
| Héroe | joystick + 4 skills | mismo control con **aliento** (100; 4/s combate) y anillo de acción |
| Auto-batalla | timer opaco | simulación con informe de la Crónica ("qué salió bien/mal") |
| Daño | fórmula compilada oculta | fórmulas abiertas en `docs/batalla/01_CIFRAS.md`, validadas contra la sensación de BoC |
| Gráficos | sprites 2017 | WebGL moderno: luz volumétrica, sangre estilizada, terreno con niebla — "mucho más bonito a primera vista" |
