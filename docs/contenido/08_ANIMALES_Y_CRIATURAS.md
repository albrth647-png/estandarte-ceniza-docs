# 08 · Animales y criaturas — lo que no empuña nada

**Estado:** ✅ **aprobado por el dueño (aprobación en bloque, 2026-09-30). Documento final.**

> El mundo no solo tiene gente: tiene **bichos que dan ambiente, bestias que te atacan y una
> leyenda que quizá sea real**. Aquí están qué son, dónde salen y para qué sirven. Los encuentros,
> en `../mundo/02_VIAJE_Y_ENCUENTROS.md`; los modelos, en `../arte/01_ASSETS.md`; la caza como
> comida, en `../mundo/10_SUPERVIVENCIA_Y_DESCANSO.md`.
>
> **Fauna, ids y frecuencias son propuesta de diseño** (cambiables → `../DECISIONES.md`).

---

## 1. Animales del mundo (ambiente y economía)

| id | Animal | Dónde | Interactúa | Para qué |
|---|---|---|---|---|
| `perro` | Perro | Aldeas, posadas | Sí: te sigue, avisa | Compañía; avisa de emboscada |
| `caballo` | Caballo | Establos, caminos | Sí: monta PNJ | Transporte/mensajero (`13_MONTURAS_Y_TRANSPORTE.md`) |
| `buey` | Buey | Aldeas, carretas | Sí | Tira de la carreta (`13_*`) |
| `oveja` | Oveja | Prados | No (botín) | Cuero y grano (`05_RECURSOS_Y_MERCADO.md`) |
| `cabra` | Cabra | Serranía | No | Leche, cuero |
| `gallina` | Gallina | Corrales | No | Comida (`14_COMIDAS_Y_BEBIDAS.md`) |
| `gato` | Gato | Casas, graneros | No | Ambiente |
| `mula` | Mula | Caminos, mercaderes | Sí | Carga de convoy (`13_*`) |

- **Regla:** los animales de ambiente **nunca** son decorado puro si se pueden tocar: o dan un
  recurso o dan un aviso (coherente con «nadie es decorado»).
- **El perro** es el único que **entra en el campo** como unidad de apoyo ligera
  (`00_TROPAS.md` §3.4).

---

## 2. Animales peligrosos

| id | Bestia | Dónde | Peligro | Se caza por |
|---|---|---|---|---|
| `lobo` | Lobo | Bosque espeso, de noche | Ataca en manada de 2-4 | Cuero, carne |
| `jabali` | Jabalí | Arboleda, matorral | Embestida | Carne |
| `oso` | Oso | Serranía, ruina | Muy peligroso; nunca solo al principio | Cuero grueso |
| `cuervos` | Bandada de cuervos | Caminos, ruinas | No pelea: **delata** tu posición | Ambiente/aviso |

- **Son encuentros de viaje** (`../mundo/02_VIAJE_Y_ENCUENTROS.md` §2), no campos formales: se
  resuelven con el motor de campo si hay combate (`../batalla/00_REGLAS.md`).
- **Las bestias no rinden** como un ejército: se **espantan** o se cazan; no hay «4 salidas» con
  un lobo (`../sistemas/02_PRISIONEROS.md`).
- **El oso** es el único enemigo que **puede herir de gravedad** (da una **cicatriz de batalla**,
  `../sistemas/07_CICATRICES.md` §2) — nunca mata solo (Pilar 3).
- **Los cuervos** son el aviso clásico: donde se posan, hay cuerpos o una emboscada.

---

## 3. Criaturas (leyenda)

- **La leyenda:** en el **Paso del Juramento** dicen que se oyen los cuarenta que no cruzaron
  (`../historia/07_LEYENDAS_Y_RUMORES.md`). Lo que la gente llama **«Las Ánimas del Paso»** puede
  no ser un cuento.
- **`cri_animas` (Las Ánimas del Paso):** criaturas **de leyenda propia**, no «no-muertos» de otra
  franquicia (`../arte/01_ASSETS.md` §4). Se apoyan en los 4 GLB de esqueleto que hoy quedan como
  **reserva**.
- **✅ Decidido (2026-10-01): son 4 (`cri_animas`, «Las Ánimas del Paso») y sí matan.** Cuatro
  figuras que se levantan en el Paso del Juramento y **pelean de verdad**; solo en sitios de
  leyenda, nunca en la aldea ni en el camino corriente.
- **Entran en Fase 4** (`../historia/07_LEYENDAS_Y_RUMORES.md`).

> **Regla de originalidad (dura):** ninguna criatura copia silueta, nombre ni mito de otro juego
> (regla 8 de `../../AGENTS.md`). Si no tiene mito propio de Valcoria, no entra.

---

## 4. Qué se puede hacer con ellos

