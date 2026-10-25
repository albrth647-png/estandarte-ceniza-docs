# 08 · Agua, ríos y puentes — cruzar cuesta

**Estado:** ✅ **aprobado por el dueño (aprobación en bloque, 2026-09-30). Documento final.**

> El **río Ulia** parte Valcoria (`00_MAPA.md` §1) y los cruces son **puntos de decisión**:
> peaje, emboscada o atajo. El vado ya existe como **terreno** (`06_TERRENO_DEL_MUNDO.md`);
> aquí se rige el **cruce**.

---

## 1. Formas de cruzar

| Cruce | Coste | Ventaja | Riesgo |
|---|---|---|---|
| **Vado** | 0 | Atajo; sin peaje | Terreno ×0,6; resbalón (`../batalla/02_TERRENO.md` §7); emboscada `++` |
| **Puente** | Peaje (si lo cobran) | Firme, sin resbalón; paso ancho | Cuello de botella; el que cobra manda |
| **Barca** | Peaje | Evita el vado | Poca capacidad (2-4 personas por viaje) |
| **Paso de piedra** | 0 | Firme | Estrecho (1,5 m); fácil de cortar |

- **El vado es el cruce por defecto** si no hay puente (`06_TERRENO_DEL_MUNDO.md` §1).
- **Nunca hay cruce letal:** el agua no ahoga al jugador (regla: *el fallo nunca atasca*).

---

## 2. Peajes y quien cobra

- **El peaje de Altamir** es el canónico (`03_LUGARES.md`, `../sistemas/06_ECONOMIA.md` §4): **5 oro
  por persona · 20 por carro**.
- **Peaje sin derecho** = deuda de la casa, no precio legal: puedes pagar, negociar o pelear
  (`../contenido/01_ENEMIGOS.md` §4).
- **Contrabando:** por la Ribera se cruza fuera de hora; sube el riesgo y el beneficio
  (`../sistemas/06_ECONOMIA.md` §6).

---

## 3. El agua en la batalla

- **Terreno `vado`:** freno ×0,6, cobertura 1, sin carga, resbalón (Desvío al doble)
  (`../batalla/02_TERRENO.md`).
- **Campo `vado_orilla`** (`../batalla/05_CATALOGO_DE_CAMPOS.md`): pasillo de 1,5 m; quien defiende
  el vado pelea de uno en uno.
- **Salpicaduras:** efecto de escena (`../arte/04_EFECTOS_Y_PARTICULAS.md`).

---

## 4. Datos, tipos y validación

- **Datos:** `data/agua.json` — `{ id, tipo (vado/puente/barca/paso), peaje, capacidad, riesgo }`.
- **Tipos:** `Cruce` en `js/data/game_types.js`.
- **Validación:** cruce con `data/lugares.json` (todo sitio junto al río declara su cruce) y con
  `data/terreno.json` (`vado`) en `tools/validate_data.js`.
- **Sistema puro:** elegir cruce y aplicar peaje/riesgo vive en `js/systems/viaje.js`; sin DOM ni
  reloj.
- **Tests:** `tests/agua.test.js`: sin puente siempre hay vado; el peaje sin derecho marca deuda;
  ningún cruce bloquea el paso.

---

## 5. Cifras que fija este documento

| Cifra | Valor |
|---|---|
| Formas de cruce | 4 |
| Peaje de Altamir | 5 oro/persona · 20/carro |
| Barca | 2-4 personas/viaje |
| Terreno vado | ×0,6 · cobertura 1 · sin carga |
| Paso estrecho | 1,5 m |
| Cruce letal | **nunca** |

---

## 6. Qué entra en la demo (Fase 1) — y qué sigue

> **Hasta aquí la demo.** El **cruce del tramo de camino** (puente o vado, `03_LUGARES.md` §2),
> con su peaje y su emboscada. El **tipo de terreno `vado`** entra con el mapa completo
> (`06_TERRENO_DEL_MUNDO.md` §4).

> **Y sigue el juego completo.** El **Ulia**, las barcas de la Ribera y los pasos de montaña se
> añaden **con este mismo formato**; crecer = más filas en `agua.json`, no otro sistema.

---

## 7. Fuera de este documento

- Mapa y ríos → `00_MAPA.md`
- Terreno y sus frenos → `06_TERRENO_DEL_MUNDO.md`
- Viaje y encuentros → `02_VIAJE_Y_ENCUENTROS.md`
- Combate en el vado → `../batalla/02_TERRENO.md`
- Precios y peajes → `../sistemas/06_ECONOMIA.md`
