# 02 · Capitanes y némesis — los que se acuerdan de ti

**Estado:** ✅ **aprobado por el dueño (aprobación en bloque, 2026-09-30). Documento final.**

> El eslogan tiene su segunda mitad: *«Cada enemigo se acuerda de ti. Y no todos mueren.»* Un
> **capitán** es una unidad **con nombre, memoria y voluntad**; los demás son tropa rasa. Aquí está
> **qué es, cómo crece, cómo vuelve y cómo se convierte en tu némesis**. La forma de pelear de su
> familia, en `01_ENEMIGOS.md`; su memoria, en `../sistemas/00_MEMORIA_Y_DEUDA.md`; sus stats, en
> `../batalla/01_CIFRAS.md` §1–§2; su IA, en `../batalla/03_IA_Y_ORDENES.md` §4.
>
> **Nombres e ids son propuesta de diseño** (cambiables → `../DECISIONES.md`).

---

## 1. Qué es un capitán (y qué no)

| | Capitán | Tropa rasa |
|---|---|---|
| **Identidad** | Tiene id, nombre y ficha | Solo id de familia |
| **Memoria** | **Completa** (32 hechos, relevante) | Ligera (1 ficha) |
| **Moral** | Propia; su ruptura pesa **×2** en los suyos | Una por unidad |
| **Decisión** | Cada **2 s** (piensa) | Cada **0,5 s** (reacciona) |
| **Contextura** | Mientras vive, su gente recupera **+1/s** extra | — |
| **Fin de batalla** | Se le aplican las **4 salidas** con nombre | Se resuelve en bloque |

- Un capitán **no es solo una tropa con más vida**: es una unidad que **decide** y a la que el
  mundo **recuerda** (`../batalla/03_IA_Y_ORDENES.md` §4).
- **Relevante:** todo capitán se marca con `relevante: true` en su ficha y gasta una plaza del
  tope de **60 relevantes** (`../sistemas/00_MEMORIA_Y_DEUDA.md` §8).

---

## 2. Rangos y rasgos

### 2.1 Rangos de mando (una casa o banda por encima)

| Rango | Quién | `rango_casa` | Vida extra | Manda a |
|---|---|---|---|---|
| **Capitán de casa** | Oficial de una casa noble | **+20** | +20 (160 → 180) | Una cuadrilla entera |
| **Teniente** | Mando de una patrulla | **+10** | +10 (→ 170) | Una patrulla |
| **Caudillo** | Cabeza de la otra ribera | +10 | +10 | Su gente del vado |
| **Cabecilla** | Jefe de bandidos | **0** | +0 (160) | Su banda (rara vez capitán) |

- **Stats base del capitán** (`../batalla/01_CIFRAS.md` §1–§2): vida **160**, ataque **30**,
  defensa **30**; el rango de casa sube la vida (§ tabla), no el daño.
- **Un solo capitán por cuadrilla o patrulla** (`01_ENEMIGOS.md`); un bandido solo tiene cabecilla.

### 2.2 Rasgos (los lee la IA)

| Rasgo | Familia que lo usa | Cómo decide |
|---|---|---|
| **Hostigador** | Bandidos de camino | Ataca y se aparta; huye antes (rompe a 10) |
| **Disciplinado** | Cuadrilla de casa | Mantiene formación, protege al capitán |
| **Patrulla** | Patrulla de Altamir | Cobra y avisa antes de pelear; se retira sin jefe |
| **Fanático** | Gente de la otra ribera | No se rinde hasta romperse; pelea en su vado |
| **Vengativo** | Los `rencorosos` | **Te busca a ti**, no la victoria |

- Los rasgos salen de `01_ENEMIGOS.md` §2; un capitán **hereda el rasgo de su familia** y le añade
  la **voluntad** de §3.

---

## 3. Cómo crece un capitán

- **Su nivel base es el de la zona** (`../sistemas/12_NIVELES_DEL_HEROE.md` §3), **+1** por ser
  capitán. Un capitán fijo de la historia lleva **nivel clavado** (no depende de la zona).
- **No sube de nivel por acumular:** sube por **sobrevivir con testigos**. Cada vez que **huye
  vivo** o **se rinde y lo dejas ir** (`../sistemas/02_PRISIONEROS.md` §4), gana **1 de rango
  propio** (techo **+3**).
- **Rango propio** modula (no reescribe) sus stats: **+5 de vida** y **+1 de ataque** por punto.
  Un capitán que te ha sobrevivido **dos veces** pelea distinto.
- **Rencor:** un hecho capital contra él o su casa (`../sistemas/00_MEMORIA_Y_DEUDA.md` §7) lo
  vuelve **vengativo** y lo devuelve con refuerzos de su casa.
- **Techo de balance:** el rango propio nunca rompe `../batalla/01_CIFRAS.md`; el capitán sigue
  siendo batible por tu vanguardia (Pilar 6).

