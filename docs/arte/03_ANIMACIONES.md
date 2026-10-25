# 03 · Animaciones — cómo se mueve todo

**Estado:** ✅ **aprobado por el dueño (aprobación en bloque, 2026-09-30). Documento final.**

> Las animaciones **sirven al juego**: los tiempos se **atan a las cifras de combate**
> (`../batalla/01_CIFRAS.md`), no al revés. Viven en la escena (regla 11 de `../../AGENTS.md`);
> el motor puro solo conoce tiempos.

---

## 1. Estados de un personaje

| Estado | Clip | Cuándo | Nota |
|---|---|---|---|
| **Idle** | `idle` | Quieto | Respira; postura según arma |
| **Andar** | `walk` | 3,0 m/s | `../mundo/01_EXPLORACION.md` §3 |
| **Correr** | `run` | 5,0 m/s / 4,5 tropa | Huida: 5,5 m/s |
| **Atacar** | `attack` | Cadencia **1,2 s** (héroe) | El golpe conecta al final del clip |
| **Guardia** | `block` | Ventana **0,5 s** | Reduce 75 % (`01_CIFRAS.md` §3) |
| **Desvío** | `dodge` | **0,35 s** | Invulnerabilidad breve |
| **Herido** | `hit` | Al recibir daño | Corta el ataque, no el movimiento |
| **Caer** | `death` | Vida a 0 | Baja de campaña (`../contenido/00_TROPAS.md` §7) |
| **Cargar** | `charge` | Orden Cargar | +30 % velocidad 5 s |

- **Regla de oro:** el clip de ataque **no dura más que la cadencia**; si el arte pide otra cosa,
  manda la cifra (`01_CIFRAS.md`).

---

## 2. Tiempos y mezcla

- **Transiciones:** fundido entre clips de **120 ms** (andar→correr, idle→atacar).
- **Velocidad atada al movimiento:** el clip avanza según la velocidad real, para no «patinar».
- **Golpe conecta a mitad/final del clip**, nunca al empezar (evita el «golpe fantasma»).
- **Animación de muerte:** **2 s** y se queda en el suelo; se retira del campo tras la batalla.

---

## 3. Props y estructuras

- **Props animados:** bandera (viento), puerta (bisagra), carro (volcado) — clips cortos, no
  interrumpibles.
- **Nada de árboles animados:** la vegetación se mueve por **shader** o no se mueve
  (`../mundo/07_PROPS_Y_VEGETACION.md`).
- **Instancing:** las animaciones no se aplican a props instanciados (coste); solo a los únicos.

---

## 4. Qué se puede y qué no (presupuesto)

- **Máximo de animadores a la vez:** 10+10 (batalla) + héroe; el resto, LOD estático si aplica.
- **Sin cinemáticas:** no hay animaciones faciales ni labiales; los PNJ **parpadean y gesticulan
  poco**.
- **Sin ragdolls:** la muerte es un clip, no física (rendimiento y tono sobrio).

---

## 5. Datos, tipos y validación

- **Datos:** `data/animaciones.json` — `{ id, clip, duracion_ms, bucle, atado_a }`.
- **Tipos:** `Animacion` en `js/data/game_types.js`.
- **Validación:** el `clip` existe en el `.glb` (cruce con `data/assets.json`) y la duración es
  coherente con `01_CIFRAS.md`; sin eso, falla (`tools/validate_data.js`).
- **Tests:** `tests/animaciones.test.js`: el ataque no supera la cadencia; andar/correr se mezclan;
  una animación sin clip rompe la carga.

---

## 6. Cifras que fija este documento

| Cifra | Valor |
|---|---|
| Fundido entre clips | 120 ms |
| Ataque (héroe) | ≤ 1,2 s (cadencia) |
| Guardia | 0,5 s · Desvío 0,35 s |
| Muerte | 2 s (clip, sin ragdoll) |
| Animadores a la vez | 10+10 + héroe |
| Animaciones faciales | **no** |

---

## 7. Qué entra en la demo (Fase 1) — y qué sigue

> **Hasta aquí la demo.** Los 9 estados de §1 para héroe y tropas, las 3 armas base y los props
> animados, con los tiempos de `01_CIFRAS.md`.

> **Y sigue el juego completo.** Monturas, criaturas y estructuras complejas añaden clips **con
> estas mismas reglas** (duración atada a cifras, sin ragdoll, mismas transiciones).

---

## 8. Fuera de este documento

- Cifras de combate → `../batalla/01_CIFRAS.md`
- Modelos y clips → `01_ASSETS.md`
- Efectos → `04_EFECTOS_Y_PARTICULAS.md`
- Estilo → `00_ESTILO.md`
