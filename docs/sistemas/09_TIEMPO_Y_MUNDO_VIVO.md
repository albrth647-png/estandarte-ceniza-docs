# 09 · Tiempo y mundo vivo — lo que se mueve sin ti

**Estado:** ✅ **aprobado por el dueño (aprobación en bloque, 2026-09-30). Documento final.**

> El mundo **no espera al jugador** (`../historia/01_ESTRUCTURA.md`: «la carne la escribe la
> partida»). Cada día y cada estación, casas, deudores y caminos **avanzan solos**. Todo con el
> **día de juego** (`../mundo/05_TIEMPO_DEL_MUNDO.md`) y **determinista** (misma semilla = mismo
> mundo). Entra en la **Fase 2**; la demo lo tiene apagado.

---

## 1. Qué se mueve sin ti

| Se mueve | Ritmo | Efecto que notas |
|---|---|---|
| **Cobranzas de casas** | por estación | Deudas que se pagan o se enconan |
| **Precios** | por estación | Comida y hierro suben/bajan (`06_ECONOMIA.md` §5) |
| **Encargos** | cada 3-7 días | El tablón se renueva (`../misiones/01_TABLONES_Y_PORTAVOCES.md`) |
| **Rumores** | por lugar | Nacen y se enfrían (7 días) |
| **Rencores** | por hechos | Se heredan; marcan casas (`00_MEMORIA_Y_DEUDA.md` §7) |
| **Patrullas** | por tramo | Cambian de sitio; te buscan o se apartan |

---

## 2. Cómo se simula (barato y determinista)

- **No hay agentes caminando por el mapa** en tiempo real: el mundo se resuelve **por eventos** al
  **avanzar el día** (`../mundo/05_TIEMPO_DEL_MUNDO.md` §3).
- **Semilla de partida:** mismas decisiones y mismo día → mismo mundo.
- **Sin reloj real:** `js/systems/mundo_vivo.js` recibe el día de juego y el RNG inyectados (regla 9 de
  `../../AGENTS.md`).

---

## 3. Qué le pasa a lo que dejaste a medias

- **Encargo vencido:** lo coge otro; el mundo no se detiene (`../misiones/01_TABLONES_Y_PORTAVOCES.md` §4).
- **Deuda sin cobrar:** el acreedor busca a otro, o la hereda (`00_MEMORIA_Y_DEUDA.md` §5).
- **Casa sin rostro:** si muere su último miembro, se **extingue** y la deuda desaparece.
- **Nada se evapora solo:** la deuda viaja; el mundo la reasigna.

---

## 4. La Crónica como ventana

- Todo lo importante que pasa sin ti deja **una línea** en la Crónica (`04_CRONICA.md`): el jugador
  se entera sin que el juego se lo cuente en la cara.
- **Regla:** el mundo vivo **informa**, no **persigue**.

---

## 5. Datos, tipos y validación

- **Datos (por crear):** `data/mundo_vivo.json` — `{ evento, ritmo_dias, efecto, condicion }`.
- **Tipos:** `EventoMundo` en `js/data/game_types.js`.
- **Validación:** cada `efecto` referencia un sistema existente (precio, encargo, rencor); sin
  referencia, falla (`tools/validate_data.js`).
- **Sistema puro:** `js/systems/mundo_vivo.js`; sin DOM, sin reloj.
- **Tests (por escribir):** `tests/mundo_vivo.test.js`: el mundo avanza solo con el día; la misma semilla repite
  los eventos; ningún evento deja una deuda sin salida.

---

## 6. Cifras que fija este documento

| Cifra | Valor |
|---|---|
| Ritmo base | por **estación** (28 días) para precios/casas |
| Tablones | cada 3-7 días |
| Rumores | 7 días |
| Agentes en tiempo real | **ninguno** |
| Determinismo | misma semilla = mismo mundo |
| Demo | **apagado** (Fase 2) |

---

## 7. Qué entra en la demo (Fase 1) — y sigue

> **Hasta aquí la demo.** El mundo vivo está **apagado**: solo avanzan los plazos de encargos,
> favor y rumor (`../mundo/05_TIEMPO_DEL_MUNDO.md` §2).

> **Y sigue el juego completo.** El **mundo vivo** entra en la **Fase 2** con estas tablas:
> casas que cobran, precios que se mueven y rencores que crecen **mientras no miras**.

---

## 8. Fuera de este documento

- Días y estaciones → `../mundo/05_TIEMPO_DEL_MUNDO.md`
- Cadenas y rumores → `../misiones/03_CADENAS_Y_RUMORES.md`
- Memoria y rencores → `00_MEMORIA_Y_DEUDA.md`
- Crónica → `04_CRONICA.md`
- Economía → `06_ECONOMIA.md`
