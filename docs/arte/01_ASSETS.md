# 01 · Assets — qué hay, qué falta y de quién es

**Estado:** ✅ **aprobado por el dueño (aprobación en bloque, 2026-09-30). Documento final.**

> **Solo material propio o libre con ficha** (regla 7 de `../../AGENTS.md`; originalidad total).
> La ficha vivirá en `../../art/AUTORES.md` (por crear) y las licencias en `../../THIRD_PARTY.md` (por crear). Aquí
> está **qué hay, qué falta y cómo entra lo nuevo**.

---

## 1. Los 10 modelos `.glb` de reserva (por producir)

| Fichero | Autor | Licencia | Uso previsto |
|---|---|---|---|
| `u_knight.glb` | KayKit | CC0 1.0 | Marcado / capitán (héroe y tropa pesada) |
| `u_barbarian.glb` | KayKit | CC0 1.0 | Bandido / mercenario |
| `u_rogue.glb` | KayKit | CC0 1.0 | Explorador / tropa ligera |
| `u_rogue_hooded.glb` | KayKit | CC0 1.0 | Aldeano / encapuchado |
| `u_mage.glb` | KayKit | CC0 1.0 | Escribano / PNJ de saber |
| `u_skeleton_warrior/minion/rogue/mage.glb` (4) | KayKit | CC0 1.0 | **Reserva** (criaturas/leyenda, no confirmados para la demo) |
| `u_fox.glb` | PixelMannen + tomkranis + AsoboStudio | CC0 + **CC-BY 4.0** | Animal (`../contenido/08_ANIMALES_Y_CRIATURAS.md`) |

- **Crédito CC-BY del zorro** conservado en créditos (`../../js/scenes/sc_creditos.js`); es
  **obligatorio**.
- **Cambio (enmienda 2026-10-02, estilo película):** los **5 humanos KayKit pasan a reserva de
  prototipo** — en el campo solo van cuerpos de **proporción humana** (§2b). Los esqueletos y el
  zorro no se tocan (fauna y leyenda: decisión del dueño, `../DECISIONES.md`).
- Los **orígenes** viven en `art/origen/` (gitignored) y se regeneran con
  `tools/descargar_assets3d.mjs`.

---

## 2. Lo que falta (y para cuándo)

| Falta | Para | Nota |
|---|---|---|
| **Aldeanos y oficios** (posadero, herrero, portavoz) | Demo | Variedad de humanos; en reserva se contemplan 5 clases |
| **Elenco con cara propia**: 16 GLB clave (12 relevantes + 4 capitanes) | Demo | ~13 MB; el **resto de los personajes** es **único por piezas modulares + `semilla`** (§2b, `00_ESTILO.md` §5, `../mundo/04_PNJ.md`) |
| **Retratos pintados** de los 16 clave (estilo película) | Demo | 2D generado + upscaler; **un solo retrato vale para ES y EN** (no ×2) |
| **Cuerpos de proporción humana en todos los personajes** | Demo | Sustituyen al cartoon de KayKit: 16 clave primero, después tropa y aldeanos |
| **Props del mundo** (leña, mojón, valla, carro) | Demo | `../mundo/07_PROPS_Y_VEGETACION.md` |
| **Estructuras** (casa, posada, puerta, empalizada) | Demo/Fase 2 | `../contenido/09_EDIFICIOS_Y_ESTRUCTURAS.md` |
| **Armas y escudos variados** | Demo | Modular para dar variedad |
| **Armas nuevas del herrero** (martillo, alabarda, hoz, mandoble) × **3 apariencias** | Demo | **12 modelos** (`../sistemas/15_FABRICACION_Y_RECETAS.md` §7) ✅ 2026-10-02 |
| **Animales y criaturas** (perro, caballo, lobo, cuervo) | Fase 4 | `../contenido/08_*`, `13_*` |
| **Heráldica de casas** | Fase 2 | `../contenido/15_ESTANDARTES_E_INSIGNIAS.md` |

- **Regla:** cada pieza nueva entra **con su ficha** (autor, licencia, enlace, fecha) **antes** de
  commitearse.

### 2b. Unicidad de los personajes (opción 3-B, 2026-10-02)

- El dueño quería **que todos los personajes fueran únicos**; **un GLB por personaje no cabe**
  (decenas de PNJ × ≤ 6 MB = cientos de MB, muy por encima de los ~90 MB de la demo).
- **Solución:** **únicos sin modelo nuevo** — cada PNJ combina **piezas modulares** (cuerpo,
  ropa, arma, color) con su **`semilla`** de `data/pnj.json` (`../mundo/04_PNJ.md`): misma
  semilla = mismo aspecto en toda la partida.
- **16 GLB propios** solo para los **clave** (los 12 relevantes + 4 capitanes), que es lo que se
  mira de cerca; el resto (aldeanos, patrullas) sale de las piezas modulares.
- Las **APIs de imagen no dan modelos 3D**: generan textura, no malla — el GLB de un personaje
  sigue siendo pieza modular o modelo propio, nunca una descarga de API.

**Los retratos (enmienda 2026-10-02, estilo película):** los **16 personajes clave** tienen
**retrato pintado** a la altura de una película medieval: la cara de cerca se resuelve **en 2D**,
no en 3D (el cuerpo 3D manda en el campo; el retrato manda en el bocadillo y el diálogo).

**Los cuerpos (misma enmienda):** **todos los personajes, de proporción humana** — el dueño pide
que **lo más realista sean las personas**, así que el cartoon de muñeco **no sale en pantalla**:

- **Primer lote (los 16 clave):** cuerpos de proporción real con texturas propias (piel, lana,
  cuero, óxido) generadas con el pipeline de §3.
