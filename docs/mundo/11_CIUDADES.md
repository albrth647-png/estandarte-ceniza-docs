# 11 · Ciudades — donde manda el que cobra

**Estado:** ✅ **aprobado por el dueño (aprobación en bloque, 2026-09-30). Documento final.**

> En el reino hay **1 ciudad** (`00_MAPA.md` §2): el **Patio del Cadalso**, con muralla, mercado y
> corte. Las villas y aldeas están en `03_LUGARES.md`; aquí se detalla **la ciudad**.

---

## 1. Qué tiene siempre una ciudad

| Pieza | Para |
|---|---|
| **Muralla y puertas** | Control de entrada; peaje y toque de queda |
| **Escribanía** | Deudas, firma, **enmienda** (`../sistemas/01_FIRMA.md` §7) |
| **Tablón mayor** | Encargos de honor (Firma ≥ Correcto) |
| **Mercado** | Comprar/vender; precios de `../sistemas/06_ECONOMIA.md` |
| **Posada** | Descanso y rumores |
| **Corte / casa mayor** | Casa o autoridad que manda en la zona |
| **Plaza del cadalso** | Ejecuciones y sentencias (donde empiezas) |

- **Puede tener:** taller, cárcel, hospital de barbero, casa de baños, templo.

---

## 2. Barrios y muchedumbre

- **2-4 barrios:** mercado, artesanos, residencial, extramuros (pobreza y deudas).
- **Muchedumbre:** muchos PNJ **ligeros** (cupo 25 por lugar, `04_PNJ.md`); solo los **relevantes**
  guardan memoria completa.
- **Ley de ciudad:** dentro de murallas **no se pelea a la vista** sin consecuencias: los guardias
  y la guardia de la casa responden (`../contenido/01_ENEMIGOS.md` §4).

---

## 3. Puertas y control

- **Toque de queda de noche:** se cierran; entrar de noche exige soborno (`../sistemas/06_ECONOMIA.md` §3)
  o un favor.
- **La marca se ve en la puerta:** tu Firma y tu deuda deciden si entras, si te registran o si te
  niegan (`01_FIRMA.md` §6).
- **Un Hiena** puede entrar a un mercado… y pagar **+40 %** (`01_FIRMA.md` §3).

---

## 4. Qué se hace en una ciudad (bucle)

1. **Cobrar o aceptar** un encargo del tablón mayor.
2. **Vender/botín** y **reclutar** en el mercado.
3. **Enmendar** la Firma (100 oro + 1 día) si te has pasado.
4. **Oír rumores** en la posada (`../misiones/03_CADENAS_Y_RUMORES.md`).
5. **Descansar** y salir a camino.

---

## 5. Datos, tipos y validación

- **Datos:** `data/ciudades.json` — `{ id, barrios, servicios, corte, toque_de_queda }`; la ficha de
  sitio en `lugares.json`.
- **Tipos:** `Ciudad` en `js/data/game_types.js`.
- **Validación:** cruce de `servicios` con `lugares.json` y de la `corte` con
  `../historia/05_CASAS_Y_FACCIONES.md` en `tools/validate_data.js`.
- **Sistema puro:** control de puertas y mercado en los sistemas existentes; sin DOM ni reloj.
- **Tests:** `tests/ciudades.test.js`: la ciudad tiene los 7 servicios; el toque de queda no deja
  atrapado a nadie; una sola ciudad en el mapa base.

---

## 6. Cifras que fija este documento

| Cifra | Valor |
|---|---|
| Ciudades | **1** (Patio del Cadalso) |
| Servicios fijos | **7** |
| Barrios | 2-4 |
| Cupo de gente | 25 fichas por lugar |
| Toque de queda | noche |
| Recargos por Firma | los de `01_FIRMA.md` §3 |

---

## 7. Qué entra en la demo (Fase 1) — y sigue

> **Hasta aquí la demo.** El **Patio del Cadalso** con muralla, escribanía, tablón mayor, mercado,
> posada y plaza del cadalso; sin corte (llega con las casas).

> **Y sigue el juego completo.** La **corte**, los barrios ricos y las ciudades de las otras zonas
> se añaden **con este mismo formato**; crecer = más filas en `ciudades.json` y `lugares.json`.

---

## 8. Fuera de este documento

- Mapa y jerarquía → `00_MAPA.md`
- Ficha de sitio → `03_LUGARES.md`
- Casas y facciones → `../historia/05_CASAS_Y_FACCIONES.md`
- Economía y precios → `../sistemas/06_ECONOMIA.md`
- Firma y puertas → `../sistemas/01_FIRMA.md`
