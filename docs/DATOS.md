# Datos — checklist de `data/*.json`

> Regla dura 5 de `../AGENTS.md`: **todo JSON nuevo entra con su validador**
> (`js/data/schemas.js`) + chequeo en `tools/validate_data.js`; `loadStrings()` lanza con
> **todos** los errores juntos.
> Este fichero es el mapa: que existe, que falta y quien lo valida.

## Cómo leer este fichero

> **Aviso (2026-10-02):** los **98 documentos de diseño** (`PLAN_DOCUMENTOS.md`) declaran ya sus
> ficheros y su validador en sus apartados de «Datos, tipos y validación». Este checklist es el
> **mapa general**: lo que aquí dice «pendiente» es **pendiente de implementar**, no de diseñar.

## Existentes (8) ✅

| Fichero | Contenido | Validador |
|---|---|---|
| `strings_es.json` | 534 claves ES (portada, menu, creacion, opciones, cargar, creditos + terreno, edificios, lugares + **memoria, Firma y avisos**) | `validateStrings` |
| `strings_en.json` | 534 claves EN (**paridad obligatoria** con ES) | `validateStrings` + `validateStringsPair` |
| `terreno.json` | **9** tipos de terreno (velocidad, visibilidad, encuentro, cobertura) — paso **1.1** | `validateTerreno` |
| `props.json` | **9** familias de props (24 piezas, colisión, LOD, densidad por terreno) — **1.1** | `validateProps` |
| `edificios.json` | **14** edificios (servicio, entrable, terreno, fuego, modelo, peso) — **1.1** | `validateEdificios` |
| `assets.json` | **10** GLB existentes con ficha (espejo de `art/AUTORES.md`) — **1.1** | `validateAssets` |
| `lugares.json` | **6** sitios de la demo: rebanada de fachada (puerta, camino, plantilla) — **1.1** | `validateLugares` |
| `memoria.json` | Bandas de memoria y de Firma (7 + 7), hechos (16 + 14), topes de guardado, deuda, rencor y enmienda — **1.2** | `validateMemoria` |

Salida actual de `npm run validate`:
`OK: 534 claves ES/EN con paridad verificada.` +
`OK: terreno(9) props(9) edificios(14) assets(10) lugares(6) validados; memoria(bandas 7+7 · hechos 16+14) OK; cruces en verde.`

> **Aviso:** la mayoria de estas claves pertenecen al primer juego (Hector de la demo, mapa,
> batalla...). Todavia **no se han depurado**: cuando el diseno del juego nuevo este cerrado,
> se revisan las claves que siguen haciendo falta y se quitan las viejas. No se hace antes
> para no romper el armazón que hoy funciona.

## Pendientes ⬜ (diseño no aprobado todavia)

| Fichero | Para que | Validador previsto |
|---|---|---|
| `data/personajes.json` | NPCs y enemigos con nombre, rasgos y estadisticas de individuo | `validatePersonajes` |
| `data/mundo.json` | Zonas, caminos y plazas de Valcoria **a pie** (sin rejilla por casillas) | `validateMundo` |
| `data/combate.json` | Reglas del campo de batalla: unidades, formaciones, ordenes | `validateCombate` |
| `data/escenarios.json` | Que pasa cuando pierdes (cautiverio, rescate, arrastre...) | `validateEscenarios` |
| `data/origenes.json` | Origenes de partida (soldado/noble/mercader) con sus bonos | `validateOrigenes` |
| `data/profesiones.json` | Profesiones del heroe con sus 3 rangos (**por XP de oficio**), maestros y recurso | `validateProfesiones` |
| `data/recetas.json` | **63 recetas** (9 × 7 profesiones): item, materiales, coste y extra por rango (`sistemas/15_FABRICACION_Y_RECETAS.md`) | `validateRecetas` |

> **Ampliaciones de ficheros ya previstos** (diseno 2026-10-01, `sistemas/12` y `13`):
> `data/zonas.json` gana `nivel_min`/`nivel_max`; `data/tropas.json`, `data/companeros.json` y
> `data/capitanes.json` ganan `nivel`; `data/progresion.json` pasa a `nivel_max: 60`.

**Ninguno de estos existe todavia** y **no se crea ninguno** sin que el dueño apruebe primero
el diseño correspondiente (regla: datos → código → tests → documentación).

> **Lo que ya está diseñado y falta crear** (cada doc lo declara):
> `units/tropas.json`,
> `enemigos.json`, `capitanes.json`, `companeros.json`, `items.json` (suman el tipo `joya` y las
> 4 armas nuevas), `recursos.json` (**11** recursos: 7 de nivel 1 + `plata`, `piedra`, `cuerda`,
> `resina` de nivel 2), `comidas.json`, `estandartes.json`, `habilidades.json`,
> `profesiones.json` (+ su cruce con `lugares.json` y `props.json`, `sistemas/14_PROFESIONES.md`
> §5) y `recetas.json` (**nuevo 2026-10-02**, `sistemas/15_FABRICACION_Y_RECETAS.md` §10),
> `origenes.json` y — nuevos el 2026-10-01 — `tutoriales.json` (8 lecciones),
> `codice.json` (5 secciones) y `logros.json` (12 logros). **No se escriben en caliente:** siguen
> el orden `PLAN_DOCUMENTOS.md` → `ARQUITECTURA.md`.

## Reglas de cruce (en `tools/validate_data.js`)

- Las claves `txt_*` existen en **ambos** strings (paridad ES/EN).
- Todo asset referenciado existe en disco (`art/`, `vendor/`).
- Rutas **relativas** en `js/**`: `data/x.json`, `art/x.glb`, `vendor/...` — nunca `/...`.
- **Cruces nuevos (1.1):** toda `nombre_txt`/`atmosfera` de terreno, edificios y lugares existe
  en ES **y** EN · el `terreno` de lugares y edificios existe en `terreno.json` · las
  `plantilla` y `servicios` de lugares apuntan a edificios reales · las claves de `densidad`
  de `props.json` son terrenos reales · el `modelo` de un edificio está en `assets.json` y el
  fichero **existe en disco**.
- **Cruces nuevos (1.2):** las 44 `nombre_txt` de `memoria.json` (7 bandas de memoria + 7 de
  Firma + 16 hechos de memoria + 14 de Firma) existen en ES **y** EN. El cruce de `id` de PNJ
  con `pnj.json` sigue **dormido** hasta el paso 1.3.