- **Segundo lote:** tropa rasa, patrullas y aldeanos — **con el mismo sistema de cuerpos
  modulares + `semilla`** (§2b), no un modelo por persona.
- El **peso que suba** entra en el presupuesto de la demo **a revisar con la primera escena**
  (§3, gate del dueño).

- Se genera con la **API propia + upscaler** (§3), una vez, y **un retrato vale para ES y EN**
  (una imagen no se traduce): no multiplica idioma ni presupuesto.
- Peso propuesta: ≤ **200 KB** por retrato (16 ≈ 3 MB), **dentro** del presupuesto de la demo.
- Guardado local (`art/retratos/*.webp`), con ficha en `art/AUTORES.md`; **cero red** en
  ejecución.

---

## 3. Cómo entra un asset (pipeline)

1. **Buscar/crear** con licencia **CC0** o **CC-BY** (nada de activos de juegos de terceros).
2. **Descargar** a `art/origen/` con `tools/descargar_assets3d.mjs` (solo desarrollo).
3. **Recortar** con `tools/recortar_glb.mjs` (por crear) (quita huesos, mallas y clips que el juego no usa;
   **no altera el arte**) → `art/*.glb`.
4. **Ficha** en `art/AUTORES.md` + licencia en `THIRD_PARTY.md` si aplica.
5. **Carga** con `js/render/modelos3d.js` (por construir; GLB + aligerado); **vendorizado**, sin CDN.

**Camino de generación con IA (2026-10-02):** las piezas 2D nuevas (**retratos**, texturas,
portada, iconos, bocetos, decoración) se **generan con la API propia** (Cloudflare) + **upscaler**
del taller de herramientas del dueño, **siempre fuera de la ejecución**: el juego solo recibe el
fichero final, ya optimizado.

- La herramienta y su licencia entran en `art/AUTORES.md` **como cualquier otro asset**.
- **Las APIs de imagen no dan 3D (GLB)**: sirven para textura, portada, iconos y boceto; el modelo
  siguen siendo piezas modulares (§2b) recortadas con `tools/recortar_glb.mjs`.
- **Los buscadores de stock del taller quedan fuera de este juego** (Pexels/Pixabay/etc.): aquí
  manda la originalidad (regla 7); lo libre con ficha solo si se declara.

- **Presupuesto por asset:** un personaje ≤ **6 MB** recortado; el total de la demo **≤ ~90 MB**
  **incluido el audio ≤ 20 MB** (`02_AUDIO.md` §4) — la APK va a **~100 MB**, decisión del
  dueño 2026-10-02. Antes era 1 MB por personaje y 8 MB en total.
- 🟡 **2026-10-02:** el dueño **revisa estos topes al ver la primera escena de paisaje** (con su
  textura, su luz y su niebla reales); hasta entonces se mantienen como referencia.

---

## 4. Reglas de originalidad

- **Cero** nombres, textos o siluetas reconocibles de otros juegos.
- Los **esqueletos** quedan como **reserva**: si se usan, serán **criaturas/leyenda propias**
  (con nombre y mito de Valcoria), nunca «no-muertos» de otra franquicia.
- Los créditos **siempre** nombran al autor y la licencia de lo libre.
- Los assets **generados con IA** se declaran en su ficha (herramienta y fecha), igual que uno
  descargado: nada entra **sin dueño visible**.

---

## 5. Datos, tipos y validación

- **Datos (por crear):** `data/assets.json` — `{ id, fichero, autor, licencia, uso }`, espejo de `art/AUTORES.md` (por crear).
- **Tipos:** `Asset3D` en `js/data/game_types.js`.
- **Validación** (`tools/validate_data.js`): todo asset referenciado **existe en disco**
  (`art/`, `vendor/`) y **tiene ficha**; una referencia rota o sin licencia **falla**.
- **Tests (por escribir):** `tests/assets.test.js`: todo `.glb` de `art/` tiene fila; una referencia a un GLB
  faltante romperá la carga (cuando exista el cargador).

---

## 6. Cifras que fija este documento

| Cifra | Valor |
|---|---|
| Modelos de reserva (a producir) | **10** (~7 MB) |
| Elenco con GLB propio (demo) | **16** clave (~13 MB); el resto, modular + `semilla` ✅ 2026-10-02 |
| Retratos pintados (2D) | **16** · ≤ 200 KB c/u · 1 imagen vale ES+EN ✅ 2026-10-02 |
| Cuerpos de personaje | **proporción humana en todos**; KayKit cartoon → reserva ✅ 2026-10-02 |
| Licencias | CC0 1.0 · CC-BY 4.0 (zorro) |
| Peso por personaje | ≤ **6 MB** recortado ✅ 2026-10-02 |
| Total demo | ≤ **~90 MB** (incluido audio ≤ 20 MB; APK ~100 MB) ✅ 2026-10-02 |
| Terceros de código | Three.js r186 + loaders (MIT) |
| Red en ejecución (prevista) | **0** (todo se vendorizará) |

---

## 7. Qué entra en la demo (Fase 1) — y qué sigue

> **Hasta aquí la demo.** Los modelos de reserva + los **16 personajes clave** (por modelar) con cara propia y
> **retrato pintado**, los **aldeanos/oficios** (modulares + semilla), los **props** y las
> **estructuras** mínimas de los 6 sitios, todos con ficha y licencia.

> **Y sigue el juego completo.** Animales, monturas, heráldica y criaturas se añaden **con el
> mismo pipeline y las mismas reglas** de licencia; crecer = más filas con ficha, no un asset
> sin dueño.

---

## 8. Fuera de este documento

- Estilo y paleta → `00_ESTILO.md`
- Audio → `02_AUDIO.md`
- Animaciones → `03_ANIMACIONES.md`
- Fichas de autoría → `../../art/AUTORES.md` y `../../THIRD_PARTY.md` (por crear)
