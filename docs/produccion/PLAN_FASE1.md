# PLAN_FASE1 — cómo se construye la demo del Acto I

**Estado:** ✅ **Plan de ejecución (2026-10-02, pedido del dueño).**
**No cuenta en los 98 documentos de diseño** (es un plan de trabajo, como `PLAN_DOCUMENTOS.md`).
**Alcance:** solo la **Fase 1** — el alcance lo manda `00_ALCANCE.md`; el mapa de fases 1-5 vive
en `01_FASES.md`.

> **Cómo leerlo:** `01_FASES.md` §2 dice **qué es** la Fase 1 y **cuándo cierra**; **este documento
> dice cómo se construye** — los **88 documentos**, los **JSON**, el **código**, las **costuras de
> test** y el **gate** de cada paso.

---

## 1. Criterio: «la mejor impresión del juego»

| # | Regla | Se comprueba en |
|---|---|---|
| **I1** | **Nada a medias.** Si aparece en pantalla, funciona completo. Lo que no se pueda cerrar, **no se enseña**. | `00_ALCANCE` §5 |
| **I2** | **El núcleo tiene que verse.** Memoria, Firma, prisioneros, favores y Crónica dan **feedback visible** (aviso, color, sonido): no basta con existir en el guardado. | `../interfaz/07_AVISOS_Y_RUMORES.md` |
| **I3** | **Los 30 minutos cumplen** `00_ALCANCE` §4. Si a los 30 min no entiendes que *las deudas y la memoria son el juego*, la demo fracasa aunque esté «terminada». | prueba manual de §6 |
| **I4** | **La promesa literal manda:** *«un reino entero apunta tu nombre en un libro»* → el **Registro simple** está en la demo. | `../interfaz/05_LIBRO_MAYOR.md` |
| **I5** | **Presentación en cada paso.** El 1.7 es **acabado**, no *la primera vez que se ve bien*: cada paso cierra con su audio, su aviso y su icono. | gates de §6 |
| **I6** | **Presupuesto de impresión:** 60 fps · parpadeo ≤ 3 Hz · avisos ≤ 3 s · iconos ≥ 48 px · audio 100 % offline · humo en 2 tamaños. | `../arte/*`, `../interfaz/04_ACCESIBILIDAD.md` |
| **I7** | **Aspecto de película (2026-10-02):** dirección de fotografía en el paisaje (luz de tarde, niebla, paleta de tierra) · **todos los cuerpos, de proporción humana** · **retrato pintado** de los 16 clave en los bocadillos. Y el gama media sigue a **60 fps**: si algo pesa, se baja textura, no la escena. | `../arte/00_ESTILO.md` §1, `../arte/01_ASSETS.md` §2b |

---

## 2. Los 88 documentos, repartidos por paso

**Ningún documento se escribe (todos están ✅): aquí se dice QUÉ se usa en cada paso.**
Los **9 documentos diferidos** a las Fases 2-5 están en `01_FASES.md` §3-§6.

