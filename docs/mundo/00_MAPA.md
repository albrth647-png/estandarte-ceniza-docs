# 00 · Mapa — Valcoria por dentro y por fuera

**Estado:** ✅ **aprobado por el dueño (aprobación en bloque, 2026-09-30). Documento final.**

> Describe la **estructura** del reino (zonas, jerarquía, distancias y datos). La ficha de cada
> sitio vive en `03_LUGARES.md`; la forma de caminarlo, en `01_EXPLORACION.md`; el viaje entre
> zonas, en `02_VIAJE_Y_ENCUENTROS.md`. El alcance de la demo lo manda
> `../produccion/00_ALCANCE.md`.

---

## 1. La forma del reino

Valcoria es un reino pequeño y viejo, atravesado por el **río Ulia** y cerrado al norte por la
cordillera del **Paso del Juramento**. Cinco zonas:

| Zona | Carácter | Quién manda | Lo que ahí se juega | Banda de nivel |
|---|---|---|---|---|
| **La Marca del Sur** | Campos, aldeas y el camino real | Casas menores y la escribanía del **Patio del Cadalso** | La demo entera; los primeros encargos y la primera marca | **1 – 12** |
| **La Ribera** | Río, puentes, molinos y mercado fluvial | Mercaderes y gremios | Oro, contrabando y el trato más barato del reino | **12 – 24** |
| **La Serranía** | Pastos, hayedos y pasos de cabra | Pastoriles y crítos | Bandidos, contrabando y las mejores emboscadas | **24 – 36** |
| **Los Altos de Altamir** | Feudos, cotos y torres | **Casa Altamir** | Las casas rivales, la caza y el peaje que se cobró | **36 – 48** |
| **La Tierra del Paso** | Frontera rota, ruinas y niebla | Nadie del todo: deudores y veteranos sueltos | El **Paso del Juramento**, los 40 muertos y los cierres de la historia | **48 – 60** |

- **La banda de nivel de cada zona fija el nivel de sus enemigos** (ajuste −1/0/+1 para el capitán);
  no escala contigo. Fórmula y reglas en `../sistemas/12_NIVELES_DEL_HEROE.md` §3.

- Cada zona tiene **1 plaza fuerte** (ciudad o villa) como sede de escribanía y mercado.
- El **Patio del Cadalso** es la única **ciudad** de la demo (ficha en `03_LUGARES.md`;
  su forma en `11_CIUDADES.md`).

---

## 2. Jerarquía de los sitios

| Tipo | Cuántos en el juego | Qué tiene siempre | Qué puede tener |
|---|---|---|---|
| **Ciudad** | 1 (Patio del Cadalso) | Muralla, escribanía, tablón, posada, mercado, plaza del cadalso | Taller, cárcel, corte |
| **Villa** | 4 (una por zona) | Escribanía menor, posada, tablón | Herrero, herrador, remendón |
| **Aldea** | 16 | Pozo, portavoz, alguna casa con deuda | Establo, molino, capilla |
| **Cruce / paso** | 4 | Señal, fuego, quizá un remendón | Posada de camino, puente |
| **Refugio** | 4 | Techo y fuego | Nada más |

- **Juego completo: 29 sitios.** La demo: **6** (§7).
- Regla: **ningún sitio está a menos de media jornada de otro, ni a más de 6** — el reino se
  cruza entero en una semana de juego.

---

## 3. Distancias (en días de juego)

| De ↓ a → | Aldea | Villa | Ciudad | Otra zona |
|---|---|---|---|---|
| Aldea | 1 | 1–2 | 2–3 | 4–6 |
| Villa | — | 1–2 | 1–2 | 3–5 |
| Ciudad | — | — | — | 3–5 |

- Todo viaje se mide en **días enteros** de juego (día de juego), no en minutos reales.
- El camino **real** (pavimentado) resta 1 día a los trayectos de más de 2; el **atajo** lo
  ahorra solo a pie y con encuentro seguro de emboscada (§5).

---

## 4. Cómo se representa (grafo, no rejilla)

El mapa del reino es un **grafo de nodos y aristas**, no un tablero:

- **Nodos** = lugares (`03_LUGARES.md`): `{ id, tipo, zona, x, y, visitado }`.
- **Aristas** = caminos: `{ a, b, dias, via, riesgo }` (`via`: real / tierra / atajo).
- La exploración a pie es **3D libre dentro del nodo**; el movimiento **entre** nodos es el
  viaje por días de `02_VIAJE_Y_ENCUENTROS.md`.
- `x, y` son solo para pintar el mapa y el minimapa; **no hay movimiento por coordenadas en el
  mundo simulado** (regla: la simulación no lee píxeles).

### Datos

| Fichero | Qué guarda | Quién lo valida |
|---|---|---|
| `data/zonas.json` | Las 5 zonas | `js/data/schemas.js` + `tools/validate_data.js` |
| `data/lugares.json` | Los 29 sitios | idem, más cruce de `zona` y de tipos |
| `data/caminos.json` | Las aristas con días y riesgo | idem, más cruce `a`/`b` contra `lugares.json` |

Todo con **rutas relativas** y validación obligatoria: sin validador en verde, no arranca
(reglas 3 y 5 de `../../AGENTS.md`).

---

## 5. Qué se encuentra en cada zona

- **Encuentros** (mercaderes, reclutadores, correos) → `02_VIAJE_Y_ENCUENTROS.md`.
- **Peligros** (emboscadas de las 3 familias enemigas) → `../contenido/01_ENEMIGOS.md`.
- **Deudas pendientes**: cada zona arranca con **deudas ya vivas** — a quién se le debe, quién
  cobró y a quién no; el jugador entra en un mundo que ya estaba en conflicto.
- **Terreno** (rocío, barro, nieve…) → `06_TERRENO_DEL_MUNDO.md`.
- El **Paso del Juramento** y la **Tierra de Ninguno** son la excepción: no hay autoridad, no
  hay escribano y la Ordenanza **no se cobra** — por eso huyó todo el mundo hacia allí.

---

## 6. Reglas duras del mapa

1. **Los 6 de la demo son un subconjunto exacto** del mapa completo: nada se diseña dos veces.
2. **Todo sitio tiene razón de ser**: si un lugar no da deudas, encuentros o recursos, se
   borra del `lugares.json` (criterio de terminado).
3. **Determinismo**: el mapa no cambia solo; solo cambia por hechos del jugador
   (`09_TIEMPO_Y_MUNDO_VIVO.md` para el mundo que se mueve).
4. **Sin coordenadas en la simulación**: posiciones de juego = nodo + arista.

---

## 7. Qué entra en la demo (Fase 1)

- **1 zona**: La Marca del Sur, con **6 sitios**: la ciudad del **Patio del Cadalso**, **3
  aldeas**, **1 tramo de camino** y **2 hitos** (posada y cruce) ocupando los nodos de esa
  zona — sin salir de ella.
- Camino real y un atajo; los otros 4 días de viaje no existen aún (se tocan en Fase 2).
- **Mismo formato de datos** que el juego completo: `lugares.json` y `caminos.json` con la
  lista recortada. Crecer = añadir filas, no rehacer.

---

## 8. Cifras que fija este documento

| Cifra | Valor |
|---|---|
| Zonas | 5 (1 en la demo) |
| Sitios completo / demo | 29 / 6 |
| Tipos de sitio | ciudad · villa · aldea · cruce · refugio |
| Distancia mínima / máxima | media jornada / 6 días |
| Caminos | real (−1 día) · tierra · atajo |
| Datos | `data/zonas.json`, `data/lugares.json`, `data/caminos.json` |

---

## 9. Fuera de este documento

- Ficha de cada sitio → `03_LUGARES.md`
- Cómo se camina y se mira → `01_EXPLORACION.md`
- Viaje y encuentros → `02_VIAJE_Y_ENCUENTROS.md`
- La ciudad entera → `11_CIUDADES.md`
- Terreno, agua y vegetación → `06_TERRENO_DEL_MUNDO.md`, `07_PROPS_Y_VEGETACION.md`,
  `08_AGUA_RIOS_Y_PUENTES.md`
