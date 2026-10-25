# 05 · Tiempo del mundo — días, franjas y lo que caduca

**Estado:** ✅ **aprobado por el dueño (aprobación en bloque, 2026-09-30). Documento final.**

> **Todo se mide en días de juego** (día de juego), nunca en minutos reales (regla 8 de
> `../../AGENTS.md`). El tiempo entra **inyectado** en los sistemas puros; ninguno mira el reloj
> del dispositivo (`../../AGENTS.md`, regla 9 de determinismo).

---

## 1. Unidades de tiempo

| Unidad | Equivale a | Uso |
|---|---|---|
| **Franja** | 4 al día | Rutinas de PNJ y tabla de encuentros (`02_VIAJE_Y_ENCUENTROS.md` §2) |
| **Día** | 4 franjas | Unidad de todo: viajes, encargos, deudas |
| **Semana** | 7 días | Resúmenes de Crónica, refresco de tablones |
| **Estación** | 28 días (4 semanas) | Clima (`09_CLIMA_Y_ESTACIONES.md`) |
| **Año** | 112 días (4 estaciones) | Cronología y hitos largos |

- **Las 4 franjas:** amanecer (06-10) · mediodía (10-16) · atardecer (16-20) · noche (20-06).
- **La noche** se viaja solo si lo pides, con **peligro ×2** (`02_VIAJE_Y_ENCUENTROS.md` §5).

---

## 2. Qué gira sobre el tiempo

| Sistema | Qué caduca / avanza |
|---|---|
| **Deudas** | **Nunca** caducan ni generan intereses (`../sistemas/00_MEMORIA_Y_DEUDA.md` §5) |
| **Favor (deuda blanca)** | Caduca a **90 días** (`../sistemas/03_FAVORES.md`) |
| **Encargos** | Su plazo en días; al vencer, lo coge otro (`../misiones/01_TABLONES_Y_PORTAVOCES.md`) |
| **Rumores** | Se enfrían a los **7 días** (`../misiones/03_CADENAS_Y_RUMORES.md`) |
| **Salarios** | Se pagan **cada día** (`../sistemas/06_ECONOMIA.md` §3) |
| **Tablones** | Se renuevan cada 3-7 días |

- **El mundo se mueve sin ti** en la Fase 2 (`../sistemas/09_TIEMPO_Y_MUNDO_VIVO.md`): casas,
  cobranzas y rencores avanzan cada estación.

---

## 3. Cómo se representa

- El HUD muestra **«Día N»** (`../interfaz/02_HUD.md` §2); la **hora** se siente por la luz
  (`../arte/00_ESTILO.md` §3), no por un reloj.
- **Sin esperas reales:** pasar un día es una **acción** (descansar o viajar), no un temporizador.
- **El tiempo avanza al jugar**, nunca en segundo plano con la app cerrada (offline).

---

## 4. Datos, tipos y validación

- **Datos (por crear):** `data/tiempo.json` — `{ franjas, dias_semana, dias_estacion }`.
- **Tipos:** `Franja` y `Calendario` en `js/data/game_types.js`.
- **Validación:** esquema; coherencia con los plazos de encargos y la caducidad del favor
  (`tools/validate_data.js`).
- **Sistema puro:** `js/systems/tiempo.js` — avanza el día y dispara caducidades; sin reloj real,
  `dt` inyectado.
- **Tests (por escribir):** `tests/tiempo.test.js`: 4 franjas por día; la estación dura 28 días; una deuda **nunca**
  caduca por tiempo.

---

## 5. Cifras que fija este documento

| Cifra | Valor |
|---|---|
| Franjas por día | **4** |
| Días por semana | **7** |
| Días por estación | **28** |
| Días por año | **112** |
| Caducidad del favor | 90 días |
| Caducidad del rumor | 7 días |
| Caducidad de la deuda | **ninguna** |

---

## 6. Qué entra en la demo (Fase 1) — y qué sigue

> **Hasta aquí la demo.** Días, franjas y noche, con las caducidades de encargos, favor y rumor;
> el Acto I abarca unos **20-40 días de juego**.

> **Y sigue el juego completo.** Estaciones y el **mundo vivo** (Fase 2) avanzan con estas mismas
> unidades; crecer = más eventos por estación, no otra escala de tiempo.

---

## 7. Fuera de este documento

- Viaje y encuentros → `02_VIAJE_Y_ENCUENTROS.md`
- Clima → `09_CLIMA_Y_ESTACIONES.md`
- Mundo vivo → `../sistemas/09_TIEMPO_Y_MUNDO_VIVO.md`
- HUD → `../interfaz/02_HUD.md`
