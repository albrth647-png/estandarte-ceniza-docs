# 06 · PERSONAJES Y REINOS — Cómo se construyen los señores de la guerra

> Dossier 06. Personajes (`chars.dat`), reinos (`init_datas.dat`, `kd.dat`) y cómo el
> mundo arranca con su reparto político. Es la base "viva" sobre la que Valcoria monta
> los capitanes con memoria.

## 1. El modelo de un personaje (compañero, rey o vasallo)

```xml
<char>
  <char_id>102</char_id> <char_type>0</char_type>
  <char_name>Archduck Williams</char_name> <char_name_cn>威廉姆公爵</char_name_cn>
  <face>3</face> <weapon>1</weapon>
  <base_str>11</base_str> <base_agi>10</base_agi> <base_int>5</base_int>
  <growth_str>0.4578</growth_str> <growth_agi>0.423574</growth_agi> <growth_int>0.208626</growth_int>
  <def_level>20</def_level>            <!-- nivel inicial -->
  <def_money>5000</def_money>          <!-- dinero inicial -->
  <def_honor>6</def_honor>             <!-- honor inicial -->
  <def_exploit>0</def_exploit>         <!-- méritos/explotaciones -->
  <skills>101,102,103,104,105,106,107</skills>   <!-- sabe habilidades -->
  <talent>t_rid,3|t_atk,4|t_def,3|t_lead,2|…</talent>  <!-- talentos con valor -->
  <def_equip>203,20|704,10|903|0|0|0</def_equip>  <!-- equipo por ranura -->
  <home_city>0</home_city> <show_prop>100</show_prop>
</char>
```

Claves del modelo:
- **Tres atributos con crecimiento decimal por nivel** (STR/AGI/INT ~+0,2–0,5/nivel) —
  los mismos atributos que luego filtran los talentos (`depend`).
- **Equipamiento por ranuras** (`def_equip`: arma+escudo|casco|armadura|…).
- **Honor y méritos** como segunda moneda social (recompensas, lealtad).
- Los NPCs **también tienen skills y talentos**: cualquier señor puede ser retado en
  duelo o servir de compañero — el material de los "capitanes con memoria".

## 2. El reparto político inicial (`init_datas.dat`)

```
Reino 2: rey 105 · vasallos 118(lealtad 100), 119(100), 120(95)… 128(80)
         sitios: 5(guarnición 105,118,119) | 6(120,121) | 9(122,128) | 53(123)…
```

- **6+ reinos** con rey, corte de vasallos **con lealtad 75–100** y sitios guarnecidos.
- El reino 1 es el del jugador (Casadoria, arrasado: sin sitios).
- La lealtad (`id:valor`) es el estado político de partida: sube con regalos/victorias,
  baja con hambre/derrotas — más tarde decide defecciones.

## 3. Economía social visible en los datos

- `def_money` inicial por personaje (5000 un archiduque vs 800 un capitán).
- `sl.dat` (tienda) vende además packs con `ms_pid/google_pid/ios_pid` → moneda real.
  Para Valcoria: **fuera**; solo moneda de juego (oro canónico 100 al empezar).

## 4. Decisión para Valcoria — de lista de NPCs a capitanes con memoria

| Aspecto | BoC | Valcoria |
|---|---|---|
| Personajes | tabla plana con stats | mismos stats + **ficha viva**: biografía corta, deudas, rencores, lazos (Sistema de Memoria propio, sin tocar la patente Nemesis: nada de órdenes globales al mundo, todo crece de encuentros con el jugador) |
| Lealtad | número 75–100 estático al inicio | lealtad **dinámica** con razones recordadas ("me abandonaste en Bain") |
| Honor/méritos | números | honor con **eco narrativo** en la Crónica |
| Reinos | init XML | mismo init declarativo en JSON + corte con personalidad |