| Paso | Documentos que usa | N.º |
|---|---|---|
| **1.1 · Esqueleto de exploración** | `../mundo/01_EXPLORACION` · `../mundo/06_TERRENO_DEL_MUNDO` · `../mundo/07_PROPS_Y_VEGETACION` · `../contenido/09_EDIFICIOS_Y_ESTRUCTURAS` · `../interfaz/00_CONTROLES` · `../interfaz/02_HUD` · `02_GUARDADO_Y_DATOS` | **7** |
| **1.2 · Memoria y Firma** | `../sistemas/00_MEMORIA_Y_DEUDA` · `../sistemas/01_FIRMA` · `../mundo/04_PNJ` · `../interfaz/07_AVISOS_Y_RUMORES` | **4** |
| **1.3 · El mundo de la demo** | `../mundo/00_MAPA` · `../mundo/02_VIAJE_Y_ENCUENTROS` · `../mundo/03_LUGARES` · `../mundo/05_TIEMPO_DEL_MUNDO` · `../mundo/08_AGUA_RIOS_Y_PUENTES` · `../mundo/09_CLIMA_Y_ESTACIONES` · `../mundo/10_SUPERVIVENCIA_Y_DESCANSO` · `../mundo/11_CIUDADES` · `../interfaz/08_TRANSICIONES_Y_CARGAS` | **9** |
| **1.4 · El campo de batalla** | `../batalla/00_REGLAS` · `01_CIFRAS` · `02_TERRENO` · `03_IA_Y_ORDENES` · `04_PRESENTACION` · `05_CATALOGO_DE_CAMPOS` · `06_BATALLAS_DE_LA_HISTORIA` · `../contenido/00_TROPAS` · `01_ENEMIGOS` · `02_CAPITANES_Y_NEMESIS` · `06_HABILIDADES` · `10_VOCES_Y_GRITOS` · `11_TABLAS_DE_BOTIN` · `12_TRAMPAS_Y_OBSTACULOS` · `13_MONTURAS_Y_TRANSPORTE` · `15_ESTANDARTES_E_INSIGNIAS` · `../sistemas/12_NIVELES_DEL_HEROE` · `13_ESTADISTICAS_DEL_HEROE` | **18** |
| **1.5 · Después de la batalla** | `../sistemas/02_PRISIONEROS` · `03_FAVORES` · `04_CRONICA` · `05_PROGRESION` · `06_ECONOMIA` · `11_DEUDAS_DEL_JUGADOR` · `14_PROFESIONES` · `15_FABRICACION_Y_RECETAS` · `../contenido/04_ITEMS_Y_EQUIPO` · `05_RECURSOS_Y_MERCADO` · `14_COMIDAS_Y_BEBIDAS` | **11** |
| **1.6 · El Acto I completo** | `../historia/00_PREMISA` · `01_ESTRUCTURA` · `02_PERSONAJES` · `03_RECORRIDO` · `04_GUION` · `05_CASAS_Y_FACCIONES` · `06_CRONOLOGIA` · `07_LEYENDAS_Y_RUMORES` · `08_TEXTO_DEL_MUNDO` · `../misiones/00..05` (6) · `../interfaz/03_I18N_Y_TONO` · `05_LIBRO_MAYOR` · `../contenido/03_COMPANEROS` | **18** |
| **1.7 · Pulido** | `../arte/00_ESTILO` · `01_ASSETS` · `02_AUDIO` · `03_ANIMACIONES` · `04_EFECTOS_Y_PARTICULAS` · `05_ICONOS` · `../interfaz/01_PANTALLAS` · `04_ACCESIBILIDAD` · `10_TUTORIAL_Y_FIRST_RUN` · `11_AVISOS_DE_CONTENIDO` | **10** |
| **1.8 · Cierre y publicación** | `00_ALCANCE` · `01_FASES` · `03_RIESGOS` · `04_QA` · `05_MERCADO_Y_LANZAMIENTO` · `06_LEGAL_Y_AUTORIA` · `07_RELEASES_Y_VERSIONES` · `08_PLATAFORMAS_Y_MINIMOS` · `09_PRIVACIDAD_Y_DATOS` · `10_BUILD_Y_FIRMA_APK` · `11_PLAYTEST_Y_BETA` | **11** |

**Total: 88 de los 97 documentos de diseño** (el resto: 9 diferidos + `01_FASES`, que es el mapa de
fases). A ellos se suma `../COBERTURA_REQUISITOS.md` (trazabilidad, no de fase).

---

## 3. Datos nuevos por paso (cada uno con su validador)

| Paso | `data/*.json` que se crean |
|---|---|
| **1.1** | `lugares.json` (fachadas) · `terreno.json` · `props.json` · `edificios.json` · `assets.json` |
| **1.2** | `memoria.json` (rangos, hechos, pesos ±2/5/10/15, **topes de guardado**) |
| **1.3** | `zonas.json` · `lugares.json` (6 sitios) · `caminos.json` · `ciudades.json` · `tiempo.json` · `agua.json` · `clima.json` · `supervivencia.json` · `pnj.json` |
| **1.4** | `tropas.json` (3) · `enemigos.json` (3 familias) · `capitanes.json` (4+) · `combate.json` · `campos.json` (2) · `habilidades.json` · `botin.json` · `estandartes.json` · `voces.json` · `trampas.json` · `facciones.json` · `progresion.json` · `origenes.json` · `transporte.json` |
| **1.5** | `economia.json` · `escenarios.json` (cautiverio) · `recursos.json` (7) · `items.json` · `comidas.json` · `favores.json` · `profesiones.json` · `recetas.json` (3 base) |
| **1.6** | `encargos.json` (6) · `encargos_historia.json` · `dialogos.json` · `rumores.json` · `tablones.json` · `cronologia.json` · `texto_mundo.json` · `personajes.json` · `companeros.json` · **300-450 claves `txt_*` ×2** |
| **1.7** | `audio.json` · `animaciones.json` · `efectos.json` · `iconos.json` · `estilo.json` · `tutoriales.json` |
| **1.8** | — |

Cada JSON entra con su esquema en `js/data/schemas.js` y su cruce en `tools/validate_data.js`
(regla 5): **sin validador en verde, no se considera cerrado**.

