# Valcoria — Deuda de Sangre · Guía para Agentes AI

Juego web medieval single-player, **1.ª persona**, 100 % offline y estático.
**Stack previsto:** JavaScript ES2022 + JSDoc (sin transpilador) · Three.js/WebGL2 con reserva
a 2D · JSON de datos · `localStorage` · Node ≥ 18 solo para tooling/tests.

> **Estado greenfield:** hoy este repositorio es **solo documentación** (98 documentos de
> diseño). No hay `js/`, `data/`, `tests/` ni `tools/`: todo lo que sigue es **el contrato que
> el build cumplirá desde el primer commit** (Fase 1, `docs/produccion/PLAN_FASE1.md`). Cuando
> exista el código, las herramientas de QA se crean en el paso 1.1 y estas reglas pasan a
> verificarse con `npm run qa`.

## El contrato de QA (se construye en el paso 1.1)

```bash
npm run qa              # = check + tamano + lint + validate + docs + test:cov + smoke + vivo
npm run check           # tsc estricto sobre js/, tools/, tests/
npm run tamano          # 500 lineas/archivo (+ aviso a 450) y peso maximo en data/ y css/
npm run validate        # node tools/validate_data.js (JSON jugables)
npm run docs            # node tools/check_docs.mjs (enlaces markdown)
npm run test            # node --test "tests/*.test.js"
npm run smoke           # Chromium headless + index.html?smoke=1
npm run vivo            # Chromium + CDP: recorrido real (caminar, mirar, guardar, recargar);
                        # mide fps y 0 errores de consola
npm run serve           # servidor estatico local puerto 8123
```

**El QA DEBE pasar entero antes de dar una tarea por hecha** (en cuanto exista el build).
Para el cierre de cada fase se navega ADEMAS con el MCP de navegador del entorno
(`docs/produccion/04_QA.md` §4b) sobre `npm run serve`.

## Reglas duras (el código que se escriba las cumple desde el minuto uno)

1. **`js/**` solo globals de navegador.** Si aparece `process`, `require` o `__dirname` en `js/`,
   ESLint falla y la APK se rompería. Node solo en `tools/` y `tests/`.
2. **Sistemas puros.** `js/systems/*` no tocan DOM, ni `fetch`, ni reloj. Reciben dependencias
   (RNG, dt). Las escenas dibujan; los sistemas simulan. Esto permite testear sin navegador.
3. **Rutas de datos relativas.** Siempre `data/*.json`, nunca `/data/...` (regla APK/Capacitor).
   Lo mismo con `vendor/` y `art/`.
4. **Tipos una sola vez.** Typedefs en `js/data/game_types.js`, se importan con
   `import("./game_types.js").X`. `tsc` en estricto: sin `any` implícito, sin vars sin usar.
5. **Datos validados o no arranca.** Todo JSON nuevo entra con su validador en
   `js/data/schemas.js` + chequeo en `tools/validate_data.js`. La carga de textos lanza con
   todos los errores juntos.
6. **Guardado versionado.** El módulo de guardado define `SAVE_VERSION` (arranca en **1**) y la
   migración aditiva; corrupto → copia de seguridad (`valcoria_save.corrupt`), nunca arrancar
   con datos rotos. Todo lo nuevo que entre al guardado es **aditivo** y **acotado** (el
   `localStorage` del móvil ronda 5 MB).
7. **Originalidad.** Cero activos, nombres o textos de juegos de terceros. Arte y audio: solo
   material propio o libre con ficha (ver `THIRD_PARTY.md`, por crear en la Fase 1).
8. **Offline y sin esperas reales.** Nada de servidores, CDNs ni «vuelve en 24 h»: todo el
   gating es en días de juego acelerables jugando.
9. **Determinismo.** Misma partida = mismo mundo. El tiempo siempre **entra inyectado** por
   parámetro; ningún sistema consulta el reloj del sistema.
10. **Paridad ES/EN.** Toda clave `txt_*` nace en **ambos** idiomas en el mismo commit.
11. **Presentación en escenas.** Efectos visuales y audio viven solo en `js/scenes/*`, nunca en
    `js/systems/*`.
12. **Tope de 500 líneas por archivo.** Ningún archivo de código (`js/`, `tools/`, `tests/`,
    `css/`) puede pasar de **500 líneas**: el que se pase **se divide según su longitud**
    (un archivo = una responsabilidad; si aún no cabe, `x.js` + `x_datos.js`, `x_sistema.js`
    …). Lo verificará `npm run tamano` dentro de `npm run qa`. **Aviso desde 450 líneas**:
    dividir *antes* de tocar el tope.

## Más reglas duras

13. **Todo check emitido se afirma.** Un `checks.push(...)`, un `assert` o un estado de humo
    que nadie lee puede mentir en verde. Cada check emitido tiene su `assert` (o su lectura) en
    un test; si no puede verificarse desde fuera, no se emite.
14. **Una decisión, un sitio.** Un valor (un tope, un umbral, un color de marca, una versión)
    vive en **un** módulo y el resto lo importa. Nada de constantes repetidas que se
    desincronizan al cambiar uno.
