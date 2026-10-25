# Arquitectura — como se construye algo aqui

> `../AGENTS.md` da las **reglas duras**; este documento da las **recetas**. No se duplica nada:
> si algo choca, manda `../AGENTS.md`.

## Boot (una sola via)

```
index.html → js/main.js
  1. OptionsStore        eb_opts (core/options.js): idioma, escala, calidad, daltonismo
  2. loadStrings()       data/strings_*.json validados (fallo = aviso en #boot-status, nunca excepcion)
  3. initI18n(es|en)     claves txt_*  (core/i18n.js)
  4. saveSystem          eb_save + slots (core/save.js)
  5. registro de escenas core/scene_manager.js
  6. GameLoop            core/game_loop.js → update(dt) + render() de la escena activa
```

Los datos de juego (personajes, mundo, memoria) **aun no se cargan**: entran por `loadStrings()`
con su validador cuando su diseno este aprobado.

## Contrato de escena

```js
/** @type {Scene} */
const scene = {
  enter()  {},           // montar estado y DOM (opcional)
  exit()   {},           // soltar TODO lo que creaste (opcional)
  update(dt) {},         // ms; la simulacion nunca usa relojes propios (opcional)
  render() {},           // pintar (canvas o DOM)
};
```

- Las escenas devuelven `Scene`; en tests se llaman `scene.enter?.()`, `exit?.()`, `update?.(n)`.
- `js/systems/*` son **puros**: reciben dependencias (RNG, dt), ni DOM, ni fetch, ni reloj.
- `js/scenes/*` dibujan y manejan HUD; **no** simulan.

## Receta A — anadir una escena

1. `js/scenes/sc_<nombre>.js` con `createScene(deps)` que devuelva el objeto `Scene`.
2. Registrarla en `js/main.js` (registro de escenas) y decidir su acceso (menu, transicion).
3. Textos: claves `txt_<pantalla>_*` en **ambos** strings (receta B).
4. Test espejo `tests/scene_<nombre>.test.js` con `setupDom()` + `realData()` de
   `tests/helpers/dom.js`.
5. `npm run qa` verde.

## Receta B — anadir una clave de texto

1. `data/strings_es.json` **y** `data/strings_en.json` con la misma clave `txt_...`.
2. Uso en codigo: `t("txt_...")` — **nunca** texto literal visible.
3. `tests/strings.test.js` verifica paridad y que toda clave usada existe.

## Receta C — anadir un `data/*.json`

1. Esquema en `js/data/schemas.js`: `validate<Nombre>(data, ...)` con mensajes acumulados.
2. Entrada en `tools/validate_data.js` y en la carga (`js/data/loader.js`).
3. Typedefs **solo** en `js/data/game_types.js` (import con `import("./game_types.js").X`).
4. Si los tests lo usan, anadirlo a `tests/helpers/dom.js` (`realData`).
5. `docs/DATOS.md`: moverlo de "pendientes" a "existentes" con su validador.
6. Rutas **relativas** (`data/x.json`, nunca `/data/...`).

## Receta D — anadir un test

1. `tests/<modulo>.test.js`, minimo 3 casos: **normal, borde, error**.
2. `node:test` + `assert/strict`; DOM falso con `setupDom()`.
3. `npm run test:cov` exige **>=90%** sobre `js/**`; usa el `debug` de la escena para llegar a
   los caminos raros.

## Receta E — tocar diseno

1. **Primero el doc**, despues el codigo, despues los tests (`../AGENTS.md`, Orden).
2. Si codigo y doc discrepan: se alinea **uno** de los dos y se anota en `docs/DECISIONES.md`.
3. Toda cifra nueva es **decision del dueño**: no se inventa ni se copia de otros juegos.

## Render

- `js/render/webgl.js` — `soportaWebGL2()` / `diagnosticoWebGL()`: si no hay WebGL2, el juego
  sigue en 2D y el motivo queda registrado.
- `js/render/modelos3d.js` — catalogo unidad → `.glb`, clips por accion, `aligerar()` (funde
  mallas por esqueleto+material) y `cargarModelos()`. La carga es asincrona (import dinamico).
- `vendor/three/` — Three.js r186 + GLTFLoader vendorizados (MIT). **Rutas relativas siempre.**

## Puertas de `npm run qa`

`check (tsc estricto) → lint (eslint 10) → validate (JSON) → docs (enlaces markdown) →
test:cov (>=90%) → smoke (Chromium headless)`.
