# 13 · Estadísticas del héroe — de qué está hecho

**Estado:** ✅ **aprobado por el dueño (aprobación en bloque, 2026-09-30). Documento final.**
**Enmienda 2026-10-01:** el dueño pidió un documento **propio** de estadísticas del héroe, separado
del de niveles (`12_NIVELES_DEL_HEROE.md`). Aquí viven **origen, atributos y todo lo que se deriva**
de ellos; las **stats del campo** (vida/ataque/defensa/daño) son de `../batalla/01_CIFRAS.md` y aquí
solo se **enlazan**.

> Cómo te creas (3 pasos: dificultad → nombre + 10 puntos → origen), en `../interfaz/` y en
> `js/scenes/sc_crea.js`. La **partida** ya guarda `atributos` (FUE/AGI/INT), `origen`, `honor`,
> `prestigio` y `moral`. Este documento dice **qué significa cada número**.

---

## 1. Los tres orígenes (ya en el código)

Eliges **un origen**; decora tu pasado y te da un sesgo, **no** una clase (no hay clases,
`05_PROGRESION.md` §1). Cifras **ya implementadas** en `construirPartida()`:

| Origen | Puntos | Oro inicial | Otros |
|---|---|---|---|
| **Soldado** | **+2 FUE** | 100 **+20** = 120 | Flag `origen_it_espada_gastada` (espada gastada) |
| **Noble arruinado** | — | 100 **+40** = 140 | **Honor 20** (base 10, +10) y **+1 prestigio** |
| **Mercader** | — | 100 **+50** = 150 | Flags `origen_it_queso_x4` y `origen_t_comercio` |

- **Dificultad «escaramuza»:** el oro inicial **×1,3** (soldado 156 · noble 182 · mercader 195).
- **Base común:** oro **100**, honor **10**, prestigio **0**, moral de campaña **50**
  (`js/scenes/sc_crea.js`, `js/core/save.js`).
- **El origen no cambia la verdad de la historia:** la noche del Paso es la misma para los tres
  (`../historia/02_PERSONAJES.md`).

---

## 2. Atributos (FUE · AGI · INT)

- **10 puntos a repartir** entre los tres (`PUNTOS_TOTALES = 10`), **mínimo 1** en cada uno.
- **Reparto por defecto:** FUE **4** · AGI **3** · INT **3** (`createDefaultSave`).
- **Cada atributo empieza a contar desde 3** (el «hombre corriente»): lo que pase de 3 es tu sesgo;
  lo que baje de 3 es tu precio.

| Atributo | Qué mueve | Regla ✅ |
|---|---|---|
| **FUE** (Fuerza) | Ataque **cuerpo a cuerpo** | `+1 de ataque` por punto |
| **AGI** (Agilidad) | **Aliento** y **Desvío** | `+0,5/s` de regeneración y `−1` de coste de Desvío cada 3 puntos |
| **INT** (Inteligencia) | **XP** y **trato** | `+5 %` de XP y `−2 %` de precio al comprar (regateo) |

- ✅ **Cerrado (2026-10-01):** las tres reglas están **aprobadas** (opción A); registro en
  `../DECISIONES.md`. Hoy en código solo **FUE** tiene efecto (el origen soldado, +2); AGI e INT
  se implementan en la Fase 2.
- **Techo de balance:** ningún reparto rompe el **daño máximo por golpe** de
  `../batalla/01_CIFRAS.md` §2 (90 héroe / 45 tropa). Los atributos matizan; el techo manda.

---

## 3. Stats derivadas (lo que ves en el HUD)

| Stat | De dónde sale | Dónde se fija |
|---|---|---|
| **Vida** | `120 + 10 × (nivel − 1)` (nivel 60 → **710**) | `12_NIVELES_DEL_HEROE.md` §2 · `../batalla/01_CIFRAS.md` §1 |
| **Ataque** | base por nivel (28 … **164** a nivel 60) **+ FUE** | `../batalla/01_CIFRAS.md` §2 |
| **Defensa** | base por nivel (18 … **177** a nivel 60) | `../batalla/01_CIFRAS.md` §2 |
| **Aliento** | **100**, regenera **5/s** (**+ AGI**) | `../batalla/01_CIFRAS.md` §3 |
| **Cadencia / Guardia / Desvío** | 1,2 s · 0,5 s · 0,35 s (**Desvío − AGI**) | `../batalla/01_CIFRAS.md` §3 |
| **Moral de campo de la unidad** | **100** al empezar | `../batalla/01_CIFRAS.md` §5 |
| **Moral de campaña** | **50** base (sube/baja por hechos) | `../sistemas/08_LUTO_Y_MORAL.md` |
| **Honor** | **10** (+10 noble) | Este doc §1 · `../sistemas/01_FIRMA.md` |
| **Prestigio** | **0** (+1 noble) | `createDefaultSave`, `../sistemas/00_MEMORIA_Y_DEUDA.md` |

