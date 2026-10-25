# 06 · Minimapa — orientarse sin jugar con un plano

**Estado:** ✅ **aprobado por el dueño (aprobación en bloque, 2026-09-30). Documento final.**

> El mundo se recuerda **caminándolo** (`../mundo/00_MAPA.md`). El minimapa existe para **no
> perderse**, no para pensar por ti: enseña lo que ya viste y **nada más**. Entra en la **Fase 2**;
> la demo se orienta con carteles y bocadillos.

---

## 1. Qué es y qué no

- **Es** una **capa pequeña** (esquina superior) que dibuja el grafo de sitios y caminos
  (`../mundo/00_MAPA.md` §4) y **tu posición en el nodo**.
- **No es** un radar: no enseña enemigos, ni tesoros, ni rutas óptimas.
- **No invade el centro**: vive en una esquina y se **desvanece** al moverse (`02_HUD.md` §1).

---

## 2. Qué se ve (y qué hay que ganarse)

| Elemento | Cuándo aparece |
|---|---|
| **Sitios visitados** | Al visitarlos (nunca antes) |
| **Caminos** | Al recorrerlos |
| **Sitios oídos** (rumor) | Como un **punto difuso**, sin nombre |
| **Deudas vivas** | Solo las del sitio donde estás |
| **Rutas no tomadas** | **No** se muestran |
| **Enemigos cercanos** | **Nunca** (eso lo dice el mundo, `../contenido/01_ENEMIGOS.md` §4) |

- **«Qué hay que ganarse»:** cada zona nueva empieza **en negro**; se pinta andando y oyendo.

---

## 3. Cómo no tapa el juego

1. **Tamaño contenido:** ocupa como máximo **1/6** de la pantalla y es **semitransparente**.
2. **Se desvanece** al caminar o al entrar en combate; se abre a toque largo si se quiere mirar.
3. **En batalla no existe**: el campo se lee con los ojos (`../batalla/04_PRESENTACION.md` §1).
4. **El paso a pantalla completa** (mapa de viaje, `01_PANTALLAS.md`) es otra cosa: el minimapa
   es una **capa**, el mapa de viaje es una **pantalla**.

---

## 4. Datos, tipos y validación

- Lee `SaveState` (sitios/caminos visitados) y `data/lugares.json` + `data/caminos.json`.
- **Tipos:** `EstadoMapa` en `js/data/game_types.js`.
- **Pintura** en escena; **no simula** (regla 2 de `../../AGENTS.md`).
- **Tests:** `tests/scene_minimapa.test.js`: un sitio no visitado no se dibuja; el minimapa respeta
  el tamaño; nada aparece en batalla.

---

## 5. Cifras que fija este documento

| Cifra | Valor |
|---|---|
| Tamaño máximo | 1/6 de pantalla, semitransparente |
| En batalla | **no existe** |
| Enemigos / tesoros | **nunca** se muestran |
| Sitios | solo visitados u oídos (difusos) |
| Desvanecido | al moverse o combatir |

---

## 6. Qué entra en la demo (Fase 1) — y qué sigue

> **Hasta aquí la demo.** **No hay minimapa** (llega en la Fase 2): la orientación se resuelve con
> **carteles de camino**, el **mapa de viaje** y los bocadillos (`../mundo/03_LUGARES.md`).

> **Y sigue el juego completo.** El minimapa entra en la **Fase 2** con las reglas de §2-§3: lee
> los nodos visitados del mismo `SaveState`, sin añadir campos.

---

## 7. Fuera de este documento

- El mapa y el grafo → `../mundo/00_MAPA.md`
- El mapa de viaje → `../mundo/02_VIAJE_Y_ENCUENTROS.md`
- El HUD → `02_HUD.md`
- Estilo y color → `../arte/00_ESTILO.md`
