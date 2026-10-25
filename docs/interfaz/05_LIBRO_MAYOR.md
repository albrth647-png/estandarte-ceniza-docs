# 05 · Libro Mayor — la pantalla de tu registro

**Estado:** ✅ **aprobado por el dueño (aprobación en bloque, 2026-09-30). Documento final.**

> El Libro Mayor es **la pantalla del sistema de memoria**: leer quién te debe y a quién le debes,
> tus favores, tus rencores y tu Crónica. Es la cara visible de `../sistemas/00_MEMORIA_Y_DEUDA.md`
> y `../sistemas/04_CRONICA.md`. **Entra de lleno en la Fase 2**; en la demo hay una versión simple.

---

## 1. Qué se lee (pestañas)

| Pestaña | Qué muestra | Fuente |
|---|---|---|
| **Deudas** | `d > 0` (te deben) y `d < 0` (debes), con banda y día | `00_MEMORIA_Y_DEUDA.md` §5 |
| **Favores** | Deuda blanca activa y su **caducidad** | `../sistemas/03_FAVORES.md` |
| **Rencores** | Quién te odia y por qué; la **casa** marcada | `00_MEMORIA_Y_DEUDA.md` §7 |
| **Crónica** | Tu diario, día a día | `../sistemas/04_CRONICA.md` |
| **Firma** | Tu banda y los últimos 16 hechos públicos | `01_FIRMA.md` §4 |

- **Nunca muestra el número** de rango/Firma: muestra **bandas** y palabras, como el HUD.
- **Solo aparecen los «relevantes»** con memoria completa y las deudas firmes; el resto del mundo
  se resume («otros 140 te recuerdan»).

---

## 2. Cómo se lee (sin marear)

- **Lista con toque:** tocar una persona abre su ficha (banda, deuda, hechos, día).
- **Deslizar arriba/abajo** para leer; **deslizar a los lados** cambia de pestaña
  (`00_CONTROLES.md` §3, arrastre doble).
- **Buscador por nombre** cuando la lista crece (Fase 2+).
- **Resumen arriba:** deuda total, favor más urgente, rencor más peligroso.

---

## 3. La red de rencores (grafo visible)

- En Fase 2, la pestaña de rencores dibuja un **grafo simple**: tú en el centro, las **casas**
  alrededor, líneas más gruesas = más rencor.
- **No es un mapa estratégico**: no se interactúa con él; solo **se lee** quién se mueve contra ti.
- Al tocar una casa, se ven sus miembros relevantes y la deuda heredada
  (`00_MEMORIA_Y_DEUDA.md` §5).

---

## 4. Reglas de casa

1. **El registro no se puede abrir en mitad de un diálogo ni de un combate cuerpo a cuerpo**: se
  abre desde exploración o desde el menú.
2. **No pausa el mundo** salvo en las pantallas de sistema (días de juego, nunca reloj real).
3. **Todo lo que enseña es dato guardado**, no cálculo nuevo: si algo no está en el guardado, no
  se inventa.
4. **Nada de spoilers:** el Libro enseña lo que el jugador ya sabe (hechos vividos).

---

## 5. Datos, tipos y validación

- Lee `SaveState.memoria`, `.firma`, `.cronica` (SAVE_VERSION 3). **No añade campos.**
- **Tipos:** `PestanaLibro` en `js/data/game_types.js`.
- **Pintura** en escena (`js/scenes/sc_libro.js`) con el kit DOM; **no simula** (regla 2).
- **Tests:** `tests/scene_libro.test.js`: las 5 pestañas se pintan; un guardado vacío no rompe; el
  grafo de rencores no dibuja un rencor caducado.

---

## 6. Cifras que fija este documento

| Cifra | Valor |
|---|---|
| Pestañas | **5** (deudas · favores · rencores · crónica · firma) |
| Personas listadas | relevantes + deudas firmes; el resto, resumen |
| Hechos de Firma mostrados | últimos **16** |
| Entradas de Crónica | 200 (`../sistemas/04_CRONICA.md`) |
| Números exactos | **no** se muestran (bandas) |

---

## 7. Qué entra en la demo (Fase 1) — y qué sigue

> **Hasta aquí la demo.** Una versión **simple** del registro: lista de **Crónica** y de deudas/
> favores de los 6 sitios (`../produccion/00_ALCANCE.md`); la Firma se ve en el HUD.

> **Y sigue el juego completo.** El **Libro Mayor completo** (5 pestañas + grafo de rencores +
> buscador) llega en la **Fase 2**; lee los mismos datos, no cambia el guardado.

---

## 8. Fuera de este documento

- La memoria y los rencores → `../sistemas/00_MEMORIA_Y_DEUDA.md`
- La Crónica → `../sistemas/04_CRONICA.md`
- Los favores → `../sistemas/03_FAVORES.md`
- El HUD y las bandas → `02_HUD.md`, `../sistemas/01_FIRMA.md`
- Avisos sin abrir pantalla → `07_AVISOS_Y_RUMORES.md`
