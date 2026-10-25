# 11 · Tablas de botín — qué se encuentra

**Estado:** ✅ **aprobado por el dueño (aprobación en bloque, 2026-09-30). Documento final.**

> El botín **no es un pozo sin fondo**: sale de **lo que ya existía** y pasó por tus manos
> (`../sistemas/06_ECONOMIA.md` §7). Aquí están **qué suelta cada enemigo, cada sitio y cada
> situación**, con qué **probabilidad** y **hasta dónde puedes llevarte**. Los precios, en
> `05_RECURSOS_Y_MERCADO.md`; el equipo, en `04_ITEMS_Y_EQUIPO.md`; las piezas únicas, en
> `07_ARTEFACTOS.md`.
>
> **Botines, pesos y probabilidades son propuesta de diseño** (cambiables → `../DECISIONES.md`).

---

## 1. La regla de oro del botín

1. **Nada injusto:** siempre hay un **botín garantizado** pequeño; lo raro es **extra**, no la base.
2. **Determinista:** con el **RNG de la partida** y su semilla, el mismo saqueo da lo mismo
   (`../batalla/00_REGLAS.md` §10). Se puede guardar y no cambia.
3. **Nada se fabrica:** el hierro sale de hierro que existía; el oro, de una bolsa que había.
4. **El botín pesa:** lo que no cabe en la mochila **se queda en el barro** (`04_ITEMS_Y_EQUIPO.md` §5).
5. **Se lee sin frenar:** el saqueo es un **toque**, no una pantalla de inventario
   (`../mundo/01_EXPLORACION.md` §6).

---

## 2. De dónde sale (contenedores)

| id | Contenedor | Dónde | Se abre con |
|---|---|---|---|
| `cuerpo` | Cuerpo | Tras un combate o un hallazgo | Toque |
| `arcon` | Arcón | Casas, escribanía, ruina | Toque o **pico** (`04_ITEMS_Y_EQUIPO.md` §3.3) |
| `carreta` | Carreta volcada | Camino, campo (punto de interés) | Fuerza / tiempo |
| `ruina` | Ruina | Serranía, Tierra del Paso | — |
| `saco` | Saco / alijo | Aldeas, graneros | Toque |

- **Un contenedor no se abre dos veces:** se marca como saqueado en el guardado (sin campo nuevo,
  se deriva del `save`).

---

## 3. Tabla por familia enemiga

Botín **garantizado** + **extra** por tirada. Los ids de familia son de `01_ENEMIGOS.md`.

| Familia | Garantizado | Extra (peso) |
|---|---|---|
| **Bandidos de camino** | 5-15 oro | cuero (alto) · ballesta común (medio) · raciones (alto) |
| **Cuadrilla de casa** | 15-40 oro · 1 hierro | escudo común (medio) · arma `buena` (bajo) · cota (bajo) |
| **Patrulla de Altamir** | 10-25 oro | raciones (alto) · hierro (medio) · **recibo de peaje** (único, medio) |
| **Gente de la otra ribera** | 8-20 oro | honda común (alto) · raciones (medio) · amuleto (bajo) |
| **`rencorosos`** | El de su origen + su **rencor** | lo que llevara encima |

- **El botín de un capitán** (`02_CAPITANES_Y_NEMESIS.md`): el de su familia **+ 40-80 oro** y una
  pieza `buena`.
- **El recibo de peaje** de la patrulla es un **documento de trama**: prueba el peaje sin derecho
  (`../mundo/08_AGUA_RIOS_Y_PUENTES.md` §2).

---

## 4. Botín señalado (solo si hiciste algo)

| Situación | Botín señalado |
|---|---|
| **Perdonaste** a un capitán | Él te lo devuelve con un favor (`../sistemas/03_FAVORES.md`) |
| **Llegaste antes** que la patrulla | La carreta entera, sin desperdicio |
| **Cumpliste** el encargo sin cobrar de más | Recompensa `buena`/`rara` (`../misiones/04_PAGOS_Y_RECOMPENSAS.md` §2) |
| **Rompiste la empalizada** tú | Lo de dentro, entero (`12_TRAMPAS_Y_OBSTACULOS.md`) |
| **Hallazgo de leyenda** | Un artefacto (`07_ARTEFACTOS.md` §3) |

