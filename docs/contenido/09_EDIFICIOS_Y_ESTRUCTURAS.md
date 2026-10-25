# 09 · Edificios y estructuras — lo que se levanta

**Estado:** ✅ **aprobado por el dueño (aprobación en bloque, 2026-09-30). Documento final.**

> Un edificio en Valcoria **tiene una función**: se entra para descansar, curar, reclutar,
> truequear, cobrar un encargo o enterrar a un muerto. Aquí está el **catálogo**, **quién los
> levanta o los quema** y cuáles tienen **interior jugable**. Las fichas de sitio, en
> `../mundo/03_LUGARES.md`; la ciudad, en `../mundo/11_CIUDADES.md`; los modelos, en
> `../arte/01_ASSETS.md`.
>
> **Edificios, ids y cifras son propuesta de diseño** (cambiables → `../DECISIONES.md`).

---

## 1. Catálogo y servicio

| id | Edificio | Servicio que da | Referencia |
|---|---|---|---|
| `casa_aldea` | **Casa de aldea** | Techo, fuego, un rumor | `../mundo/10_SUPERVIVENCIA_Y_DESCANSO.md` |
| `posada` | **Posada** | Cama, comida, **rumores** | `../mundo/10_SUPERVIVENCIA_Y_DESCANSO.md` |
| `casa_alquilada` | **Casa alquilada** | **Cuartos para rehenes** · renta diaria | `../sistemas/02_PRISIONEROS.md` §3.1 |
| `capilla` | **Capilla** | **Funeral** (+10 moral), juramento · **taller del Sanador** | `../sistemas/08_LUTO_Y_MORAL.md` §3 |
| `granero` | **Granero** | Grano, **comida de la compañía** | `05_RECURSOS_Y_MERCADO.md` |
| `herreria` | **Herrería** | Reparar, **mejorar** y **fabricar** equipo del héroe | `04_ITEMS_Y_EQUIPO.md` §4 · `../sistemas/15_FABRICACION_Y_RECETAS.md` §1 |
| `barberia` | **Barbería** | **Curar** fuera de combate | `00_TROPAS.md` §3.3 |
| `tablon` | **Tablón / portavocía** | Publica encargos | `../misiones/01_TABLONES_Y_PORTAVOCES.md` |
| `escribania` | **Escribanía** | Deuda, **enmienda**, honor | `../sistemas/01_FIRMA.md` §7 |
| `mercado` | **Mercado** | Comprar/vender · **taller del Tratante** | `05_RECURSOS_Y_MERCADO.md` §4 |
| `torre` | **Torre** | Vigía; avisa de patrullas | `01_ENEMIGOS.md` §4 |
| `empalizada` | **Empalizada** | Defensa; se rompe a hachazos | `12_TRAMPAS_Y_OBSTACULOS.md` |
| `puente_piedra` | **Puente de piedra** | Cruce firme sin peaje propio | `../mundo/08_AGUA_RIOS_Y_PUENTES.md` §1 |
| `ruina` | **Ruina** | Refugio, botín, leyenda | `11_TABLAS_DE_BOTIN.md` |

- **La sede del Escribano** es la `escribania` de la ciudad (`../mundo/11_CIUDADES.md` §1).
- **Todo edificio justifica su existencia con un servicio** (regla de `../mundo/03_LUGARES.md` §4):
  si no da nada, no existe.

---

## 2. Quién los levanta, quién los quema

| Actor | Qué hace | Consecuencia |
|---|---|---|
| **La aldea** | Construye casas, granero, tablón | Repone daños con el tiempo (mundo vivo) |
| **Una casa** | Levanta torre, empalizada, herrería | Control de la zona; peaje |
| **La Escribanía** | Pone escribanía y sello | Autoridad de la Ordenanza |
| **Los bandidos** | **Quema** granero y posada | Sube el hambre y la inseguridad |
| **La guerra entre casas** | Derriba puentes, corta caminos | Cierra un tramo hasta que se resuelva |
| **Tú** | Puedes **incendiar** (provocas hambre y memoria en contra) | Firma −7 (`../sistemas/01_FIRMA.md` §4) |

- **El jugador alquila, no levanta ni controla:** la `casa_alquilada` se alquila por días y **no da
  peaje ni control de zona** — eso sigue siendo de las casas nobles del mundo.
- **Quemar un edificio no es gratis:** deja **memoria en contra** del lugar y de su casa
  (`../sistemas/00_MEMORIA_Y_DEUDA.md` §4) y sube el precio del grano (`05_RECURSOS_Y_MERCADO.md` §3).
- **El fuego avisa** con humo antes de dañar (`../batalla/02_TERRENO.md` §7): nunca atrapa sin salida.

---

## 3. Interiores jugables

- **Entran 5** (no se modela el interior de todo): `posada`, `herreria`, `escribania`, `capilla`
  y `granero`.
- El resto son **fachadas con colisión** y una interacción de puerta (abrir = cambiar de nodo o
  mostrar panel), sin interior 3D.
- **Dentro:** una sala pequeña con su punto de servicio (mesa, yunque, altar) enfocable
  (`../mundo/01_EXPLORACION.md` §6).
