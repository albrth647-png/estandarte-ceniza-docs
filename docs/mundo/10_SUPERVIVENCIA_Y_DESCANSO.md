# 10 · Supervivencia y descanso — comer, dormir, aguantar

**Estado:** ✅ **aprobado por el dueño (aprobación en bloque, 2026-09-30). Documento final.**

> Una compañía de deudores **come y duerme** o se deshace. Aquí está **cuánto aguanta tu gente** y
> cómo se recupera. Los precios, en `../sistemas/06_ECONOMIA.md`; la moral, en
> `../sistemas/08_LUTO_Y_MORAL.md`. La demo usa **posada y fuego**.

---

## 1. Comer

- Cada tropa consume **1 ración al día** (el héroe, 1).
- **Un rehén también come:** mientras espera en un cuarto, consume **1 ración/día**
  (`../sistemas/02_PRISIONEROS.md` §3.1).
- **Sin raciones:** la moral baja **−5/día** y la lealtad cae (`../sistemas/10_LEALTAD_Y_DESERCION.md`).
- **De dónde sale la comida:** comprar (2 oro/ración), grano de aldea, caza (`../contenido/08_ANIMALES_Y_CRIATURAS.md`) o botín.
- **La comida se estropea despacio** en el camino (no hay gestión de nevera): se simplifica.

---

## 2. Descansar

| Dónde | Coste | Recupera |
|---|---|---|
| **Posada** | 5 oro/noche (+ cena) | Vida y moral **completas**; rumores (`../misiones/03_CADENAS_Y_RUMORES.md`) |
| **Fuego de camino** | leña (`../mundo/07_PROPS_Y_VEGETACION.md`) | Vida parcial; moral según clima |
| **Campamento** | leña + tiempo | Vida parcial; sin rumores |
| **Refugio** | 0 | Techo y fuego; sin servicio |

- **Dormir es una acción de un día de juego**, no un temporizador real (`05_TIEMPO_DEL_MUNDO.md`).
- **De noche, sin techo:** peligro `×2` y moral baja (`02_VIAJE_Y_ENCUENTROS.md` §5).

---

## 3. Heridas y salud

- **Vida del héroe** recupera con descanso y con el **barbero** (`../contenido/00_TROPAS.md` §3.3).
- **Heridas de campaña** (Fase 4): las cura el barbero fuera de combate; sin él, se arrastran
  (`../arte/00_ESTILO.md`).
- **La niebla, el frío y el hambre no matan solos:** debilitan, nunca acaban la partida
  (regla: *el fallo nunca atasca*).

---

## 4. Caer lejos de todo

- Si caes **lejos de un sitio** (Pilar 3, `../sistemas/02_PRISIONEROS.md` §7): te puede **arrastrar**
  un aldeano, **rescatarte** un Hermano de sangre, o **cobrarte** el captor. **Nunca** un Game Over.
- Si estás lejos y **sin comida**, el mundo ofrece una salida: posada a crédito, encargo de
  `escoltar`, o la aldea que te fía (`00_MEMORIA_Y_DEUDA.md`).

---

## 5. Datos, tipos y validación

- **Datos:** `data/supervivencia.json` — `{ racion_dia, descanso, coste, penalizacion_hambre }`.
- **Tipos:** `Descanso` y `Racion` en `js/data/game_types.js`.
- **Validación:** cruce de precios con `data/economia.json` y de props (leña) con `data/props.json`
  en `tools/validate_data.js`.
- **Sistema puro:** `js/systems/supervivencia.js` — consumo, descanso y penalización; sin DOM ni
  reloj (día por `save.day`).
- **Tests:** `tests/supervivencia.test.js`: sin raciones la moral baja; dormir en posada recupera
  entero; el hambre no mata.

---

## 6. Cifras que fija este documento

| Cifra | Valor |
|---|---|
| Ración por unidad y día | **1** |
| Sin raciones | moral **−5/día** |
| Posada | 5 oro/noche (recupera completo) |
| Fuego / campamento | leña · recupera parcial |
| Noche sin techo | peligro ×2 · moral baja |
| Hambre / frío letal | **nunca** solo |

---

## 7. Qué entra en la demo (Fase 1) — y qué sigue

> **Hasta aquí la demo.** **Posada y fuego** (como fija `02_VIAJE_Y_ENCUENTROS.md` §5): comer,
> dormir, recuperar y la penalización por hambre; sin heridas de campaña.

> **Y sigue el juego completo.** Campamentos, heridas, caza y clima duro entran en la **Fase 4**
> con estas mismas reglas; crecer = más filas en `supervivencia.json`.

---

## 8. Fuera de este documento

- Precios → `../sistemas/06_ECONOMIA.md`
- Moral y luto → `../sistemas/08_LUTO_Y_MORAL.md`
- Clima → `09_CLIMA_Y_ESTACIONES.md`
- Comidas y bebidas → `../contenido/14_COMIDAS_Y_BEBIDAS.md`
- Caer → `../sistemas/02_PRISIONEROS.md`
