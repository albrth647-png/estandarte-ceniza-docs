# 07 · Props y vegetación — árboles, arbustos y todo lo que no se camina

**Estado:** ✅ **aprobado por el dueño (aprobación en bloque, 2026-09-30). Documento final.**

> El catálogo es **propio** (originalidad total, regla 8 de `../../AGENTS.md`). Qué se ve, dónde
> se coloca y **cuánto** cabe antes de perder frames.

---

## 1. Catálogo

| Familia | Piezas | Dónde | ¿Se puede tocar? |
|---|---|---|---|
| **Árboles altos** | encina, haya, pino | bosque, arboleda | No (colisión sólo del tronco) |
| **Árboles bajos** | almendro, peral, sauce | aldeas, riberas | Sí: sombra y cobertura |
| **Arbustos** | jaras, espinos, zarzas | campo abierto | No: se atraviesan (ocultan piernas) |
| **Césped y hierba** | 3 alturas instanciadas | donde hay tierra | No |
| **Rocas** | laja, peña, mojón | roca, camino | Sí (colisión) |
| **Leña y troncos** | tronco caído, pila | bosque, aldeas | **Sí: recolectable** |
| **Hitos de camino** | mojón, estaca, señal | camino real, cruces | Sí: lectura |
| **Vallas y setos** | valla, seto vivo, cerca | aldeas, prados | Valla: colisión · seto: no |
| **Cañas y juncos** | junco | orillas, vados | No |

- Cada pieza tiene **LOD** y **colisión declarada** en su ficha.
- **Todo es original o con licencia** (KayKit CC0 ya incorporado; ficha en
  `../arte/01_ASSETS.md`).

---

## 2. Cómo se colocan

1. **Semilla por zona**: la vegetación de una zona se genera con el RNG de esa zona → siempre
   el mismo bosque en la misma partida (determinismo visual).
2. **Sin invadir:** nunca sobre camino real (2,5 m libres), ni sobre un objetivo interactuable,
   ni delante de la puerta de un sitio.
3. **Densidad por terreno** (`06_TERRENO_DEL_MUNDO.md`): bosque espeso = 3× la
   arboleda clara.
4. **Z-sorted** por instancias; la hierba se pinta **sin** sombra propia (ahorro grande).

---

## 3. Presupuesto de render (gama media, 60 fps)

| Elemento | Máximo por zona | Distancia | LOD |
|---|---|---|---|
| Hierba instanciada | **3 000** | 25 m | ×1 → ×0,5 a 15 m → off |
| Arbustos | **400** | 45 m | 2 LOD |
| Árboles | **250** | 60 m (niebla) | 3 LOD |
| Rocas / troncos | **200** | 60 m | 2 LOD |
| Props de aldea | **150** | 60 m | 2 LOD |
| Dibujo total | **60 m** con niebla final | | |

- **Instancing** obligatorio para hierba y arbustos.
- Si una zona se pasa de presupuesto, se recorta **densidad**, nunca distancia de dibujo
  (recortar distancia se nota más).
- Verificable con el humo (por implementar) en 960×683 y 960×540.

---

## 4. Papel en el juego (no son decoración)

- **Arbustos y setos** cortan la visión: menos visibilidad = más emboscadas (tabla de
  encuentros) y mejor sigilo.
- **Troncos y rocas** son cobertura en combate (`../batalla/02_TERRENO.md`).
- **Leña recolectable**: recurso de descanso (`10_SUPERVIVENCIA_Y_DESCANSO.md`).
- **Mojones y señales** son texto de mundo (`../historia/08_TEXTO_DEL_MUNDO.md`).

---

## 5. Datos

- `data/props.json`: familia, piezas, colisión, LOD, densidad por terreno.
- Colocación pura en `js/systems/props.js` (semilla inyectada, sin DOM ni reloj) + tests en
  `tests/props.test.js`: misma semilla = mismo bosque; nada sobre el camino.

---

## 6. Qué entra en la demo (Fase 1)

- Familias completas del catálogo, con la **mitad de las piezas** (12 modelos de los 24):
  encina, haya, almendro, jaras, zarzas, césped ×3, laja, tronco, mojón, valla, junco.
- Presupuesto **entero** desde el principio (no se optimiza después).
- La demo solo tiene 6 sitios: su presupuesto es una fracción del tope.

---

## 7. Cifras que fija este documento

| Cifra | Valor |
|---|---|
| Piezas del catálogo | 24 (12 en la demo) |
| Hierba / arbustos / árboles | 3 000 / 400 / 250 por zona |
| Distancia de dibujo | 60 m |
| Libre de obstáculos en camino | 2,5 m |
| Densidad | ×1 a ×3 según terreno |

---

## 8. Fuera de este documento

- Terreno bajo los pies → `06_TERRENO_DEL_MUNDO.md`
- Estilo, paleta y luces → `../arte/00_ESTILO.md`
- De dónde salen los modelos → `../arte/01_ASSETS.md`
- Ríos y puentes → `08_AGUA_RIOS_Y_PUENTES.md`
