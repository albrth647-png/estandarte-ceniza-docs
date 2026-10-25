# 09 · Códice y bestiario — lo que descubres de Valcoria

**Estado:** ✅ **aprobado por el dueño (2026-10-01, ronda 4-A). Documento final.**

> La Crónica (`../sistemas/04_CRONICA.md`) escribe **lo que te pasó**; el **Códice** reúne **lo que
> el mundo es** y lo que has ido conociendo: lugares, gente, casas, criaturas y leyendas. Es
> **conquista, no catálogo**: todo empieza vacío y **se llena mirando, hablando y peleando**. El
> bestiario es la sección de las criaturas. **Cifras de este documento son propuesta de diseño**
> (cambiables → `../DECISIONES.md`).

---

## 1. Qué es (y qué no)

- **Es:** una pantalla de consulta con **5 secciones** (§2), dentro del Registro
  (`../interfaz/05_LIBRO_MAYOR.md` no cambia; el Códice es **una pestaña más del Registro**, no una pantalla
  nueva, `01_PANTALLAS.md`).
- **No es:** un diario (eso es la Crónica), un logro (`../produccion/12_LOGROS_Y_ESTADISTICAS.md`)
  ni una wiki del menú principal.
- **Empieza vacío:** en una partida nueva hay **0** fichas. Lo que no has visto, no está.
- **Nunca enseña números crudos:** el Códice cuenta **en palabras** («aguanta las cargas»,
  «huella en la ceniza»); las cifras siguen viviendo en `../batalla/01_CIFRAS.md`.

---

## 2. Las 5 secciones

| Sección | Qué reúne | Cómo se llena |
|---|---|---|
| **Lugares** | Los sitios que has pisado | Entrar en el sitio (nodo del grafo) |
| **Gente** | Personajes con los que hablaste | Terminar **1 diálogo** con ellos |
| **Casas** | Las casas y facciones | Trato o mención con **1 miembro** |
| **Bestiario** | Criaturas y bandas | **Ver** a la criatura (no hace falta matarla) |
| **Leyendas** | Lo que se cuenta de Valcoria | Oír la leyenda (rumor, cartel o copla) |

- **La entrada es por hecho, no por menú:** no hay botón «registrar»; el mundo lo hace solo.
- **Idéntica en ES y EN** (regla 10): cada ficha nace con sus dos textos.

---

## 3. Las fichas (el molde único)

Toda ficha, de cualquier sección, tiene **exactamente esto**:

| Campo | Contenido | Tope |
|---|---|---|
| **Nombre** | el del lugar/personaje/casa/criatura | 1 línea |
| **Qué es** | 1 frase | ≤ 90 caracteres |
| **Lo que importa** | 1 frase con la que **juegas** (deuda, terreno, miedo, trueque) | ≤ 90 caracteres |
| **Tu trato** | cómo te ve a ti (si se conoce) | 1 frase o vacío |

- **El bestiario añade 2 campos:** «dónde vive» y «qué le frena» (en palabras: «el fuego lo
  espanta», «la carga lo abate» — remite a `../batalla/02_TERRENO.md`, sin cifras).
- **Sin spoiler:** una ficha **nunca** cuenta finales, tramas futuras ni números de recompensa.
- **Marca de conocimiento:** si solo has **oído** de algo (rumor), la ficha se crea **a medias**
  con la marca «de oídas»; al verlo/personalmente, se completa.

---

## 4. Cuánto cabe (presupuesto)

| Cota | Valor | Motivo |
|---|---|---|
| Fichas del **juego completo** | **≤ 120** | legible de un vistazo |
| Fichas de la **demo** | **≤ 30** | el Acto I y sus alrededores |
| Secciones | **5** | ninguna se añade sin decisión en `../DECISIONES.md` |
| Texto por ficha | ≤ **4** líneas | el texto cuesta ×2 (ES/EN) |
| Peso | ≤ **80 KB** por idioma | entra en el techo del Registro/Libro Mayor |

