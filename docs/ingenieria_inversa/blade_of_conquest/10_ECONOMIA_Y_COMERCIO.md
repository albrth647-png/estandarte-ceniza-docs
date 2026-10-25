# 08 · ECONOMÍA Y COMERCIO — Cómo fluye el oro

> Dossier 08. El dinero en BoC: qué entra, qué sale, cómo se comercia y cómo se
> liquida la semana. Fuente: tablas `trade`/`grocer`/`blacksmith` de `map_objs.dat`,
> `gdl.dat` (botín global), `sl.dat` (tienda/IAP) y clase nativa `AEWeeklyBudget`.

## 1. Las tres fuentes de oro (y el gasto)

| Flujo | Mecánica | Dato original |
|---|---|---|
| Botín de batalla | cada tropa muerta suelta (`drops`) y `gdl.dat` añade botín global por rango de nivel | `gdl`: lv 1–5 → 50 %: oro 10–20 · 100 %: item 101 |
| Impuestos de sitios | prosperidad de cada sitio → ingreso periódico | `def_prosp`/`max_prosp` + `AEWeeklyBudget` |
| Comercio | comprar barato en un sitio, vender en otro | tablas `trade` distintas por ciudad (items 2001–2016) |
| **Gastos** | reclutas (`hire_price`), mejoras (`up_price`), equipo (`pl.dat`), herrería | tablas de unidades e items |

## 2. La gramática de las tablas de mercado

Todas comparten el formato de probabilidad+payload:

```
trade: 100.0:2001,5,10,0,0;  100.0:2002,3,6,0,0;  50.0:2014,1,3,0,0
       │    │    │  │        └ probabilidad de que el lote aparezca ese día
       │    │    └──┴── cantidad mínima–máxima disponible
       │    └── item_id (pl.dat)
       └── 100.0 = siempre en stock
```

- **Ciudades** (tipo 1): 4–8 líneas de `trade` (luxaciones, armas) + `grocer` (comida).
- **Ranchos** (tipo 7): venden caballos (items 800/801) por `grocer`.
- **Forjas** (tipo 6): `blacksmith` fabrica equipo con probabilidad (60 % item 100…),
  probablemente con materiales + oro.

## 3. El ciclo semanal (`AEWeeklyBudget`, 26 métodos)

La clase nativa con nombre más revelador del sistema económico: liquidación semanal de
impuestos por sitio y sueldos/gastos. En la UI existe `WeeklyBudget.csb` — el jugador ve
el cierre de semana. La prosperidad del sitio (`def_prosp`, sube hasta `max_prosp`)
hace de base imponible; saqueos y guerra la degradan.

## 4. La tienda IAP (`sl.dat`) — para saber qué NO copiar

- `sl.dat` mezcla la tienda de juego con SKUs reales (`ms_pid`, `google_pid`, `ios_pid`,
  precios por plataforma). Categorías (`category`) y iconos.
- Valcoria: la demo es **offline sin IAP**; se conserva la tienda local de comercio
  (`AETradeBox`) y se descarta el resto. Canon de oro inicial: **100** (soldado 120 ·
  noble 140 · mercader 150; escaramuza ×1,3) — ya fijado en `docs/sistemas/06_ECONOMIA.md` §9.

## 5. Decisión para Valcoria — economía legible

| Aspecto | BoC | Valcoria |
|---|---|---|
| Mercados | tiradas de probabilidad por sitio | mismas tablas JSON **+ precios vivos** (escasez real, estaciones, guerra cerca sube precios de armas) |
| Impuestos | prosperidad → presupuesto opaco | liquidación semanal línea a línea en pantalla (propina la misma idea de `WeeklyBudget`) |
| Botín | `drops` + `gdl` global | mismos dos niveles (por unidad + por rango de nivel de la banda) |
| Herrería | fabricación probabilística | recetas visibles con % — sin azar oculto en lo que se paga |
| IAP | sí (`sl.dat` SKUs) | **no** en la demo |