**Fuera de la Fase 1:** `cicatrices`, `luto`, `lealtad`, `mundo_vivo`, `artefactos`, `animales`,
`codice`, `logros`.

---

## 4. Código nuevo por paso

| Paso | `js/systems/*` (puros: sin DOM, sin `fetch`, sin reloj) | `js/scenes/*` (solo dibujan) | Render |
|---|---|---|---|
| **1.1** | `exploracion.js` · `terreno.js` · `props.js` · `edificios.js` | `sc_exploracion.js` | `js/render/escena3d.js` |
| **1.2** | `memoria.js` · `firma.js` · `pnj.js` | `sc_exploracion.js` + **cola de avisos en `js/scenes/avisos.js`** (aparte de la escena, regla 12 de tope 500 líneas) | síntesis de aviso (Web Audio) |
| **1.3** | `viaje.js` · `tiempo.js` · `clima.js` · `supervivencia.js` · `rumores.js` | `sc_mundo.js` | — |
| **1.4** | `campo.js` · `ia.js` · `tropas.js` · `enemigos.js` · `habilidades.js` · `botin.js` · `estandartes.js` · `trampas.js` · `progresion.js` | `sc_batalla.js` | pooling + LOD |
| **1.5** | `prisioneros.js` · `favores.js` · `cronica.js` · `economia.js` · `pagos.js` · `mercado.js` · `items.js` · `comida.js` · `profesiones.js` · `fabricacion.js` | `sc_postbatalla.js` · `sc_tienda.js` | — |
| **1.6** | `encargos.js` · `tablon.js` · `texto_mundo.js` · `companeros.js` | `sc_historia.js` · `sc_libro.js` | — |
| **1.7** | `tutorial.js` · `avisos.js` | `sc_pantallas.js` | audio · animaciones · efectos |
| **1.8** | — | — | build y firma de APK |

**Guardado:** `SAVE_VERSION` **1** desde el paso 1.1; si un paso añade campos al esquema, la
versión sube de forma **aditiva** (`02_GUARDADO_Y_DATOS.md`). La migración se probará en cada
subida (DoD, regla 6).
> **Lectura (greenfield):** el guardado nace en **v1** con el esquema completo de la demo declarado
> desde el principio (los campos quedan vacíos hasta que su sistema entra). Así ningún campo cambia
> de número y ninguna migración se rehace; las versiones futuras solo crecen de forma aditiva.

---

## 5. Costuras de test (TDD: se acuerdan ANTES de escribir código)

Costura = **interfaz pública** por la que se observa el comportamiento. Rojo → verde, **una
rebanada vertical a la vez** (nunca «todos los tests y luego todo el código»). El test no mira
dentro: sobrevive a cualquier reescritura interna.

| Paso | Costura pública | Casos (normal · borde · error) |
|---|---|---|
| **1.1** | `colisiona(pos, obstaculos)` · `enfocable(pos, dir, dist)` | normal / pegado al muro / `dist` negativa |
| **1.2** | `aplicarHecho(ficha, hecho, dia)` · `bandaDe(rango)` · `aplicarFirma(estado, hecho, conTestigos)` · `rangoInicialPorFirma(firma)` · `colaAvisos(encolar, tick)` | normal / en el tope ±100 y techo de rencor −20 / hecho fuera de catálogo y aviso caducado |
| **1.3** | `diasDeViaje(origen, destino, clima)` · `tiradaEncuentro(estado, rng)` | normal / mismo nodo / zona desconocida |
| **1.4** | `tick(dt, campo, ordenes, rng)` · `moralDe(unidad)` · `romperMoral(bando)` | normal / `dt` 0 / unidad muerta |
| **1.5** | `salidas(prisionero)` · `rescate(nivel, tipo)` · `redito(dias)` · `cobrarFavor(favor, dia)` · `recetaAplicable()` | normal / cuarto lleno / receta sin material |
| **1.6** | `validarEncargo(encargo)` · `avanzarObjetivo(objetivo, hecho)` | normal / objetivo cumplido / sin salida |
| **1.7** | `leerAviso(aviso, cpc)` · `claveDe(tutorial)` | normal / al tope de frecuencia / clave huérfana |
| **1.8** | `migrar(guardado)` · `slotLibre()` | normal / corrupto → respaldo / versión futura |

Con la **regla del repo** encima: ≥ 3 casos por módulo y cobertura ≥ 90 % sobre `js/**`.
RNG y `dt` **siempre inyectados** (determinismo, regla 9 de `AGENTS.md`).

---

## 6. Los pasos, uno a uno

