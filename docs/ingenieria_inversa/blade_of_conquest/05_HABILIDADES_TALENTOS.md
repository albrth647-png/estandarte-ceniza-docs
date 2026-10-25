# 05 · HABILIDADES Y TALENTOS — Cómo se construyen los árboles del héroe

> Dossier 05. El árbol de habilidades del héroe (32 skills) y los talentos (17),
> extraídos de `assets/datas/skills.dat` y `tlt.dat`. Estructura, fórmulas y su
> reconstrucción mejorada en Valcoria.

## 1. El modelo de una habilidad

| Campo | Significado |
|---|---|
| `sk_code` | id (101–108 Guerrero, 201–208 Mago, 301–308 Clérigo, 401–408 Batidor) |
| `sk_type` | 0 = pasiva · 1 = ataque activo · 2 = buff/aura · 4 = invocación · 5 = curación · 6 = resurrección |
| `sk_class` | familia (0 Guerrero, 1 Mago, 2 Clérigo, 3 Batidor) |
| `tgt_type` | tipo de objetivo (0 propio, 1 enemigo, 2 área, 3 aliado, 4 muerto, 5/6/7 especiales) |
| `max_level` | techo (normalmente 5; finales de rama: 3) |
| `pre_skill` / `pre_skill_lv` | **prerrequisito** — admite OR con `|` (p. ej. `106\|107`) |
| `sp_cost[5]` | puntos de skill por nivel (todos 1) |
| `limit_lv[5]` | nivel del héroe requerido por peldaño (1,2,3,4,5) |
| `val1..val5[5]` | valores de efecto por nivel (semántica depende de `sk_type`) |
| `mp[5]` | coste de mana por nivel (las pasivas: 0) |
| `cd_time[5]` | recarga por nivel |
| `global_cd` | recarga global compartida (3 s habitual) |

**Las 4 escuelas × 8 habilidades, con ramas de 5+5+3** (dos prerrequisitos encadenados y
una habilidad remate que exige `A|B`):

- **Guerrero (1xx)**: Fierce Blow (daño+aturdimiento) → Whirlwind → Battle Roar / Block →
  Bloodthirsty / Shield Walls → **Heroic Charge** (remate, requiere Roar|Walls).
- **Mago (2xx)**: Firebolt / Meditation → Frostbolt → Chain Lightning / Fire Wall →
  Summon Dead / Magic Shield → **Summon The Doom**.
- **Clérigo (3xx)**: Pray / Perseverance → Holy Light → Heroism / Faith →
  Blessing / Light Shines → **Resurrection**.
- **Batidor (4xx)**: Snipe / Agile → Wind Walk → Antimagic Arrow / Hawkeye →
  Arrow Rain / Miracle Arrow → **Thorns Growing**.

Las pasivas (`sk_type:0`) dan % directo (Strong +2–10 % atk…); los remates de rama son
las habilidades de firma con 3 niveles.

## 2. Talentos (`tlt.dat`) — 17 pasivas de campaña

| Código | Tipo | Depende de | Nombre |
|---|---|---|---|
| t_atk, t_def, t_tch | 0 | STR-type | Combat Skill, Tough Body, Coach |
| t_sht, t_rid | 0 | AGI-type | Archery, Ride Skill |
| t_mat, t_mag | 0 | INT-type | Magic Power, Mana Affinity |
| t_cmd, t_spk, t_mng, t_egn | 2 | INT-type | Control, Eloquence, Logistics, Engineering |
| t_lead, t_heal | 1 | INT-type | Leadership, Medicine |
| t_rob, t_cap | 1 | STR-type | Plunder, Capture |
| t_gud, t_trd | 2 | AGI-type | Guide, Commerce |

`depend` referencia al atributo base del héroe (STR/AGI/INT) que desbloquea/refuerza el
talento — el sistema conecta atributos → talentos → campaña (saqueo, captura de
prisioneros, ingeniería de asedio, comercio).

## 3. Cómo interactúa en batalla

- Las activas consumen **mana** (`mp`) del héroe, respetan `cd_time` propio y un
  `global_cd` compartido; las cajas de skill (`AESkillBox`, 40 métodos; `AESkillSelBox`,
  37) gestionan selección y teclas rápidas.
- `tgt_type` decide el enrutado del efecto (auto-buff, proyectil, área, cadáver…);
  el motor aplica `val1..val5` del nivel aprendido.
- Las pasivas se aplican al calcular stats del héroe antes de la batalla.

## 4. Decisión para Valcoria — del mana al aliento

| Aspecto | BoC | Valcoria |
|---|---|---|
| Recurso | mana por skill (`mp`) | **aliento** (100, regenera 4/s en combate · 5/s fuera — canon ya fijado) |
| Recarga | `cd_time` + `global_cd` fijo | mismas dos capas de recarga, mostradas en el anillo de acción |
| Árboles | 4 escuelas × 8, ramas 5+5+3 | misma métrica de árbol (legible en JSON) con las 4 escuelas reconvertidas: Filo (guerrero), Aza (batidor), Lumbre (mago), Cura (clérigo) — nombres de mundo Valcoria |
| Prerrequisitos | `pre_skill` con OR | igual + requisitos narrativos (actos de la Crónica desbloquean remates) |
| Talentos | 17 pasivas por atributo | mismos perfiles (sanguinario, capataz, orador…) ligados al sistema de Deuda y capitanes con memoria |
| Números | `val1..val5` opacos | cada valor con etiqueta visible en ficha (daño, duración, radio) |
