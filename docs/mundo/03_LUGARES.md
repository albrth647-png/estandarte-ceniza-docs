# 03 · Lugares — la ficha de cada sitio

**Estado:** ✅ **aprobado por el dueño (aprobación en bloque, 2026-09-30). Documento final.**

> `00_MAPA.md` decide la **estructura** del reino (5 zonas, 29 sitios, grafo). Aquí está la
> **ficha de cada sitio**: para qué sirve, quién vive y qué deuda tiene. Los nombres de esta
> ficha son **propuesta de diseño**; si el dueño los cambia, se anota en `../DECISIONES.md`.

---

## 1. La ficha (idéntica para los 29 sitios)

| Campo | Qué guarda |
|---|---|
| `id` | `snake_case` único (`vega_quemada`) |
| `tipo` | ciudad · villa · aldea · cruce · refugio |
| `zona` | La Marca del Sur · Ribera · Serranía · Altos · Tierra del Paso |
| `servicios` | posada, tablón, mercado, escribanía, herrero, establo, fuego |
| `gente` | ids de PNJ que viven ahí (cupo: 25 — `../sistemas/00_MEMORIA_Y_DEUDA.md` §8) |
| `deudas` | deudas **vivas** con las que arranca el sitio (a quién, cuánto, en qué forma) |
| `encargos` | encargos de su tablón (`../misiones/*`) |
| `terreno` | terreno de su campo de batalla (`../batalla/02_TERRENO.md`) |
| `atmosfera` | clave `txt_lugar_*` con la primera impresión |

Todo vivirá en `data/lugares.json` (por crear), validado por el validador (cruce con `zonas.json` y
`caminos.json`). **Si un sitio no tiene deudas, encargos o recursos, no existe**: se borra.

---

## 2. Los 6 sitios de la demo (Fase 1)

| Sitio | Tipo | Razón de ser | Su deuda viva |
|---|---|---|---|
| **Patio del Cadalso** | ciudad | Empiezas aquí: la sentencia, Doña Sira y tu primera marca | La Casa Altamir pagó la puerta abierta del Paso |
| **Vega Quemada** | aldea | Tu **primera cobranza**: gente que ni sabe quién eres | Un viejo que se fugó con el peaje |
| **Casar de la Nava** | aldea | **Reclutar** Marcados y escuchar al portavoz | La cuadrilla que se queda con lo de otros |
| **Herreruela** | aldea | **Comprar** y reparar; el trato barato de la marca | El herrero le debe a la escribanía |
| **Posada de la Deuda Blanca** | cruce (hito) | **Descansar**, rumores y el primer favor | La posadera guarda una deuda que nadie cobra |
| **Cruce de las Dos Sendas** | cruce (hito) | **Encuentros y emboscadas**: el campo de las batallas de camino | Patrulla de Altamir que cobra peaje sin derecho |

- **1 encargo por sitio = 6 encargos** (`../misiones/00_TIPOS_DE_ENCARGO.md`).
- **3 campos** de batalla: llanura del camino, aldea y bosque (`../batalla/02_TERRENO.md`).
- **12 PNJ con memoria completa** repartidos: 8 del elenco + 4 de mundo; el resto, memoria
  ligera (cupo 25 por sitio).

---

## 3. Los 28 sitios restantes (juego completo)

Ya están contados en `00_MAPA.md` §2 (1 ciudad, 4 villas, 16 aldeas, 4 cruces, 4 refugios).
Su ficha se escribe en la **Fase 2 en adelante**, con este mismo molde: nunca se inventa un
sitio sin su deuda viva.

---

## 4. Reglas duras

1. **Todo sitio se justifica con una deuda, un encargo o un recurso.**
2. Cada sitio tiene **al menos un PNJ que te recuerda** (memoria ligera) y los que son
   relevantes, completa.
3. El **terreno** del sitio decide su campo de batalla: no hay campos inventados.
4. Nombres y textos con claves `txt_lugar_*`, paridad ES/EN.

---

## 5. Qué entra en la demo (Fase 1)

Los **6** de §2, con sus deudas, encargos y gente. Ningún otro sitio se construye (alcance
§2.3); el formato de datos será el del juego completo.

---

## 6. Cifras que fija este documento

| Cifra | Valor |
|---|---|
| Sitios demo / completo | 6 / 29 |
| Encargos por sitio | 1 |
| Cupo de gente por sitio | 25 |
| PNJ de memoria completa en la demo | 12 |
| Campos de batalla en la demo | 2 |

---

## 7. Fuera de este documento

- Zonas, distancias y grafo → `00_MAPA.md`
- Rutinas y oficios de la gente → `04_PNJ.md`
- Los encargos → `../misiones/*`
- La ciudad entera → `11_CIUDADES.md`
