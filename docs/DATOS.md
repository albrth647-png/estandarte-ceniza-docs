# Datos — checklist de `data/*.json`

> Regla dura 5 de `../AGENTS.md`: **todo JSON nuevo entra con su validador**
> (`js/data/schemas.js`) + chequeo en `tools/validate_data.js` (módulos por crear en el
> paso 1.1); la carga de textos lanzará con **todos** los errores juntos.
> Este fichero es el mapa: qué datos llevará el juego, en qué orden se crean y quién los
> valida. **Ningún JSON existe todavía**: el proyecto es greenfield (solo documentación).

## Cómo leer este fichero

> **Aviso:** los **98 documentos de diseño** (`PLAN_DOCUMENTOS.md`) declaran ya sus ficheros
> y su validador en sus apartados de «Datos, tipos y validación». Este checklist es el
> **mapa general** de los ficheros que se crearán en la Fase 1
> (`produccion/PLAN_FASE1.md`), en el orden de siempre: datos → código → tests → documentación.

## Fase 1 — los 8 primeros (paso 1.1/1.2)

| Fichero (por crear) | Contenido | Validador previsto |
|---|---|---|
| `strings_es.json` | claves ES de la demo (portada, menú, creación, exploración, avisos, memoria, Firma); **el catálogo se depura al cerrar la ronda de diseño** | `validateStrings` |
| `strings_en.json` | claves EN (**paridad obligatoria** con ES, mismo commit) | `validateStrings` + `validateStringsPair` |
| `terreno.json` | **9** tipos de terreno (velocidad, visibilidad, encuentro, cobertura) — paso **1.1** | `validateTerreno` |
| `props.json` | **9** familias de props (24 piezas, colisión, LOD, densidad por terreno) — **1.1** | `validateProps` |
| `edificios.json` | **14** edificios (servicio, entrable, terreno, fuego, modelo, peso) — **1.1** | `validateEdificios` |
| `assets.json` | **10** GLB de reserva con ficha (espejo de `art/AUTORES.md`, por crear) — **1.1** | `validateAssets` |
| `lugares.json` | **6** sitios de la demo: rebanada de fachada (puerta, camino, plantilla) — **1.1** | `validateLugares` |
| `memoria.json` | Bandas de memoria y de Firma (7 + 7), hechos (16 + 14), topes de guardado, deuda, rencor y enmienda — **1.2** | `validateMemoria` |

**Reglas de cruce** (las aplicará `tools/validate_data.js` cuando exista):

- Las claves `txt_*` existen en **ambos** strings (paridad ES/EN).
- Todo asset referenciado existirá en disco (`art/`, `vendor/`).
- Rutas **relativas** en `js/**`: `data/x.json`, `art/x.glb`, `vendor/...` — nunca `/...`.
- Toda `nombre_txt`/`atmosfera` de terreno, edificios y lugares existe en ES **y** EN.
- El `terreno` de lugares y edificios existe en `terreno.json`; las `plantilla` y
  `servicios` de lugares apuntan a edificios reales; las claves de `densidad` de
  `props.json` son terrenos reales; el `modelo` de un edificio está en `assets.json` y el
  fichero **existirá en disco**.
- Las 44 `nombre_txt` de `memoria.json` (7 bandas de memoria + 7 de Firma + 16 hechos de
  memoria + 14 de Firma) existen en ES **y** EN. El cruce de `id` de PNJ con `pnj.json`
  queda **dormido** hasta el paso 1.3.

## Diseñados y pendientes de crear (su doc de diseño ya está aprobado)

| Fichero (por crear) | Para qué | Validador previsto |
|---|---|---|
| `data/personajes.json` | NPCs y enemigos con nombre, rasgos y estadísticas de individuo | `validatePersonajes` |
| `data/mundo.json` | Zonas, caminos y plazas de Valcoria **a pie** | `validateMundo` |
| `data/combate.json` | Reglas del campo de batalla: unidades, formaciones, órdenes | `validateCombate` |
| `data/escenarios.json` | Qué pasa cuando pierdes (cautiverio, rescate, arrastre...) | `validateEscenarios` |
| `data/origenes.json` | Orígenes de partida (soldado/noble/mercader) con sus bonos | `validateOrigenes` |
| `data/profesiones.json` | Profesiones del héroe con sus 3 rangos (**por XP de oficio**), maestros y recurso | `validateProfesiones` |
| `data/recetas.json` | **63 recetas** (9 × 7 profesiones): item, materiales, coste y extra por rango (`sistemas/15_FABRICACION_Y_RECETAS.md`) | `validateRecetas` |

> **Ampliaciones previstas** (diseño 2026-10-01, `sistemas/12` y `13`):
> `data/zonas.json` llevará `nivel_min`/`nivel_max`; `data/tropas.json`,
> `data/companeros.json` y `data/capitanes.json` llevarán `nivel`; `data/progresion.json`
> fijará `nivel_max: 60`.

**Y los catálogos declarados por su documento** (cada uno entra con el paso de su sistema):
`tropas.json`, `enemigos.json`, `capitanes.json`, `companeros.json`, `items.json` (con el
tipo `joya` y las 4 armas de fabricación), `recursos.json` (**11** recursos: 7 de nivel 1
incluidos `hierbas` y `carne`, + `plata`, `piedra`, `cuerda`, `resina` de nivel 2),
`comidas.json`, `estandartes.json`, `habilidades.json`, `profesiones.json` (+ su cruce con
`lugares.json` y `props.json`, `sistemas/14_PROFESIONES.md` §5), `recetas.json`
(`sistemas/15_FABRICACION_Y_RECETAS.md` §10), `origenes.json`, `tutoriales.json`
(8 lecciones), `codice.json` (5 secciones) y `logros.json` (12 logros).
**No se escribe ninguno en caliente:** primero se aprueba el orden en `PLAN_DOCUMENTOS.md`
y se sigue la receta de `ARQUITECTURA.md`.
