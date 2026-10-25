# 08 · Luto y moral — la muerte pesa

**Estado:** ✅ **aprobado por el dueño (aprobación en bloque, 2026-09-30). Documento final.**

> Una compañía de deudores **entierra a los suyos** (`../historia/00_PREMISA.md`). Aquí está lo
> que pasa **después** del campo: la moral que baja, la **semana de luto** y lo que cuesta. La
> moral **en batalla** vive en `../batalla/01_CIFRAS.md` §5; esto es **fuera** del campo.

---

## 1. Cuando cae alguien tuyo

- **Muerte de tropa = baja de campaña** (`../batalla/00_REGLAS.md` §9): no vuelve.
- **Efecto inmediato:** la moral del bando en el campo baja como manda `01_CIFRAS.md` §5
  (muerte a < 6 m **−15**, vista **−8**).
- **Fuera del campo:** su nombre entra en la **Crónica** (`04_CRONICA.md`) y su **casa queda
  marcada** (herencia de deuda, `00_MEMORIA_Y_DEUDA.md` §5).

---

## 2. La semana de luto

- **Dura 7 días de juego** (`../mundo/05_TIEMPO_DEL_MUNDO.md`).
- **Efecto:** la compañía **no sube moral** por encima de un techo temporal (**≤ 70**) y los
  reclutadores ofrecen **menos gente**.
- **Se acorta** con: funeral pagado (`../sistemas/06_ECONOMIA.md` §3) o un triunfo **con testigos**.
- **Nunca bloquea:** se puede seguir jugando; solo se nota.

---

## 3. Moral de la compañía (fuera del campo)

| Hecho | Efecto |
|---|---|
| **Funeral** pagado | +10 moral tras el luto |
| **Botín repartido** | +5 moral (una vez por botín) |
| **Sin pagar salarios** | −5/día (`../sistemas/06_ECONOMIA.md` §3) |
| **Sin comida** | −5/día (`../mundo/10_SUPERVIVENCIA_Y_DESCANSO.md` §1) |
| **Triunfo con testigos** | +10 y baja la Firma enemiga |
| **Traición o huida** | −15 y posible rencor (`04_CRONICA.md`) |

- La **moral de compañía** y la **moral de campo** son **dos marcadores distintos**: la primera
  es de campaña; la segunda, del combate (100 → ruptura).

---

## 4. El capitán que cae

- La muerte de un **capitán con nombre** (tuyo o enemigo) **pesa el doble** en los suyos
  (`../batalla/01_CIFRAS.md` §5) y **entra en la Crónica** con nombre y casa.
- Un capitán enemigo muerto **no vuelve**; uno que huyó **sí** (`../contenido/01_ENEMIGOS.md` §3).

---

## 5. Datos, tipos y validación

- **Datos (por crear):** `data/luto.json` — `{ luto_dias, techo_moral, efectos }`.
- **Tipos:** `Luto` en `js/data/game_types.js`.
- **Validación:** cruce con `data/economia.json` (coste de funeral) y `../batalla/01_CIFRAS.md`
  (moral) en `tools/validate_data.js`.
- **Sistema puro:** `js/systems/luto.js` — aplica luto y moral de campaña; sin DOM ni reloj (día
  por día de juego).
- **Tests (por escribir):** `tests/luto.test.js`: el luto dura 7 días; sin salarios la moral baja −5/día; la
  muerte de un capitán pesa doble.

---

## 6. Cifras que fija este documento

| Cifra | Valor |
|---|---|
| Semana de luto | **7 días** |
| Techo de moral en luto | ≤ 70 |
| Funeral | +10 moral |
| Sin salarios / sin comida | −5/día |
| Muere un capitán | peso ×2 |
| Recuperación | no se acorta por pagar dinero sola |

---

## 7. Qué entra en la demo (Fase 1) — y sigue

> **Fuera de la demo (Fase 4).** En el Acto I una baja **es una unidad menos** y nada más: ni
> funerales, ni semana de luto, ni moral de compañía (recorte de `../produccion/00_ALCANCE.md` §5,
> 2026-10-02). El **luto de 7 días** y los **3 funerales** se construyen en la Fase 4.

> **Y sigue el juego completo.** Traiciones, deserciones por hambre y funerales de casa se añaden
> **con estas mismas reglas**; crecer = más filas en `luto.json`, no otro marcador.

---

## 8. Fuera de este documento

- Moral en combate → `../batalla/01_CIFRAS.md`
- Tropas y veteranía → `../contenido/00_TROPAS.md`
- Lealtad y deserción → `10_LEALTAD_Y_DESERCION.md`
- Crónica → `04_CRONICA.md`
- Economía (funerales) → `06_ECONOMIA.md`
