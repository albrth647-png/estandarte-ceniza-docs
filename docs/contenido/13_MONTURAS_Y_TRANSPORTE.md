# 13 · Monturas y transporte — cómo se viaja

**Estado:** ✅ **aprobado por el dueño (aprobación en bloque, 2026-09-30). Documento final.**

> Decisión de diseño: **hasta el Acto I el jugador va a pie, siempre.** El Pilar 4 es *«explorar
> Valcoria a pie»* (`../VISION_JUEGO_COMPLETO.md`) y montar a caballo en la demo lo rompería (y
> encarecería el arte). **Ampliación 2026-10-01:** **después de la demo (Capítulo 1) se desbloquea
> la profesión Equitación** (`../sistemas/14_PROFESIONES.md` §4): **se compra** como cualquier
> profesión y a partir de ahí puedes montar. El caballo existe desde el minuto cero **en el mundo**
> (mensajeros, convoyes), no bajo tus piernas. Lo que sí puedes tener de verdad es una **carreta de
> compañía** que carga y transporta. El viaje por días, en `../mundo/02_VIAJE_Y_ENCUENTROS.md`;
> los cruces, en `../mundo/08_AGUA_RIOS_Y_PUENTES.md`.
>
> **Ids, cifras y la carreta son propuesta de diseño** (cambiables → `../DECISIONES.md`).

---

## 1. La decisión base: a pie

- **El jugador camina** (3,0 m/s andar · 5,0 m/s correr · 1,2 m/s sigilo,
  `../mundo/01_EXPLORACION.md` §3). **En la demo y el Acto I no monta**: no hay galope, ni
  caballo propio, ni combate montado del héroe.
- **Por qué:** el pilar es recorrer el reino **con las botas**, y el arte de montura (modelo,
  animación, cámara, combate) no cabe en el presupuesto sin romper el estilo low-poly
  (`../arte/00_ESTILO.md`).
- **Lo que sí existe:** caballos y mulas **de otros** (mensajeros, patrullas, convoyes) que se ven
  y se enfocan (`../contenido/08_ANIMALES_Y_CRIATURAS.md` §1) — y a los que puedes **ganar** en una
  persecución.
- **✅ Decidido (2026-10-01): montar entra por la profesión «Equitación».** Se desbloquea **tras el
  Capítulo 1** (es decir, **después de la demo**) y se **compra** (`../sistemas/14_PROFESIONES.md`
  §2). **No** es mejora dura de Fase 5 ni un sistema nuevo: es **una fila más** en
  `profesiones.json`.

---

## 2. Ventajas y costes de cada forma

| Forma | Velocidad de viaje | Ruido/visibilidad | Coste | Carga |
|---|---|---|---|---|
| **A pie** | Base | Normal | 0 | Mochila 12 (`04_ITEMS_Y_EQUIPO.md` §5) |
| **Carreta de compañía** | **−20 %** | Ruido **+** y visible | Compra + **buey/mula** | **+20 huecos** |
| **Barca (puntual)** | No cambia el viaje | Baja | Peaje | 2-4 personas por viaje |
| **Caballo de otros** | — | — | — | Solo montas con la profesión **Equitación** (§1) |

- **La carreta frena:** no entra en bosque espeso, vado ni pasillo de 1,5 m
  (`../mundo/06_TERRENO_DEL_MUNDO.md`, `../mundo/08_AGUA_RIOS_Y_PUENTES.md`): donde no pasa, te
  toca **dejarla** o **dar rodeo**.
- **Ser visible cuesta:** con carreta, la tabla de encuentros sube (más apetecible para bandidos)
  en `../mundo/02_VIAJE_Y_ENCUENTROS.md` §2.

---

## 3. La carreta de compañía

- **Qué es:** un carro tirado por **buey o mula** que **sigue tu viaje por el camino** y carga lo
  que tu espalda no.
- **Para qué:**
  - **Oro y botín:** hasta **+20 huecos** de carga (`04_ITEMS_Y_EQUIPO.md` §5).
  - **Heridos:** lleva a un **compañero o tropa caído** sin dejarlo en el campo
    (`../sistemas/08_LUTO_Y_MORAL.md`).
  - **Instrumentos:** la empalizada, el pico pesado, la tienda de campaña.
- **De dónde sale:** se **compra** en ciudad o se **recupera** de una cuadrilla
  (`11_TABLAS_DE_BOTIN.md`). No se construye por menú (no hay base-building;
  `09_EDIFICIOS_Y_ESTRUCTURAS.md`).
- **Qué la amenaza:** un **asalto** puede volcarla y quitarte la carga
  (`12_TRAMPAS_Y_OBSTACULOS.md` §2); sin buey/mula, no se mueve.

