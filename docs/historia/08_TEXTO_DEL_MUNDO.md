# 08 · Texto del mundo — carteles, cartas y lápidas

**Estado:** ✅ **aprobado por el dueño (aprobación en bloque, 2026-09-30). Documento final.**

> El texto que **está en el mundo** y se lee **enfocando y tocando** (`../mundo/01_EXPLORACION.md`
> §6, tipo «Lectura»). No es diálogo ni Crónica: es **lo que alguien dejó escrito**. Todo con
> claves `txt_mundo_*` y paridad ES/EN.

---

## 1. Las familias de texto

| Familia | Dónde | Ejemplo |
|---|---|---|
| **Cartel** | Tablones, puertas, cruces | Ordenanza, prohibiciones, avisos de peaje |
| **Inscripción** | Mojones, fuentes, muros | Nombre de un muerto, una deuda grabada |
| **Carta / pliego** | Arcón, mensajero, cadáver | Ruegos, contratos, órdenes |
| **Lápida / epitafio** | Camposanto, ruina | Una vida y su cuenta |
| **Libro** | Escribanía, casas | El Libro Mayor, registros |
| **Coplas / canción** | Posada | La versión popular de un hecho |

---

## 2. El estilo (fijo)

1. **Corto:** cartel ≤ 2 líneas; carta ≤ 5; lápida ≤ 3.
2. **Seco y legal en los carteles** (dictados por Escribanos), **humano en las cartas**.
3. **Sin narrador:** lo que se lee **no explica** el juego; **siembra** (rumor, deuda, leyenda).
4. **Con fecha y firma cuando toca:** «Fecha…» y una **marca de Escribano**.

---

## 3. Dónde se colocan

- Los pone el mundo por **plantilla + semilla**, no a mano uno a uno (`../mundo/07_PROPS_Y_VEGETACION.md` §2):
  un mojón lleva su inscripción; una puerta, su cartel.
- **No se repiten** en exceso: el mismo cartel solo aparece donde tiene sentido.
- **Siempre cerca de algo jugable:** un cartel de peaje, junto al cruce; una lápida, junto a una
  deuda.

---

## 4. Cómo se leen

- **Enfocar + tocar** → panel de lectura (DOM), con la clave del idioma activo.
- **No bloquea el mundo** más de lo necesario; se cierra con un toque.
- Lo leído queda anotado en la **Crónica** si es relevante (`../sistemas/04_CRONICA.md`).

---

## 5. Datos, tipos y validación

- **Datos (por crear):** `data/texto_mundo.json` — `{ id, familia, clave_txt, lugar, requisito? }`.
- **Tipos:** `TextoMundo` en `js/data/game_types.js`.
- **Validación:** toda `clave_txt` tiene **pareja ES/EN** (`validateStringsPair`); el `lugar`
  existe en `lugares.json` (`tools/validate_data.js`).
- **Sistema puro:** la colocación vivirá en `js/systems/texto_mundo.js` (semilla inyectada); la
  pintura, en escena.
- **Tests (por escribir):** `tests/texto_mundo.test.js`: toda clave tiene pareja; nada se coloca sobre un
  interactuable; un texto sin lugar no rompe la carga.

---

## 6. Cifras que fija este documento

| Cifra | Valor |
|---|---|
| Familias | **6** |
| Cartel | ≤ 2 líneas |
| Carta | ≤ 5 líneas |
| Lápida | ≤ 3 líneas |
| Claves | `txt_mundo_*` con paridad ES/EN |
| Colocación | plantilla + semilla por zona |

---

## 7. Qué entra en la demo (Fase 1) — y sigue

> **Hasta aquí la demo.** Carteles de **tablón y peaje**, las primeras **inscripciones** del cruce
> y **1-2 cartas** conectadas al giro de las páginas.

> **Y sigue el juego completo.** Lápidas, coplas y los **registros del Libro Mayor** se añaden con
> estas mismas reglas; crecer = más filas en la tabla de texto del mundo.

---

## 8. Fuera de este documento

- Cómo se camina y se lee → `../mundo/01_EXPLORACION.md`
- Leyendas y rumores → `07_LEYENDAS_Y_RUMORES.md`
- Diálogo y guion → `04_GUION.md`
- Crónica → `../sistemas/04_CRONICA.md`