- **El botín señalado no cae por RNG:** exige un **hecho** en tu memoria
  (`../sistemas/00_MEMORIA_Y_DEUDA.md` §4). Si no lo hiciste, no existe.

---

## 5. Límites del saqueo

| Cota | Valor |
|---|---|
| Lo que no cabe | Se queda en el suelo (mochila de `04_ITEMS_Y_EQUIPO.md` §5) |
| Un contenedor | Se vacía **una vez** |
| Botín por enemigo | 1 tirada de extra (nunca 5) |
| Botín señalado | 1 por situación |
| Artefactos | Nunca por botín aleatorio (`07_ARTEFACTOS.md` §1) |
| Curva de venta | El exceso **hunde el precio** (`05_RECURSOS_Y_MERCADO.md` §3) |

- **Saquear a un sitio** (no a un enemigo): deja **memoria en contra** del lugar
  (`../sistemas/00_MEMORIA_Y_DEUDA.md` §4, hecho 7 · −7) y puede encender rencor.

---

## 6. Cómo se lee en pantalla (sin ralentizar)

- **Un toque** recoge el botín garantizado y muestra **una línea de 3 s** con lo ganado
  (`../interfaz/02_HUD.md`).
- Los **extras** se apuntan con su icono (`../arte/05_ICONOS.md`); no hay popup modal.
- El **botín que no cabe** deja un aviso suave («No te cabe») y se queda visible para volver.
- **Nada de animación larga de saqueo:** el juego no se para por hurgar en un bolsillo.

---

## 7. Datos, tipos y validación

- **Datos:** `data/botin.json` — `{ id, contenedor, familia, garantizado, extras: [{ id, peso }],
  senalado }`.
- **Tipos:** `Botin` en `js/data/game_types.js` (una sola vez, regla 4).
- **Validación:** esquema en `js/data/schemas.js` + cruce de `familia` con `data/enemigos.json`, de
  los `extras` con `data/items.json`/`data/recursos.json` y de `senalado` con los hechos de
  memoria en `tools/validate_data.js`.
- **Sistema puro:** `js/systems/botin.js` — tirada con **RNG inyectado**, aplica límites y botín
  señalado; sin DOM, sin reloj.
- **Tests:** `tests/botin.test.js`, mínimo 3 casos (normal, borde, error): la misma semilla da el
  mismo botín; siempre hay garantizado; un contenedor vaciado no vuelve a dar.

---

## 8. Cifras que fija este documento

| Cifra | Valor |
|---|---|
| Contenedores | **5** |
| Garantizado por familia | **sí** (5-40 oro + 1 recurso) |
| Extras | 1 tirada por enemigo |
| Botín de capitán | familia + **40-80 oro** + pieza `buena` |
| Botín señalado | exige **hecho** en memoria |
| Artefactos por botín | **0** |
| Determinismo | misma semilla = mismo botín |

---

## 9. Qué entra en la demo (Fase 1) — y qué sigue

> **Hasta aquí la demo.** El botín de las **3 familias** del Acto I (`01_ENEMIGOS.md`), los
> **cuerpos**, los **arcones** de aldea y las **carretas volcadas** del cruce, con la semilla y los
> límites. El **recibo de peaje** y el botín señalado de la primera batalla, funcionando.

> **Y sigue el juego completo.** Las familias de la otra ribera y los `rencorosos`, las **ruinas**
> y los alijos de casa se añaden **con estas mismas reglas**: crecer = más filas en `botin.json`,
> no otra tirada.

---

## 10. Fuera de este documento

- Precios y curva de venta → `05_RECURSOS_Y_MERCADO.md`, `../sistemas/06_ECONOMIA.md`
- Equipo y rarezas → `04_ITEMS_Y_EQUIPO.md`
- Piezas únicas → `07_ARTEFACTOS.md`
- Familias enemigas → `01_ENEMIGOS.md`
- Pagos de encargo → `../misiones/04_PAGOS_Y_RECOMPENSAS.md`
- Iconos del botín → `../arte/05_ICONOS.md`
