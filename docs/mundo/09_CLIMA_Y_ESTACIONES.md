# 09 · Clima y estaciones — el cielo también cobra

**Estado:** ✅ **aprobado por el dueño (aprobación en bloque, 2026-09-30). Documento final.**

> El clima **no es decorado**: cambia el viaje, la moral y el precio de la comida. Se mide en
> **estaciones** (`05_TIEMPO_DEL_MUNDO.md`: 28 días). Entra de lleno en la **Fase 4**; la demo usa
> lluvia y niebla simples.

---

## 1. Las cuatro estaciones

| Estación | Carácter | Qué trae |
|---|---|---|
| **Deshielo** | Barro y ríos crecidos | Vados peligrosos; caminos pesados |
| **Estío** | Polvo y calor | Más viaje, menos agua; grano barato |
| **Cosecha** | Trabajo y mercado | Precios bajos de comida; más gente en camino |
| **Fría** | Nieve y hambre | Viaje lento; comida cara; moral frágil |

---

## 2. Fenómenos y su efecto

| Fenómeno | Efecto |
|---|---|
| **Lluvia** | Barro **+1 día** en trayectos largos (`06_TERRENO_DEL_MUNDO.md` §1); visibilidad media |
| **Niebla** | Visibilidad **baja**; más emboscadas (`02_VIAJE_Y_ENCUENTROS.md` §2) |
| **Nieve** | Velocidad **×0,8** en todo el mundo; refugio obligatorio de noche |
| **Calor** | Consumo de agua y comida sube; moral baja en marchas largas |
| **Tormenta** | No se viaja; se espera (día perdido) o se paga posada |

- **El clima afecta a los dos bandos:** en el campo, lluvia/nieve **no distingue** de quién es la
  tropa (`../batalla/02_TERRENO.md` §2).

---

## 3. Efecto en moral y economía

- **Moral** (`../sistemas/08_LUTO_Y_MORAL.md`): Fría y tormenta **bajan** la moral de la
  compañía; Cosecha la sube.
- **Comida** (`../contenido/14_COMIDAS_Y_BEBIDAS.md`): el precio sube en Fría y baja en
  Cosecha (`../sistemas/06_ECONOMIA.md` §5).
- **Ingresos:** la Ribera comercia más en Cosecha; la Serranía se cierra en Fría.

---

## 4. Cómo se representa

- **Luz y cielo** cambian con la estación y la hora (`../arte/00_ESTILO.md` §3): sin HUD de clima.
- **El mundo avisa:** barro, ríos crecidos y niebla **se ven** antes de sufrirlos
  (`../interfaz/07_AVISOS_Y_RUMORES.md`).
- **Sin esperas reales:** una tormenta es un **día de juego**, no un temporizador.

---

## 5. Datos, tipos y validación

- **Datos (por crear):** `data/clima.json` — `{ id, estacion, efecto_viaje, efecto_moral, efecto_precio }`.
- **Tipos:** `Estacion` y `Fenomeno` en `js/data/game_types.js`.
- **Validación:** cruce con `data/tiempo.json` (estaciones de 28 días) y con `data/terreno.json`
  (barro) en `tools/validate_data.js`.
- **Sistema puro:** `js/systems/clima.js` — aplica efectos por estación/franja; sin DOM, sin reloj
  (el día entra inyectado), RNG inyectado.
- **Tests (por escribir):** `tests/clima.test.js`: la estación dura 28 días; lluvia añade 1 día al trayecto; el
  clima no distingue de bando.

---

## 6. Cifras que fija este documento

| Cifra | Valor |
|---|---|
| Estaciones | **4** (Deshielo · Estío · Cosecha · Fría) |
| Duración | 28 días (`05_TIEMPO_DEL_MUNDO.md`) |
| Lluvia | +1 día en trayectos largos |
| Nieve | velocidad ×0,8 |
| Tormenta | no se viaja (1 día) |
| Niebla | visibilidad baja |
| Efecto por bando | **igual** para todos |

---

## 7. Qué entra en la demo (Fase 1) — y qué sigue

> **Hasta aquí la demo.** **Lluvia** (barro +1 día) y **niebla** (más emboscadas) simples; sin
> estaciones completas.

> **Y sigue el juego completo.** Las **4 estaciones**, nieve, calor y tormentas entran en la
> **Fase 4** con estas mismas tablas; crecer = más filas en `clima.json`, no otro sistema.

---

## 8. Fuera de este documento

- Días y franjas → `05_TIEMPO_DEL_MUNDO.md`
- Hora y luz → `../arte/00_ESTILO.md`
- Viaje → `02_VIAJE_Y_ENCUENTROS.md`
- Comida y economía → `../contenido/14_COMIDAS_Y_BEBIDAS.md`, `../sistemas/06_ECONOMIA.md`
