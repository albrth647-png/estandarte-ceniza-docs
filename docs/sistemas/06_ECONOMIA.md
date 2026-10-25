# 06 · Economía — el oro y la sangre

**Estado:** ✅ **aprobado por el dueño (aprobación en bloque, 2026-09-30). Documento final.**

> En Valcoria **la deuda se mide en oro**, pero se paga también en servicio y en sangre
> (`00_MEMORIA_Y_DEUDA.md` §5). Aquí vive **el dinero del reino**: de dónde sale, en qué se va,
> a qué precio y por qué no se puede romper. Los **precios de catálogo** (armas, recursos) están
> en `../contenido/05_RECURSOS_Y_MERCADO.md` y `../contenido/04_ITEMS_Y_EQUIPO.md`; este
> documento fija el **marco** y las cifras de juego.

---

## 1. La moneda y el marco de sangre

- **Moneda jugable:** el **oro** (una sola divisa; hay plata y cobre de sabor, pero cuentan como
  fracciones de oro).
- **Unidad de la Ordenanza:** el **marco de sangre** — lo que vale una vida en los libros.
  **1 marco = 10 oro.** La Crónica y los Escribanos hablan en marcos; el bolso, en oro.
- **Redondeo:** las cuentas son enteras; los céntimos no existen en Valcoria.

---

## 2. De dónde sale el oro

| Fuente | Cuánto | Dónde |
|---|---|---|
| **Cobranza de deudas** | El importe de la deuda (`d`) | Encargos y tablones (`../misiones/04_PAGOS_Y_RECOMPENSAS.md`) |
| **Botín** | `../contenido/11_TABLAS_DE_BOTIN.md` | Batallas y contenedores |
| **Rescates** | (nivel + 10) × 10 (capitán) | `02_PRISIONEROS.md` §3 |
| **Rédito de un rehén retenido** | rescate ÷ 10 por día (tope 10 días) | `02_PRISIONEROS.md` §3.1 |
| **Contratos** | Pago por encargo | Tablones y portavoces |
| **Venta** | Precio de mercado | `../contenido/05_RECURSOS_Y_MERCADO.md` |
| **Servicio** | 0 oro, pero **paga deuda** | `00_MEMORIA_Y_DEUDA.md` §5 |

- **Empezar:** **50 oro** y una espada alquilada. No eres pobre por casualidad: el cadalso te
  quitó todo (`../historia/01_ESTRUCTURA.md`, prólogo).
- **Deuda inicial del jugador:** **20 marcos = 200 oro** (la primera cobranza del Acto I).

---

## 3. En qué se va

| Gasto | Cuánto |
|---|---|
| **Recluta** de una tropa | 30–60 oro (`../contenido/00_TROPAS.md` §3) |
| **Salario diario** por tropa | 2–5 oro/día (ídem) |
| **Comida y posada** | comida 2 oro · noche de posada 5 oro |
| **Renta de la casa alquilada** | **5 oro/día** (cuartos para rehenes, `02_PRISIONEROS.md` §3.1) |
| **Equipo y mejoras** | `../contenido/04_ITEMS_Y_EQUIPO.md` |
| **Fabricar en el taller del sitio** (cuesta oro, 0 días) | `15_FABRICACION_Y_RECETAS.md` §4 y §6 |
| **Rescate** (si caes tú) | (nivel + 10) × 10 oro |
| **Fianza / rehén** | `02_PRISIONEROS.md` §3 |
| **Soborno** | 20–50 oro (guardia, ronda, Escribano menor) |
| **Enmienda de Firma** | **100 oro** + 1 día (`01_FIRMA.md` §7) |
| **Luto y funerales** | `08_LUTO_Y_MORAL.md` |

- **Los salarios se cobran por día** (`save.day`): sin oro, la lealtad cae y pueden desertar
  (`10_LEALTAD_Y_DESERCION.md`).

---

## 4. Precios de referencia

| Cosa | Precio base |
|---|---|
| Jornal de un peón (para comparar) | 1 oro/día |
| Un hombre libre (componenda) | **20 marcos = 200 oro** |
| Caballo de labor | 80 oro (monturas, Fase 4) |
| Peaje de Altamir | 5 oro por persona · 20 oro por carro |
| Noche de posada + cena | 7 oro |
| Renta de la casa alquilada | 5 oro/día |
| Reparar arma | 10–25 oro |

- **El peaje de Altamir cobrado «sin derecho»** es deuda de la casa, no precio legal
  (`../historia/02_PERSONAJES.md`, Casa Altamir).

---

## 5. Elasticidad (qué encarece y qué abarata)

