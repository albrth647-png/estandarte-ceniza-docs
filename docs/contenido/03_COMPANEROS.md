# 03 · Compañeros — los que caminan contigo

**Estado:** ✅ **aprobado por el dueño (aprobación en bloque, 2026-09-30). Documento final.**

> Los **Marcados** son tropa que peleas; un **compañero** es un **aliado con nombre, oficio y
> pasado propio** que camina a tu lado y te cambia cómo juegas. El motor que ya existe
> (`js/systems/dialogue.js`, nodos `une`) y el campo `SaveState.companeros` nacieron para esto.
> La tropa reclutable, en `00_TROPAS.md`; el capitán enemigo que se voltea, en
> `02_CAPITANES_Y_NEMESIS.md`; su memoria, en `../sistemas/00_MEMORIA_Y_DEUDA.md`.
>
> **Nombres e ids son propuesta de diseño** (cambiables → `../DECISIONES.md`). Propuesta inicial
> del dueño: **pocos y con alma**.

---

## 1. Qué es un compañero (y qué no)

| | Compañero | Tropa (Marcado) | Capitán volteado |
|---|---|---|---|
| **Ficha** | Completa: nombre, oficio, pasado, razón para seguirte | Ligera | Completa (enemiga) |
| **Combate** | Pelea **contigo** en el campo como unidad propia | Forma en tu vanguardia | Manda a su gente por ti |
| **Fuera del campo** | Aporta **oficio, consejo y contactos** | Solo come y cobra | Manda y cobra rencor |
| **Lealtad** | Tiene su **propia** lealtad y se puede ir | Deserta por salario/comida | Te sirve con su rencor dentro |
| **Se puede perder** | Muere y **no vuelve** | Baja de campaña | Vuelve a su casa si huye |

- Un compañero **tiene casa, cuenta y miedo** (`../historia/00_PREMISA.md`): no es un botón, es
  una persona que puede marcharse.
- **Caben pocos:** el compañero no es un mercenario; es **una relación** (`../VISION_JUEGO_COMPLETO.md`).

---

## 2. Quiénes pueden unirse (propuesta)

| id | Nombre | Oficio | Por qué te sigue | Entra |
|---|---|---|---|---|
| `cmp_la_sorda` | **La Sorda** | Guía del camino | Te vio cobrar y le debes el primer aviso | **Fase 1 (demo)** |
| `cmp_maese_orencio` | **Maese Orencio** | Barbero viejo | Curó a los cuarenta; quiere cerrar esa cuenta | Fase 2 |
| `cmp_lanza_rota` | **Lanza Rota** | Sargento de los cuarenta | Fue el único que llegó vivo del Paso contigo | Fase 2 |
| `cmp_la_escribana_joven` | **Escribana joven** | Escribana de la Sangre | Arriesga su pluma por la verdad de la puerta | Fase 3 |

- **Cada uno aporta algo que no es +1 en una tabla:** la guía abre atajos y evita emboscadas
  (`../mundo/02_VIAJE_Y_ENCUENTROS.md`), el barbero cura de campaña (`../sistemas/08_LUTO_Y_MORAL.md`),
  el sargento manda una segunda orden, la escribana abre puertas de la Firma
  (`../sistemas/01_FIRMA.md` §7).
- **Nombres, ids y el número son ya propuesta cerrada** (✅ 4 compañeros, 1 en la demo):
  el dueño los fija en `../DECISIONES.md` antes de que entren en `data/`.

### 2.1 Ficha de cada compañero

