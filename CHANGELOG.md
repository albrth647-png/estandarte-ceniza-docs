# Changelog

Resumen por entregas (para el **rollback** en pre-publicacion).
Formato: cambios agrupados por fase/version; la linea `Unreleased` es lo que hay en `master`.

## [Unreleased] — Juego nuevo: Valcoria — Deuda de Sangre

### Limpieza completa del primer juego (2026-09-30)

- **Nuevo proyecto de diseño:** `docs/VALCORIA_DEUDA_DE_SANGRE.md` (pilares, bucle, controles,
  memoria, mercado, decisiones cerradas). La copia de portada `VALCORIA.md` se retiro en el
  2026-10-03: era el mismo log de decisiones en dos sitios y ya vivia todo ahi (§9).
- **Se elimina por completo el juego anterior** (mapa por casillas + batalla táctica):
  16 ficheros de `js/` (8.448 líneas), 29 tests (7.914 líneas), los datos `world/units/terrain/
  maps/formations/events/companions` y toda la documentación de `docs/demo/` y de los planes
  de fase. **Todo queda en el historial de git (commit `6fcddb7`).**
- **Se conserva el armazón:** `core/` (bucle, escenas, entrada, RNG, guardado versionado,
  i18n, opciones, pantalla), escenas de menú, `dialogue.js`, `render/webgl.js` y
  `render/modelos3d.js`, `vendor/three/` y `art/` (ahora sí versionados).
- **Documentación rehecha:** `README.md`, `AGENTS.md` (fuera la regla del «motor intacto»),
  `docs/README.md`, `docs/ARQUITECTURA.md`, `docs/DATOS.md`, `THIRD_PARTY.md` y ficha nueva
  `art/AUTORES.md` (10 modelos GLB con autor y licencia).
- **`npm run qa` en verde tras la limpieza:** tsc + eslint limpios, 198 tests, cobertura
  93,77 %, `validate` con 426 claves ES/EN, 0 enlaces rotos y `SMOKE OK` en 2 ventanas.

## [Unreleased] — Fase 3 (en curso)

### Mazmorras y cierre de Fase 3 — hito A6/A7 (2026-09-30)

- **Mazmorras jugables (A6):** `js/scenes/sc_mazmorra.js` (pantalla de la cadena de 3
  batallas, PV conservados entre batallas, retirada sin premio parcial, jefe al final y
  pantalla de premio) + cableado completo en `js/main.js` (`onMazmorra` del mapa,
  `origen: "mazmorra"` en la batalla y retorno con `resumen`). Antes el boton **Entrar** de
  la plaza no hacia nada. El botin lo escribe `onRecompensa` sobre el guardado activo
  (autosave tras cada batalla; el mapa ya autoguarda al salir).
- **Datos:** `world.json` declara la cadena (`mazmorra.batallas[]`, 6 batallas `b_maz_*` en
  `llanura_del_este`) y `schemas.js` valida ids, niveles crecientes y jefe en la ultima
  batalla (`validate_data` → 15 batallas). Textos `txt_maz_*` completos (422 claves ES/EN).
- **Tests (+25):** `tests/scene_mazmorra.test.js` (8) y `tests/mazmorra_e2e.test.js` (4,
  mapa → mazmorra → 3 batallas → premio con las escenas reales); ampliados
  `tests/mazmorras.test.js`, `tests/resultado.test.js` (`ResumenBatalla.ejercito`) y
  `tests/scene_battle.test.js` (fraccion de PV).
- **Estado de A7:** `npm run qa` verde (681 tests, 95,96 % stmts / 90,53 % ramas, smoke a
  2 resoluciones) y los 7 tests obligatorios en verde. El test de «100 semanas pasivas» se
  reasigna a la **Fase 5** (necesita la economia semanal): documentado en `08_QA.md` y
  `PLAN_FASE3_8_HITOS.md` §6. Queda el barrido de 10 min en el movil del dueno.

### Anadido (2026-09-28)

