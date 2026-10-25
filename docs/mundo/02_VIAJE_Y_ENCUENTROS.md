# 02 · Viaje y encuentros — el camino entre sitios

**Estado:** ✅ **aprobado por el dueño (aprobación en bloque, 2026-09-30). Documento final.**

> El mapa (nodos y aristas) está en `00_MAPA.md`; caminar dentro de un sitio, en
> `01_EXPLORACION.md`. Aquí se decide **lo que pasa entre un sitio y otro**, que es donde
> nacen las batallas, los rumores y la Firma.

---

## 1. Cómo se viaja

1. En el borde de un sitio (o en su mapa) eliges **destino**: solo destinos unidos por una
   arista del grafo (`00_MAPA.md` §4).
2. Ves el **coste en días** de esa arista (y el modificador de camino real / atajo).
3. Confirmas → el viaje **se resuelve por días**, con una tirada de encuentro por día.

**Sin esperas reales (regla 9):** el viaje se representa en la pantalla de mapa, **1,5 s por
día** (máximo 9 s por trayecto) o instantáneo con la opción «viaje rápido». Nunca hay cámara
de carreta en movimiento ni pantalla negra esperando.

---

## 2. Una tirada por día

Cada día de viaje se tira **una vez** contra la tabla de su **zona** y su **franja horaria**:

| Franja | Peso |
|---|---|
| Amanecer (06–10) | Exploración y gente de oficio |
| Mediodía (10–16) | Trato y patrullas |
| Atardecer (16–20) | Encuentros de camino |
| Noche (20–06) | Peligro alto; solo si decides caminar de noche (−1 día, peso duplicado del peligro) |

### Tabla base de encuentros (pesos por zona)

| Encuentro | Marca del Sur | Ribera | Serranía | Altos | Tierra del Paso |
|---|---|---|---|---|---|
| Nada notable | 30 | 30 | 25 | 30 | 20 |
| Mercader o carro | 15 | 25 | 8 | 15 | 5 |
| Reclutador (Marcados) | 10 | 8 | 12 | 8 | 10 |
| Correo o mensaje | 8 | 10 | 5 | 10 | 5 |
| Patrulla de casa enemiga | 10 | 8 | 12 | 15 | 8 |
| **Emboscada** | 12 | 7 | 20 | 10 | 20 |
| Ruina, pozo o restos | 5 | 5 | 8 | 7 | 17 |
| Peregrino o huido | 10 | 7 | 10 | 5 | 15 |

- La **Firma** y tu **memoria** mueven los pesos: una Firma temible baja el peso de
  emboscada de quien te conoce y sube el de patrulla (te buscan).
- Todo con **RNG inyectado** (semilla de partida): dos partidas iguales encuentran lo mismo.

---

## 3. Qué hace cada encuentro

| Encuentro | Resultado |
|---|---|
| Mercader / carro | Trato corto sin salir del camino |
| Reclutador | Un Marcado se alista si tu Firma y tu oro dan pie |
| Correo | Noticia, encargo nuevo o recuerdo que te busca |
| Patrulla | Habla, se aparta o pelea según memoria y Firma |
| **Emboscada** | **Batalla** con el campo del terreno donde estés (`../batalla/00_REGLAS.md`) |
| Ruina / poza | Recurso o herida; lectura ambiental |
| Peregrino | Rumor (`../misiones/03_CADENAS_Y_RUMORES.md`) |

- Un encuentro con gente **mueve la Firma solo si hay testigos** (regla de `01_FIRMA.md`).

---

## 4. Dónde se pelea

La emboscada abre el campo **con el terreno del tramo**: camino real → llanura; bosque →
bosque; vado → orilla. El campo **nunca** es un sitio inventado: sale del terreno del mapa
(`../batalla/02_TERRENO.md`).

---

## 5. Noches y descanso

- De noche se viaja **solo si lo pides** (y el peligro se duplica).
- Dormir en el camino = refugio, aldea o posada. El descanso completo del juego completo
  (raciones, campamentos) está en `10_SUPERVIVENCIA_Y_DESCANSO.md`; la demo solo
  usa **posada y fuego**.

---

## 6. Datos, tipos y validación

- `data/encuentros.json`: pesos por zona y franja, con validador en `tools/validate_data.js`.
- Sistema puro: `js/systems/viaje.js` — calcula días, tira encuentros con el RNG inyectado y
  devuelve resultados; **no** dibuja ni espera relojes.
- Tests: `tests/viaje.test.js` (normal, borde, error) — incluye que la misma semilla repite
  el mismo trayecto.

---

## 7. Qué entra en la demo (Fase 1)

- Solo **1 tramo de camino** con la tabla de la **Marca del Sur** (fila 1).
- Los 6 tipos de encuentro: nada, mercader, reclutador, correo, patrulla y emboscada
  (ruinas y peregrinos quedan para Fase 2 con el mapa grande).
- Viaje a 1,5 s por día, sin esperas reales.
- **Misma estructura de datos** que el juego completo: añadir zonas = añadir filas.

---

## 8. Cifras que fija este documento

| Cifra | Valor |
|---|---|
| Tiradas | 1 por día de viaje |
| Animación | 1,5 s por día (máx. 9 s) · instantáneo opcional |
| Pesos | Tabla por zona (§2), sin normalizar |
| Noche | opcional · peligro ×2 |
| Semilla | la de la partida (determinismo) |

---

## 9. Fuera de este documento

- El grafo y las distancias → `00_MAPA.md`
- El campo donde se pelea → `../batalla/02_TERRENO.md`
- Los rumores que abre un encuentro → `../misiones/03_CADENAS_Y_RUMORES.md`
- Ficha de cada destino → `03_LUGARES.md`