15. **Targets táctiles verificados, no de palabra.** Todo elemento pulsable de la interfaz
    medirá **≥ 48 px** en su lado menor (`docs/produccion/04_QA.md` §I6). Un test lo
    comprobará **leyendo el CSS de verdad**.
16. **Ningún paso se enseña sin acabar (I5).** Un paso cierra con su **aviso, su icono y su
    sonido**: si algo sale en pantalla sin icono, sin sonido o sin salir de la escena, está a
    medio hacer. `PLAN_FASE1.md` §1 I5 manda sobre este recordatorio.
17. **Los conflictos de docs se anotan, no se heredan.** Cuando dos documentos se contradigan y
    ambos digan «esto manda», el conflicto se **anota al cerrar la tarea** en el documento
    afectado y, si cambia el diseño, en `docs/DECISIONES.md`. Un doc obsoleto no se corrige en
    silencio.
18. **`npm run tamano` mirará código *y* peso.** Además de las 500 líneas, comprobará el
    **peso máximo** de cada fichero de `data/` y `css/` (los JSON se descargan al móvil y el
    juego es offline: un fichero enorme rompe el arranque o la carga).

## Estructura prevista (capacidades, no inventario)

Este bloque describe **qué vivirá dónde** cuando exista el código. Para ver ficheros reales,
`ls js/* data css` (cuando existan).

| Carpeta | Capacidad prevista |
|---|---|
| `index.html` | shell horizontal, `#ui` (toda la interfaz), `#boot-status` (arranque) |
| `css/` | interfaz: paleta, layout y hoja de cada escena; targets táctiles ≥ 48 px (regla 15) |
| `js/main.js` | arranque: datos → guardado → escenas → bucle; y el modo humo |
| `js/core/` | infraestructura: bucle, escenas, input, RNG, i18n, opciones, pantalla, **audio** y guardado |
| `js/data/` | carga y **validación** de JSON, y los typedefs (`game_types.js`) |
| `js/render/` | dibujo 3D: contexto WebGL, carga y aligerado de GLB, escena, reserva a 2D |
| `js/systems/` | **simulación pura** (sin DOM, sin reloj): diálogo, edificios, exploración, firma, memoria, props, terreno |
| `js/scenes/` | pantallas y HUD: pintan y capturan entrada, no simulan (regla 2) |
| `data/` | contenido jugable en JSON + `strings_es/en.json` (paridad obligatoria, regla 10) |
| `art/` + `vendor/` | modelos GLB propios y Three.js (local, sin CDN: regla 8) |
| `tools/` | Node puro: servidor, validaciones, tamaño, enlaces, humo y navegación en vivo |
| `tests/` | `node:test` + jsdom; espejan `js/`; un fichero por módulo |
| `docs/` | diseño por carpetas; el índice y qué manda sobre qué están en `docs/README.md` |

## Convenciones

| Elemento | Regla |
|---|---|
| Estilo | ES2022, `const` primero, `eqeqeq`, sin `var`, JSDoc en toda función pública |
| Nombres | `snake_case` archivos/ids de datos, `camelCase` funciones, `PascalCase` clases |
| Datos | ids `snake_case` (`puerto_ceniza`), claves de texto `txt_*`, colores `#rrggbb` |
| Tests | `tests/<modulo>.test.js`, mínimo 3 casos (normal, borde, error); `node --test` |
| Tamaño | ≤ **500 líneas** por archivo; dividir por longitud si se pasa (`npm run tamano`) |
| DoD tarea | `npm run qa` verde (incluye `vivo`: 0 errores de consola en el recorrido) + guardar/cargar intacto + doc actualizado si cambia diseño |
| DoD fase | lo de arriba + la **prueba manual de 10 min** de `docs/produccion/04_QA.md` §4 + navegación con MCP |
| Bugs | `ID \| fecha \| pantalla \| pasos \| esperado \| actual \| ALTA/MEDIA/BAJA \| ABIERTO→EN CURSO→ARREGLADO→VERIFICADO` — un ALTA bloquea avanzar; registro en `docs/BUGS.md` |
| Orden | **datos → código → tests → documentación**. Nunca al revés. |

## Mapa de documentos

- **Idea del juego** (pilares, bucle, controles, decisiones cerradas): `docs/VALCORIA_DEUDA_DE_SANGRE.md`.
- **Visión y teoría de longevidad**: `docs/VISION_JUEGO_COMPLETO.md`.
- **Índice (qué manda sobre qué)**: `docs/README.md`.
- **Plan de documentos** (checklist de todo lo que el juego lleva dentro): `docs/PLAN_DOCUMENTOS.md`.
- **Historia del juego** (premisa, estructura, personajes): `docs/historia/`.
- **Mecánicas candidatas** (análisis; no aprobadas): `docs/MECANICAS.md`.
- **Recetas** (añadir escena, texto, JSON o test): `docs/ARQUITECTURA.md`.
- **Checklist de `data/*.json`**: `docs/DATOS.md`.
- **Log de decisiones del dueño** (no reabrir lo cerrado): `docs/DECISIONES.md`.
- **Registro de bugs**: `docs/BUGS.md`.
- **Reglas duras del código** (este documento) vs. instalar y correr: `README.md`.
