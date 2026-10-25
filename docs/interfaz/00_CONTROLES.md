# 00 · Controles — deslizar para sentir, tocar para responder

**Estado:** ✅ **aprobado por el dueño (aprobación en bloque, 2026-09-30). Documento final.**

> Pilar 1: los controles **táctiles** son el primer pilar del juego. Sin mando, sin teclado.
> Describe el **juego completo**; la demo los usa tal cual.

---

## 1. Filosofía

1. **Deslizar para sentir, tocar para responder.** Lo que se arrastra mueve el mundo (mirar,
   caminar); lo que se toca **decide** (hablar, atacar, dar una orden).
2. **Siempre los mismos sitios:** palanca fija abajo-izquierda, botones fijos abajo-derecha,
   el centro **libre** para mirar y tocar.
3. **Un solo pulgar basta** para jugar cualquier pantalla; los dos pulgares dan precisión.
4. **Nada esconde un menú dentro de un menú**: dos toques como máximo para cualquier acción.

---

## 2. Mapa de controles (horizontal, 960×540 base)

| Zona | Situación | Qué hace |
|---|---|---|
| **Palanca** | Inferior izq. (120×120 px) | Mover (relativa a la mirada). Invisible hasta que el pulgar toca su zona (+20 % opacidad al tocarla) |
| **Zona de mirada** | Todo el centro y la mitad derecha | Arrastrar = girar cámara. Zona **sin dibujar**: no compite con nada |
| **Botón de acción** | Inferior der. (72×72 px) | Contextual: hablar / coger / atacar |
| **Botón secundario** | Encima del anterior (56×56 px) | Acción secundaria: toque largo (400 ms) — agacharse, inspeccionar |
| **Botón de órdenes** | Solo en batalla, franja central inferior | Barra de órdenes de las tropas (`../batalla/04_PRESENTACION.md`) |
| **Botón de correr** | Junto a la palanca (56×56 px) | Mantener = correr; sin él, andar |

- **Objetivos táctiles ≥ 48 px** (regla de `../../AGENTS.md`), y los primarios **≥ 56 px**.
- **Zona muerta de 16 px** entre la palanca y la mirada: un pulgar que se desliza no dispara
  miradas por accidente.
- Nada se pinta a menos de **24 px** del borde (bordes de pantalla táctil).

---

## 3. Gestos

| Gesto | Duración / recorrido | Significado |
|---|---|---|
| **Toque** | < 250 ms, < 12 px | Responder: el botón, el objeto enfocado, la opción |
| **Toque largo** | ≥ 400 ms | Acción secundaria (no destructiva sin confirmación) |
| **Arrastre** | ≥ 12 px | Mirar (en zona de mirada) o mover (en palanca) |
| **Arrastre doble** | dos dedos | Reservado: deslizar páginas del Libro Mayor (Fase 2) |

- Un **toque nunca se interpreta como arrastre** ni al revés (umbrales de `js/core/input.js`).
- **Arrastrar cancela el enfocar** al instante: el jugador siempre manda.

---

## 4. Controles por pantalla

| Pantalla | Controles |
|---|---|
| Exploración | Palanca + mirar + botón de acción + correr |
| Diálogo | Opciones como botones grandes (≥ 56 px); toque largo = ver la frase anterior |
| Batalla | Palanca (sigues siendo una unidad) + botones de combate del héroe + barra de órdenes |
| Post-batalla | Botones grandes, **uno por salida** (nunca un menú anidado) |
| Mapa / Crónica / Libro | Lista con toque; deslizar arriba/abajo para leer |
| Menús y opciones | Botones ≥ 48 px; los deslizadores se al soltar (patrón ya existente) |

---

## 5. Opciones de control (Pantalla Opciones)

| Opción | Valores |
|---|---|
| Sensibilidad del giro | 5 niveles |
| Invertir eje vertical | sí / no |
| Enfocar automáticamente | sí / no |
| Lado de la palanca | izquierda / derecha (modos diestro y zurdo) |
| Modo un pulgar | sí / no (palanca centrada abajo) |
| Vibración táctil | sí / no (donde el dispositivo la tenga) |

---

## 6. Accesibilidad

- Todo objetivo **≥ 48 px** y separado **≥ 8 px** de su vecino.
- Modo un pulgar (§5) y modo «sin manos duras»: reducir la necesidad de mantener pulsado.
- Las acciones destructivas (ejecutar, borrar guardado) exigen **confirmación de dos toques**.

---

## 7. Datos, tipos y validación

- Gestos: `js/core/input.js` (ya existe y está testado) — la escena decide qué hace cada gesto.
- Las reglas de radio y enfocar: `js/systems/exploracion.js` (puro).
- Tests: `tests/input.test.js` (existentes) + `tests/exploracion.test.js`.

---

## 8. Qué entra en la demo (Fase 1)

- Palanca, mirar, acción, correr y toque largo: **todo activo** en el hito 1.1.
- Opciones de control con sus 6 filas.
- Sin vibración si el dispositivo no la tiene (nunca rompe).

---

## 9. Cifras que fija este documento

| Cifra | Valor |
|---|---|
| Objetivo táctil | ≥ 48 px (primarios ≥ 56) |
| Palanca | 120×120 px |
| Zona muerta palanca/mirada | 16 px |
| Toque | < 250 ms y < 12 px |
| Toque largo | ≥ 400 ms |
| Arrastre | ≥ 12 px |
| Separación entre objetivos | ≥ 8 px |

---

## 10. Fuera de este documento

- Cómo se enfoca y se interactúa con el mundo → `../mundo/01_EXPLORACION.md`
- Pantallas y navegación → `01_PANTALLAS.md`
- HUD y botones de batalla → `02_HUD.md`, `../batalla/04_PRESENTACION.md`
- Accesibilidad ampliada → `04_ACCESIBILIDAD.md`
