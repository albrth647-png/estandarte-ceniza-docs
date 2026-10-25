# 07 · Artefactos y recompensas — las piezas que se recuerdan

**Estado:** ✅ **aprobado por el dueño (aprobación en bloque, 2026-09-30). Documento final.**

> Un **artefacto** no es «un ítem mejor»: es una **pieza única con historia y dueño anterior** que
> **cambia una regla** o **pesa en la balanza** de la asamblea. El equipo común, en
> `04_ITEMS_Y_EQUIPO.md`; su rastro narrativo, en `../sistemas/04_CRONICA.md`; los tres finales, en
> `../sistemas/11_DEUDAS_DEL_JUGADOR.md`.
>
> **Artefactos, ids y efectos son propuesta de diseño** (cambiables → `../DECISIONES.md`).

---

## 1. Qué es un artefacto (y qué no)

1. **Único:** solo existe uno de cada; no se compra ni se duplica.
2. **Con dueño anterior:** siempre tuvo un dueño, una casa o un muerto que lo reclama.
3. **Cambia una regla o pesa en un juicio:** no da +2 de ataque. Da una **puerta** o un **voto**.
4. **Con rastro:** quién lo quiere, quién lo llora y quién lo reclama va escrito en la Crónica
   (`../sistemas/04_CRONICA.md`).

- **Nunca** es una pieza de botín aleatoria (`11_TABLAS_DE_BOTIN.md`): se **gana** (§3).
- La **`nombrada`** de `04_ITEMS_Y_EQUIPO.md` §2 es la categoría de rareza; el **artefacto** es la
  pieza con historia de este documento (puede ser también `nombrada`).

---

## 2. Las piezas (propuesta)

| id | Artefacto | Qué es | Efecto (regla) | Dueño anterior |
|---|---|---|---|---|
| `art_sello_mayor` | **El sello del Escribano Mayor** | Sello del Libro | Abre la **Escribanía** y permite **1 enmienda gratis** | El Maestro Ambrosio |
| `art_contrato_altamir` | **El contrato robado** | Contrato que Altamir quemó | **Prueba** en la asamblea (voto de la Escribanía) | Casa Altamir |
| `art_estandarte_cuarenta` | **El estandarte de los cuarenta** | Bandera de la Compañía del Paso | Tus **Marcados** empiezan con **+10 de moral** en el campo | Los cuarenta (muertos) |
| `art_paginas` | **Las páginas arrancadas** | Hoja del Libro Mayor | Abre el **Acto II** (la verdad de la puerta) | El Teniente |
| `art_espada_beltran` | **La espada de Beltrán** | La del capitán muerto | Cierra la **deuda de Sira** (`../sistemas/11_DEUDAS_DEL_JUGADOR.md` §1) | Doña Sira |
| `art_marca_borrada` | **La marca borrada** | Piel de un Escribano perdonado | Un PNJ de banda **Verdugo** pasa a **Hostil** (una vez) | El Escribano que huiste |

- **El sello, el contrato y las páginas** son **de trama**: sin ellos no se cierra bien un acto
  (`../historia/01_ESTRUCTURA.md`).
- **El estandarte** es el único que **da combate**, y lo da a **convicción**, no a daño.
- **La marca borrada** es un artefacto de **misericordia**: sirve para no cerrar puertas del todo
  (Pilar 3: *el fallo nunca atasca*).

---

## 3. Cómo se ganan

| Vía | Ejemplo | Referencia |
|---|---|---|
| **Batalla** | Recuperar el contrato del arcón de un capitán | `../batalla/00_REGLAS.md` §9 |
| **Rescate / perdón** | El Escribano que perdonaste te deja el sello | `../sistemas/02_PRISIONEROS.md` §4 |
| **Favor cobrado** | Un contacto te entrega las páginas | `../sistemas/03_FAVORES.md` §4 |
| **Hallazgo** | En una ruina o un contenedor señalado | `11_TABLAS_DE_BOTIN.md` |
| **Decisión de la asamblea** | Te lo concede una facción | `../sistemas/11_DEUDAS_DEL_JUGADOR.md` §3 |

- **Botín señalado:** un artefacto sale **solo si hiciste algo** (perdonaste, llegaste antes,
  cumpliste). No cae por RNG puro (`11_TABLAS_DE_BOTIN.md` §3).
- **Nunca bloquea:** si pierdes una puerta a un artefacto, hay **otra** para la misma trama
  (el contrato tiene copia, el sello tiene testigo).

---

## 4. Trofeos contables vs. piezas que cambian reglas

