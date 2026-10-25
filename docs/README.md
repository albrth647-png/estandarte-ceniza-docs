# docs — indice (que manda sobre que)

> Este indice **apunta, no duplica**: si aqui y en otro documento dicen distinto, gana el
> otro documento. Los numeros viven en un solo sitio; aqui solo se enlaza.

## Jerarquia en caso de conflicto

1. `VALCORIA_DEUDA_DE_SANGRE.md` — **la idea del juego** (manda en pilares, bucle y
   decisiones cerradas).
2. `VISION_JUEGO_COMPLETO.md` — teoria de longevidad y principios de adaptacion (manda en
   principios; es idea, no diseno cerrado).
3. `DECISIONES.md` — log fechado de decisiones del dueño (no reabrir lo cerrado).
4. `ARQUITECTURA.md` — recetas de codigo (organiza, no legisla).
5. `DATOS.md` — checklist de `data/*.json`.
6. `BUGS.md` — registro de bugs (un ALTA bloquea avanzar).
7. `../AGENTS.md` — reglas duras del codigo (no de diseno) · `../README.md` — instalar y correr.

## Documentos

| Documento | Para que |
|---|---|
| [`VALCORIA_DEUDA_DE_SANGRE.md`](VALCORIA_DEUDA_DE_SANGRE.md) | **La idea del juego**: que es, pilares, bucle, controles, memoria, mercado, riesgos y decisiones cerradas. **Empezar aqui.** |
| [`VISION_JUEGO_COMPLETO.md`](VISION_JUEGO_COMPLETO.md) | Por que unos juegos duran meses: horizontes, mejoras duras, agentes con memoria, reloj propio, capas, repeticion con variacion, cronicas. Incluye preguntas abiertas. |
| [`ARQUITECTURA.md`](ARQUITECTURA.md) | Recetas: anadir una escena, una clave `txt_*`, un `data/*.json`, un test. |
| [`DATOS.md`](DATOS.md) | Que ficheros de datos existen, que falta, quien los valida. |
| [`DECISIONES.md`](DECISIONES.md) | Decisiones del dueno con fecha, ya tomadas. |
| [`MECANICAS.md`](MECANICAS.md) | 10 mecanicas candidatas analizadas (encaje, coste, ejes compartidos, ranking). **Candidatas, no decisiones.** |
| [`PLAN_DOCUMENTOS.md`](PLAN_DOCUMENTOS.md) | **La checklist del proyecto completo**: todo lo que el juego lleva dentro, con casillas ✅/🟡 y el orden de trabajo. |
| [`PLAN_MIGRACION_3D.md`](PLAN_MIGRACION_3D.md) | **La capa de dibujo** (fases 0-6): escena única, cámara 1.ª, niebla 60 m, LOD, pooling y reserva a 2D. Plan, no documento de diseño (no cuenta en los 98). |
| [`PROPUESTA_DE_DOCUMENTOS.md`](PROPUESTA_DE_DOCUMENTOS.md) | **Que contendra cada uno de los 98 documentos** y el orden en que se escriben (aprobado 2026-09-30). |
| [`ANALISIS_COBERTURA_DOCUMENTOS.md`](ANALISIS_COBERTURA_DOCUMENTOS.md) | 🧪 **documento de trabajo**: mapea una lista externa de tipos de documento contra los 98; senala 7 huecos (ya redactados 2026-10-01) y lo que queda fuera de alcance. No cuenta en los 98. |
| [`COBERTURA_REQUISITOS.md`](COBERTURA_REQUISITOS.md) | **Trazabilidad**: cada regla dura, pilar y requisito no funcional → documento → test/comando que lo verificará. |
| [`PENDIENTES.md`](PENDIENTES.md) | 🧪 **documento de trabajo**: barrido de **todo lo abierto (🟡)** documento por documento, con la lista maestra. No cuenta en los 98. |
| [`produccion/PLAN_FASE1.md`](produccion/PLAN_FASE1.md) | **El plan de construcción de la demo** (paso a paso: sus 88 documentos, sus JSON, sus sistemas y sus gates). Plan, no documento de diseño. |
| [`historia/`](historia/README.md) | **La historia del juego**: premisa, estructura, actos, finales, personajes, códice y bestiario. Indice en su `README.md`. |
| [`mundo/`](mundo/README.md) | Como es Valcoria y como se camina: mapa, exploracion, viajes, lugares, PNJ y tiempo. |
| [`contenido/`](contenido/README.md) | Los catalogos jugables: tropas, enemigos, capitanes, companeros, items, mercado, habilidades, artefactos, animales, edificios, botin, trampas, comidas y estandartes. |
| [`misiones/`](misiones/README.md) | Encargos, tablones, cadenas, rumores, pagos y los encargos de la historia. |
| [`sistemas/`](sistemas/README.md) | Memoria y deuda, Firma, prisioneros, favores, Cronica, niveles 1-60, estadisticas del heroe, progresion, economia, cicatrices, luto y mundo vivo. |
| [`batalla/`](batalla/README.md) | El campo de batalla: reglas, cifras, terreno, IA/ordenes y presentacion. |
| [`interfaz/`](interfaz/README.md) | Controles, pantallas, HUD, tono/i18n, accesibilidad, tutorial y avisos de contenido. |
| [`arte/`](arte/README.md) | Estilo visual, assets y audio (100 % offline). |
| [`produccion/`](produccion/README.md) | Alcance, fases, guardado, riesgos, QA, mercado, legal, build/firma de la APK, playtest, logros. |
| [`BUGS.md`](BUGS.md) | Registro de bugs con su formato y severidad. |

## Pendiente de documentar

🟡 **La estructura completa del proyecto vive ya en carpetas** — `historia/`, `mundo/`,
`contenido/`, `misiones/`, `sistemas/`, `batalla/`, `interfaz/`, `arte/` y `produccion/` —,
cada una con su `README.md` como indice. La lista con casillas y el estado de cada documento
esta en `PLAN_DOCUMENTOS.md`.

Regla: **no se escribe un documento de diseno hasta que el dueño aprueba el contenido**. Lo
pendiente se marca 🟡 aqui, nunca se rellena inventando.

🟡 **El hueco de numeración `interfaz/09` es intencional** (no hay doc 09): no se rellena sin
decisión del dueño.

## Reglas de mantenimiento

1. Documentacion **actualizada en la misma tarea** que cambia el diseno (DoD).
2. Un doc nuevo **solo con lo ya decidido**; lo pendiente se marca 🟡.
3. Si anades un doc, enlazalo desde aqui (si no, es un doc huerfano).
4. Enlaces relativos verificados por `tools/check_docs.mjs` (por crear en el paso 1.1; parte de `npm run qa`).
5. **Todos los documentos se escriben completos y finales** (decision del dueno, 2026-09-30):
   no se dejan esquemas a medias ni se reescriben; si una cifra queda pendiente, se marca 🟡
   **dentro** del documento y se cierra cuando el dueno la aprueba.
6. **Todos los documentos son del juego FINAL, no de la demo** (decision del dueno,
   2026-09-30): se disena el juego completo (mundo, 10+ por bando, todos los sistemas); dentro
   de cada documento se **marca** que parte entra en la demo (Fase 1) y que parte es
   continuacion (`produccion/01_FASES.md`). Un documento recortado a la demo es un error.
   El unico doc que acota a la demo es `produccion/00_ALCANCE.md`, porque para eso existe.
