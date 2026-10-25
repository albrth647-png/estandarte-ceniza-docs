# 05 · Encargos de la historia — los que no se generan solos

**Estado:** ✅ **aprobado por el dueño (aprobación en bloque, 2026-09-30). Documento final.**

> Los encargos generados (`03_CADENAS_Y_RUMORES.md`) son la carne; **estos once son la columna
> vertebral** (`../historia/01_ESTRUCTURA.md`). Se escriben a mano, **no caducan** y llevan la
> trama. Las líneas, en `../historia/04_GUION.md`.

---

## 1. Los encargos fijos

| id | Quién lo da | Acto | Qué es |
|---|---|---|---|
| `hist_primera_deuda` | Doña Sira (cadalso) | Prólogo | Cobrar 20 marcos y empezar a pagar la espada |
| `hist_peaje` | Portavoz de Vega Quemada | I | El viejo que se fugó con el peaje |
| `hist_marcados` | Portavoz de Casar de la Nava | I | Reunir a los Marcados (reclutar) |
| `hist_herreruela` | El herrero / la escribanía | I | Deuda del herrero y el trato de la marca |
| `hist_posada` | La posadera (Deuda Blanca) | I | El primer favor: proteger a un huido |
| `hist_cruce` | Portavoz del cruce | I | Limpiar el camino → **primera batalla** |
| `hist_paginas` | El viejo del gremio | I (giro) | Descubrir las **páginas arrancadas** |
| `hist_contratos` | Doña Sira | II | Averiguar por qué faltan los contratos |
| `hist_altamir` | Casa Altamir | II | Los tres giros: Ambrosio · la viuda · el Teniente |
| `hist_teniente` | (confesión) | II | La verdad de la puerta (flashback 2) |
| `hist_asamblea` | Los Escribanos | III | Preparar y vivir la **asamblea** |

- **Acto I = 6 encargos, uno por sitio** (`../produccion/00_ALCANCE.md` §3); el del Patio del Cadalso (`hist_primera_deuda`) arranca en el prólogo.

---

## 2. Qué abre y cierra cada uno

- **Cada encargo fijo pone una bandera** (`espada_reclamada`, `paginas_arrancadas`,
  `teniente_vivo`, `final_*`) que abre el siguiente (`../historia/04_GUION.md` §8).
- **Los 6 del Acto I** se pueden hacer en **cualquier orden** (excepto `hist_cruce`, que viene
  después de tener compañía); todos llevan al **giro**.
- **`hist_asamblea`** no se ofrece hasta que `hist_altamir` y `hist_teniente` cierran: es el
  punto de no retorno (`../historia/01_ESTRUCTURA.md`).

---

## 3. Cómo se combinan con los generados

- **La costura no se nota:**
  1. La columna fija el **marco** (un sitio, un PNJ, una bandera).
  2. Los generados llenan el **tiempo entre hitos** (cobranzas, rumores, batallas).
  3. Si falta un hito, **el generado no lo sustituye**: espera.
- **Regla:** un encargo generado **nunca** contradice una bandera de la columna. Si la tocaría,
  se **descarta** en la validación (`02_ESTRUCTURA_DE_ENCARGO.md` §6).

---

## 4. Qué pasa si el jugador los ignora

- **No caducan** (`01_TABLONES_Y_PORTAVOCES.md` §4): se pueden retomar siempre.
- **El mundo sigue y cobra:** mientras no avanzas, la memoria y el mundo vivo hacen su trabajo
  (te buscan, suben precios, abren rencores). Ignorar la columna **tiene coste**, no bloqueo.
- **Nunca** se pierde la partida por no seguir la columna: se llega más tarde y con más deudas
  encima.

---

## 5. Claves `txt_*`

- **Esquema:** `txt_enc_hist_<hito>_<n>` para el cartel y el diálogo; las líneas largas viven en
  `../historia/04_GUION.md`.
- **Paridad ES/EN obligatoria** (regla 10). Muestra:

| Clave | ES | EN |
|---|---|---|
| `txt_enc_hist_primera_deuda_t` | «Veinte marcos. Empieza por ahí.» | "Twenty marks. Start there." |
| `txt_enc_hist_paginas_t` | «Alguien arrancó páginas.» | "Someone tore out pages." |
| `txt_enc_hist_asamblea_t` | «La asamblea te espera en el Paso.» | "The assembly awaits at the Pass." |

---

## 6. Datos, tipos y validación

- **Datos (por crear):** `data/encargos_historia.json` — mismo formato que `02_ESTRUCTURA_DE_ENCARGO.md` §1,
  con `plazo_dias: 0` (no caducan) y `cadenas` de la columna.
- **Tipos:** `EncargoHistoria` en `js/data/game_types.js` (una sola vez, regla 4).
- **Validación:** esquema en `js/data/schemas.js` + cruce de **banderas** y orden de hitos en
  `tools/validate_data.js`: un hito no puede pedir una bandera que no existe antes.
- **Sistema puro:** los hitos se resuelven en `js/systems/encargos.js` con las banderas de
  `SaveState`; sin DOM ni reloj.
- **Tests (por escribir):** `tests/encargos_historia.test.js`, mínimo 3 casos (normal, borde, error): el orden de
  los 6 del Acto I es libre; `hist_asamblea` no se ofrece antes de tiempo; ninguna bandera queda
  inalcanzable.

---

## 7. Cifras que fija este documento

| Cifra | Valor |
|---|---|
| Encargos fijos | **11** (6 en el Acto I) |
| Plazo | **0** (no caducan) |
| Orden del Acto I | libre entre los 6 (excepto tras tener compañía) |
| Banderas de trama | `espada_reclamada`, `paginas_arrancadas`, `teniente_vivo`, `final_*` |
| Punto de no retorno | `hist_asamblea` |
| Claves | `txt_enc_hist_*` con paridad ES/EN |

---

## 8. Qué entra en la demo (Fase 1) — y qué sigue

> **Hasta aquí la demo.** Los **6 encargos, uno por sitio**, y el **giro** de las páginas
> (`hist_primera_deuda` … `hist_paginas`), con sus banderas y su orden libre
> (`../produccion/00_ALCANCE.md`).

> **Y sigue el juego completo.** `hist_contratos`, `hist_altamir`, `hist_teniente` y
> `hist_asamblea` (Actos II-III) usan **el mismo formato y el mismo motor**: crecer = más filas en
> `encargos_historia.json`, no un sistema nuevo.

---

## 9. Fuera de este documento

- La estructura y los giros → `../historia/01_ESTRUCTURA.md`
- Las líneas de las escenas → `../historia/04_GUION.md`
- Formato de datos → `02_ESTRUCTURA_DE_ENCARGO.md`
- Cadenas y rumores → `03_CADENAS_Y_RUMORES.md`
- Capitanes y némesis de la trama → `../contenido/02_CAPITANES_Y_NEMESIS.md`
