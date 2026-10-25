# 00 · Tipos de encargo — qué trabajos hay

**Estado:** ✅ **aprobado por el dueño (aprobación en bloque, 2026-09-30). Documento final.**

> Un encargo es **una deuda que otro quiere que cobres tú** (`../historia/00_PREMISA.md`). Aquí
> está **qué clases de trabajo existen**; dónde se cogen, en `01_TABLONES_Y_PORTAVOCES.md`; cómo
> se definen en datos, en `02_ESTRUCTURA_DE_ENCARGO.md`; cuánto pagan, en
> `04_PAGOS_Y_RECOMPENSAS.md`. **Nombres e ids son propuesta de diseño.**

---

## 1. Las once clases de encargo

| id | Clase | Qué se te pide | Plazo | Qué puede salir mal | Se cobra | Origen |
|---|---|---|---|---|---|---|
| `cobrar` | **Cobrar una deuda** | Que el deudor pague (o que lo pague su casa) | 2-5 días | El deudor huye, miente o pelea | El importe + comisión | **Sistema** |
| `escoltar` | **Escoltar** | Llevar a alguien o algo de un sitio a otro | 1-3 días | Emboscada en el camino | Oro fijo | Sistema |
| `rescatar` | **Rescatar** | Sacar a alguien de una cuadrilla o un calabozo | 1-4 días | Muerte del rehén, rescate a medias | Oro + favor | Manual |
| `limpiar` | **Limpiar un camino** | Echar a los que asaltan un tramo | 1-3 días | Los bandidos vuelven con su casa | Oro + botín | Sistema |
| `mediar` | **Mediar** | Poner paz entre dos partes en deuda | 2-5 días | Elegir bando; el otro te lo cobra | Pago de uno o los dos | Manual |
| `vigilar` | **Vigilar / hacer guardia** | Una puerta, una noche, un carro | 1-2 días | Nada pasa… o pasa y lo ves | Salario fijo | Sistema |
| `mensaje` | **Llevar mensaje** | Un pliego o un aviso, de mano propia | 1-4 días | El mensaje compromete a quien lo lleva | Oro + información | Sistema |
| `vengar` | **Vengar (feudo)** | Cobrar una ofensa que pide sangre | 3-10 días | Feudo abierto: la casa responde | Pago de la casa + rencores | **Sistema** |
| `investigar` | **Investigar** | Averiguar un hecho, un nombre, una deuda | 5-15 días | La verdad no se puede probar | Información → Acto III | Manual |
| `fianza` | **Sacar de la cárcel** | Pagar por alguien y responder por él | 1-2 días | Se fuga y la fianza es tuya | El deudor te lo debe | Manual |
| `oficio` | **Encargo de oficio** | El maestro de tu profesión te pide un trabajo de tu oficio | 2-5 días | El plazo se pasa y la pieza no sale | **XP de oficio** + oro | **Maestro** |

- **`oficio` es la clase 11** (añadida 2026-10-02): **no sale del tablón**, la reparte **el maestro**
  de tu profesión activa, **3 por rango**. **Paga en XP de oficio** (`+40`) **+ oro**, no en XP del
  héroe, y **cada una trae 1 receta** al cerrarla. Detalle en
  `../sistemas/15_FABRICACION_Y_RECETAS.md` §9.

- **11 clases** en el juego completo (`../produccion/00_ALCANCE.md` §3).
- **«Sistema»** = nace solo de deudas, rencores y memoria; **«manual»** = escrito a mano en la
  historia o en un sitio; **«Maestro»** = la reparte el maestro de tu profesión.

---

## 2. Qué clase pide cada cosa (el encargo sigue a la deuda)

- **Hay deuda firme** (`d ≠ 0`) → **cobrar** o **vengar**, según el tiempo y el rencor.
- **Hay alguien en peligro** → **rescatar** o **escoltar**.
- **Hay un camino roto** → **limpiar**.
- **Hay dos casas enfrentadas** → **mediar** (y elige bando).
- **Hay un secreto** (Acto II) → **investigar**.

> **Regla dura:** ningún encargo pide lo que ya tienes. Siempre nace de una deuda, un rencor o
> un vacío concreto.

---

## 3. Encargos que chocan entre sí

- **Dos casas, una deuda:** puedes aceptar el mismo objetivo de dos acreedores; solo uno cobra,
  y **el otro te lo apunta** (memoria, hecho 9 · Incumplimiento).
- **Mediar sin bando:** intentar cobrar a los dos **rompe** el encargo y **enciende** a ambos.
- **Regla:** un encargo nuevo que **contradice** uno activo se avisa al aceptarlo («Esto rompe lo
  prometido a <nombre>»); aceptarlo es una decisión con testigos.

---

## 4. Datos, tipos y validación

- **Datos (por crear):** `data/encargos.json` — cada encargo trae su `clase` (una de las 11) y el resto de
  campos de `02_ESTRUCTURA_DE_ENCARGO.md`.
- **Tipos:** `ClaseEncargo` en `js/data/game_types.js` (una sola vez, regla 4).
- **Validación:** esquema en `js/data/schemas.js` + cruce de `clase` con esta lista y de ids de
  PNJ en `tools/validate_data.js`.
- **Sistema puro:** la generación de encargos por deuda y rencor vive en
  `js/systems/encargos.js`; sin DOM, sin reloj, RNG inyectado.

---

## 5. Cifras que fija este documento

| Cifra | Valor |
|---|---|
| Clases de encargo | **11** |
| Generados por el sistema | cobrar · escoltar · limpiar · vigilar · mensaje · vengar |
| Escritos a mano | rescatar · mediar · investigar · fianza |
| Del maestro de la profesión | **oficio** (9: 3 por rango) ✅ 2026-10-02 |
| Plazos | 1-15 días según clase |
| Choques | se avisan, nunca se ocultan |

---

## 6. Qué entra en la demo (Fase 1) — y qué sigue

> **Hasta aquí la demo.** **6 encargos**, uno por sitio (`../mundo/03_LUGARES.md` §2):
> `cobrar` (Patio del Cadalso y Vega Quemada), `vigilar`/`escoltar` (Posada de la Deuda Blanca),
> `mensaje` (Herreruela), `mediar`/recluta (Casar de la Nava) y `limpiar` (Cruce de las Dos
> Sendas, la batalla). Clases con estas mismas reglas.

> **Y sigue el juego completo.** Las **11 clases**, incluidas `rescatar`, `vengar`, `investigar` y
> `oficio` (los 9 encargos del maestro), se añaden **con este mismo formato y estos plazos**; crecer =
> más encargos en `encargos.json`, no una clase nueva cada vez.

---

## 7. Fuera de este documento

- Dónde se cogen → `01_TABLONES_Y_PORTAVOCES.md`
- Cómo se definen → `02_ESTRUCTURA_DE_ENCARGO.md`
- Cadenas y rumores → `03_CADENAS_Y_RUMORES.md`
- Cuánto pagan → `04_PAGOS_Y_RECOMPENSAS.md`
- Los 9 encargos de oficio y el XP de oficio → `../sistemas/15_FABRICACION_Y_RECETAS.md`
- Los de la trama → `05_ENCARGOS_DE_LA_HISTORIA.md`