---

## 4. Cómo vuelve (las cinco puertas)

| Salida que tomaste | Qué pasa con él | Vuelve como |
|---|---|---|
| **Huyó** | Se refugia en su casa y lo cuenta | **Némesis** de su familia, con refuerzos |
| **Se rindió y lo rescataste** | Vuelve a casa con deuda blanca (`f=1`) | **Amigo** que puede voltearse solo |
| **Lo retuviste (rehén)** | Su casa paga o se doblega | Su casa **debe**; él puede guardarte rencor |
| **Lo volteaste** | Pasa a tu catálogo con su rencor dentro | **Capitán tuyo** (`03_COMPANEROS.md` aparte) |
| **Lo compraste** | Cambia de bando una vez | Se acuerda él **y su casa** (`01_ENEMIGOS.md` §5) |
| **Lo ejecutaste** | Su casa hereda el rencor (`−15`, hecho 13) | **Némesis heredada** (hijo o casa, `−5`) |

- **Regla dura:** ningún capitán rendido **desaparece**; o vuelve con su casa, o pasa a tu fila,
  o deja un heredero que se acuerda. **Nadie es decorado.**
- **Si lo liberas, vuelve más duro:** un capitán al que **dejas ir**, **rescatas** o **compras**
  gana **+1 de rango propio** (§3) y vuelve **con refuerzos** de su casa. **El némesis que liberas
  es más duro que la primera vez** — y si vuelve a caer en tus manos, su deuda sube.
- **El que huye** es el caso más común (`../batalla/00_REGLAS.md` §9): se guarda su ficha y vuelve
  en la tabla de encuentros (`../mundo/02_VIAJE_Y_ENCUENTROS.md` §2) con el peso de su rencor.

---

## 5. Némesis de la historia y némesis generadas

### 5.1 Fijas (las pone el guion)

| id | Nombre (prop.) | Casa / familia | Por qué te busca |
|---|---|---|---|
| `nem_teniente` | **El Teniente** | Altamir | Sabes lo que hizo en el Paso (`../historia/02_PERSONAJES.md`) |
| `nem_cabecilla_dos_sendas` | El Cabecilla de las Dos Sendas | Bandidos | Le cortaste el negocio en el cruce |
| `nem_patrulla_altamir` | Teniente de Altamir | Patrulla | Cobras sin permiso en su camino |

- **El Teniente** es la némesis vertebral: el libro lo da por muerto, pero **hay dos hombres que
  salieron del paso** (`../historia/02_PERSONAJES.md`). Su ficha vive aquí y su verdad, en el
  Acto II (`../historia/04_GUION.md`).
- Las otras dos son **recurrentes del camino**: aparecen, huyen y vuelven.

### 5.1.1 Ficha de cada némesis fija

| | **El Teniente** | **El Cabecilla de las Dos Sendas** | **Teniente de Altamir** |
|---|---|---|---|
| **id** | `nem_teniente` | `nem_cabecilla_dos_sendas` | `nem_patrulla_altamir` |
| **Nivel** | **40** (clavado) | **nivel de zona** | **nivel de zona** |
| **Familia** | Cuadrilla de casa | Bandidos de camino | Patrulla de Altamir |
| **Rasgo** | Disciplinado | Hostigador | Patrulla |
| **Rango / arma** | Capitán de casa · espada y escudo | Cabecilla · ballesta | Teniente · lanza |
| **Qué lo rompe** | Nivel 0 (no se rinde) | Rompe a **10** y huye | Nivel 0; se repliega sin jefe |
| **Cómo vuelve** | Némesis heredada (su hijo la hereda) | Vuelve con su banda al cruce | Vuelve con la patrulla y refuerzos |
| **Qué te pide** | La verdad del Paso, no tu vida (Acto II) | El negocio del cruce | El peaje que no le pagaste |

### 5.2 Generadas (las produce tu partida)

- Nacen de la **memoria** y la **Firma** (`01_ENEMIGOS.md` §2, familia `rencorosos`):
  - el capitán al que **ejecutaste** y dejó pariente,
  - el que **volteaste** y se arrepiente,
  - el **huido** que vuelve con su casa,
  - el acreedor al que **no pagaste**.
- **No son anónimas:** toda némesis generada tiene **una razón escrita** en tu memoria (quién,
  qué hecho, qué día). Si no hay hecho, no hay némesis.

---

## 6. Favores y deudas de un capitán

- **Te debe un favor** (lo rescataste sin cobrar): puedes cobrarlo una vez —
  **deserción de una unidad suya** o **puerta abierta** (`../sistemas/03_FAVORES.md` §4).
- **Le debes un favor** (te perdonó la vida al caer): no puedes **retenerlo ni ejecutarlo** sin
  pagarlo antes (`../sistemas/03_FAVORES.md` §5).
