# 09 · ENEMIGOS DEL MUNDO — Bandas errantes, respawn y guardia

> Dossier 09. Cómo BoC puebla el continente de peligro: las 34 bandas de `ed.dat`
> (enemigos desplegados) y su ciclo de vida en el mapa.

## 1. El modelo de una banda enemiga

```xml
<ed>
  <ed_id>101</ed_id> <ed_type>0</ed_type>
  <rs_time>36</rs_time>          <!-- TIEMPO DE RESPAWN (horas de juego) -->
  <map_pos>2050,4950</map_pos>   <!-- coordenada de aparición -->
  <move_mode>2</move_mode>       <!-- patrón de movimiento -->
  <guard_radius>260</guard_radius> <!-- radio de patrulla/guarda -->
  <min_level>2</min_level> <max_level>6</max_level>  <!-- rango de nivel de la banda -->
  <army_list>802,4,6,1:100.0</army_list>  <!-- composición del ejército -->
  <drops>100.0:1,20,40,0,0; 100.0:10,5,10,0,0; 5.0:5; 10.0:100,1,1,1,50,50.0|200,…</drops>
</ed>
```

| Campo | Qué hace |
|---|---|
| `ed_type` | familia de amenaza (0 = bandidos; hay 34 repartidas por el mapa) |
| `rs_time` | tras ser destruida, la banda reaparece a las N horas de juego — **el mundo nunca se vacía** |
| `move_mode` | estática/patrulla/acecho (2 en la mayoría: patrulla) |
| `guard_radius` | radio (px) alrededor de `map_pos` dentro del que patrulla |
| `min/max_level` | nivel de la banda → escala de tropas y botín |
| `army_list` | unidades que la componen con proporciones (`802,4,6` = unidad 802, 4–6 efectivos; `1:100.0` chance) |
| `drops` | botín por vencerla — nota el caso compuesto `10.0:100,…50.0\|200,…` (probabilidad anidada: "de ese 10 %, 50/50 entre X e Y") |

## 2. Por qué este diseño funciona (y se conserva)

- **Presión constante**: siempre hay peligro cerca (`guard_radius` 260 px ≈ patrulla local)
  sin bloquear el camino — el jugador elige pelear.
- **Escala por zona**: bandas débiles cerca del inicio, fuertes hacia el interior —
  la dificultad se pinta en el mapa, no en menús.
- **Respawn declarativo**: matar a todos los bandidos no "gana" el juego; el mundo se
  re-puebla por tabla (`rs_time`), no por scripts.

## 3. Decisión para Valcoria — bandas con rostro

| Aspecto | BoC | Valcoria |
|---|---|---|
| Bandas | 34 entradas anónimas con respawn | mismas tablas JSON + **cabecillas con nombre** que recuerdan al jugador (memoria) y huyen si su reputación los precede |
| Respawn | `rs_time` horas | igual, con razón visible en la Crónica ("los forajidos vuelven a la foresta de Corvo") |
| Composición | `army_list` con proporciones | igual + veteranía acumulada de la banda superviviente |
| Botín | `drops` anidados | misma gramática de tiradas, expuesta en ficha de banda |
