# 05 · Progresión — cómo sube el héroe y la compañía

**Estado:** ✅ **aprobado por el dueño (aprobación en bloque, 2026-09-30). Documento final.**

> El héroe **sube**, pero con **techo**: el juego no premia al que acumula, premia al que cobra y
> recuerda. Las cifras de vida/ataque, en `../batalla/01_CIFRAS.md`; el aforo, en
> `../contenido/00_TROPAS.md` §4. **La escala completa (héroe, tropas y zonas) vive en
> `12_NIVELES_DEL_HEROE.md`.**

---

## 1. Niveles del héroe

- **Nivel 1 … 60** (`NIVEL_MAX = 60` ya en `js/core/save.js`); **la demo llega hasta el 15**
  (`12_NIVELES_DEL_HEROE.md` §1).
- **Vida:** `120 + 10 × (nivel − 1)` (nivel 60 → **710**); ataque/defensa, en `../batalla/01_CIFRAS.md` §2.
- **XP:** `60 × nivel` para subir (tabla completa y bandas de zona en `12_NIVELES_DEL_HEROE.md` §2).
- **Se sube por:** cerrar encargos, ganar batallas y **resolver deudas** (no por matar a lo bruto).
- **Sin clases ni talentos:** el héroe es **un deudor con espada**, no un árbol de talentos de
  estadísticas. Lo que **sí** tiene es un **árbol de habilidades activas/pasivas** que se **elige**
  con puntos (`../contenido/06_HABILIDADES.md` §4): no da poder, da **elección**.

---

## 2. Qué ganas al subir

| Al subir | Efecto |
|---|---|
| **Vida / daño** | Los de `../batalla/01_CIFRAS.md` |
| **Aforo** | +2 por nivel (`../contenido/00_TROPAS.md` §4) |
| **Puntos de juramento** | **1 cada 6 niveles** (6 · 12 · … · 60) → **10**, para el árbol de habilidades (`../contenido/06_HABILIDADES.md` §4) |
| **Cabida de encargos** | Sin cambio (5, `../misiones/01_TABLONES_Y_PORTAVOCES.md`) |
| **Acceso** | Puertas por Firma y memoria, **no** por nivel |

- **El nivel no da puertas sociales:** eso es la **Firma** (`01_FIRMA.md`) y la **memoria**
  (`00_MEMORIA_Y_DEUDA.md`). El nivel da **aguante**.

---

## 3. Progresión de las tropas

- **Veteranía** por batallas ganadas (`../contenido/00_TROPAS.md` §6): a los hitos, **+2 ataque** o
  **+4 vida** (a elegir por rol).
- **Techo:** la mejora no rompe el balance de `../batalla/01_CIFRAS.md`; los montados y
  especialistas cierran sus cifras en la Fase 4.
- **El que muere, muere:** no hay resurrección; el luto se paga (`08_LUTO_Y_MORAL.md`).

---

## 4. Mejoras duras (Fase 5)

- Las mejoras **duras** (que cambian cómo juegas, no solo números) llegan en la **Fase 5**
  (`../produccion/01_FASES.md` §6), con base en `../VISION_JUEGO_COMPLETO.md`.
- **El árbol de habilidades no es una mejora dura de Fase 5:** es de la **Fase 3** y su sitio es
  `../contenido/06_HABILIDADES.md` §4 (elección entre pocas habilidades, no potencia).
- **Nunca** rompen el guardado: son aditivas y acotadas.

---

## 5. Datos, tipos y validación

- **Datos:** `data/progresion.json` — `{ nivel_max, vida_base, incremento, veteranias }`.
- **Tipos:** `Progresion` y `Veterania` en `js/data/game_types.js`.
- **Validación:** coherencia con `NIVEL_MAX` de `save.js` y con `../batalla/01_CIFRAS.md` §1
  (`tools/validate_data.js`).
- **Sistema puro:** `js/systems/progresion.js` — sube nivel y veteranía; sin DOM ni reloj.
- **Tests:** `tests/progresion.test.js`: el nivel no pasa de 15; la vida cuadra con la fórmula; la
  mejora no supera el techo de balance.

---

## 6. Cifras que fija este documento

| Cifra | Valor |
|---|---|
| Nivel máximo | **60** |
| Vida del héroe | 120 + 10 × (nivel − 1) (710 a 60) |
| Aforo | +2 por nivel (techo 40, nivel 18) |
| Escala y zonas | `12_NIVELES_DEL_HEROE.md` |
| Puntos de juramento | 1 cada 6 niveles (+1 por deuda mayor, **tope total 10**) → ≤ 10 |
| Veteranía | +2 ataque o +4 vida por hito |
| Mejoras duras | Fase 5 |
| Sube por | encargos, batallas, deudas |

---

## 7. Qué entra en la demo (Fase 1) — y qué sigue

> **Hasta aquí la demo.** Niveles **1-15** (tope de la demo; el juego completo llega a 60) con la
> fórmula de vida, subida por encargos y batallas, los **puntos de juramento** (nivel 6 en
> adelante) con el **primer piso** del árbol de habilidades
> (`../contenido/06_HABILIDADES.md` §4.3) y la primera veteranía de tropa.

> **Y sigue el juego completo.** Las **mejoras duras** y las cifras de montados/especialistas
> entran en Fase 4-5 **sin cambiar el techo** ni el guardado.

---

## 8. Fuera de este documento

- Vida y daño → `../batalla/01_CIFRAS.md`
- Aforo y veteranía → `../contenido/00_TROPAS.md`
- Árbol de habilidades → `../contenido/06_HABILIDADES.md` §4
- Escala de niveles y zonas → `12_NIVELES_DEL_HEROE.md`
- Firma y puertas → `01_FIRMA.md`
- Fases → `../produccion/01_FASES.md`