Cada paso cierra con: **`npm run qa` verde + hito jugable + presentación mínima (I5)**.

### 1.1 · Esqueleto de exploración
- **Hito:** caminas en 1.ª persona, miras, entras y sales de un sitio y **el juego guarda**.
- **Datos:** `lugares`, `terreno`, `props`, `edificios`, `assets`.
- **Código:** `sc_exploracion.js` + `exploracion/terreno/props/edificios.js` + `escena3d.js`.
- **Tests:** costuras de 1.1 + `exploracion`, `terreno`, `props`, `edificios`.
- **Gate:** humo 2 tamaños · 10 min sin errores · **QA verde**.
- **Riesgo:** controles incómodos → **probar con pulgares reales antes de 1.2**.
- **Esfuerzo:** **M**.

### 1.2 · Memoria y Firma
- **Hito:** enfocas la escribanía, haces una **enmienda** y tu **Firma cambia de banda** delante de
  todos; el cambio **queda guardada** y su aviso se oye solo (sin popup). Si abajo no llega con
  todo lo que promete el enunciado original («un PNJ al que perdonas te recuerda»), **se recorta
  el enunciado, no la calidad** (I1): el perdón es un **fin de batalla (1.4/1.5)** y el **recuerdo
  personal** no es observable en el mundo hasta que `pnj.json` llegue en **1.3**. Aquí la memoria
  se comprueba **en los tests puros y en la sonda `?debug=1`**, no fingiéndose en pantalla.
- **Datos:** `memoria.json` con **topes de guardado**.
- **Código (por construir):** `memoria.js`, `firma.js`, `pnj.js` · guardado: campos de memoria y Firma (aditivo).
- **Tests:** costuras de 1.2 (RNG solo donde el diseño lo pida: **en memoria y Firma no hay**
  ninguno — los pesos están fijados en tabla, así que no se inventa).
- **Gate:** cobertura ≥ 90 % en esos módulos · **topes fijados aquí** · presentación mínima
  (01_FASES §7): aviso con su icono y su **sonido sintetizado** (Web Audio, offline; el
  catálogo completo de audio va en **1.7**).
- **Riesgo:** el guardado se llena → recortar **topes**, nunca la mecánica.
- **Esfuerzo:** **S**.

### 1.3 · El mundo de la demo
- **Hito:** recorres el camino entero entre los **6 sitios**, con viaje por días y encuentros.
- **Datos:** `zonas`, `lugares` (6), `caminos`, `ciudades`, `tiempo`, `agua`, `clima`, `supervivencia`, `pnj`.
- **Código:** `viaje`, `tiempo`, `clima`, `supervivencia`, `rumores` + `sc_mundo.js`.
- **Tests:** costuras de 1.3 + `viaje`, `tiempo`, `clima`, `supervivencia`, `pnj`.
- **Gate:** `npm run validate` verde · cada sitio con su razón de ser · sin esperas reales.
- **Riesgo:** mapa más grande que el alcance → **manda `00_ALCANCE` (6 sitios)**.
- **Esfuerzo:** **M**.

### 1.4 · El campo de batalla (pequeño, completo)
- **Hito:** ganas **rompiendo la moral**; tres huyen; esgrimes en 1.ª persona con tus botones y tu
  barra de órdenes. **5-6 por bando** (8 en el cierre).
- **Datos:** los 14 JSON de la fila 1.4.
- **Código:** `campo`, `ia`, `tropas`, `enemigos`, `habilidades`, `botin`, `estandartes`,
  `trampas`, `progresion` + `sc_batalla.js` · guardado: campos de batalla (aditivo).
- **Tests:** costuras de 1.4 + `campo`, `ia`, `tropas`, `enemigos`, `campos`.
- **Gate:** pruebas **puras** de la simulación · humo con el campo abierto · **fps medidos**.
- **Riesgo:** 6 unidades aprietan en móvil → presupuesto de render y campos simples; subir a 8
  antes de 1.5 si no se siente.
- **Esfuerzo:** **L** (camino crítico).

### 1.5 · Después de la batalla
- **Hito:** capturas a un capitán, lo **volteas** y te lo encuentras después; si **caes tú**, el
  mundo decide y **no te atasca**; la profesión del origen fabrica sus **3 recetas base**.
- **Datos:** los 8 JSON de la fila 1.5.
- **Código:** `prisioneros` (4 salidas + §3.1 cuartos), `favores`, `cronica`, `economia`,
  `mercado`, `items`, `profesiones`, `fabricacion` · guardado: campos de economía (aditivo).
- **Tests:** costuras de 1.5 + `prisioneros`, `favores`, `cronica`, `economia`, `profesiones`,
  `recetas`, `migracion`.
