# 03 · i18n y tono — cómo se escribe Valcoria

**Estado:** ✅ **aprobado por el dueño (aprobación en bloque, 2026-09-30). Documento final.**

> Todo texto visible nace **en ES y EN a la vez** (regla 10 de `../../AGENTS.md`) y pasa por una
> clave `txt_*` (el motor `js/core/i18n.js` y `t(clave)` ya existen). Aquí están **la voz, el
> tamaño y el estilo** de esos textos.

---

## 1. La voz del juego

1. **Sobria y concreta:** fecha, nombre y sitio. Sin épica prestada ni adjetivos de relleno.
2. **La ley está en la boca de todos:** se habla de deudas, cuentas y marcos como del tiempo.
3. **Nadie da discursos:** una idea por línea; si hace falta más, se parte.
4. **El tono no juzga:** el mundo describe; el jugador decide (`../historia/00_PREMISA.md`).
5. **Tú eres un deudor, no un héroe:** la voz trata al jugador como un hombre con marca, no como
   un elegido.

---

## 2. Esquema de claves `txt_*`

| Prefijo | Para |
|---|---|
| `txt_esc_<escena>_<n>` | Columna vertebral (`../historia/04_GUION.md`) |
| `txt_ui_*` | Botones, menús, opciones |
| `txt_hud_*` | HUD de exploración y batalla |
| `txt_mem_*` | Reacciones de memoria |
| `txt_enc_*` / `txt_enc_hist_*` | Encargos (`../misiones/*`) |
| `txt_mundo_*` | Carteles, lápidas, cartas |
| `txt_cron_*` | Crónica |
| `txt_rumor_*` / `txt_aviso_*` | Rumores y avisos |
| `txt_lugar_*` / `txt_npc_*` | Fichas de sitio y de PNJ |

- **`snake_case`, sin mayúsculas ni espacios.** Una clave no se reutiliza con dos sentidos.

---

## 3. Paridad ES/EN (obligatoria)

- Toda clave nace **en `strings_es.json` y `strings_en.json` en el mismo commit**.
- `npm run validate` falla si falta una pareja (`validateStringsPair`); `npm run qa` no pasa.
- **El ingles conserva el tono**, no la sintaxis: no se traduce palabra por palabra; se traduce
  **voz**.
- **Nada de texto fuera de clave:** ni un cartel, ni un error de sistema.
- **El audio sigue al texto (2026-10-02):** toda **voz pre-generada** existe **en ES y EN** con
  la misma clave (`../arte/02_AUDIO.md` §1); una clave marcada como hablada sin su pareja de
  audio **falla** el validador igual que una clave de texto sin traducir.

---

## 4. Tamaño y formato

- **Máximo 2 líneas** por bocadillo; **≤ 90 caracteres** por línea (móvil).
- **Números en cifras** (`20 marcos`, `Día 12`), no en palabras.
- **Nada de comillas raras** ni emojis en los textos de juego.
- **Los nombres propios no se traducen** (Valcoria, Altamir, Doña Sira); sí sus títulos cuando
  proceda.

---

## 5. Glosario de términos (una sola vez)

| Término | Qué es (y qué **no**) |
|---|---|
| **Héroe** | El jugador, una unidad más del campo (`../batalla/00_REGLAS.md` §4) |
| **Marcado** | Tropa reclutada: deudor que paga sirviendo |
| **Unidad** | Cualquier combatiente, tuyo o enemigo |
| **Capitán / cabecilla** | Enemigo con nombre y memoria (`../contenido/02_CAPITANES_Y_NEMESIS.md`) |
| **Compañero** | Aliado con ficha e historia propia (`../contenido/03_COMPANEROS.md`) |
| **Marco de sangre** | Unidad de deuda; 1 marco = 10 oro (`../sistemas/06_ECONOMIA.md`) |
| **Escribano de la Sangre** | Quien escribe las cuentas; autoridad de la Ordenanza |
| **Libro Mayor** | El registro del reino; su pantalla, en Fase 2 |

- El glosario **manda** sobre cualquier sinónimo suelto: no se usan dos palabras para lo mismo.

---

## 6. Dónde vive cada texto

- Las escenas de la columna → `../historia/04_GUION.md`.
- Reacciones, ruinas y carteles → `../historia/08_TEXTO_DEL_MUNDO.md`.
- Encargos → `../misiones/*`. Crónica → `../sistemas/04_CRONICA.md`.
- **Ninguna frase se escribe dos veces:** se compone desde plantillas (`string` con huecos).

---

## 7. Datos, tipos y validación

- **Datos:** `data/strings_es.json` / `strings_en.json` (paridad). Ya existe la infraestructura.
- **Tipos:** `Idioma` y `ClaveTexto` en `js/data/game_types.js`.
- **Validación:** `validateStrings` + `validateStringsPair` en `js/data/schemas.js` y
  `tools/validate_data.js`.
- **Tests:** `tests/i18n.test.js` (existente) + paridad de claves nuevas.

---

## 8. Cifras que fija este documento

| Cifra | Valor |
|---|---|
| Idiomas | **2** (ES, EN) con paridad obligatoria |
| Audio hablado | **2** idiomas, misma paridad que el texto ✅ 2026-10-02 |
| Líneas por bocadillo | ≤ 2 · ≤ 90 caracteres |
| Prefijos de clave | los de §2 |
| Glosario | 8 términos (§5) |
| Texto sin clave | **0** |

---

## 9. Qué entra en la demo (Fase 1) — y qué sigue

> **Hasta aquí la demo.** Las claves del prólogo, el Acto I, los 6 encargos y las 6 fichas de
> sitio, con **paridad ES/EN al 100 %** en texto y en voz (`../produccion/00_ALCANCE.md`).

> **Y sigue el juego completo.** Cada acto y cada catálogo nuevo **nace con su pareja EN**; el
> presupuesto del alcance (300-450 ×2) se ajusta al escribir, no se reescribe.

---

## 10. Fuera de este documento

- Las líneas de la trama → `../historia/04_GUION.md`
- El texto ambiental → `../historia/08_TEXTO_DEL_MUNDO.md`
- Cómo se pinta → `02_HUD.md`, `01_PANTALLAS.md`
- El motor i18n → `js/core/i18n.js`