| Tipo | Qué hace | Ejemplo |
|---|---|---|
| **Trofeo** | Vale **oro y respeto**; se puede empeñar o mostrar | Una enseña de casa tomada |
| **Pieza que cambia reglas** | Abre puertas, suma votos o da moral | El sello, el contrato, el estandarte |

- **Los trofeos no dan stats** y **no ocupan hueco de mochila**: van al **estante** (§6).
- Un trofeo puede **venderse** (`05_RECURSOS_Y_MERCADO.md`) — con **memoria en contra** de su casa
  (`../sistemas/00_MEMORIA_Y_DEUDA.md` §4).

---

## 5. Cuántos caben y cómo se guardan

| Cota | Valor |
|---|---|
| Artefactos en el juego completo | **6** |
| Estante (huecos de artefacto) | **6** (no ocupa mochila) |
| Peso | **0** (no es carga, `04_ITEMS_Y_EQUIPO.md` §5) |
| Guardado | ids en `SaveState.artefactos`; **nada de duplicados** |

- **Regla dura:** ningún artefacto de trama ocupa una plaza que pueda **bloquear** otra cosa
  (`../produccion/02_GUARDADO_Y_DATOS.md`). El estante nunca se llena de basura.
- **Las páginas** se guardan como **bandera** (`paginas_arrancadas`, `../historia/04_GUION.md`) y
  también como artefacto: el guion manda.

---

## 6. Su rastro narrativo

- Cada artefacto **entra en la Crónica** al ganarse, con su dueño anterior
  (`../sistemas/04_CRONICA.md` §2).
- **Quién lo quiere:** una casa, un heredero o un Escribano puede **reclamarlo** y volver a por él
  (`02_CAPITANES_Y_NEMESIS.md` §5).
- **Quién lo llora:** el objeto de un muerto pesa en la memoria de su casa
  (`../sistemas/00_MEMORIA_Y_DEUDA.md` §7).
- **Devolverlo** puede valer más que quedárselo: un favor, una enmienda, un voto
  (`../sistemas/03_FAVORES.md`).

---

## 7. Datos, tipos y validación

- **Datos (por crear):** `data/artefactos.json` — `{ id, nombre_txt, efecto, dueno, via, unico, trama }`.
- **Tipos:** `Artefacto` en `js/data/game_types.js` (una sola vez, regla 4).
- **Validación:** esquema en `js/data/schemas.js` + cruce de los artefactos `trama` con las
  banderas de `../historia/04_GUION.md` (p. ej. `paginas_arrancadas`) en `tools/validate_data.js`.
- **Sistema puro:** `js/systems/artefactos.js` — concede, consulta y aplica el efecto de regla; sin
  DOM, sin reloj.
- **Tests (por escribir):** `tests/artefactos.test.js`, mínimo 3 casos (normal, borde, error): un artefacto único
  no se duplica; el estandarte da +10 de moral; perder una vía de trama no deja la partida sin
  cierre.

---

## 8. Cifras que fija este documento

| Cifra | Valor |
|---|---|
| Artefactos | **6** |
| Estante | 6 huecos · peso 0 |
| Que dan combate | **1** (el estandarte: +10 moral a los Marcados) |
| Que cambian reglas / pesan | 5 |
| Vías de obtener | **5** (§3) |
| Duplicados | **no** |

---

## 9. Qué entra en la demo (Fase 1) — y qué sigue

> **En la demo:** los **2 objetos de historia** — el **estandarte de los cuarenta** (botín del
> cierre del Acto I) y **las páginas arrancadas** (el giro final, `../historia/04_GUION.md`) —,
> como **objetos corrientes** de `04_ITEMS_Y_EQUIPO.md`, **sin** efecto de regla.
> **Fuera (Fase 5):** el **estante**, el efecto de regla y el resto de artefactos (recorte de
> `../produccion/00_ALCANCE.md` §5, 2026-10-02).

> **Y sigue el juego completo.** El sello, el contrato, la espada de Beltrán y la marca borrada se
> añaden **con estas mismas reglas y este mismo estante**: crecer = más filas en
> `artefactos.json`, no un sistema nuevo.

---

## 10. Fuera de este documento

- Equipo y rarezas → `04_ITEMS_Y_EQUIPO.md`
- Botín y probabilidades → `11_TABLAS_DE_BOTIN.md`
- Crónica y memoria → `../sistemas/04_CRONICA.md`, `../sistemas/00_MEMORIA_Y_DEUDA.md`
- Favores → `../sistemas/03_FAVORES.md`
- Los finales y la asamblea → `../sistemas/11_DEUDAS_DEL_JUGADOR.md`
- Banderas y guion → `../historia/04_GUION.md`, `../historia/01_ESTRUCTURA.md`