- **Documentacion nueva:** `README.md` (raiz), `docs/README.md` (indice), `docs/DATOS.md`,
  `docs/BUGS.md`, `docs/DECISIONES.md`, `docs/ARQUITECTURA.md`, `docs/PLAN_MIGRACION_3D.md`,
  `docs/demo/diseno/{FACCIONES,RECURSOS,MISIONES,FLUJOS,TUTORIAL,PANTALLA_FINAL}.md`.
- **Documentacion de sistemas nuevos (2026-09-28, 🟡 diseno cerrado):** `diseno/CRUDAN.md`
  (culdán: reaparición +1 nivel), `diseno/MOTIVACION_MOVIMIENTO.md` (rondas circulares),
  `diseno/RAZAS.md` (raza neutral, 4 tropas), `diseno/HEROES_DECISION.md` (IA de héroes),
  `diseno/ANIMACION_NIVEL.md` (nivel de personaje), `diseno/CAMARA.md` (zoom ×2 + 3D inclinada),
  `diseno/MAZMORRAS.md` (5 mazmorras, 2 en demo) + guia `diseno/ORIENTACION_NUEVO_DISENO.md`.
- **Ampliados:** `ITEMS_EQUIPO.md` (rarezas + 19 items + 6 artefactos), `00_ALCANCE.md`
  (20 misiones), `01_PORTADA_MENU.md` (esquema completo SaveState v2), `TEXTOS.md` (`txt_mis_*`, `txt_rareza_*`).
- **Herramienta:** `tools/check_docs.mjs` (enlaces markdown) enganchado a `npm run qa`.
- **Balance:** honor base **18 → 10** con noble **+10** (codigo, tests y docs sincronizados).

### Batalla 2D — hito A1 (2026-09-28)

- **Motor (`js/systems/battle.js`):** 4 ordenes globales (`setOrder` + `mayChase` + ventana de
  carga `CHARGE`), habilidades 2–4 (`castShout`/`castFirebolt`/`castSignal`, mapa `SKILLS`,
  `skillCdMs` por habilidad como objeto), estandarte por bando (aura 120 px +10% ataque,
  regen de moral, caída −25, captura a 3 s, reposicion con CD 8 s, `auraMul`), cadena de
  huida −10 a 6.25 tiles con antidoto de grito/estandarte, mana regen 4/s.
- **HUD (`js/scenes/sc_battle.js`):** barra final con info del escuadron, 4 botones de orden,
  4 habilidades + Estandarte + Cancelar (coste/CD/mana siempre visibles, modo apuntado con
  area dibujada), fila superior con pausa, velocidad 1×/1.5×/2× y retirada; panel de
  resultado VICTORIA/DERROTA. Todo por `t(clave)` (27 claves nuevas ES/EN: `txt_bat_*`,
  `txt_ord_*`, `txt_hab_*`, `txt_res_*` → 305 totales).
- **Tests (+41):** `battle_ordenes`, `battle_habilidades`, `battle_estandarte`,
  `scene_battle_hud`; escena de batalla ahora inicializa i18n en tests.
- **Docs:** `HABILIDADES.md` (estados ✅, mana 4/s), `04_BATALLA.md` §4, `TEXTOS.md` y
  `DATOS.md` (305 claves), `PLAN_FASES_DEMO.md` (casillas A1), `DECISIONES.md`.

## [0.1.0] — Fase 1 (2026-09-26)

- Portada animada, menu completo, creacion de personaje, opciones.
- Guardado v2 con `migrateSave`, slots manuales, export/import `.json`.
- i18n minima `t(clave)` ES/EN con paridad validada.

## Fases intermedias (ver `docs/PLAN_FASES_DEMO.md`)

- **Fase 2 (2026-09-27):** mapa global 48×32, 17 plazas, A*, reloj, encuentros → pantalla previa.
- **Fase 4 (2026-09-27):** 7 escenas del Acto I, dialogos con maquina de escribir, 6 companeros,
  8 eventos fijos + 3 semanales, decisiones con efecto.

## Como se usa este archivo

1. Antes de una fase grande: linea nueva en `Unreleased`.
2. Al cerrar la fase con QA verde: mover a `[0.x.y] — Fase N (fecha)`.
3. Si algo se rompe en produccion: volver al ultimo tag que tenga `npm run qa` verde.
