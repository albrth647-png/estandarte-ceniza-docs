# 04 · Pagos y recompensas — cuánto vale cada encargo

**Estado:** ✅ **aprobado por el dueño (aprobación en bloque, 2026-09-30). Documento final.**

> El marco del dinero vive en `../sistemas/06_ECONOMIA.md` (1 marco = 10 oro, recargos por Firma).
> Aquí está **cuánto paga cada clase de encargo y cómo se negocia**. Las clases, en
> `00_TIPOS_DE_ENCARGO.md`.

---

## 1. Tarifas base por clase

| Clase | Tarifa base | Nota |
|---|---|---|
| `cobrar` | **15 % del importe** cobrado (mín. 20 oro) | Si el deudor paga de verdad |
| `escoltar` | **60-120 oro** según distancia | Riesgo de emboscada |
| `rescatar` | **rescate + 20 %** (`../sistemas/02_PRISIONEROS.md`) | El rescate lo paga la casa |
| `limpiar` | **80-150 oro** + botín | El botín es tuyo |
| `mediar` | Pago de **una o de las dos partes** | Cobrar a las dos es riesgo de romperlo |
| `vigilar` | **10-20 oro/día** | Salario, no premio |
| `mensaje` | **20-50 oro** + información | El mensaje vale por lo que revela |
| `vengar` | **precio de la sangre** (componenda) | La casa paga por el feudo |
| `investigar` | **50-200 oro** + información | Se paga por lo que descubres |
| `fianza` | **el importe + 10 %** | El deudor te lo queda debiendo |
| `oficio` | **20-90 oro** + **XP de oficio** | La reparte el maestro; **3 por rango** ✅ 2026-10-02 |

- **De qué depende:** peligro, distancia, quién paga (casa rica o aldeano), **tu Firma**
  (recargos de `../sistemas/06_ECONOMIA.md` §5) y si hay **testigos**.

---

## 2. En qué se cobra (no siempre oro)

| Forma | Cuándo |
|---|---|
| **Oro** | Lo normal |
| **Favor** | Quien no tiene oro pero puede abrirte una puerta (`../sistemas/03_FAVORES.md`) |
| **Información** | Rumor, nombre, prueba (clave en el Acto II) |
| **Deuda perdonada** | Te dan por saldada una deuda tuya (`../sistemas/00_MEMORIA_Y_DEUDA.md` §5) |
| **Mercancía** | Grano, hierro, equipo (`../contenido/05_RECURSOS_Y_MERCADO.md`) |
| **Servicio** | El deudor paga con trabajo (forma de deuda) |
| **XP de oficio** | Solo en los encargos `oficio` del maestro (`../sistemas/15_FABRICACION_Y_RECETAS.md` §9): **+40** cada uno |

- **Se negocia el `recompensa` al aceptar**, no después. Lo pactado es lo que la memoria guarda.
- **Los encargos `oficio` además dan 1 receta** al cerrarlos
  (`../sistemas/15_FABRICACION_Y_RECETAS.md` §5 y §9).

---

## 3. Negociar

- **Regateo: ±20 %** sobre la tarifa base, con toque largo para **ofrecer** (no un minijuego).
- **Qué lo mueve:**
  - **Firma** (Honrado/Palabra dada piden más con razón; Hiena pide y le pagan por miedo),
  - **memoria** (banda Amigo concede; Hostil aprieta),
  - **urgencia** (contrarreloj sube el precio),
  - **testigos** (regatear delante de todos deja fama).
- **Coste de regatear:** cada intento gasta **una mañana** (medio día de juego) y puede **bajar**
  la oferta si abusas.

---

## 4. Cobrar de más (y saquear al cliente)

- **Pasarte de lo pactado** (quedarte con más del `recompensa`, saquear, no devolver el sobrante):
  - memoria del cliente y de los testigos,
  - **Firma** según el hecho (robo/despojo −7, cobro por la fuerza −6, `../sistemas/01_FIRMA.md` §4),
  - y **rencor** si humillas o arruinas.
- **No hay «cobrar de más» sin coste:** el mundo apunta lo que haces, incluso cuando te sale bien.

---

## 5. Cuando el cliente no puede pagar

- **Plazo:** concede **+5 días** y cobra con recargo del 10 %… o pierde.
- **Servicio / trueque:** cobra en trabajo, grano o equipo (§2).
- **Perdona:** convierte su deuda en **deuda blanca** (un favor, `../sistemas/03_FAVORES.md`) —
  pierdes oro hoy, ganas puerta mañana.
- **Ejecuta la prenda:** si el acreedor te lo permite, puedes tomar algo en garantía (memoria en
  contra). **Nunca** la vida por una deuda menor: eso es un feudo (§`vengar`).

---

## 6. Datos, tipos y validación

- **Datos:** las tarifas viven en `data/encargos.json` (`recompensa`) con los modificadores de
  `data/economia.json`; **no** se escriben en el código.
- **Tipos:** `Recompensa` y `Negociacion` en `js/data/game_types.js` (una sola vez, regla 4).
- **Validación:** esquema en `js/data/schemas.js` + cruce de tarifas con `data/economia.json` en
  `tools/validate_data.js`.
- **Sistema puro:** `js/systems/pagos.js` (o dentro de `encargos.js`) — calcula tarifa, regateo y
  recargos; sin DOM, sin reloj, RNG inyectado.
- **Tests:** `tests/pagos.test.js`, mínimo 3 casos (normal, borde, error): el regateo no supera
  ±20 %; cobrar de más deja memoria en contra; un cliente sin oro siempre tiene salida (§5).

---

## 7. Cifras que fija este documento

| Cifra | Valor |
|---|---|
| Comisión de cobro | 15 % (mín. 20 oro) |
| Regateo | **±20 %** |
| Prórroga | +5 días (o +2 con banda Amigo, `01_TABLONES_Y_PORTAVOCES.md`) |
| Recargo por plazo | +10 % |
| Recargos por Firma | los de `../sistemas/06_ECONOMIA.md` §5 |
| Coste de regatear | media jornada por intento |
| Formas de cobro | 6 (§2) |

---

## 8. Qué entra en la demo (Fase 1) — y qué sigue

> **Hasta aquí la demo.** Las tarifas de las clases usadas en el Acto I (`cobrar`, `vigilar`,
> `escoltar`, `mensaje`, `mediar`, `limpiar`) y el cobro en **oro, favor o información**.

> **Y sigue el juego completo.** Las clases de `vengar`, `investigar` y `fianza`, el cobro en
> **mercancía** y la compra de deudas ajenas (`../sistemas/06_ECONOMIA.md` §6) llegan con el
> reino grande; las fórmulas (±20 %, 15 %, prórroga) **no cambian**.

---

## 9. Fuera de este documento

- El marco económico → `../sistemas/06_ECONOMIA.md`
- Clases de encargo → `00_TIPOS_DE_ENCARGO.md`
- Dónde se cogen → `01_TABLONES_Y_PORTAVOCES.md`
- Favores y deuda blanca → `../sistemas/03_FAVORES.md`
- Los pagos de la trama → `05_ENCARGOS_DE_LA_HISTORIA.md`
