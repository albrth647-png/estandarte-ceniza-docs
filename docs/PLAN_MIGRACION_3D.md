# PLAN_MIGRACION_3D — la capa de dibujo del juego (fases 0-6)

**Estado:** ✅ **Plan de construcción (2026-10-02; saneado en greenfield 2026-10-25).**
**No cuenta en los 98 documentos de diseño** (es un plan de trabajo, como `PLAN_DOCUMENTOS.md`).
**El nombre del fichero se conserva por estabilidad de enlaces:** ya no hay «migración» —
el juego nace 3D (1.ª persona) y esta capa **se construye desde cero**.

> **Regla que gobierna este documento:** la **simulación es pura** — `js/systems/*` sin DOM, sin
> `fetch`, sin reloj — y **la UI vive en DOM**. El 3D es **solo la capa de dibujo**.

---

## 1. Piezas previstas (nada existe todavía)

| Pieza | Estado |
|---|---|
| `vendor/three/` (Three.js r186 + GLTFLoader, MIT) | ⬜ **por vendorizar** |
| `js/render/webgl.js` (diagnóstico + reserva a 2D si WebGL2 falla) | ⬜ **por crear** |
| `js/render/modelos3d.js` (carga y aligerado de GLB) | ⬜ **por crear** |
| `art/` (10 modelos GLB de reserva con autor y licencia) | ⬜ **por producir** (fichas en `art/AUTORES.md`, por crear) |
| **Escena única, cámara 1.ª, render por escena** | ⬜ **por construir** (fase 0) |
| **Colisión y exploración en 3D** | ⬜ **por construir** (fase 1) |
| **Campo de batalla en 3D** (unidades, pooling) | ⬜ **por construir** (fase 3) |

Es decir: **no hay motor ni material aún**. Este plan ordena cómo se construyen.

---

## 2. Principios (no se negocian)

1. **La simulación no importa `three`.** `js/systems/*` calcula; `js/scenes/*` dibuja (reglas 2 y
   11 de `../../AGENTS.md`). Ningún test de sistema importa `three`.
2. **UI en DOM, mundo en canvas.** HUD, menús, Registro y avisos son DOM sobre el canvas, con
   targets ≥ 48 px (`../interfaz/00_CONTROLES.md`).
3. **Un renderer por aplicación, una escena por pantalla.** Al cambiar de escena se hace
   `dispose()` de geometrías, materiales y texturas: sin fugas entre pantallas.
4. **Reserva a 2D siempre disponible:** si `webgl.js` no confirma WebGL2, el juego sigue siendo
   jugable (menús + escenas planas). El render 3D es **capa**, no requisito duro.
5. **Presupuesto antes que calidad:** 60 fps en un dispositivo modesto manda sobre más polígonos
   (`../arte/00_ESTILO.md`, `../produccion/08_PLATAFORMAS_Y_MINIMOS.md`).
6. **Offline total:** sin CDN, sin texturas remotas, todo relativo (`vendor/`, `art/`).

---

## 3. Las 6 capas

| Capa | Archivo | Qué hace |
|---|---|---|
| Diagnóstico | `js/render/webgl.js` | detecta WebGL2, shader de reserva, avisos |
| Modelos | `js/render/modelos3d.js` | carga GLB, aligerado (recorte de vértices/normales) |
| **Escena** | **`js/render/escena3d.js` (nuevo)** | `Scene` · `PerspectiveCamera` · `WebGLRenderer` · `Fog` 60 m · `resize` · `dispose()` |
| Terreno/props | desde `js/systems/terreno.js` y `props.js` | posiciones, colisiones y LOD **calculados en sistemas**, consumidos por render |
| Unidades | desde `js/systems/campo.js` | posiciones por tick → objetos de escena (pooling) |
| Audio | `js/render/audio.js` (nuevo, 1.7) | síntesis Web Audio / muestras propias, 3 buses (`../arte/02_AUDIO.md`) |

---

## 4. Fases 0-6 (una por hito jugable, misma cadencia que `01_FASES.md`)

