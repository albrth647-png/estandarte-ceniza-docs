# Valcoria — Deuda de Sangre · Guía para Agentes AI (OpenCode)

Juego web medieval single-player, **1.ª persona**, 100 % offline y estático.
**Stack:** JavaScript ES2022 + JSDoc (sin transpilador) · Three.js/WebGL2 con reserva a 2D ·
JSON de datos · `localStorage` · Node ≥ 18 solo para tooling/tests.

```bash
# QA (DEBE pasar entero antes de dar una tarea por hecha)
npm run qa              # = check + tamano + lint + validate + docs + test:cov + smoke + vivo
npm run check           # tsc estricto sobre js/, tools/, tests/
npm run tamano          # 500 lineas/archivo (+ aviso a 450) y peso maximo en data/ y css/
npm run validate        # node tools/validate_data.js (JSON jugables)
npm run docs            # node tools/check_docs.mjs (enlaces markdown)
npm run test            # node --test "tests/*.test.js"
npm run smoke           # Chromium headless + index.html?smoke=1 (requiere chromium)
npm run vivo            # Chromium + CDP: portada -> menu -> creacion -> exploracion
                        # (caminar, mirar, enfocar, umbral, guardar) -> recarga y
                        # continuar -> opciones/idioma; mide fps y 0 errores de consola
npm run serve           # servidor estatico local puerto 8123
# El QA ya incluye `vivo`, asi que el 0 errores de consola del recorrido es automatico.
# Para el cierre de cada fase se navega ADEMAS con el MCP de navegador del entorno
# (cdp-browser-mcp-server, docs/produccion/04_QA.md §4b) sobre `npm run serve`.
```

## Estado

🟡 **Fase 1 en marcha.** El juego es **«Valcoria — Deuda de Sangre»** (nombre cerrado; el antiguo
«Estandarte de Ceniza» era otro juego). Hoy hay **pantalla jugable de principio a fin**:
portada → menú → creación → **exploración en 1.ª persona** (caminar, mirar, enfocar, cruzar
umbrales, firmar, guardar y recargar) con armazón completo (guardado versionado v3, i18n ES/EN,
túnel 3D, avisos, audio). Mundo, combate y memoria completa siguen por construir.

- Qué se está construyendo y en qué orden: `docs/produccion/PLAN_FASE1.md` (el plan manda) y
  `docs/produccion/01_FASES.md` (reglas del método). El hito 1.2 está cerrado.
- La idea aprobada: `docs/VALCORIA_DEUDA_DE_SANGRE.md`. Lo cerrado, no se reabre:
  `docs/DECISIONES.md`.
- El código del juego de casillas y batalla táctica **se eliminó por completo** (commit
  `6fcddb7`). **No lo resucites**: si algo de ese diseño vuelve, será por decisión del dueño
  documentada en `docs/DECISIONES.md`.

## Estructura (capacidades, no rutas)

Este bloque describe **qué vive dónde**, no el inventario de ficheros: el árbol se queda obsoleto
y un doc obsoleto envenena el contexto de cada tarea. Para ver ficheros, `ls js/* data css`.

| Carpeta | Capacidad |
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

## Reglas duras (no romper)

1. **`js/**` solo globals de navegador.** Si aparece `process`, `require` o `__dirname` en `js/`,
   ESLint falla y la APK se romperia. Node solo en `tools/` y `tests/`.
2. **Sistemas puros.** `js/systems/*` no tocan DOM, ni `fetch`, ni reloj. Reciben dependencias
   (RNG, dt). Las escenas dibujan; los sistemas simulan. Esto permite testear sin navegador.
3. **Rutas de datos relativas.** Siempre `data/*.json`, nunca `/data/...` (regla APK/Capacitor).
   Lo mismo con `vendor/` y `art/`.
4. **Tipos una sola vez.** Typedefs en `js/data/game_types.js`, se importan con
   `import("./game_types.js").X`. `tsc` en estricto: sin `any` implicito, sin vars sin usar.
5. **Datos validados o no arranca.** Todo JSON nuevo entra con su validador en
   `js/data/schemas.js` + chequeo en `tools/validate_data.js`. `loadStrings()` lanza con
   todos los errores juntos.
6. **Guardado versionado.** `save.js`: `SAVE_VERSION`, `migrateSave()`, corrupto → backup
   `eb_save.corrupt`, nunca arrancar con datos rotos. Todo lo nuevo que entre al guardado es
   **aditivo** y **acotado** (el `localStorage` del movil ronda 5 MB).
7. **Originalidad.** Cero activos, nombres o textos de juegos de terceros. Arte y audio: solo
   material propio o libre con ficha (ver `THIRD_PARTY.md`).
8. **Offline y sin esperas reales.** Nada de servidores, CDNs ni "vuelve en 24 h": todo el
   gating es en dias de juego acelerables jugando.
9. **Determinismo.** Misma partida = mismo mundo. El tiempo siempre **entra inyectado** por
   parametro; ningun sistema consulta el reloj del sistema.
10. **Paridad ES/EN.** Toda clave `txt_*` nace en **ambos** idiomas en el mismo commit.
11. **Presentacion en escenas.** Efectos visuales y audio viven solo en `js/scenes/*`, nunca en
    `js/systems/*`.
