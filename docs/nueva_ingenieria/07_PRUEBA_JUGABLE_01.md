# 07 · Prueba jugable 01 — «Vega Quemada» (el pedazo del juego)

**Estado:** ✅ construida y verificada en navegador (2026-10-26). Demo jugable, no documentación.
**Tipo:** vertical slice de combate en 1.ª persona · Three.js (WebGL) sobre Next.js 16 · todo el código es nuevo (regla greenfield).

> Esta prueba existe para responder una sola pregunta del dueño: **«¿cómo se va a VER el juego?»** —
> estilo Blade of Conquest pero mucho mejor, con más gráfico y más tecnología. No es un mockup:
> es un pedazo del juego real donde se entra, se pelea, se muere y se gana.

## 1. Qué contiene

| Sistema | En la prueba | Fuente del canon |
|---|---|---|
| **Aliento** | 100 máx · regenera 4/s en combate, 8/s fuera · con la guardia alzada no respiras | `../batalla/01_CIFRAS.md` §3 |
| **Bloqueo** | el golpe bloqueado entra al **40 %** (mitiga 60 %) y cuesta **10 de aliento** | Fase B fila 11 (cerrada, decisión delegada) |
| **Guardia rota** | sin aliento → golpe completo + **1 s de tambaleo** (pantalla, controles y espada caen) | Fase B fila 11 |
| **Daño** | var ±10 % · crítico 5 % ×1,5 · números de daño flotantes | `../batalla/01_CIFRAS.md` |
| **Capitanes con memoria** | el Capitán Ceniza registra si abusas del bloqueo (ratio > 0,38) y **finge ataques** para vaciarte el aliento; la Crónica lo anuncia | visión Valcoria (memoria de los capitanes) |
| **Construcción** | las **2 torres de la demo** están en pie y el **hueco de la 3.ª** está marcado con mojoneras; acercarse lo cuenta la Crónica | Fase B fila 4 (torres puras en demo) |
| **Crónica** | panel vivo abajo-izquierda: caídas, bloqueos, guardia rota, oleadas, el capitán que finge | `../sistemas/05_CRONICA.md` (espíritu) |
| **Oleadas** | 3: saqueadores → más saqueadores → **Capitán Ceniza** + escolta | demo |

## 2. La escena: Vega Quemada (sitio real de la demo)

Construida según `../arte/00_ESTILO.md` (aprobado por el dueño):
- **Luz oblicua de tarde** + **niebla que corta a 60 m** — la niebla es información, no adorno.
- **Paleta mundo:** ceniza / óxido / piedra / hierro; **acentos escasos:** oro (estandarte y heráldica), sangre (vida), ámbar (fuego y ojos de los enemigos).
- **Fotograma de película:** tone mapping ACES, sombras suaves de tarde, ceniza cayendo siempre, humo y brasas en las fogatas, siluetas tragadas por la niebla.
- **El Estandarte** ondea con tela animada y heráldica propia: la espada rota en oro sobre hierro.
- **Sonido 100 % generado por código** (WebAudio, sin archivos): viento, dron, silbar del acero, golpe sordo, clang de bloqueo, boom de guardia rota, cuerno de oleada.

## 3. Verificación (QA en navegador, 2026-10-26)

- **Canon verificado numéricamente** vía gancho de depuración:
  - Bloqueo: golpe de 13 → entra **4,9** (40 % con var) y aliento 100 → 90 (−10). ✔
  - Guardia rota con aliento insuficiente: golpe completo (**12,8 ≈ 13**) + `tambaleo = 1,0 s`. ✔
- **Flujo completo jugable:** menú → oleadas → enemigos que rodean y telegrafían → muerte con estadísticas (bajas / bloqueos / guardias rotas / tiempo) → reinicio limpio. ✔
- 0 errores de consola; ESLint y TypeScript limpios.

## 4. Cómo se ejecuta

Proyecto Next.js (puerto 3000, `bun run dev`). La prueba es la ruta `/`, corre entera en el
navegador (cliente), sin base de datos ni servicios. Controles: **WASD** moverse · **clic** golpear ·
**clic derecho (mantener)** bloquear · **Esc** pausa. En táctil: deslizar para moverse/mirar y
botones GOLPEAR / BLOQUEAR.

## 5. Lo que esta prueba decide de cara a la Fase D

1. **La dirección «mucho más bonito» funciona** con las reglas del doc de estilo: tarde + niebla + paleta ceniza + acentos escasos = fotograma de película con low-poly ligero.
2. **El bloqueo del 40 % se siente** — el coste de aliento crea la decisión táctica que quería la visión; la guardia rota castiga el spam sin matar la defensa.
3. **El capitán que finge** es barato de construir (una rama en la IA de windup) y vale oro en sensación de «memoria». Se queda.
4. **Siguiente ronda sugerida:** mapa del mundo con paralaje y día-noche (escena 1 del mockup) con esta misma paleta y luz.