- **Debe sangre:** si te lo lleva a ti de rehén y no puede pagar su rescate, su **deuda** pasa a
  ti (`../sistemas/02_PRISIONEROS.md` §3 · voltear).
- Un capitán **nunca** es deuda menor: su rescate es **(nivel + 10) × 10 oro** (fórmula de
  `../sistemas/00_MEMORIA_Y_DEUDA.md` §5).

---

## 7. Topes y guardado (sin reventar el guardado)

| Cota | Valor | Motivo |
|---|---|---|
| Capitanes con memoria completa | dentro de los **60 relevantes** | `../sistemas/00_MEMORIA_Y_DEUDA.md` §8 |
| Hechos por capitán | **32** (4 intocables) | idem §2.2 |
| Rencores por capitán | **3** | idem §7 |
| Rango propio | 0 … **+3** | §3 |
| Guardado del catálogo | **no añade campos nuevos** | Vivirá en `memoria` (aditivo) |

- **Nunca se pierde** el `id`, el `r`, la `d`, el `f` ni el `rw` de un capitán al superar la cota
  (`../sistemas/00_MEMORIA_Y_DEUDA.md` §8): la memoria se apaga, la deuda no.

---

## 8. Datos, tipos y validación

- **Datos (por crear):** `data/capitanes.json` — `{ id, nombre_txt, familia, rango, rasgo, casa, stats, botin,
  vuelve, es_nemesis }`.
- **Tipos:** `Capitan` en `js/data/game_types.js` (una sola vez, regla 4).
- **Validación:** esquema en `js/data/schemas.js` + cruce con `data/enemigos.json` (familia y
  rasgo), con `data/facciones.json` (casa) y con `data/pnj.json` (su ficha de memoria) en
  `tools/validate_data.js`. Sin validador, `loadData()` no arranca (regla 5).
- **Sistema puro:** la vuelta y el rencor de un capitán vivirán en `js/systems/enemigos.js` +
  `js/systems/memoria.js`; sin DOM, sin reloj, RNG inyectado.
- **Tests (por escribir):** `tests/capitanes.test.js`, mínimo 3 casos (normal, borde, error): un capitán huido
  vuelve con su casa; un ejecutado deja héroe heredero; un capitán sin hecho de memoria no puede
  ser némesis.

---

## 9. Cifras que fija este documento

| Cifra | Valor |
|---|---|
| Capitanes por cuadrilla / patrulla | **1** · 1 |
| Vida base / ataque / defensa | **160 / 30 / 30** |
| Nivel | zona **+1** · fijo si es de la historia (el **Teniente: 40**) |
| Extra por rango de casa | **+20** (capitán) · +10 (teniente/caudillo) |
| Percepción | **2 s** (tropa: 0,5 s) |
| Contextura | recuperación **+1/s** extra · ruptura **×2** |
| Rango propio | 0…+3 · +5 vida · +1 ataque cada punto |
| Liberado / rescatado | **+1 rango propio** y vuelve con refuerzos (más duro) |
| Rescate | **(nivel + 10) × 10 oro** |
| Voltear | banda ≥ **Amigo (+30)** o **(nivel + 10) × 12 oro** |
| Topes | dentro de los 60 relevantes · 32 hechos · 3 rencores |

---

## 10. Qué entra en la demo (Fase 1) — y qué sigue

> **Hasta aquí la demo.** **4+ capitanes** con memoria (`../produccion/00_ALCANCE.md` §3) en los
> **3 tipos de encuentro** del Acto I: un **cabecilla** de bandidos, un **capitán de cuadrilla** y
> un **teniente de Altamir**, más el **primer huido que vuelve**. El **Teniente** se menciona y se
> reserva para el Acto II. Las 4 salidas, el rescate y el rencor funcionan con estas mismas cifras.

> **Y sigue el juego completo.** Todas las **casas y familias** (`01_ENEMIGOS.md`) y sus capitanes
> se añaden **con estas mismas reglas**: crecer = más filas en `capitanes.json` y `enemigos.json`,
> no un sistema nuevo. La cifra no cambia al escalar.

---

## 11. Fuera de este documento

- Familias y rasgos → `01_ENEMIGOS.md`
- IA, capitán y contextura → `../batalla/03_IA_Y_ORDENES.md` §4
- Stats de combate → `../batalla/01_CIFRAS.md`
- Las 4 salidas y los rescates → `../sistemas/02_PRISIONEROS.md`
- Memoria, rencores y herencia → `../sistemas/00_MEMORIA_Y_DEUDA.md`
- Aliados con ficha propia → `03_COMPANEROS.md`
- Botín de un capitán → `11_TABLAS_DE_BOTIN.md`
- Casas y facciones → `../historia/05_CASAS_Y_FACCIONES.md`
