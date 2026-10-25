# VALCORIA — Prueba de Juego 01 · «Vega Quemada»

**Rebanada jugable real** del proyecto *Estandarte de Ceniza*: batalla en primera
persona contra saqueadores y el Capitán Ceniza, construida para que el dueño
vea (y juegue) cómo se verá el juego — estilo del prototipo anterior, pero con
3D en tiempo real, luces de tarde, niebla, ceniza viva y sonido procedural.

## Cómo jugar (sin instalar nada)

1. Descarga `VALCORIA_prueba_juego_01.html` (un solo archivo, ~900 KB).
2. Haz doble clic: se abre en tu navegador. **Funciona sin conexión.**
3. Controles: `WASD` moverse · **clic izquierdo** golpear · **clic derecho
   (mantener)** bloquear · `Esc` pausa. En móvil: desliza + botones.

Si el repo tiene GitHub Pages activado, también está en:
`https://albrth647-png.github.io/estandarte-ceniza-docs/demo/`

## Qué canon encarna (verificado numéricamente en navegador)

| Regla (Fase B) | Valor | Verificado |
|---|---|---|
| Aliento | 100 · regen 4/s combate, 8/s demo fuera · bloqueando no respiras | ✓ |
| Bloqueo | golpe entra al **40 %** y cuesta **10 de aliento** | ✓ (13 → 5,09; aliento −10) |
| Guardia rota | sin aliento: golpe completo + **1 s de tambaleo** | ✓ (13 → 12,79; 1,0 s) |
| Daño | var ±10 % · crítico 5 % ×1,5 | ✓ |
| Capitán con memoria | finge el golpe para vaciarte el aliento | ✓ (oleada 3) |

Fuentes: `docs/ingenieria_inversa/fase_B_tabla_decisiones.md` (filas 4 y 11) ·
`docs/batalla/01_CIFRAS.md` §3 · estilo: `docs/arte/00_ESTILO.md`.

## Tecnología (todo nuevo, nada copiado del prototipo)

- **Three.js r186 + WebGL** (motor propio en `src/game/` del proyecto web:
  mundo, enemigos con IA, FX, audio 100 % sintetizado con WebAudio).
- Empaquetado a **un único HTML autónomo** (sin servidor, sin CDN, sin build
  en el navegador): React + Three.js + motor + CSS Tailwind, todo inline.
- Reconstrucción: `scripts/valcoria_demo/build.sh` en el workspace.
