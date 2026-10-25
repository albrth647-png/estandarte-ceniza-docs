# Arquitectura — cómo se construirá algo aquí

> `../AGENTS.md` da las **reglas duras**; este documento da las **recetas**. No se duplica
> nada: si algo choca, manda `../AGENTS.md`.
> **Estado greenfield:** esto es el **plan de construcción** del build (Fase 1). Ningún
> módulo citado existe todavía; las rutas son la estructura prevista.

## Boot (una sola vía, por diseñar)

```
index.html → js/main.js
  1. OptionsStore        valcoria_opts (core/options.js): idioma, escala, calidad, daltonismo
  2. loadStrings()       data/strings_*.json validados (fallo = aviso en #boot-status, nunca excepción)
  3. initI18n(es|en)     claves txt_*  (core/i18n.js)
  4. saveSystem          valcoria_save + slots (core/save.js)
  5. registro de escenas core/scene_manager.js
  6. GameLoop            core/game_loop.js → update(dt) + render() de la escena activa
```

Los datos de juego (personajes, mundo, memoria) entran por `loadStrings()` y sus cargas
propias **con su validador** cuando su diseño esté aprobado (checklist en `DATOS.md`).

## Contrato de escena

```js
/** @type {Scene} */
const scene = {
  enter()  {},           // montar estado y DOM (opcional)
  exit()   {},           // soltar TODO lo que creaste (opcional)
  update(dt) {},         // ms; la simulación nunca usa relojes propios (opcional)
  render() {},           // pintar (canvas o DOM)
};
```

- Las escenas devolverán `Scene`; en tests se llamará `scene.enter?.()`, `exit?.()`,
  `update?.(n)`.
- `js/systems/*` serán **puros**: recibirán dependencias (RNG, dt), ni DOM, ni `fetch`, ni
  reloj.
- `js/scenes/*` dibujarán y manejarán HUD; **no** simularán.

## Receta A — añadir una escena

1. `js/scenes/sc_<nombre>.js` con `createScene(deps)` que devuelva el objeto `Scene`.
2. Registrarla en `js/main.js` (registro de escenas) y decidir su acceso (menú, transición).
3. Textos: claves `txt_<pantalla>_*` en **ambos** strings (receta B).
4. Test espejo `tests/scene_<nombre>.test.js` con `setupDom()` + `realData()` de
   `tests/helpers/dom.js`.
5. `npm run qa` verde (cuando exista el build).

## Receta B — añadir una clave de texto

1. `data/strings_es.json` **y** `data/strings_en.json` con la misma clave `txt_...`.
2. Uso en código: `t("txt_...")` — **nunca** texto literal visible.
3. `tests/strings.test.js` verificará paridad y que toda clave usada existe.

## Receta C — añadir un `data/*.json`

1. Esquema en `js/data/schemas.js`: `validate<Nombre>(data, ...)` con mensajes acumulados.
2. Entrada en `tools/validate_data.js` y en la carga (`js/data/loader.js`).
3. Typedefs **solo** en `js/data/game_types.js` (import con `import("./game_types.js").X`).
4. Si los tests lo usan, añadirlo a `tests/helpers/dom.js` (`realData`).
5. `docs/DATOS.md`: moverlo de «pendientes» a «creados» con su validador.
6. Rutas **relativas** (`data/x.json`, nunca `/data/...`).

## Receta D — añadir un test

1. `tests/<modulo>.test.js`, mínimo 3 casos: **normal, borde, error**.
2. `node:test` + `assert/strict`; DOM falso con `setupDom()`.
3. `npm run test:cov` exigirá **>=90 %** sobre `js/**`; usa el `debug` de la escena para
   llegar a los caminos raros.

## Receta E — tocar diseño

1. **Primero el doc**, después el código, después los tests (`../AGENTS.md`, Orden).
2. Si código y doc discrepan: se alinea **uno** de los dos y se anota en `docs/DECISIONES.md`.
3. Toda cifra nueva es **decisión del dueño**: no se inventa ni se copia de otros juegos.

## Render (previsto)

- `js/render/webgl.js` — `soportaWebGL2()` / `diagnosticoWebGL()`: si no hay WebGL2, el
  juego seguirá en 2D (reserva) y el motivo quedará registrado.
- `js/render/modelos3d.js` — catálogo unidad → `.glb`, clips por acción, `aligerar()`
  (funde mallas por esqueleto+material) y `cargarModelos()`. La carga será asíncrona
  (import dinámico).
- `vendor/three/` — Three.js (r186 planeado) + GLTFLoader vendorizados (MIT).
  **Rutas relativas siempre. Se vendorizará, sin CDN.**

## Puertas de `npm run qa` (por construir en el paso 1.1)

`check (tsc estricto) → tamano (500 líneas + peso) → lint (eslint) → validate (JSON) →
docs (enlaces markdown) → test:cov (>=90 %) → smoke (Chromium headless) → vivo (recorrido
real con 0 errores de consola)`.
