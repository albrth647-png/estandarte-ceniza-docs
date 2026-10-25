# 06 · Batallas de la historia — las que no se generan solas

**Estado:** ✅ **aprobado por el dueño (aprobación en bloque, 2026-09-30). Documento final.**

> La trama monta **pocas batallas, y grandes**: la mayoría de los combates del juego los **genera
> el sistema** (`../contenido/01_ENEMIGOS.md` §1). Aquí están **las fijas**, con su montaje y sus
> consecuencias. Las reglas, en `00_REGLAS.md`; los campos, en `05_CATALOGO_DE_CAMPOS.md`.

---

## 1. Las batallas fijas

| id | Momento | Bando enemigo | Campo | Unidades | Consecuencia |
|---|---|---|---|---|---|
| `bat_ensenanza` | Acto I · Cruce de las Dos Sendas | `cuervos_del_camino` | `llanura_camino` | 5-6 | Enseña moral, huida y las 4 salidas |
| `bat_aprieta` | Acto I · camino de Herreruela | `cuadrilla_de_casa` | `aldea` | 5-6 | Primer capitán con nombre; introduce el volteo |
| `bat_cierre_acto` | Acto I · final del acto | `patrulla_de_altamir` | `bosque` | **8** | El giro de las páginas arrancadas |
| `bat_asamblea` | Acto III · el Paso | la casa que elijas | `puerta_ciudad` | 10+ | Cierra la historia (según el final) |

- **La demo son las 3 del Acto I** (`../produccion/00_ALCANCE.md` §3): la que enseña, la que
  aprieta y la del cierre.

---

## 2. Montaje (cómo se hace grande una batalla fija)

1. **Antes:** una escena corta que pone el **porqué** (2-6 líneas, `../historia/03_RECORRIDO.md`).
2. **Aviso y despliegue** como cualquier campo (`00_REGLAS.md` §2), pero con **capitanes con
   nombre** y **bandera de casa**.
3. **Durante:** las reglas son **las mismas**; lo que cambia es la **composición** y que el enemigo
   **te busca** (memoria/Firma, `03_IA_Y_ORDENES.md` §3).
4. **Después:** las **4 salidas** (`../sistemas/02_PRISIONEROS.md`) con **personajes que vuelven**.

- **Ninguna batalla fija usa reglas especiales:** si el jugador pierde, **la historia sigue**
  (`01_FASES.md` §1 regla 7).

---

## 3. La batalla del Paso (flashback)

- La caída del Paso del Juramento es **el recuerdo que explica tu condena**
  (`../historia/02_PERSONAJES.md`).
- **✅ Decidido (2026-10-01): es una ESCENA RECUERDO.** La caída del Paso se ve como **recuerdo**
  (la noche de la guardia y la puerta, `../historia/01_ESTRUCTURA.md` y
  `../historia/03_RECORRIDO.md`), **no** como defensa jugable.
  - Por eso **no** se juega campo `puerta_ciudad`: la derrota del Paso se **siente**, no se juega.
  - **No consume** recursos ni vidas reales (es un recuerdo) y su verdad se completa en el Acto II.

---

## 4. Qué pasa si pierdes una batalla fija

- **Nunca bloquea:** caes, el mundo cobra (rescate/servicio/rehén, `../sistemas/02_PRISIONEROS.md` §7) y la
  trama **espera**.
- La batalla se puede **reintentar** más tarde con más gente o mejor posición; el enemigo
  **recuerda** que le ganaste antes (memoria) o que huiste.
- **Las consecuencias narrativas no se pierden:** el hito de la trama se reencauza.

---

## 5. Datos, tipos y validación

- **Datos (por crear):** `data/batallas_historia.json` — `{ id, momento, enemigo, campo, unidades, banderas }`.
- **Tipos:** `BatallaHistoria` en `js/data/game_types.js`.
- **Validación:** `campo` existe en `data/campos.json`, `enemigo` en `data/enemigos.json`; las
  `banderas` son las de `../historia/04_GUION.md` (`tools/validate_data.js`).
- **Sistema puro:** el montaje usará `js/systems/campo.js` (por construir); la escena solo pinta.
- **Tests (por escribir):** `tests/batallas_historia.test.js`: cada batalla fija es **perdible sin bloquear**; las
  banderas quedan alcanzables; el flashback guionizado no da recursos.

---

## 6. Cifras que fija este documento

| Cifra | Valor |
|---|---|
| Batallas fijas | **4** (3 en el Acto I) |
| Unidades Acto I | 5-6 · **8** en el cierre |
| Unidades Acto III | 10+ |
| Reglas especiales | **ninguna** |
| Derrota | nunca bloquea · se puede reintentar |
| Flashback del Paso | ✅ **escena recuerdo** (decidido 2026-10-01) |

---

## 7. Qué entra en la demo (Fase 1) — y qué sigue

> **Hasta aquí la demo.** Las **3 batallas del Acto I** (`bat_ensenanza`, `bat_aprieta`,
> `bat_cierre_acto`) con sus capitanes y consecuencias.

> **Y sigue el juego completo.** `bat_asamblea` (Acto III) y las batallas de casa del Acto II se
> montan **con las mismas reglas y los mismos campos**; crecer = más filas y más unidades, no
> batallas «con guion».

---

## 8. Fuera de este documento

- Reglas y fases → `00_REGLAS.md`
- Catálogo de campos → `05_CATALOGO_DE_CAMPOS.md`
- IA y capitanes → `03_IA_Y_ORDENES.md`
- Prisioneros → `../sistemas/02_PRISIONEROS.md`
- La estructura de la trama → `../historia/01_ESTRUCTURA.md`
