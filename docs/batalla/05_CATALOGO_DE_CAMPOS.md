# 05 · Catálogo de campos — los escenarios concretos

**Estado:** ✅ **aprobado por el dueño (aprobación en bloque, 2026-09-30). Documento final.**

> `02_TERRENO.md` dice **cómo** el terreno forma el campo; este documento lista **los campos
> concretos** que pueden abrirse en el reino. Todos nacen del terreno del tramo (§4 de
> `../mundo/02_VIAJE_Y_ENCUENTROS.md`) y **ninguno se inventa** (`02_TERRENO.md` §8).

---

## 1. Las seis plantillas

| id | Campo | Terreno base | Cobertura media | Carga | Ancho de paso |
|---|---|---|---|---|---|
| `llanura_camino` | **Llanura de camino** | Camino real / tierra | 0 | **Sí** | abierto |
| `bosque` | **Bosque espeso** | Bosque espeso / arboleda | 3 | No | estrecho |
| `aldea` | **Aldea** | Tierra / rocío + props | 1-2 | Sí (calles) | medio |
| `vado_orilla` | **Vado / orilla** | Vado / rocío | 1 | No | 1,5 m |
| `puerta_ciudad` | **Puerta de ciudad** | Muralla / escalera | 2 | No | 1,5 m |
| `ruina` | **Ruina** | Roca / pedral + escombros | 2 | No | medio |

- Cada plantilla usa los **efectos de `02_TERRENO.md`** tal cual; aquí solo se eligen **forma y
  puntos de interés**.

---

## 2. Puntos de interés por campo (≤ 4, `02_TERRENO.md` §9)

| Campo | Puntos típicos |
|---|---|
| Llanura de camino | Mojón/estaca · carro volcado · valla |
| Bosque | Árbol caído · tronco (leña) · seto espeso |
| Aldea | Puerta · carro · fuego/hogar · empalizada |
| Vado / orilla | Vado · cañas · puente (si hay) |
| Puerta de ciudad | Portón · escalera · almena |
| Ruina | Muro caído · escombro · hogar frío |

- **Siempre hay salida:** ningún campo cierra su única salida (§9 de `02_TERRENO.md`).

---

## 3. Qué campo sale en cada sitio/zona

- El campo **sale del terreno del tramo** (no se elige a mano): al abrirse una batalla,
  `js/systems/campo.js` (por construir) tomará el terreno dominante y elegirá la plantilla (§1).
- **Por zona:** Marca del Sur → `llanura_camino`, `aldea`; Ribera → `vado_orilla`; Serranía →
  `bosque`, `ruina`; Altos → `bosque`, `puerta_ciudad`; Tierra del Paso → `ruina`, `bosque`.
- **Variedad sin repetir:** con la **semilla de la partida** se colocan manchas y puntos de interés
  (`02_TERRENO.md` §8): mismo tramo, mismo campo.

---

## 4. Tamaño y escala

- **Escala del campo:** 10+10 unidades del Pilar 6 caben en **~120 × 120 m** con la vista de 60 m
  (`02_TERRENO.md` §6); los campos estrechos (vado, puerta) usan **pasillos** de 1,5 m.
- **Duración objetivo:** 90-240 s (`01_CIFRAS.md` §6) — el tamaño no debe alargar la pelea, solo
  darle forma.

---

## 5. Datos, tipos y validación

- **Datos (por crear):** `data/campos.json` — `{ id, terreno_base, cobertura, carga, ancho_paso, puntos }`.
- **Tipos:** `PlantillaCampo` en `js/data/game_types.js`.
- **Validación:** cada `terreno_base` existe en `data/terreno.json`; los `puntos` existen en
  `data/props.json` (`tools/validate_data.js`); ≤ 4 puntos.
- **Sistema puro:** `js/systems/campo.js` elige plantilla y siembra puntos; sin DOM ni reloj.
- **Tests (por escribir):** `tests/campos.test.js`: todo terreno mapea a ≥ 1 plantilla; nunca se superan 4 puntos;
  el campo estrecho no bloquea la salida.

---

## 6. Cifras que fija este documento

| Cifra | Valor |
|---|---|
| Plantillas | **6** |
| Puntos de interés | ≤ 4 por campo |
| Escala de campo | ~120 × 120 m |
| Pasillos estrechos | 1,5 m |
| Vista de campo | 60 m |
| Duración objetivo | 90-240 s |

---

## 7. Qué entra en la demo (Fase 1) — y qué sigue

> **Hasta aquí la demo.** **3 plantillas** (`../produccion/00_ALCANCE.md` §2.5): `llanura_camino`, `aldea` y
> `bosque`, con sus puntos de interés y estas reglas.

> **Y sigue el juego completo.** `vado_orilla`, `puerta_ciudad` y `ruina` se añaden **con el mismo
> formato de datos y las mismas reglas**; crecer = más filas en `campos.json`, no un motor nuevo.

---

## 8. Fuera de este documento

- Cómo el terreno forma el campo → `02_TERRENO.md`
- Reglas y fases → `00_REGLAS.md`
- Las batallas de la trama → `06_BATALLAS_DE_LA_HISTORIA.md`
- Props y vegetación → `../mundo/07_PROPS_Y_VEGETACION.md`
- Estructuras → `../contenido/09_EDIFICIOS_Y_ESTRUCTURAS.md`