| Acción | Cómo | Qué da |
|---|---|---|
| **Cazar** | Encuentro o sigilo (`../mundo/01_EXPLORACION.md` §3) | Carne (raciones) y cuero |
| **Comerciar** | Vender cuero/carne en el mercado | Oro (`05_RECURSOS_Y_MERCADO.md`) |
| **Domesticar** | Solo con **perro** (y mula, Fase 4) | Apoyo o carga |
| **Espantar** | Antorcha o ruido | Evita el combate |

- **La caza es la comida del pobre:** sin oro, se come de lo que se caza
  (`../mundo/10_SUPERVIVENCIA_Y_DESCANSO.md` §1).
- **Nada de mascotas con nombre** en la demo (una cosa es el perro de apoyo, otra un compañero,
  `03_COMPANEROS.md`).

---

## 5. Arte y animación

- **Modelos:** el **zorro** ya existe (`art/u_fox.glb`, CC0 + CC-BY); perro, caballo, lobo y cuervo
  están en la lista de **falta** (`../arte/01_ASSETS.md` §2), Fase 4.
- **Animación:** 3 clips por bestia (idle, andar, atacar/morder); sin ragdoll
  (`../arte/03_ANIMACIONES.md` §4).
- **Sin sombra propia** salvo el héroe y props cercanos (`../arte/00_ESTILO.md` §3).
- **Crédito del zorro** obligatorio en créditos: CC-BY (`../produccion/06_LEGAL_Y_AUTORIA.md`).

---

## 6. Cómo aparecen sin volverse ruido

- **Dónde:** los animales de ambiente **viven en su sitio** (semilla por zona,
  `../mundo/07_PROPS_Y_VEGETACION.md` §2); las bestias salen en la **tabla de encuentros**
  (`../mundo/02_VIAJE_Y_ENCUENTROS.md` §2).
- **Cuándo:** las bestias, de **noche** o en bosque espeso; de día, casi nunca (`§2`).
- **Cuántas:** máximo **1 encuentro de bestias por día de juego**, y **nunca** dos seguidos
  (RNG inyectado, determinista).
- **La leyenda** no sale por azar: solo en **sitios de leyenda** y tras haber oído el rumor
  (`../sistemas/04_CRONICA.md`).

---

## 7. Datos, tipos y validación

- **Datos:** `data/animales.json` — `{ id, tipo (ambiente/peligro/criatura), donde, peligro,
  caza, domestica, modelo }`.
- **Tipos:** `Animal` y `Criatura` en `js/data/game_types.js` (una sola vez, regla 4).
- **Validación:** esquema en `js/data/schemas.js` + cruce del `modelo` con `data/assets.json`
  (ficha y licencia) y de la `zona` con `data/lugares.json` en `tools/validate_data.js`.
- **Sistema puro:** `js/systems/animales.js` — aparición, caza y espanto; sin DOM, sin reloj (día
  por `save.day`), RNG inyectado.
- **Tests:** `tests/animales.test.js`, mínimo 3 casos (normal, borde, error): no sale una bestia en
  la aldea; no hay dos encuentros de bestias seguidos; un animal sin modelo en disco rompe la carga.

---

## 8. Cifras que fija este documento

| Cifra | Valor |
|---|---|
| Animales de ambiente | **8** |
| Animales peligrosos | **4** |
| Criaturas de leyenda | **1** tipo · `cri_animas` · **4** unidades · **matan** ✅ |
| Clips por bestia | 3 (sin ragdoll) |
| Encuentros de bestias | ≤ 1/día · nunca 2 seguidos |
| Bestias que rinden | **ninguna** (se espantan o se cazan) |
| Modelo existente | zorro (CC0 + CC-BY) |

---

## 9. Qué entra en la demo (Fase 1) — y qué sigue

> **En la demo:** la **oveja/gallina de aldea** y **los cuervos** solo como **decoración**
> (`../mundo/07_PROPS_Y_VEGETACION.md`), sin comportamiento propio.
> **Fuera (Fase 4):** el **perro** de apoyo y aviso, las bestias y las criaturas — este sistema
> **no se construye** en el Acto I (recorte de `../produccion/00_ALCANCE.md` §5, 2026-10-02).

> **Y sigue el juego completo.** Lobos, jabalíes, osos, mulas, caza y **Las Ánimas del Paso**
> (Fase 4) se añaden **con estas mismas reglas**: crecer = más filas en `animales.json` con su
> ficha de asset, no un sistema nuevo.

---

## 10. Fuera de este documento

- Encuentros y viaje → `../mundo/02_VIAJE_Y_ENCUENTROS.md`
- Comida y caza → `../mundo/10_SUPERVIVENCIA_Y_DESCANSO.md`, `14_COMIDAS_Y_BEBIDAS.md`
- Modelos y licencias → `../arte/01_ASSETS.md`
- Animaciones → `../arte/03_ANIMACIONES.md`
- Monturas y transporte → `13_MONTURAS_Y_TRANSPORTE.md`
- Leyendas → `../historia/07_LEYENDAS_Y_RUMORES.md`