| | **La Sorda** | **Maese Orencio** | **Lanza Rota** | **Escribana joven** |
|---|---|---|---|---|
| **id** | `cmp_la_sorda` | `cmp_maese_orencio` | `cmp_lanza_rota` | `cmp_la_escribana_joven` |
| **Oficio** | Guía del camino | Barbero viejo | Sargento de los cuarenta | Escribana de la Sangre |
| **Rol / arma** | Apoyo · honda | Apoyo · cuchillo | Línea · lanza | Apoyo · daga |
| **Nivel de entrada** | el de la zona (Marca del Sur, 1-12) | zona + 2 | zona | zona |
| **Casa** | ninguna (camino) | gremio de barberos | Casa Altamir (rencoroso) | Ordenanza de la Sangre |
| **Entra** | **Fase 1 (demo)** | Fase 2 | Fase 2 | Fase 3 |
| **Cómo se une** | Nodo `une` al cierre del Acto I | Lo buscas tras el Paso | Lo encuentras vivo: único del Paso contigo | Te sigue para escribir la verdad |
| **Aporte** | Atajo y aviso de emboscada | Cura de campaña (1/batalla) | **Segunda orden** local | Abre puertas de la Firma |
| **Qué lo rompe** | Que maltrates a su gente | Que dejes morir a un herido | Que negocies con Altamir | Que quemes un archivo |
| **Qué lo devuelve** | Salvarla o pagarle su cuenta | Curar a los suyos | Vengar el Paso contigo | Publicar la verdad |

- **Todos pelean a tu lado con su nivel** (escala 1-60, `../sistemas/12_NIVELES_DEL_HEROE.md` §4) y
  siguen las **órdenes globales**, sin micromando (§4.2).

---

## 3. El motor que ya existe (no se reescribe)

- **Nodos `une`:** el diálogo de la historia marca `[une] <companero_id>`; al ejecutarse, el id
  entra en `SaveState.companeros` (`js/systems/dialogue.js`).
- **Condición `companero`:** las escenas y opciones pueden exigir `condicion: { companero: "id" }`;
  `cumpleCondicion()` ya lo resuelve (regla 4 de `../../AGENTS.md`: se **extiende**, no se rehace).
- **Condiciones existentes que también se usan:** `honor_min/max`, `oro_min`, `flag`, `sin_flag`
  (el guion las usa en `../historia/04_GUION.md`).
- **Lo nuevo es aditivo:** el sistema puro `js/systems/companeros.js` lee el `companeros` del
  guardado y aplica sus aportes; **no** cambia el runner de diálogo.

---

## 4. Qué aportan

### 4.1 Fuera del campo (oficio, consejo, contactos)

| Aporte | Efecto | Límite |
|---|---|---|
| **Atajo / guía** | Revela un peligro o acorta un viaje | 1 vez por día de juego |
| **Cura de campaña** | Cura una herida fuera de combate | 1 por batalla (`../sistemas/08_LUTO_Y_MORAL.md`) |
| **Contacto** | Abre una puerta o una tienda cerrada | Según su casa y su memoria |
| **Consejo** | Un aviso del mundo sin popup | Como `../interfaz/07_AVISOS_Y_RUMORES.md` |

### 4.2 Dentro del campo

- Un compañero pelea como **una unidad de tu bando**, con su rol (`00_TROPAS.md` §2) y las stats
  de `../batalla/01_CIFRAS.md` que le toquen por su arma.
- **No se le da orden individual:** obedece las **órdenes globales** como todos
  (`../batalla/03_IA_Y_ORDENES.md`) — el juego no vuelve al micromando.
- **Si cae:** muerte de compañero = **baja de campaña** y **luto** (`../sistemas/08_LUTO_Y_MORAL.md`),
  con su nombre en la Crónica (`../sistemas/04_CRONICA.md`). **No vuelve.**

---

## 5. Lealtad y despedidas

- **Su lealtad es propia,** aparte de la moral de campaña (`../sistemas/10_LEALTAD_Y_DESERCION.md`).
- **Se va si:**
  - ves maltrato a su gente o a su casa (memoria, hechos 7/8/12),
  - incumples lo prometido (hecho 9 · −5),
  - te vuelves **Hiena** y su banda era Honrado o mejor (`../sistemas/01_FIRMA.md` §3).
- **Se queda si:** le salvas la vida (hecho 3 · +10), cumples tu palabra o **pagas su cuenta**
  (hecho 5 · +8).