| Fase | Qué se gana | Se cierra con | Hito de `01_FASES.md` |
|---|---|---|---|
| **0 · Base** | `escena3d.js`: escena, cámara, renderer, `pixelRatio ≤ 2`, `resize`, `dispose()`, cueva de diagnóstico | humo + 10 min sin errores | previo a **1.1** |
| **1 · Exploración 1.ª persona** | movimiento, colisión (de `terreno.js`/`props.js`), **niebla 60 m**, fachadas de sitio | costuras `colisiona()`/`enfocable()` | **1.1** |
| **2 · Sitios** | 6 fachadas + 5 interiores + panel de puerta (casa alquilada) | recorrer los 6 sin atascos | **1.3** |
| **3 · Campo de batalla** | unidades 3D con **pooling**, LOD de tropa, animaciones, daño flotante, partículas | 5-6 por bando a 60 fps | **1.4** |
| **4 · Presentación** | iluminación, sombras suaves, niebla por zona, efectos con topes (`../arte/04_EFECTOS_Y_PARTICULAS.md`) | **I6** (presupuesto de impresión) | **1.7** |
| **5 · Rendimiento y peso** | fusión de geometrías estáticas, atlas, LOD por distancia, atlas de sombras | 60 fps medidos + assets ≤ ~90 MB | **1.7** |
| **6 · Publicación** | build de APK con `vendor/` y `art/` empaquetados, WebGL2 mínimo, fallback | `npm run qa` + `10_BUILD_Y_FIRMA_APK.md` | **1.8** |

---

## 5. Técnicas obligatorias (de la referencia de Three.js)

- **Cámara:** una `PerspectiveCamera` por pantalla; `aspect` + `updateProjectionMatrix()` en cada
  `resize`.
- **Niebla:** `Fog` lineal a **60 m** (paleta y lectura de `../arte/00_ESTILO.md`).
- **Pixel ratio:** `Math.min(window.devicePixelRatio, 2)` — doble resolución no dobla la calidad.
- **Fusión:** `mergeGeometries` para props y fachadas estáticas (menos draw calls).
- **LOD:** `THREE.LOD` para tropas lejanas y props de fondo.
- **Pooling:** las unidades del campo se **reusan**, nunca se crean/destruyen por batalla.
- **Frappeo:** frustum culling activo y bounding boxes correctas.
- **Limpieza:** `dispose()` de geometrías, materiales, texturas y renderer al cambiar de escena.
- **Clock propio:** `delta` por frame para animaciones; **la simulación sigue recibiendo `dt`
  inyectado** (determinismo, regla 9).

---

## 6. Riesgos WebGL y abstracción (lo que cita `ANALISIS_COBERTURA`)

| Riesgo | Detección temprana | Plan B |
|---|---|---|
| Pérdida de contexto WebGL (`webglcontextlost`) | aviso en `webgl.js` | restaurar escena desde el estado puro; si falla, modo 2D |
| Renderizador alternativo / shaders incompatibles | fase 0 en dispositivo modesto | material `MeshBasicMaterial` de reserva (sin luces) |
| Precisión GLSL en GPUs antiguas | humo en 2 tamaños + dispositivo real | evitar efectos con `float` fraccionario fino; versionar `vendor/` |
| Rendimiento < 60 fps | **medición obligatoria** en fase 5 | LOD + fusión + menos partículas **antes** que quitar unidades |
| Fuga de memoria al cambiar de pantalla | 10 min sin errores (gate de todos los pasos) | `dispose()` centralizado en `escena3d.js` |
| WebGL2 no disponible | `webgl.js` | **reserva 2D**: el juego sigue siendo jugable |

**Abstracción:** todo lo que dibuja pasa por `escena3d.js`; las escenas **nunca** crean un
`WebGLRenderer` propio. Así el render es una capa sustituible (adaptador de plataforma) y la
entrada (`interfaz/00_CONTROLES.md`) no depende de ella.

---

## 7. Fuera de este documento

- Qué dibuja cada pantalla y su HUD → `../batalla/04_PRESENTACION.md`, `../interfaz/02_HUD.md`
- Estilo, paleta, LOD y niebla → `../arte/00_ESTILO.md`
- Presupuesto de peso y pipeline de assets → `../arte/01_ASSETS.md`
- Mínimos y rendimiento → `../produccion/08_PLATAFORMAS_Y_MINIMOS.md`
- Orden de construcción de la demo → `produccion/01_FASES.md` (§2.5)
- Reglas duras del código → `../../AGENTS.md`