- **Gate:** migración probada · **0 caminos sin salida** · **máximo 4 decisiones** post-batalla.
- **Riesgo:** demasiadas decisiones → recortar a las 4 esenciales.
- **Esfuerzo:** **M**.

### 1.6 · El Acto I completo
- **Hito:** la demo **se juega del cadalso al giro final**, con el flashback del Paso y el
  **Registro simple** (I4).
- **Datos:** los 9 JSON de la fila 1.6 + **300-450 claves `txt_*` ×2**.
- **Código:** `encargos`, `tablon`, `texto_mundo`, `companeros` + `sc_historia.js`, `sc_libro.js`.
- **Tests:** costuras de 1.6 + `encargos`, `rumores`, `cronica`, `companeros`.
- **Gate:** **paridad ES/EN 100 %** · recorrido sin atascos · el giro cierra con gancho.
- **Riesgo:** el guion se desborda → recortar **secundario**, nunca la columna vertebral.
- **Esfuerzo:** **L** (camino crítico).

### 1.7 · Pulido de la demo
- **Hito:** demo presentable a alguien ajeno: **se ve, se oye y se siente** como una **película
  medieval** — paisaje con luz y niebla, personas de proporción humana con su retrato, voz del
  elenco relevante y audio offline.
- **Datos:** `audio`, `animaciones`, `efectos`, `iconos`, `estilo`, `tutoriales` (los retratos y
  cuerpos entran por `assets.json`, creado en 1.1).
- **Código:** `tutorial`, `avisos` + pantalla del Registro completa.
- **Gate:** 10 min sin errores · sin bajones en un dispositivo modesto · **I6** e **I7** completos
  · **el dueño aprueba los topes de MB al ver la primera escena de paisaje** (gate de peso,
  `../arte/01_ASSETS.md` §3).
- **Riesgo:** pulir antes de que el bucle funcione → **prohibido**: va después de 1.6.
- **Esfuerzo:** **M**.

### 1.8 · Cierre y publicación de la demo
- **Hito:** una persona que no eres tú la descarga y juega sus 2-3 horas.
- **Gate:** `npm run qa` verde + humo en dos ventanas + guardados migrables desde la penúltima
  versión + **playtest de 5 jugadores** **antes** de publicar.
- **Riesgo:** publicar sin demostrar la promesa → revisar `00_ALCANCE.md` §4.
- **Esfuerzo:** **S**.

---

## 7. Orden crítico y esfuerzo

| Paso | Esfuerzo | Depende de |
|---|---|---|
| 1.1 | **M** | — |
| 1.2 | **S** | 1.1 |
| 1.3 | **M** | 1.1 |
| 1.4 | **L** | 1.1, 1.3 |
| 1.5 | **M** | 1.4 |
| 1.6 | **L** | 1.5 |
| 1.7 | **M** | 1.6 |
| 1.8 | **S** | 1.7 |

**Camino crítico: 1.1 → 1.4 → 1.6 → 1.8.** El 1.4 es el que más alarga; el 1.2 es el más barato
y no debe esperar a 1.3. Los hitos de 1.1 y 1.3 se pueden **probar con pulgares reales en
paralelo** mientras avanza 1.4, sin abrir la Fase 2.

---

## 8. Criterio de terminado de la Fase 1

Hereda `00_ALCANCE.md` §6 y añade el criterio de impresión:

1. **Se juega de principio a fin** (prólogo → giro final) sin atascos ni callejones sin salida.
2. **El fallo nunca bloquea**: caer, perder una batalla o no pagar siempre dan salida.
3. **Guardado intacto**: guardar, cargar, migrar, slots y respaldo del corrupto, funcionando.
4. **`npm run qa` verde** (check + lint + validate + docs + tests ≥ 90 % + humo 2 tamaños).
5. **Paridad ES/EN** y **cero enlaces rotos**.
6. **10 minutos sin errores en consola.**
7. **Los primeros 30 minutos cumplen** `00_ALCANCE` §4 (**I3**).
8. **Los 5 sistemas núcleo se ven y se sienten** (**I2**).

---

## 9. Fuera de este documento

- Alcance de la demo y qué queda fuera → `00_ALCANCE.md`
- Mapa de fases 1-5 y reglas del método → `01_FASES.md` §1-§2
- Qué JSON existe y quién los valida → `../DATOS.md`
- Riesgos con detección temprana y plan B → `03_RIESGOS.md`
- Capa de dibujo (fases 0-6) → `../PLAN_MIGRACION_3D.md`
- Criterio de QA y DoD → `04_QA.md`