- **Moral de campo ≠ moral de campaña:** la primera es de la batalla (`01_CIFRAS.md` §5); la
  segunda vive en el guardado (`SaveState.moral`, base 50) y la mueven el luto y los hechos.
- **Equipo y mejoras:** suben stats dentro de su rareza (`../contenido/04_ITEMS_Y_EQUIPO.md`);
  **nunca** cambian el rol ni pasan el techo.
- **Artefactos:** cambian **reglas**, no números (`../contenido/07_ARTEFACTOS.md`).

---

## 4. Del héroe a los demás (dónde mirar)

- **Tropas, compañeros y capitanes** usan las **stats base** de `../batalla/01_CIFRAS.md` §1–§2 y
  **escalan por nivel** con la fórmula de `12_NIVELES_DEL_HEROE.md` §5. El héroe no: su curva es
  explícita.
- **El enemigo de zona** sale con el nivel de su zona (`12_NIVELES_DEL_HEROE.md` §3).

---

## 5. Datos, tipos y validación

- **Datos:** `data/progresion.json` (vida base, incremento) y `data/origenes.json` **(nuevo
  propuesto)** — `{ id, bonos: { atributos, oro, honor, prestigio }, flags }`.
- **Tipos:** `Origen` y `Atributos` **ya existen** en `js/data/game_types.js`; el héroe ya guarda
  `atributos`, `origen`, `honor`, `prestigio` y `moral` (`SaveState`). **Sin campos nuevos.**
- **Validación:** esquema en `js/data/schemas.js` + cruce de los bonos con `BASE_GOLD`/`BASE_HONOR`
  de `sc_crea.js` y del reparto de atributos con `PUNTOS_TOTALES = 10`, en `tools/validate_data.js`.
- **Sistema puro:** `js/systems/progresion.js` aplica atributos y nivel; sin DOM, sin reloj.
- **Tests:** `tests/progresion.test.js` y `tests/scene_crea.test.js`: el reparto no pasa de 10
  puntos; ningún atributo baja de 1; los bonos de origen cuadran; ningún efecto supera el techo de
  daño.

---

## 6. Cifras que fija este documento

| Cifra | Valor |
|---|---|
| Orígenes | **3** (soldado · noble · mercader) |
| Puntos de atributo | **10** (mín. **1** cada uno) |
| Reparto por defecto | FUE 4 · AGI 3 · INT 3 |
| Punto neutro | **3** por atributo |
| Oro inicial | **100** (+20 · +40 · +50) · escaramuza ×1,3 |
| Nivel máximo del héroe | **60** (`12_NIVELES_DEL_HEROE.md`) |
| Honor / prestigio base | **10 / 0** (noble: **20 / 1**) |
| Moral de campaña | **50** base |
| FUE / AGI / INT | +1 ataque · +0,5/s aliento y −1 Desvío · +5 % XP y −2 % precio ✅ |

---

## 7. Qué entra en la demo (Fase 1) — y qué sigue

> **Hasta aquí la demo.** La **creación de partida** completa (dificultad, nombre, 10 puntos,
> origen), con los tres orígenes y sus bonos; **FUE** ya afecta al ataque; el héroe va del nivel
> **1 al 15** (**tope de la demo**; el juego completo llega a 60). Honor, prestigio y moral de
> campaña funcionan con sus valores base.

> **Y sigue el juego completo.** Los efectos de **AGI** e **INT** están **cerrados** (2026-10-01)
> y se **implementan** en la Fase 2-3 **con estas mismas reglas**: más filas en `origenes.json`, no
> un sistema nuevo.

---

## 8. Fuera de este documento

- Niveles, XP y zonas → `12_NIVELES_DEL_HEROE.md`
- Stats del campo y daño → `../batalla/01_CIFRAS.md`
- Cómo sube el héroe → `05_PROGRESION.md`
- Equipo y rarezas → `../contenido/04_ITEMS_Y_EQUIPO.md`
- Firma y honor → `01_FIRMA.md`
- Creación de partida (pantalla) → `js/scenes/sc_crea.js`
