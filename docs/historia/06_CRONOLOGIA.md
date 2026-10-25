# 06 · Cronología — la línea de tiempo que no se contradice

**Estado:** ✅ **aprobado por el dueño (aprobación en bloque, 2026-09-30). Documento final.**

> Todo lo datable del reino, para que **nada se contradiga** entre historia, mundo y encargos.
> Fechas **relativas al Día 1** (el prólogo). La línea de la **partida** vive en la Crónica
> (`../sistemas/04_CRONICA.md`); esta es la del **mundo**.

---

## 1. Antes de la partida (fondo)

| Momento | Qué pasó | Lo que dejó |
|---|---|---|
| **Hace ~6 generaciones** | Guerra de venganzas sin fin entre casas | El terreno para la Ordenanza |
| **Hace ~5 generaciones** | Los **Reyes de la Bruma** dictan la **Ordenanza de la Sangre** | Deuda heredable, deuda blanca, marcas, Escribanos |
| **Hace ~3 generaciones** | Se funda la **Escribanía** y el Libro Mayor se vuelve ley | «Lo que no está en el libro, no pasó» |
| **Hace ~80 años** | Se alza **Casa Altamir** como dueña del paso | El peaje |
| **Año −12** | Nace el protagonista | — |
| **Año −3** | El protagonista se alista en la **Compañía del Paso** | Lealtad a Beltrán |

---

## 2. El año de la partida (fondo reciente)

| Momento | Qué pasó | Bandera de trama |
|---|---|---|
| **Día −120** | Altamir debía a los cuarenta **la tercera parte del peaje** | `deuda_cuarenta` |
| **Día −90** | El **Teniente** gira el cerrojo; el Paso cae | `paso_caido` |
| **Día −89** | Muere **Beltrán**; solo un hombre «sale» del paso | `beltran_muerto` |
| **Día −2** | Te leen sentencia de «vida por vida» en el **Patio del Cadalso** | — |
| **Día 1** | **Prólogo**: Doña Sira **reclama la espada** | `espada_reclamada` |

---

## 3. La línea de la partida (hitos)

| Hito | Cuándo | Bandera |
|---|---|---|
| **Acto I · el giro** | Al cerrar las cobranzas | `paginas_arrancadas` |
| **Acto II · los 3 giros** | Investigación | `verdad_ambrosio`, `teniente_vivo` |
| **Acto III · la asamblea** | En el Paso | `final_*` |

- **Regla:** ningún documento puede fechar un hecho del Paso **después** del Día −89, ni hacer
  vivir a Beltrán.

---

## 4. Qué se puede datar (y qué no)

- **Se data:** reinados, casas, el Paso, la sentencia, los hitos.
- **No se data:** la vida diaria del jugador (eso es la Crónica) ni cifras que el jugador no
  necesita.
- **El calendario del juego** (días/semanas/estaciones): `../mundo/05_TIEMPO_DEL_MUNDO.md`.

---

## 5. Datos, tipos y validación

- **Datos:** `data/cronologia.json` — `{ id, cuando, hecho, bandera }`.
- **Tipos:** `Hito` en `js/data/game_types.js`.
- **Validación:** coherencia entre fechas (un hecho no precede a su causa) y existencia de las
  `bandera` en `../historia/04_GUION.md` (`tools/validate_data.js`).
- **Tests:** `tests/cronologia.test.js`: Beltrán no actúa tras el Día −89; el Paso cae antes del
  Día 1; una bandera citada existe en el guion.

---

## 6. Cifras que fija este documento

| Cifra | Valor |
|---|---|
| Ordenanza | hace ~5 generaciones |
| Altamir dueña del paso | hace ~80 años |
| Paso del Juramento | Día −90 |
| Sentencia | Día −2 |
| Prólogo | **Día 1** |
| Actos | I, II y III (`01_ESTRUCTURA.md`) |

---

## 7. Qué entra en la demo (Fase 1) — y qué sigue

> **Hasta aquí la demo.** Todo el **Acto I**: fondo de la Ordenanza, el Paso, la sentencia, el
> prólogo y el giro de las páginas.

> **Y sigue el juego completo.** Los hitos del **Acto II y III** se añaden **con esta misma línea
> de tiempo**; crecer = más filas en `cronologia.json`, sin reescribir el pasado.

---

## 8. Fuera de este documento

- La premisa → `00_PREMISA.md`
- La estructura → `01_ESTRUCTURA.md`
- El elenco → `02_PERSONAJES.md`
- Fechas del juego → `../mundo/05_TIEMPO_DEL_MUNDO.md`
