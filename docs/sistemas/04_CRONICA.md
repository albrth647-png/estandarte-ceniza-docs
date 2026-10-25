# 04 · Crónica — el diario autoescrito

**Estado:** ✅ **aprobado por el dueño (aprobación en bloque, 2026-09-30). Documento final.**

> La Crónica es **la novela de tu partida**: los sistemas guardan **enums** (memoria y Firma) y
> la Crónica los convierte en **prosa legible** para que veas tu historia con los nombres que
> tú mismo escribiste (`00_MEMORIA_Y_DEUDA.md` §2.2, `01_FIRMA.md` §4). No inventa nada: solo
> redacta lo que pasó.

---

## 1. Qué es (y qué no es)

- **Es** un **diario autoescrito**: cada día de juego deja su línea; los hechos importantes, su
  párrafo.
- **Es la voz de los que sobrevivan:** no la tuya, no la del narrador omnisciente. La cuenta
  «el que quedó para contarlo» — por eso cambia de tono según tu **Firma**.
- **No es** un registro de acciones ni un contador de daño: anota lo que **tiene nombre** (una
  persona, una deuda, un juramento). La Crónica no dice «mataste 12», dice **a quién**.

---

## 2. Qué anota

Solo hechos con **testigos o con nombre** (`00_MEMORIA_Y_DEUDA.md` §4, `01_FIRMA.md` §4):

| Se anota | Plantilla base (`txt_cron_*`) |
|---|---|
| **Batalla** (quién, dónde, cómo acabó) | «En <sitio>, <bando> se deshizo» |
| **Bajas** de tu gente (nombre y casa) | «Enterramos a <nombre>, de <casa>» |
| **Deudas** contraídas o cobradas | «Le pagamos a <nombre> lo que se le debía» |
| **Favores** concedidos y cobrados | «<nombre> nos debe una» |
| **Rescates y rendiciones** | «<nombre> volvió a casa, con las manos vacías» |
| **Ejecuciones** | «<nombre> no salió de <sitio>» |
| **Rencores** que nacen o se apagan | «La casa <casa> ya no nos saluda» |
| **Juramentos y encargos** cumplidos | «Prometimos <x>; lo hicimos» |
| **Resumen del día** | «Día <n>: <una línea>» |

- **Lo que no se ve, no se crónica:** igual que la Firma, un hecho sin testigos no entra.
- **Cada entrada guarda su `día`** y el **enum**; el texto se compone al leer, no al guardar.

---

## 3. Cómo lo escribe

- **Plantillas con huecos** por idioma: `strings_es.json` / `strings_en.json`, claves `txt_cron_*`
  con **paridad obligatoria** (regla 10). Ej.: `txt_cron_batalla = "En {sitio}, {bando} se deshizo."`.
- **Se rellenan con datos, no con texto libre:** `{nombre}`, `{casa}`, `{sitio}`, `{oro}` salen de
  las fichas; nunca de frases escritas a mano por el jugador.
- **Tres voces** según la banda de Firma (`01_FIRMA.md` §3):
  1. **Piadosa** (Palabra dada / Honrado): recuerda a los que perdonaste.
  2. **Neutra** (Correcto / Sin nombre / Duro): cuenta sin adjetivos.
  3. **Implacable** (Fiera / Hiena): cuenta a los que cayeron por tu mano, sin disculpa.
- **Un hecho, una línea:** la Crónica no repite; si algo se desborda, se **resume** (§4).

---

## 4. Tope de entradas (y qué se tira)

- **Tope: 200 entradas** en toda la partida · **≤ 64 KB** de `SaveState`.
- Al llenarse: los días sin hecho pasan a un **resumen por capítulo** (una línea cada 7 días); los
  hechos **capitales** (rescate, ejecución, rencor, final) **nunca se tiran**.
- **Prioridad al desbordar:** hechos *capitales* y con **nombre** > hechos de rango bajo > resumen.
- Igual que la memoria: se apaga el detalle, **nunca** la deuda ni el nombre de quien la tiene.

---

## 5. Dónde se lee

- **En la demo:** lista simple al abrir el registro (día + línea), con toque para ver el párrafo.
- **En el juego completo:** dentro del **Libro Mayor** (`../interfaz/05_LIBRO_MAYOR.md`), la
  pantalla del registro; se desliza para leer (`../interfaz/00_CONTROLES.md` §4).
- **Al final del acto** y en el **epílogo** (`../historia/01_ESTRUCTURA.md`): un cierre que
  recoge las entradas capitales de tu partida.

---

## 6. El tono

- **Sobria y concreta:** fechas, nombres y sitios. Sin épica prestada.
- **Con la mirada de los que quedan:** la Crónica juzga poco y recuerda mucho — igual que el
  mundo del juego.
- **Consistente con la Ordenanza:** una vida es una cuenta; la Crónica la apunta como tal.

---

## 7. Datos, tipos y validación

- **Guardado:** campo `cronica` (array de `{d, t, e}` — día, tipo, datos) en `SaveState` →
  `SAVE_VERSION` 3 (aditivo), junto a `memoria`, `firma` y `prisioneros`.
- **Tipos:** `EntradaCronica` y `VozCronica` en `js/data/game_types.js` (una sola vez, regla 4).
- **Validación:** esquema en `js/data/schemas.js` + paridad de `txt_cron_*` en `tools/validate_data.js`.
- **Sistema puro:** `js/systems/cronica.js` — compone el texto desde plantillas y enums; sin DOM,
  sin reloj (recibe `save.day`), RNG no lo necesita.
- **Tests:** `tests/cronica.test.js`, mínimo 3 casos (normal, borde, error): un hecho sin testigos
  no entra; el tope resume y no tira capitales; paridad ES/EN de las plantillas.

---

## 8. Cifras que fija este documento

| Cifra | Valor |
|---|---|
| Entradas | **200** por partida |
| Tamaño máximo | **≤ 64 KB** |
| Resumen al llenarse | 1 línea cada **7 días** |
| Voces | **3** (piadosa · neutra · implacable) |
| Hechos capitales | **nunca** se tiran |
| Claves | `txt_cron_*` con paridad ES/EN |

---

## 9. Qué entra en la demo (Fase 1) — y qué sigue

> **Hasta aquí la demo.** El diario con batallas, bajas, deudas, favores y rescates del Acto I,
> en **lista simple** y con la voz que corresponda a tu Firma (`../produccion/00_ALCANCE.md` §2.1).

> **Y sigue el juego completo.** El **Libro Mayor** como pantalla propia y el **epílogo** que
> cose las entradas capitales llegan con la Fase 2 y la Fase 3; la **misma estructura de datos**
> y las mismas plantillas, sin rehacer nada.

---

## 10. Fuera de este documento

- Los hechos y sus enums → `00_MEMORIA_Y_DEUDA.md`, `01_FIRMA.md`
- La pantalla donde se lee → `../interfaz/05_LIBRO_MAYOR.md`
- Recorrido y guion que la alimentan → `../historia/03_RECORRIDO.md`, `../historia/04_GUION.md`
- Avisos y recuerdos sueltos → `../interfaz/07_AVISOS_Y_RUMORES.md`
- Cómo se guarda → `../produccion/02_GUARDADO_Y_DATOS.md`
