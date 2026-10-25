# 04 · PNJ — la gente que llena Valcoria

**Estado:** ✅ **aprobado por el dueño (aprobación en bloque, 2026-09-30). Documento final.**

> Todo PNJ es un **deudor, un acreedor o un testigo** (`../sistemas/00_MEMORIA_Y_DEUDA.md`).
> Nadie es decorado. Aquí está **quién vive en el mundo, qué hace y qué recuerda**. Las fichas de
> sitio, en `03_LUGARES.md`; sus textos, en `../historia/08_TEXTO_DEL_MUNDO.md`.

---

## 1. Los oficios (roles)

| Oficio | Qué hace | Es «relevante» |
|---|---|---|
| **Portavoz** | Habla por la aldea; publica encargos | Sí |
| **Posadero/a** | Da cama, comida y **rumores** | Sí |
| **Escribano de la Sangre** | Escribe deudas; enmienda la Firma | Sí |
| **Herrero / remendón** | Repara, vende hierro | No (ligero) |
| **Mercader** | Compra y vende | No |
| **Aldeano/a** | Trabaja; recuerda y habla | No |
| **Escribano joven** | El que te lee la sentencia | Sí (historia) |
| **Marcado** | Se alista contigo | No (ligero) |

- **Relevante** = memoria completa (`00_MEMORIA_Y_DEUDA.md` §2.2); el resto, **memoria ligera**.

---

## 2. Rutinas (vida sin el jugador)

- Cada PNJ tiene una **rutina ligera**: dónde está al amanecer, mediodía, atardecer y noche
  (`../mundo/05_TIEMPO_DEL_MUNDO.md`).
- **No caminan por simulación real:** están en un **punto por franja**; el jugador los ve donde
  toca. Barato y suficiente.
- **De noche** se cierran puertas y suben los peligros (`02_VIAJE_Y_ENCUENTROS.md` §5).

---

## 3. Qué dicen y qué recuerdan

- **Dicen** según su banda de memoria y su Firma contigo: saludo, queja, aviso o amenaza.
- **Recuerdan** sus hechos (`00_MEMORIA_Y_DEUDA.md` §4): un perdón, un robo, una deuda.
- **El cupo por lugar es 25** (`00_MEMORIA_Y_DEUDA.md` §8): el lugar no «acuerda» más gente de la
  que se ve.

---

## 4. Qué hacen fuera de la conversación

| Se mueven | Se quedan |
|---|---|
| Portavoces, mercaderes, patrullas (de paso) | Aldeanos, herreros, posaderos (de su sitio) |
| Un PNJ puede **buscarte** (rumor/encargo) | Un PNJ puede **esconderse** si le temes |

- **Nacen y mueren con la partida:** un PNJ puede morir en una batalla o por tu mano; su casa lo
  hereda (`00_MEMORIA_Y_DEUDA.md` §5).

---

## 5. Datos, tipos y validación

- **Datos (por crear):** `data/pnj.json` — `{ id, oficio, lugar, relevante, rutina, semilla }`.
- **Tipos:** `PNJ` en `js/data/game_types.js`.
- **Validación:** cruce de `lugar` con `lugares.json` y de `relevante` con el cupo (§8 de memoria);
  sin validador no arranca (`tools/validate_data.js`).
- **Sistema puro:** rutinas y cupos en `js/systems/pnj.js`; sin DOM, sin reloj (franja por
  día de juego).
- **Tests (por escribir):** `tests/pnj.test.js`: no se superan 25 fichas por lugar; un relevante tiene memoria
  completa; una rutina no deja a un PNJ «sin sitio».

---

## 6. Cifras que fija este documento

| Cifra | Valor |
|---|---|
| Oficios | **8** |
| Cupo por lugar | **25** fichas |
| Franjas de rutina | **4** (amanecer · mediodía · atardecer · noche) |
| Relevantes | según historia + capitanes (≤ 60 en total) |
| Herencia | hijo 100 % · casa 50 % |

---

## 7. Qué entra en la demo (Fase 1) — y qué sigue

> **Hasta aquí la demo.** Los **12 relevantes** del Acto I y los oficios de los 6 sitios (portavoz,
> posadero, herrero, aldeanos), con rutinas de 4 franjas y memoria ligera para el resto.

> **Y sigue el juego completo.** Las ciudades y zonas nuevas añaden PNJ **con este mismo formato y
> cupo**; crecer = más filas en `pnj.json`, no más memoria por cabeza.

---

## 8. Fuera de este documento

- Fichas de sitio → `03_LUGARES.md`
- Tiempo y rutinas → `05_TIEMPO_DEL_MUNDO.md`
- Memoria → `../sistemas/00_MEMORIA_Y_DEUDA.md`
- Textos → `../historia/08_TEXTO_DEL_MUNDO.md`