12. **Tope de 500 lineas por archivo.** Ningun archivo de codigo (`js/`, `tools/`, `tests/`,
    `css/`) puede pasar de **500 lineas**: el que se pase **se divide segun su longitud**
    (un archivo = una responsabilidad; si aun no cabe, `x.js` + `x_datos.js`, `x_sistema.js`
   …). Lo verifica `npm run tamano` dentro de `npm run qa`: si falla, el QA esta rojo.
    Ejemplo vivo: el guardado se divide en `js/core/guardado.js` (autoguardado) +
    `js/core/slots.js` (huecos manuales) + `js/core/save.js` (fachada que reexporta).
    **Aviso desde 450 lineas**: `npm run tamano` avisa a partir de 450 aunque no bloquee, para
    dividir *antes* de tocar el tope.

## Más reglas duras

13. **Todo check emitido se afirma.** Un `checks.push(...)`, un `assert` o un estado de humo que
    nadie lee puede mentir en verde. Cada check emitido tiene su `assert` (o su lectura) en un
    test; si no puede verificarse desde fuera, no se emite. Ejemplo vivo: `main_smoke.test.js`
    afirma cada check de `runSmoke()`.
14. **Una decisión, un sitio.** Un valor (un tope, un umbral, un color de marca, una versión)
    vive en **un** módulo y el resto lo importa. Nada de constantes repetidas que se desincronizan
    al cambiar uno.
15. **Targets táctiles verificados, no de palabra.** Todo elemento pulsable de la interfaz mide
    **≥ 48 px** en su lado menor (`docs/produccion/04_QA.md` §I6). Un test lo comprueba **leyendo
    el CSS de verdad**: si el valor cambia o desaparece, el QA se pone rojo.
16. **Ningún paso se enseña sin acabar (I5).** Un paso cierra con su **aviso, su icono y su
    sonido**: si algo sale en pantalla sin icono, sin sonido o sin salir de la escena, está a
    medio hacer. `PLAN_FASE1.md` §1 I5 manda sobre este recordatorio.
17. **Los conflictos de docs se anotan, no se heredan.** Cuando dos documentos se contradigan y
    ambos digan «esto manda», el conflicto se **anota al cerrar la tarea** en el documento
    afectado y, si cambia el diseño, en `docs/DECISIONES.md`. Un doc obsoleto no se corrige en
    silencio.
18. **`npm run tamano` mira código *y* peso.** Además de las 500 lineas, `tools/check_tamano.mjs`
    comprueba el **peso máximo** de cada fichero de `data/` y `css/` (los JSON se descargan al
    móvil y el juego es offline: un fichero enorme rompe el arranque o la carga).

## Convenciones

| Elemento | Regla |
|---|---|
| Estilo | ES2022, `const` primero, `eqeqeq`, sin `var`, JSDoc en toda funcion publica |
| Nombres | `snake_case` archivos/ids de datos, `camelCase` funciones, `PascalCase` clases |
| Datos | ids `snake_case` (`puerto_ceniza`), claves de texto `txt_*`, colores `#rrggbb` |
| Tests | `tests/<modulo>.test.js`, minimo 3 casos (normal, borde, error); `node --test` |
| Tamano | ≤ **500 lineas** por archivo; dividir por longitud si se pasa (`npm run tamano`) |
| DoD tarea | `npm run qa` verde (incluye `vivo`: 0 errores de consola en el recorrido) + guardar/cargar intacto + doc actualizado si cambia diseno |
| DoD fase | lo de arriba + la **prueba manual de 10 min** de `docs/produccion/04_QA.md` §4 + navegacion con MCP |
| Bugs | `ID \| fecha \| pantalla \| pasos \| esperado \| actual \| ALTA/MEDIA/BAJA \| ABIERTO→EN CURSO→ARREGLADO→VERIFICADO` — un ALTA bloquea avanzar; registro en `docs/BUGS.md` |
| Orden | **datos → codigo → tests → documentacion**. Nunca al reves. |

## Mapa de documentos

- **Idea del juego** (pilares, bucle, controles, decisiones cerradas): `docs/VALCORIA_DEUDA_DE_SANGRE.md`.
- **Vision y teoria de longevidad**: `docs/VISION_JUEGO_COMPLETO.md`.
- **Indice (que manda sobre que)**: `docs/README.md`.
- **Plan de documentos** (checklist de todo lo que el juego lleva dentro): `docs/PLAN_DOCUMENTOS.md`.
- **Historia del juego** (premisa, estructura, personajes): `docs/historia/`.
- **Mecanicas candidatas** (analisis; no aprobadas): `docs/MECANICAS.md`.
- **Recetas** (anadir escena, texto, JSON o test): `docs/ARQUITECTURA.md`.
- **Checklist de `data/*.json`**: `docs/DATOS.md`.
- **Log de decisiones del dueño** (no reabrir lo cerrado): `docs/DECISIONES.md`.
- **Registro de bugs**: `docs/BUGS.md`.
- **Reglas duras del codigo** (este documento) vs. instalar y correr: `../README.md`.
