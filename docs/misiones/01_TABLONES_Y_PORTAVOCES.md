# 01 · Tablones y portavoces — dónde se cogen los encargos

**Estado:** ✅ **aprobado por el dueño (aprobación en bloque, 2026-09-30). Documento final.**

> Cada sitio ofrece trabajo a su manera (`../mundo/03_LUGARES.md`). Aquí está **dónde se cuelgan
> los encargos, quién los publica y cómo se leen sin un menú pesado**. Los tipos, en
> `00_TIPOS_DE_ENCARGO.md`; el formato, en `02_ESTRUCTURA_DE_ENCARGO.md`.

---

## 1. Dónde se ofrecen

| Sitio | Quién publica | Qué ofrece | Filtro |
|---|---|---|---|
| **Tablón de aldea** | El portavoz | 2-3 encargos locales (`cobrar`, `limpiar`, `vigilar`) | Ninguno |
| **Posada / cruce** | El posadero y los que pasan | 1-2 encargos de camino (`escoltar`, `mensaje`) | Ninguno |
| **Oficina del Escribano** | El Escribano de la Sangre | Encargos de **honor** (`mediar`, `investigar`, `fianza`) | Firma ≥ **Correcto** |
| **Casa que te busca** | Una familia o una casa | Encargo **a por ti** (`cobrar`, `vengar`) | Tu **marca**/Firma y su memoria |

- **Los encargos de honor exigen banda ≥ Correcto** (`../sistemas/01_FIRMA.md` §6): un Hiena no
  recibe el trabajo fino.

---

## 2. Cómo se leen (sin menús pesados)

1. **Te acercas y enfocas** el tablón o hablas con el portavoz (`../mundo/01_EXPLORACION.md` §5).
2. El encargo se lee **como un cartel**: una línea de qué se pide y una de pago.
3. **Aceptar** es un toque; **rechazar**, otro. Sin confirmaciones dobles (salvo lo que rompe algo,
   `00_TIPOS_DE_ENCARGO.md` §3).
4. El encargo aceptado entra en el **registro** (Crónica/`../interfaz/05_LIBRO_MAYOR.md`) con su
   **plazo**.

- **Nada de listas de 30 misiones:** el tablón muestra **pocas y de sitio**. Menos es más.

---

## 3. Encargos que van a por ti

- **Por la marca:** el que te ve llegar con la marca del cadalso sabe que **cobras**; las casas
  te buscan a ti (`cobrar`, `vengar`).
- **Por la Firma:** un Hiena recibe ofertas que un Palabra dada no vería (y al revés).
- **Por la memoria:** quien te debe un favor o te tiene rencor te busca **por tu nombre**
  (`../sistemas/00_MEMORIA_Y_DEUDA.md`, `03_FAVORES.md`).
- **Por el mundo vivo:** las casas publican y retiran encargos sin ti
  (`../sistemas/09_TIEMPO_Y_MUNDO_VIVO.md`).

---

## 4. Plazos y caducidad

- Cada encargo trae su **plazo en días de juego** (`00_TIPOS_DE_ENCARGO.md` §1).
- **Al caducar:** el encargo se cae, **lo coge otro** (el mundo sigue) y tú pierdes el pago — no
  la partida. Si ya diste tu palabra, cuenta como **incumplimiento** (memoria, hecho 9 · −5).
- **Sin prórroga por oro** salvo que el acreedor sea amigo (banda ≥ Amigo): entonces concede
  **+2 días** una vez.
- **Encargos de la columna** (`05_ENCARGOS_DE_LA_HISTORIA.md`) **no caducan**: esperan.

---

## 5. Rechazar sin romper la partida

- **Rechazar un encargo normal no cuesta nada** y no cierra puertas: otro lo cogerá.
- **Rechazar lo prometido sí cuesta** (memoria y, si hubo testigos, Firma).
- **Rechazar no bloquea:** nunca hay un encargo obligatorio que atasque; la columna se puede
  retomar porque **no caduca** (§4).

---

## 6. Cuántos caben

- **Hasta 5 encargos activos** a la vez; si aceptas un sexto, el registro te pide **cerrar uno**.
- El tablón **se renueva cada 3-7 días** de juego (RNG inyectado), y **nunca** repite el mismo
  encargo dos veces seguidas.

---

## 7. Datos, tipos y validación

- **Datos:** `data/tablones.json` — `{ lugar, publica, clases, cupo, refresco_dias, filtro }`.
- **Tipos:** `Tablon` en `js/data/game_types.js` (una sola vez, regla 4).
- **Validación:** esquema en `js/data/schemas.js` + cruce con `data/lugares.json` y
  `data/encargos.json` en `tools/validate_data.js`.
- **Sistema puro:** la publicación, el refresco y la caducidad viven en
  `js/systems/tablones.js`; sin DOM, sin reloj (día por `save.day`), RNG inyectado.
- **Tests:** `tests/tablones.test.js`, mínimo 3 casos (normal, borde, error): un encargo caducado
  no rompe el registro; no se superan 5 activos; el filtro de honor respeta la Firma.

---

## 8. Cifras que fija este documento

| Cifra | Valor |
|---|---|
| Encargos activos | máximo **5** |
| Tablón de aldea | 2-3 encargos · refresco 3-7 días |
| Posada / cruce | 1-2 encargos |
| Oficina del Escribano | filtro Firma ≥ Correcto |
| Prórroga | +2 días, una vez, con banda Amigo |
| Columna vertebral | **no caduca** |
| Coste de rechazar | 0 (salvo palabra dada) |

---

## 9. Qué entra en la demo (Fase 1) — y qué sigue

> **Hasta aquí la demo.** El **tablón** de cada sitio, el **portavoz** y la **oficina del
> Escribano** del Patio del Cadalso, con los 6 encargos del Acto I y el cupo de 5 activos.

> **Y sigue el juego completo.** La **casa que te busca** y los encargos por **Firma/marca** en
> todo el reino llegan con el mapa grande; el mismo cupo y el mismo refresco, sin rehacer nada.

---

## 10. Fuera de este documento

- Las clases de encargo → `00_TIPOS_DE_ENCARGO.md`
- El formato de datos → `02_ESTRUCTURA_DE_ENCARGO.md`
- Cadenas y rumores → `03_CADENAS_Y_RUMORES.md`
- Los encargos de la trama → `05_ENCARGOS_DE_LA_HISTORIA.md`
- Fichas de sitio → `../mundo/03_LUGARES.md`
