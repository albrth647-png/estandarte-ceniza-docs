# 07 · Leyendas y rumores — lo que la gente cree

**Estado:** ✅ **aprobado por el dueño (aprobación en bloque, 2026-09-30). Documento final.**

> Aquí está **el contenido** de lo que se dice en Valcoria. La **mecánica** de cómo un rumor abre
> un encargo vive en `../misiones/03_CADENAS_Y_RUMORES.md`. **Toda leyenda esconde una deuda
> real** (regla de la casa).

---

## 1. La regla de oro

- **Lo que la gente cree** ≠ **lo que pasó**. La leyenda es la versión que sobrevive; la verdad
  está en el libro (o arrancada de él).
- **Ninguna leyenda es decorativa:** cada una **esconde un hecho cobrable** — un deudor, un
  heredero, una prueba (útil en el Acto II).

---

## 2. Leyendas del reino (catálogo)

| Leyenda | Lo que se cree | Lo que esconde |
|---|---|---|
| **Los cuarenta del Paso** | «Traidores que vendieron el paso» | Contratos **robados** del Libro Mayor |
| **La puerta abierta** | «Nadie la abrió: se abrió sola» | El **Teniente**, vivo |
| **El peaje del mes** | «Altamir cobraba lo suyo» | Debía la **tercera parte** a los cuarenta |
| **La mujer que firma** | «Doña Sira compró a un asesino» | Guarda **copia** de los contratos |
| **El Escribano bueno** | «Ambrosio salvó el reino» | Reescribió una **línea falsa** |
| **Los que no tienen marca** | «En la otra ribera no hay ley» | Gente que **escapó** de una deuda heredada |
| **El que volvió del paso** | «Solo uno salió vivo» | Salieron **dos** |

---

## 3. Cómo se siembran

- Un rumor **entra por boca** de un PNJ o un cartel (`../misiones/03_CADENAS_Y_RUMORES.md`).
- **La memoria decide quién lo suelta:** quien te debe un favor te lo dice de más; quien te odia,
  de menos o mal (mentira).
- **Se enfrían** a los 7 días si no los sigues; la **Crónica** los recuerda.

---

## 4. Mentiras y medias verdades

- Un rumor puede ser **falso a propósito** (alguien te desvía) — y entonces es un **encargo
  `investigar`**.
- **Nunca** hay un rumor que no lleve a nada: si es falso, lleva a **quién lo sembró**.

---

## 5. Datos, tipos y validación

- **Datos (por crear):** `data/rumores.json` (mecánica, `../misiones/03_CADENAS_Y_RUMORES.md`) + claves
  `txt_rumor_*` para el texto.
- **Tipos:** `Leyenda` y `Rumor` en `js/data/game_types.js`.
- **Validación:** cada leyenda referencia un `hecho`/`deuda` existente en datos
  (`tools/validate_data.js`); paridad ES/EN de sus claves.
- **Tests (por escribir):** `tests/leyendas.test.js`: toda leyenda esconde algo real; ninguna queda sin salida;
  las claves tienen pareja EN.

---

## 6. Cifras que fija este documento

| Cifra | Valor |
|---|---|
| Leyendas | **7** (§2) |
| Regla | toda leyenda esconde una deuda |
| Caducidad del rumor | 7 días (`../mundo/05_TIEMPO_DEL_MUNDO.md`) |
| Rumores por lugar | 1 (`../misiones/03_CADENAS_Y_RUMORES.md`) |
| Paridad | ES/EN obligatoria |

---

## 7. Qué entra en la demo (Fase 1) — y qué sigue

> **Hasta aquí la demo.** Las leyendas del **Paso**, el **peaje** y **el que volvió**, sembradas
> por los PNJ de los 6 sitios y conectadas al giro de las páginas.

> **Y sigue el juego completo.** Las leyendas de la **otra ribera**, **la mujer que firma** y **el
> Escribano bueno** se revelan en el Acto II con estas mismas reglas; el catálogo crece, la regla
> no cambia.

---

## 8. Fuera de este documento

- La premisa → `00_PREMISA.md`
- Las casas → `05_CASAS_Y_FACCIONES.md`
- La mecánica de rumores → `../misiones/03_CADENAS_Y_RUMORES.md`
- Textos del mundo → `08_TEXTO_DEL_MUNDO.md`