- El bestiario de la demo cuenta con las criaturas que **aparecen** en ella
  (`../contenido/01_ENEMIGOS.md`, `../contenido/08_ANIMALES_Y_CRIATURAS.md`).

---

## 5. Dónde se abre

- **Desde el Registro** (pestaña «Códice»), que ya es una tecla en el HUD
  (`01_PANTALLAS.md` §1): Registro → Códice → sección → ficha. **2 toques** como cualquier otra
  acción (`../interfaz/00_CONTROLES.md`).
- **Fuera de batalla:** igual que el Libro Mayor; el mundo sigue detrás (sin pausa total,
  `01_PANTALLAS.md` §4).
- **Aviso de novedad:** al descubrir la primera ficha de una sección, un aviso de sistema (3 s):
  «El Códice ha crecido» (`../interfaz/07_AVISOS_Y_RUMORES.md`). Solo la primera.

---

## 6. Datos, tipos y validación

- **Datos (por crear):** `data/codice.json` — `{ id, seccion, nombre_txt, que_es_txt, importa_txt, trato_txt,
  extra }`; los textos se sirven por clave `txt_codice_*` con paridad ES/EN (regla 10).
- **Tipos:** `CodiceFicha` y `CodiceSeccion` en `js/data/game_types.js` (regla 4).
- **Sistema puro:** `js/systems/codice.js` — qué fichas están **descubiertas** (hecho → ficha),
  completo o «de oídas»; sin DOM, sin reloj; los hechos entran por parámetro.
- **Guardado:** el códice entrará en el guardado de forma **aditiva** (,
  `../produccion/02_GUARDADO_Y_DATOS.md`); un códice vacío nunca rompe la carga.
- **Validación:** esquema en `js/data/schemas.js` + cruce de `seccion` con las 5 válidas y de
  paridad ES/EN en `tools/validate_data.js`.
- **Tests (por escribir):** `tests/codice.test.js`, mínimo 3 casos (normal, borde, error): entrar en un sitio
  descubre su ficha una sola vez; un rumor marca «de oídas» y verlo completa; una sección
  desconocida se rechaza.

---

## 7. Cifras que fija este documento

| Cifra | Valor |
|---|---|
| Secciones | **5** (lugares · gente · casas · bestiario · leyendas) |
| Fichas juego completo | **≤ 120** |
| Fichas demo | **≤ 30** |
| Texto por ficha | **4** líneas máximo |
| Empieza con | **0** fichas |
| Pantalla nueva | **0** (pestaña del Registro) |
| Toques hasta una ficha | **2** |
| Peso | ≤ **80 KB**/idioma |

---

## 8. Qué entra en la demo (Fase 1) — y qué sigue

> **Fuera de la demo (Fase 2).** El Acto I se lee con el **Registro simple** de
> `../interfaz/05_LIBRO_MAYOR.md` (Crónica, deudas y favores): el **códice** completo — sus 5
> secciones y su pestaña — se construye en el Acto II (recorte de `../produccion/00_ALCANCE.md`
> §5, 2026-10-02).

> **Y sigue el juego completo.** Las mismas 5 secciones crecen hasta **≤ 120 fichas** a medida que
> se abre el mapa: crecer = **más filas en la tabla del códice**, no secciones nuevas ni otro sistema.

---

## 9. Fuera de este documento

- Lo que te pasó (diario) → `../sistemas/04_CRONICA.md`
- Deudas, favores y rencores → `../interfaz/05_LIBRO_MAYOR.md`
- Leyendas como contenido → `07_LEYENDAS_Y_RUMORES.md`
- Texto del mundo (carteles, coplas) → `08_TEXTO_DEL_MUNDO.md`
- Enemigos y criaturas (catálogo jugable) → `../contenido/01_ENEMIGOS.md`, `../contenido/08_ANIMALES_Y_CRIATURAS.md`
- Logros y estadísticas → `../produccion/12_LOGROS_Y_ESTADISTICAS.md`
- Dónde vive el Registro → `../interfaz/01_PANTALLAS.md`
