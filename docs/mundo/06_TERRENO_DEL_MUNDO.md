# 06 · Terreno del mundo — qué hace bajo tus botas

**Estado:** ✅ **aprobado por el dueño (aprobación en bloque, 2026-09-30). Documento final.**

> Este documento dice qué hace el terreno **al caminar y al viajar**. Qué hace **dentro del
> campo de batalla** está en `../batalla/02_TERRENO.md` (mismo tipo de terreno, dos
> efectos). La lista de tipos es **la misma** en los dos documentos: un solo JSON.

---

## 1. Los tipos de terreno

| Tipo | Velocidad al caminar | Visibilidad | Encuentro | Nota |
|---|---|---|---|---|
| **Camino real** | ×1,0 | alta | normal | El atajo ahorra días, el real ahorra sorpresas |
| **Tierra / rodada** | ×0,95 | alta | normal | |
| **Rocío / pastizal** | ×0,9 | media | + | Moja y hace ruido: −10 % sigilo |
| **Barro** | ×0,7 | media | − | Lento y visible: +1 día si llueve |
| **Roca / pedral** | ×0,8 | alta | − | Firme, sin rastro |
| **Bosque espeso** | ×0,75 | **baja** | ++ | Corte de visión: emboscadas más probables |
| **Arboleda clara** | ×0,9 | media | + | Recogible (leña) |
| **Vado / orilla** | ×0,6 | media | ++ | El único cruce si no hay puente |
| **Escalera / muralla** | ×0,8 | alta | − | Ciudades y refugios |

- **Visibilidad** manda sobre el HUD y sobre los encuentros: en bosque espeso el aro de
  enfocar se ve antes (te acercas más sin ser visto).
- **Encuentro** modifica la tabla de `02_VIAJE_Y_ENCUENTROS.md` (+ = más probabilidad).

---

## 2. Reglas

1. **Un solo tipo por metro cuadrado**, pintado en el propio modelo 3D (sin capas que se
   pisen).
2. El terreno del **sitio** y el del **camino** es el mismo dato: no se define dos veces.
3. El terreno **no mata**: ninguna caída ni mancha de barro puede dejar al jugador tirado
   (regla: *el fallo nunca atasca*).
4. El efecto sobre la **batalla** (cobertura, desgaste, alcance) lo traduce
   `../batalla/02_TERRENO.md`.

---

## 3. Datos

- `data/terreno.json`: `{ id, nombre_txt, velocidad, visibilidad, encuentro, cobertura }`.
- Validación: esquema + cruce con `lugares.json` (todo sitio declara su terreno).
- El cálculo es puro: `js/systems/terreno.js` (por construir) (velocidad y visibilidad), sin DOM ni reloj.

---

## 4. Qué entra en la demo (Fase 1)

- **Camino real, tierra, rocío, bosque espeso y barro** (5 de los 9): cubren los **3 campos**
  de la demo (llanura de camino y bosque/aldea) y el tramo de camino.
- Vado, roca, arboleda y muralla quedan para el mapa completo (mismo JSON, se añaden filas).

---

## 5. Cifras que fija este documento

| Cifra | Valor |
|---|---|
| Tipos de terreno | 9 (5 en la demo) |
| Velocidad mínima / máxima | ×0,6 (vado) / ×1,0 (camino real) |
| Efecto en encuentro | −1 a ++2 |
| Caida letal | nunca |

---

## 6. Fuera de este documento

- Efecto en combate → `../batalla/02_TERRENO.md`
- Vegetación y props → `07_PROPS_Y_VEGETACION.md`
- Ríos, vados y puentes → `08_AGUA_RIOS_Y_PUENTES.md`
- Recolección y supervivencia → `10_SUPERVIVENCIA_Y_DESCANSO.md`