- **Voltearse en plena batalla:** posible solo con **rencor activo** o **favor cobrado en tu
  contra** (`../sistemas/10_LEALTAD_Y_DESERCION.md` §4); se prepara, no se improvisa.

---

## 6. Cuántos caben y qué pasa cuando se van

| Cifra | Valor |
|---|---|
| Compañeros en el juego completo | **4** (propuesta) |
| Compañeros en la demo | **1** (La Sorda) |
| Aporte fuera de combate | 1 por día / 1 por batalla |
| Recuperación tras irse | **una vez** por persona (`10_LEALTAD_Y_DESERCION.md`) |

- **Si se van con deudas tuyas:** el compañero que se marcha **conserva su ficha de memoria**; si
  le debías, la deuda **te sigue** (`../sistemas/00_MEMORIA_Y_DEUDA.md` §5) y puede volver a
  cobrártela.
- **Si muere:** su deuda y su favor se cierran con él (la deuda blanca **no se hereda**,
  `../sistemas/03_FAVORES.md` §2); su casa hereda la deuda **firmada** (`§5`).

---

## 7. Datos, tipos y validación

- **Datos:** `data/companeros.json` — `{ id, nombre_txt, oficio, casa, aporte, rol, stats,
  une_en, lealtad }`.
- **Tipos:** `Companero` en `js/data/game_types.js` (una sola vez, regla 4).
- **Guardado:** `SaveState.companeros` (array de ids) **ya existe**; no añade campos nuevos
  (SAVE_VERSION 3 es aditivo, `../produccion/02_GUARDADO_Y_DATOS.md`).
- **Validación:** esquema en `js/data/schemas.js` + cruce del `id` con los nodos `une` de
  `data/dialogos.json` y con `data/pnj.json` en `tools/validate_data.js`.
- **Sistema puro:** `js/systems/companeros.js` — alta, aporte y salida; sin DOM, sin reloj, RNG
  inyectado si hace falta.
- **Tests:** `tests/companeros.test.js`, mínimo 3 casos (normal, borde, error): un `une` mete el
  id en `companeros`; la condición `companero` filtra opciones; un compañero caído no vuelve.

---

## 8. Cifras que fija este documento

| Cifra | Valor |
|---|---|
| Compañeros (juego completo / demo) | **4 / 1** ✅ |
| Nivel | escala 1-60 · entra al de la zona (`../sistemas/12_NIVELES_DEL_HEROE.md` §4) |
| Rol | el de un arma de `00_TROPAS.md` §2 |
| Aporte | 1 por día · 1 por batalla |
| Vuelve tras morir | **no** |
| Recuperación tras irse | 1 vez |
| Guardado | usa `SaveState.companeros` (sin campo nuevo) |

---

## 9. Qué entra en la demo (Fase 1) — y qué sigue

> **Hasta aquí la demo.** **La Sorda**, la guía que se une al final del Acto I con el nodo `une`, y
> su aporte de atajo/aviso. El motor de diálogo, la condición `companero` y el `SaveState` ya
> funcionan con ella; el resto del catálogo existe en datos pero **no se une** hasta su fase.

> **Y sigue el juego completo.** Los otros **3 compañeros** (barbero, sargento, escribana) se
> añaden **con estas mismas reglas**: crecer = más filas en `companeros.json` y un nodo `une` más,
> no un sistema nuevo.

---

## 10. Fuera de este documento

- Motor de diálogo y nodos → `../historia/04_GUION.md`, `js/systems/dialogue.js`
- Tropas reclutables → `00_TROPAS.md`
- Capitanes enemigos → `02_CAPITANES_Y_NEMESIS.md`
- Lealtad y deserción → `../sistemas/10_LEALTAD_Y_DESERCION.md`
- Luto y Crónica → `../sistemas/08_LUTO_Y_MORAL.md`, `../sistemas/04_CRONICA.md`
- Memoria y deudas → `../sistemas/00_MEMORIA_Y_DEUDA.md`
