# 02 · Guardado y datos — el pacto con la partida

**Estado:** ✅ **aprobado por el dueño (aprobación en bloque, 2026-09-30). Documento final.**

> El guardado **nunca se rompe** (regla 6 de `../../AGENTS.md`): todo lo nuevo es **aditivo y
> acotado**, corrupto → respaldo, y **migrar jamás borra**. El motor está previsto en
> `js/core/save.js` (`SAVE_KEY = valcoria_save`, `MAX_SLOTS = 3`, `NIVEL_MAX = 60`; módulo por construir).

---

## 1. Qué guarda una partida (`SaveState`)

| Campo | Qué es | Desde |
|---|---|---|
| `version` | Versión del guardado | v1 |
| `day` | Día de juego (`../mundo/05_TIEMPO_DEL_MUNDO.md`) | v1 |
| `gold` | Oro (`../sistemas/06_ECONOMIA.md`) | v1 |
| `flags` | Banderas de trama y sistema | v1 |
| `companeros` | Compañeros unidos | v1 |
| `memoria` | Fichas de memoria (`../sistemas/00_MEMORIA_Y_DEUDA.md`) | **v1** |
| `firma` / `enmiendas` / `firmaHechos` | La Firma y sus hechos | **v1** |
| `cronica` | Entradas del diario (`../sistemas/04_CRONICA.md`) | **v1** |
| `prisioneros` | Estado del fin de batalla (`../sistemas/02_PRISIONEROS.md`) | **v1** |
| `juramento` | Puntos y nodos del árbol (`../contenido/06_HABILIDADES.md`) | **v1** |
| `codice` / `tutoriales` / `logros` | Fichas vistas, lecciones y logros (`../historia/09_CODEX_Y_BESTIARIO.md`, `../interfaz/10_TUTORIAL_Y_FIRST_RUN.md`, `12_LOGROS_Y_ESTADISTICAS.md`) | **v1** |
| `profesion` | Profesión, rango, XP y recetas (`../sistemas/14_PROFESIONES.md`) | **v1** |
| `alquiler` | Casa alquilada y cuartos de rehenes (`../sistemas/02_PRISIONEROS.md` §3.1) | **v1** |

- **Fuera del guardado de partida:** las **opciones** viven en `valcoria_opts` (`../DECISIONES.md`,
  2026-09-26), no se mezclan con la partida.

---

## 2. Versiones y migración

- **`SAVE_VERSION` = 1** (primera versión del juego). El esquema de la demo nace **completo en
  v1** (`PLAN_FASE1.md`, lectura greenfield): todos los campos de la tabla de arriba entran
  juntos. Cada campo futuro entrará en la versión en que se añada (v2, v3…) y **ningún
  documento cambia el número de un campo viejo**.
- **La migración** (función por crear) existirá para las versiones futuras: rellenará los campos
  nuevos **con valores vacíos** (`memoria` vacío, `firma` 0, `cronica` vacía…) y **nunca borra
  nada**. Hoy no hay versiones anteriores que migrar.
- **Un guardado viejo abre** siempre; uno **más nuevo** que el juego avisa y no rompe.
- 
---

## 3. Slots y respaldo

- **3 slots** (`MAX_SLOTS = 3`), cada uno con su clave; el **autoguardado** va al slot activo.
- **Corrupto → `valcoria_save.corrupt`:** nunca se arranca con datos rotos; se avisa y se ofrece el
  respaldo.
- **Guardado manual** desde el menú o al dormir (`../mundo/10_SUPERVIVENCIA_Y_DESCANSO.md`).

---

## 4. Tamaño y topes

- **`localStorage` del móvil ronda 5 MB** (regla 6): el guardado se queda muy por debajo.
- Cota asignada: **memoria ≤ 400 KB** (`00_MEMORIA_Y_DEUDA.md` §8) y **Crónica ≤ 64 KB**
  (`04_CRONICA.md` §4); el resto, corto por diseño.

---

## 5. Datos jugables (`data/*.json`)

- Rutas **relativas** (`data/x.json`, `art/x.glb`, `vendor/…`), **nunca** `/…` (regla 3, APK).
- **Todo JSON entra con su validador** (`js/data/schemas.js` + `tools/validate_data.js`); sin
  validador en verde, `loadData()`/`loadStrings()` **no arranca** (regla 5).
- La checklist de ficheros vive en `../DATOS.md`.

---

## 6. Tests

- `tests/save.test.js` + `tests/migracion.test.js` (por escribir): un guardado de una versión anterior migra hasta la
  **última versión (hoy v1)** sin perder datos; corrupto → respaldo; 3 slots independientes.
- **Cobertura ≥ 90 %** en el módulo de guardado (`../../AGENTS.md`).

---

## 7. Cifras que fija este documento

| Cifra | Valor |
|---|---|
| `SAVE_VERSION` | **1** (inicial; aditivo) |
| Slots | **3** |
| Techo de memoria | `localStorage` ~5 MB |
| Memoria | ≤ 400 KB |
| Crónica | ≤ 64 KB |
| Nivel máximo | **60** (la demo llega a 15) |
| Rutas | relativas (`data/…`) |
| Corrupto | `valcoria_save.corrupt` |

---

## 8. Qué entra en la demo (Fase 1) — y sigue

> **Hasta aquí la demo.** El guardado nace en **v1 con todo el esquema de la demo** (`memoria`,
> `firma`, `cronica`, `prisioneros`, `juramento`, códice/tutoriales/logros, `profesion` y
> `alquiler`), 3 slots y respaldo de corrupto. La migración queda como contrato para las
> versiones futuras (v2, v3…).

> **Y sigue el juego completo.** Cada sistema nuevo de las Fases 2-5 que toque el guardado **sube
> la versión de forma aditiva**; la migración se prueba en cada subida (DoD).

---

## 9. Fuera de este documento

- Tipos del guardado → `js/data/game_types.js` (por crear)
- Checklist de JSON → `../DATOS.md`
- Memoria y topes → `../sistemas/00_MEMORIA_Y_DEUDA.md`
- Crónica → `../sistemas/04_CRONICA.md`