---

## 4. Barcas y cruces

- **La barca** (`../mundo/08_AGUA_RIOS_Y_PUENTES.md` §1) es **transporte puntual**: 2-4 personas por
  viaje, con peaje; **no** cruza con carreta.
- **El vado** es el cruce por defecto sin puente (`§1`); ya es **terreno** con sus efectos
  (`../batalla/02_TERRENO.md`).
- **La carreta y los cruces:** puente de piedra o paso ancho; nunca vado ni paso de 1,5 m.

---

## 5. Cómo lo montan las casas

- **Mensajeros a caballo:** llevan un aviso o un pliego entre sitios (rumores, órdenes de casa)
  `../misiones/03_CADENAS_Y_RUMORES.md`.
- **Convoyes:** carretas con peaje (**20 oro por carro**, `../sistemas/06_ECONOMIA.md` §4) camino de
  la ciudad; se pueden **escoltar** (`../misiones/00_TIPOS_DE_ENCARGO.md`, clase `escoltar`).
- **Patrullas montadas:** las casas grandes tienen alguna; siguen siendo **tropa rasa** hasta que
  el capitán aparece (`02_CAPITANES_Y_NEMESIS.md`).

---

## 6. Arte y animación que exige cada opción

| Opción | Modelo | Animación | Estado |
|---|---|---|---|
| **A pie** | Ya hay (`u_knight` y cia.) | 9 estados (`../arte/03_ANIMACIONES.md` §1) | ✅ base |
| **Buey / mula** | Falta (Fase 4) | idle + andar | Fase 4 |
| **Carreta** | Falta (Fase 4) | clip de carro (volcado, rueda) | Fase 4 |
| **Barca** | Falta (Fase 4) | clip corto | Fase 4 |

- **Sin montar al héroe** no se necesita el coste de montura (`§1`): se ahorra modelo, silla,
  transición y cámara a caballo.
- Todo entra con **ficha y licencia** (`../arte/01_ASSETS.md` §3).

---

## 7. Datos, tipos y validación

- **Datos:** `data/transporte.json` — `{ id, tipo (pie/carreta/barca), velocidad, carga, coste,
  terreno_ok, ruido }`.
- **Tipos:** `Transporte` en `js/data/game_types.js` (una sola vez, regla 4).
- **Validación:** esquema en `js/data/schemas.js` + cruce del `terreno_ok` con `data/terreno.json` y
  del `coste`/peaje con `data/economia.json` en `tools/validate_data.js`.
- **Sistema puro:** `js/systems/transporte.js` — velocidad, carga y paso por terreno; sin DOM, sin
  reloj.
- **Tests:** `tests/transporte.test.js`, mínimo 3 casos (normal, borde, error): la carreta no pasa
  el vado; sin buey no se mueve; dejar la carreta no pierde la carga (queda en el sitio).

---

## 8. Cifras que fija este documento

| Cifra | Valor |
|---|---|
| Montar al héroe | **no** (decisión de diseño, §1) |
| Velocidad de viaje a pie | base |
| Carreta: velocidad / carga | **−20 %** / **+20 huecos** |
| Carreta: dónde no pasa | bosque espeso · vado · pasillo 1,5 m |
| Peaje por carro | **20 oro** (`../sistemas/06_ECONOMIA.md` §4) |
| Barca | 2-4 personas por viaje |
| Modelos nuevos | buey/mula, carreta, barca (Fase 4) |

---

## 9. Qué entra en la demo (Fase 1) — y qué sigue

> **Hasta aquí la demo.** El jugador **a pie** (regla de `../mundo/01_EXPLORACION.md`), el caballo
> **de los demás** (patrulla de Altamir, convoyes) y la **barca/puente** del tramo de camino. **Sin**
> carreta ni buey propios.

> **Y sigue el juego completo.** La **carreta de compañía** y los modelos de buey/mula/barca se
> añaden en la **Fase 4** con estas mismas reglas; la decisión de **a pie** no cambia al escalar.

---

## 10. Fuera de este documento

- Exploración a pie → `../mundo/01_EXPLORACION.md`
- Viaje y encuentros → `../mundo/02_VIAJE_Y_ENCUENTROS.md`
- Ríos, vados y puentes → `../mundo/08_AGUA_RIOS_Y_PUENTES.md`
- Animales y transporte animal → `08_ANIMALES_Y_CRIATURAS.md`
- Carga y mochila → `04_ITEMS_Y_EQUIPO.md`
- Peajes → `../sistemas/06_ECONOMIA.md`
- Modelos → `../arte/01_ASSETS.md`