- **La Firma manda en el mostrador** (`01_FIRMA.md` §3): **Duro +10 %** · **Fiera +25 %** ·
  **Hiena +40 %**; los amigos de la banda **Amigo** dan un **−10 %**.
- **La guerra encarece:** hierro y equipo suben cuando hay conflicto abierto.
- **La sequía y el invierno encarecen** la comida (`../mundo/09_CLIMA_Y_ESTACIONES.md`).
- **El puerto y la ribera abaratan** el trato; la serranía lo encarece (aislamiento).
- **Los precios bajan en tu contra si vendes mucho** (§7): el mercado no es un pozo sin fondo.

---

## 6. La deuda como producto

- **Comprar deudas ajenas:** puedes pagar a un acreedor por una deuda que otro te debe, y pasar a
  ser tú el acreedor (el deudor te lo agradecerá o te odiará, según su banda).
- **Vender tu deuda:** ceder lo que te deben a cambio de oro hoy — menos, pero seguro.
- **Prestar:** puedes prestar oro; el impago no lo arregla el juego, lo recuerda la memoria
  (hecho 9 · Incumplimiento, −5).
- **La deuda no genera intereses nunca** (`00_MEMORIA_Y_DEUDA.md` §5): crece por heredarse, no por
  el tiempo.

---

## 7. Reglas antiabuso (el bucle roto)

1. **Stock finito:** cada sitio tiene reserva; no hay compraventa infinita.
2. **Vender hunde el precio:** a partir de cierta cantidad, el mercado paga menos (curva suave).
3. **El botín no se fabrica:** solo sale de lo que ya existía y pasó por tus manos.
4. **Los salarios corren cada día:** una compañía grande sin ingresos se deshace sola.
5. **Los rescates y la enmienda tienen tope:** 3 enmiendas por partida; rescate con precio fijo.
6. **La deuda viaja:** no se puede «caducar» ni «lavar» para desaparecer — solo pagar, perdonar
   o quemar (`../historia/03_RECORRIDO.md`).

---

## 8. Datos, tipos y validación

- **Datos:** `data/economia.json` — `{ oro_inicial, marco_oro, salarios, precios_base,
  recargos_firma, curva_venta }`.
- **Tipos:** `Economia` y `Precio` en `js/data/game_types.js` (una sola vez, regla 4).
- **Validación:** esquema en `js/data/schemas.js` + cruce con `data/tropas.json` (salarios) y
  `data/lugares.json` (stocks) en `tools/validate_data.js`.
- **Sistema puro:** `js/systems/economia.js` — aplica precio, recargos y curva; sin DOM, sin reloj,
  recibe `save.day` y el RNG de la partida.
- **Tests:** `tests/economia.test.js`, mínimo 3 casos (normal, borde, error): el recargo de Hiena es
  +40 %; vender en masa baja el precio; un saldo negativo no rompe el guardado.

---

## 9. Cifras que fija este documento

| Cifra | Valor |
|---|---|
| Marco de sangre | **1 marco = 10 oro** |
| Oro inicial | **50** |
| Deuda inicial del jugador | **20 marcos = 200 oro** |
| Salario por tropa | 2–5 oro/día |
| Renta de la casa alquilada | 5 oro/día |
| Recluta | 30–60 oro |
| Recargos por Firma | Duro +10 % · Fiera +25 % · Hiena +40 % · Amigo −10 % |
| Rescate | (nivel + 10) × 10 oro |
| Enmienda | 100 oro · máx. 3 |
| Ingreso objetivo | **30–80 oro/h** (demo) · 100–200 oro/h (juego completo) |

---

## 10. Qué entra en la demo (Fase 1) — y qué sigue

> **Hasta aquí la demo.** Oro inicial, cobranza, botín, salarios, posada y rescate del Acto I, con
> los **recargos por Firma** activos en los 6 sitios (`../produccion/00_ALCANCE.md` §2.2). Precios
> simples, sin mercado de materias primas.

> **Y sigue el juego completo.** El **mercado completo** (recursos, materias primas, curva de
> venta), el **préstamo** y la **compra de deudas ajenas** llegan con la Fase 2/Fase 4; el marco
> (1 marco = 10 oro) y las fórmulas **no cambian**.

---

## 11. Fuera de este documento

- La deuda y su herencia → `00_MEMORIA_Y_DEUDA.md`
- Precios de rescate y fianzas → `02_PRISIONEROS.md`
- Recargos por banda → `01_FIRMA.md`
- Catálogo de recursos y mercado → `../contenido/05_RECURSOS_Y_MERCADO.md`
- Ítems y equipo → `../contenido/04_ITEMS_Y_EQUIPO.md`
- Pagos de encargos → `../misiones/04_PAGOS_Y_RECOMPENSAS.md`
