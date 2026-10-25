# 04 · Accesibilidad — que juegue quien quiera

**Estado:** ✅ **aprobado por el dueño (aprobación en bloque, 2026-09-30). Documento final.**

> Un juego de deudas no debe tener una puerta de entrada difícil. Estas opciones existen **desde
> la demo** y no cambian lo que el juego simula, solo **cómo se ve y se toca**.

---

## 1. Texto y contraste

- **Tamaño de texto:** 3 niveles (Normal · Grande · Muy grande), aplicado a **todo** el DOM.
- **Contraste:** paleta con contraste ≥ **4,5:1** para texto sobre fondo; el HUD no usa texto
  fino sobre lienzo claro.
- **Sin texto esencial en el canvas:** todo lo legible es **DOM** (`02_HUD.md` §1), para que el
  tamaño y el contraste del sistema funcionen.

---

## 2. Daltonismo

- **4 modos:** ninguno · protanopia · deuteranopia · tritanopia.
- La información **nunca depende solo del color** (aliado/enemigo/deudor se distinguen también
  por **forma y silueta** — `../arte/00_ESTILO.md`).

---

## 3. Manos y controles

- **Modo un pulgar:** palanca centrada abajo; todo lo esencial al alcance (`00_CONTROLES.md` §5).
- **Lado de la palanca:** izquierda/derecha (diestro/zurdo).
- **Sin mantener pulsado obligatorio:** el modo «sin manos duras» convierte los toques largos
  en **dos toques**.
- **Vibración** opcional y apagada por defecto donde exista.

---

## 4. Sin mareos

- **Sacudida de cámara:** apagable (≤ 6 px → 0; `../batalla/04_PRESENTACION.md` §4).
- **Balanceo (head bob):** apagable (`../mundo/01_EXPLORACION.md` §8).
- **Velocidad de giro:** 5 niveles; **invertir eje vertical**.
- **FOV:** reducido a 60° en pantallas estrechas (ya previsto); no se baja más para no marear.
- **Velocidad de caminar:** reducible a **2,0 m/s**.

---

## 5. Lectura y audición

- **Velocidad de texto:** 25 / 45 / 90 cps (valores de diseño; por implementar).
- **Saltar escena:** mantener 1 s **aplicando sus efectos**; nunca se pierde información.
- **Subtítulos:** activables; **apagarlos = saltar la narración aplicando efectos**.
- **Avisos también sonoros** (no solo visuales) para no depender de mirar el borde.

---

## 6. Sin barreras impuestas por el sistema

- **Ninguna opción de accesibilidad desactiva logros ni contenido.**
- **Ninguna requiere red** (el juego es offline, `../produccion/09_PRIVACIDAD_Y_DATOS.md`).
- **Ningún aviso parpadea** a más de 3 Hz (riesgo fotosensible).

---

## 7. Datos, tipos y validación

- Las opciones vivirán en el sistema de opciones (`js/core/options.js`, por construir), **fuera
  del guardado de partida** (`../DECISIONES.md`, 2026-09-26).
- **Tipos:** `OpcionesAccesibilidad` en `js/data/game_types.js`.
- **Validación:** las opciones se persisten con valores por defecto seguros; un valor corrupto cae
  al default, nunca rompe el arranque.
- **Tests (por escribir):** `tests/opciones.test.js` (existente) + `tests/accesibilidad.test.js`.

---

## 8. Cifras que fija este documento

| Cifra | Valor |
|---|---|
| Tamaños de texto | 3 (Normal · Grande · Muy grande) |
| Contraste mínimo | 4,5:1 |
| Modos de daltonismo | 4 |
| Velocidad de texto | 25 / 45 / 90 cps |
| Sacudida y balanceo | apagables |
| Parpadeo | ≤ 3 Hz |
| Velocidad de caminar mínima | 2,0 m/s |

---

## 9. Qué entra en la demo (Fase 1) — y qué sigue

> **Hasta aquí la demo.** **Todas** las opciones de este documento, activas desde el primer
> arranque; sin vibración si el dispositivo no la tiene.

> **Y sigue el juego completo.** Las pantallas nuevas (Libro Mayor, minimapa, asamblea) **heredan**
> estas opciones sin añadir nada: la accesibilidad es de la casa, no de cada pantalla.

---

## 10. Fuera de este documento

- Controles y gestos → `00_CONTROLES.md`
- Qué se ve → `02_HUD.md`
- Sacudidas y efectos → `../batalla/04_PRESENTACION.md`, `../arte/04_EFECTOS_Y_PARTICULAS.md`
- Textos y tono → `03_I18N_Y_TONO.md`
