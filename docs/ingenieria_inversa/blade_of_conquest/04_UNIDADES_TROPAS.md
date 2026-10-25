# 04 · UNIDADES Y TROPAS — Cómo se construyen las 23 tropas

> Dossier 04. El sistema completo de tropas de BoC, extraído de `assets/datas/units.dat`
> (XML en claro, 23 registros). Esto es "cómo se hace" — y la base para hacerlo mejor.

## 1. El modelo de una unidad (todos los campos)

| Campo | Significado | Ejemplo (Farmer) |
|---|---|---|
| `unit_id` | id único | 1 |
| `unit_name` / `_cn` | nombre EN/中文 | Farmer / 农兵 |
| `model` | id de modelo visual (`md.dat`/`mu.dat`) | 3 |
| `u_face` | retrato | uf_farmer1.png |
| `main_class` | clase base (2 = infantería) | 2 |
| `weapon` | arma base | 0 |
| `skills` | habilidades de la tropa | (vacío en milicias) |
| `pre_unit` | **unidad previa de la que mejora** (0 = inicial) | 0 |
| `unit_level` / `max_level` | nivel de recluta / techo de niveles | 0 / 10 |
| `r_level` | **nivel requerido del jugador** para reclutar | 0 |
| `hire_price` | coste de recluta | 10 |
| `up_price` | coste de **mejorar desde la unidad previa** | 1 |
| `att_int` | intervalo de ataque (s) | 2.8 |
| `ratt_int` / `ratt_eff` | intervalo de ataque a distancia y efecto de proyectil | 0 / eft_arraw1_ |
| `base_stat` | stats base: `mhp,260\|atk,40\|def,4\|cri,30\|mvspd,50\|atspd,10` | — |
| `growth` | **cuánto suma cada nivel**: `mhp,400\|atk,100\|def,40\|cri,100\|mvspd,50\|atspd,40` | — |
| `drops` | botín que suelta al morir | `100.0:1,1,3,0,0;…` |
| `exp` | experiencia que otorga al matarlo | 60 |

**Fórmula central (deducida de la tabla y confirmada por `SGUnitsData::getLevelUpExp`):**
una unidad de nivel N tiene `stat = base_stat + growth × N`, gana nivel con experiencia
acumulada, y su tope es `max_level`. El coste de mejora (`up_price`) ronda la mitad del
precio de recluta del siguiente escalón.

## 2. Las seis líneas de tropa (árbol por `pre_unit`)

```
Farmer (1) ─┬─→ Swordsman (10) → Senior (11) → Elite (12) → Royal Warriors (13)
            ├─→ Pikeman (20) → Senior (21) → Elite (22) → Royal Guard (23)
            ├─→ Trainee Archer (30) → Archer (31) → Sniper (32) → Marksman (33)
Swordsman ──→ Light Cavalry (40) → Elite (41) → Royal Cavalry (42)
Pikeman ────→ Lance Cavalry (50) → Elite (51) → Royal Lance (52)
Monk (60) ──→ Crusader (61) → Holy Warrior (62)
─── enemigo ─── Skeleton Soldier (101)
```

Precios de recluta por escalón (milicia): 10 → 80 → 160 → 320 → 480.
Requisito de nivel del héroe (`r_level`): 0 → 5 → 15 → 25 → 35.

## 3. Stats especiales por familia (lo que da sabor a cada línea)

- **Arqueros** añaden 4 campos a `base_stat`:
  `ratk` (ataque a distancia 35–50), `stspd` (velocidad de proyectil 20–26),
  `strag` (**alcance 600→750**), `stdev` (**dispersión 20→50**: más nivel, más dispersión…).
- **Monjes** añaden `mmp` (mana 80→120) y `sdr` (radio 3→5): hechiceros de apoyo.
- **Caballería** destaca en `mvspd` 90–80 (vs 50–65 a pie) y `mhp` alto (500–700).
- **Esqueleto** (enemigo) lleva `mdef` (defensa mágica) — solo él.

## 4. Cómo se recluta y mejora (flujo)

1. En cuartel (`BarracksScene.csb` + `AEUpgradeUnitBox`): lista de unidades disponibles
   filtrada por `r_level` del jugador y por el sitio (ciudad/aldea dan lo básico).
2. Pagar `hire_price` → entra en la hueste; pagar `up_price` con la unidad previa →
   **convierte** a la tropa en la siguiente del árbol (conserva nivel/efectivos según
   reglas del motor).
3. En batalla, cada tropa muerta puede soltar botín (`drops`) y da `exp` al matador;
   la unidad superviviente acumula experiencia hasta subir `max_level` niveles.

## 5. Decisión para Valcoria — el mismo árbol, mucho mejor

| Aspecto | BoC | Valcoria |
|---|---|---|
| Modelo de datos | XML privado con stats compactos | JSON `datos/unidades.json` versionado con validador (mismos campos + `etiqueta` y `rol` legibles) |
| Fórmula de nivel | `base + growth×N` implícita | fórmula explícita documentada en `docs/batalla/01_CIFRAS.md` — **sin colas de curva ocultas** |
| Árbol de mejora | lineal por `pre_unit` | mismo árbol (milicia→élite, arco, lanza, caballería, fe) + **ramas de veterano** por actos del jugador |
| Retratos/modelos | sprites frame a frame | personajes **KayKit + ILB** con animación esqueletal, equipo visible |
| Feedback | números en caja (`AEGameUtils::showUnitInfoBox`) | ficha de tropa con gráficos de progresión, daño en vivo, "deuda de sangre" narrativa |
| Dispersión de arco | `stdev` fija por nivel | dispersión dependiente de moral/aliento y terreno — arquería legible |
