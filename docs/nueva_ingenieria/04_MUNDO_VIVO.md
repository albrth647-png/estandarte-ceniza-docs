# 04 · Mundo vivo — bandas, reinos, presupuesto y mercado

> Contrato de construcción del mundo que respira. De BoC hereda: bandas con respawn
> declarativo, reinos con corte y lealtades, presupuesto semanal por personaje y
> mercados por tiradas. Valcoria los hace legibles y con memoria.

## 1. Bandas errantes (con rostro)

```jsonc
// datos/bandas.json — schema_version: 1
{
  "bandas": [
    { "id": "bandidos_corvo", "familia": "bandidos",
      "cabecilla": "Garrot el Tuerto",          // NUEVO: nombre propio + memoria
      "respawn_horas": 36, "pos": [2050, 4950],
      "modo": "patrulla", "radio_patrulla": 260,
      "nivel": [2, 6],
      "composicion": [ { "unidad": "bandido", "min": 4, "max": 6, "prob": 100 } ],
      "botin": [...] }
  ]
}
```

Ciclo de vida igual que BoC (`rs_time`, patrulla por radio) con tres mejoras:
1. El cabecilla **recuerda** al jugador: si sobrevivió a una escaramuza, la próxima vez
   comenta la herida o evita el encuentro si su fama creció (memoria barata: una fila
   por banda en el save).
2. Veteranía: la banda que huye conserva experiencia (sube de nivel la próxima vez).
3. La Crónica anuncia reapariciones con nombre de lugar, no con "respawn".

## 2. Reinos y corte (IA mínima visible)

- Estado por reino: sitios, guarniciones, lealtades (75–100 al inicio, como BoC).
- Tick semanal del reino: ingresos por prosperidad → reparto a guarniciones; si un
  sitio queda sin defensa, bandas vecinas lo saquean (regla simple, visible).
- Lealtad de vasallos sube/baja con hechos concretos registrados (regalos, victorias,
  abandono en batalla) — el germen de los capitanes con memoria.

## 3. Presupuesto semanal explicado

Paridad con `AEWeeklyBudget` (neto **por personaje**, líneas coloreadas, confirmación):

```
liquidacion_semanal():
  para cada sitio propio: ingreso += prosperidad × tasa_sitio(tipo)
  para cada compañero a sueldo: gasto += sueldo(personaje)
  neto = ingresos − gastos   →  si neto < 0: Deuda += |neto|   (la Deuda crece)
  la pantalla muestra CADA línea (verde/rojo) y permite pagar sueldos atrasados
```

## 4. Mercado vivo

- Gramática de tiradas heredada (`prob%: item, min, max, …`) por sitio.
- Precios con oferta/demanda local: comprar arma en la forja la encarece una semana;
  vender grano en ciudad asediada paga el doble. El herrería muestra recetas y % reales.
- Sin IAP: `sl.dat` se usa solo como referencia de categorías de tienda local.

## 5. Pruebas de aceptación

1. Matar toda banda y avanzar 36 h de juego la repuebla en su radio.
2. Liquidación semanal suma exactamente las líneas mostradas.
3. Un sitio sin guarnición en tick con banda cercana es saqueado (Crónica lo cuenta).
4. Precios de mercado reaccionan a compra/venta masiva (memoria de 7 días).