- **Sin interiores de casa noble** en la demo; la `torre` y la `casa_aldea` son de fachada.
- La `casa_alquilada` tampoco tiene interior 3D: se abre por **panel de puerta** (cuartos y renta,
  `../sistemas/02_PRISIONEROS.md` §3.1), como el `tablon`.

---

## 4. Cómo se encajan en el terreno

- **Regla de `../mundo/07_PROPS_Y_VEGETACION.md` §2:** ningún edificio invade el camino real
  (2,5 m libres), el objetivo interactuable ni la puerta de un sitio.
- **Se colocan por plantilla de sitio** (`../mundo/03_LUGARES.md` §1), no a mano uno a uno: la
  semilla de la zona decide variantes de tejado y desgaste.
- **El terreno manda:** un edificio en vado se calza sobre pilotes; en roca, sobre laja
  (`../mundo/06_TERRENO_DEL_MUNDO.md`).
- **Puertas de paso** de **1,5 m** (cuello de botella, `../batalla/02_TERRENO.md` §7).

---

## 5. Papel en el campo de batalla

- Como **punto de interés** (`../batalla/02_TERRENO.md` §9): puerta, carro, empalizada, hogar.
- La **empalizada** aguanta golpes y se rompe a hachazos (el **zapador**, `00_TROPAS.md` §3.3).
- El **fuego** de un edificio ardiendo es zona de riesgo (5 de daño/s, `../batalla/02_TERRENO.md` §7).
- Máximo **4 puntos** de edificio/prop por campo (`../batalla/02_TERRENO.md` §9).

---

## 6. Assets y presupuesto de peso

| Pieza | Estado | Peso objetivo |
|---|---|---|
| Casa de aldea, posada, herrería (fachada) | Falta (Fase 1) | ≤ 0,4 MB cada una |
| Torre, empalizada, puente | Falta (Fase 2) | ≤ 0,3 MB |
| Interiores (5 salas) | Falta (Fase 1) | ≤ 0,2 MB por sala |
| Ruina | Falta (Fase 2) | ≤ 0,3 MB |

- **Reutilización modular:** una misma casa con tejado y desgaste distintos hace de varias
  (`../arte/00_ESTILO.md` §5).
- **Pipeline y licencias:** todo entra con ficha (`../arte/01_ASSETS.md` §3).
- **Presupuesto total:** dentro del tope de `../arte/01_ASSETS.md` §3 (**~90 MB en la demo**, APK ~100 MB desde 2026-10-02).

---

## 7. Datos, tipos y validación

- **Datos (por crear):** `data/edificios.json` — `{ id, nombre_txt, servicio, entrable, terreno, fuego,
  modelo, peso }`.
- **Tipos:** `Edificio` en `js/data/game_types.js` (una sola vez, regla 4).
- **Validación:** esquema en `js/data/schemas.js` + cruce del `modelo` con `data/assets.json`, del
  `servicio` con `data/lugares.json` y del `terreno` con `data/terreno.json` en
  `tools/validate_data.js`.
- **Sistema puro:** la colocación y el estado (en pie / quemado) vivirán en `js/systems/edificios.js`;
  sin DOM, sin reloj (el día entra inyectado), semilla inyectada.
- **Tests (por escribir):** `tests/edificios.test.js`, mínimo 3 casos (normal, borde, error): nada se coloca sobre
  el camino; un edificio quemado no sigue dando servicio; un interior sin sala definida no rompe la
  carga.

---

## 8. Cifras que fija este documento

| Cifra | Valor |
|---|---|
| Edificios del catálogo | **14** |
| Con interior jugable | **5** (posada · herrería · escribanía · capilla · granero) |
| Puertas de paso | **1,5 m** |
| Puntos de edificio por campo | ≤ 4 |
| Fuego | 5 daño/s · avisa con humo |
| Quemar (tú) | Firma **−7** + memoria en contra |
| Peso por fachada | ≤ 0,4 MB · interior ≤ 0,2 MB |

---

## 9. Qué entra en la demo (Fase 1) — y qué sigue

> **Hasta aquí la demo.** Las **fachadas** de casa, posada, herrería, capilla, tablón, mercado y
> granero, la **casa alquilada** (panel de puerta), los **5 interiores**, el **puente** del tramo y
> la **empalizada** de aldea del Acto I, con sus servicios funcionando.

> **Y sigue el juego completo.** Torre, ruina, empalizadas de casa y estructuras de asedio se
> añaden **con estas mismas reglas y el mismo pipeline**: crecer = más filas en `edificios.json`
> con su ficha de asset, no un sistema nuevo.

---

## 10. Fuera de este documento

- Fichas de sitio → `../mundo/03_LUGARES.md`, `../mundo/11_CIUDADES.md`
- Props y vegetación → `../mundo/07_PROPS_Y_VEGETACION.md`
- Servicios y precios → `../sistemas/06_ECONOMIA.md`
- Interiores y enfocar → `../mundo/01_EXPLORACION.md`
- Trampas y obstáculos → `12_TRAMPAS_Y_OBSTACULOS.md`
- Modelos y licencias → `../arte/01_ASSETS.md`
- Puentes y vados → `../mundo/08_AGUA_RIOS_Y_PUENTES.md`
