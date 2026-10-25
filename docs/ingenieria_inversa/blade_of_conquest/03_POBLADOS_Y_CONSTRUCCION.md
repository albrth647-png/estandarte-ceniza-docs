# 03 · POBLADOS, TORRES Y CONSTRUCCIÓN — Cómo funcionan las ciudades

> Dossier 03. Cómo BoC modela **ciudades, castillos, aldeas y edificios especiales**,
> incluida la "construcción" que tiene el juego (torres de defensa, herrería, mercado)
> y su economía de prosperidad/defensa.

## 1. La taxonomía de sitios (88 en total, 9 tipos)

Extraída de `assets/datas/map_objs.dat` (comentario original: 城市表, "tabla de ciudades"):

| `mo_type` | Qué es | Cuántos | Ejemplos | Economía (`def_prosp`→`max_prosp`) | Defensa (`def_defence`→`max_defence`) |
|---|---|---|---|---|---|
| 1 | **Ciudad** | 9 | St Sith, Lorraine, Luske, Bain City, Baham, Lille, Winster, Elbetal… | 1400–1600 → **5000** | 1000–1200 → 2000 |
| 2 | **Castillo** (a veces con pueblo adosado) | 18 | Tisch, Katz, Soren, Ward, Brent, Thunder… | 820 → 2000 | 800 → 1200 |
| 3 | **Aldea** | 36 | Edessa, Zora, Agate, Liz, Roland, Balme… | 320 → 800 | 80 → 200 |
| 4 | **Abadía** | 4 | Abbey of Saint-martin, Morpheus, Reddell, Edmund | 0 → 0 | 0 → 0 |
| 5 | **Granja** | 5 | Charlie's, Denis's, Davis's, Baker's, Frank's Farm | 300 → 500 | 100 → 100 |
| 6 | **Forja (Smithy)** | 3 | Smithy ×3 | 0 → 0 | 0 → 0 |
| 7 | **Rancho** | 3 | Ranch ×3 | 0 → 0 | 0 → 0 |
| 8 | **Mina** | 6 | Badorf, Hock, Warloff, Feland, Vallis, Grief Mine | 660 → 800 | 100 → 100 |
| 9 | **Guarida de ladrones** | 4 | Thieves' den ×4 | — | — |

**Jerarquía feudal real en los datos:** las aldeas tienen campo `belong` apuntando al
castillo del que dependen (p. ej. `Edessa Village → belong: 50 (Tisch)`). Conquistar el
castillo arrastra a sus aldeas — la cadena de vasallaje está en la tabla, no en el código.

## 2. Campos de cada sitio y qué significan

```xml
<map_obj>
  <mo_id>1</mo_id> <mo_type>1</mo_type>
  <name>St Sith</name> <name_cn>圣西斯</name_cn>
  <def_prosp>1400</def_prosp>   <!-- prosperidad inicial -->
  <max_prosp>5000</max_prosp>   <!-- techo de prosperidad -->
  <def_defence>1000</def_defence> <!-- defensa inicial -->
  <max_defence>2000</max_defence> <!-- techo de defensa -->
  <tower_slot>3</tower_slot>    <!-- HUECOS DE TORRE: construcción defensiva -->
  <grocer>100.0:14,20,20,0,0;…</grocer>   <!-- tabla de provisions (comida) -->
  <trade>100.0:2001,5,10,0,0;…</trade>    <!-- tabla de mercadería (comercio) -->
  <blacksmith>…</blacksmith>    <!-- solo forjas: fabricación de equipo -->
  <belong>50</belong>           <!-- solo aldeas: castillo del que dependen -->
</map_obj>
```

- **Prosperidad** = la "salud económica" del sitio: crece/declina con el tiempo y los
  eventos; alimenta los impuestos. La clase `AEWeeklyBudget` (26 métodos) liquidaría el
  presupuesto semanal del jugador/reino.
- **Defensa** = aguante del sitio ante asedio/reducción de guarnición; al capturar cambia
  de dueño (`belong`/reino propietario en `init_datas.dat`).
- **`tower_slot`** = la única "construcción" con huecos en BoC: 3 torres por ciudad,
  2 por castillo. Las torres disparan al defensor en asedios.
- **`grocer`/`trade`/`blacksmith`** comparten gramática de botín:
  `prob%:item_id,min,max,?,precio` — el surtido del mercado se tira por probabilidad,
  distinto por sitio (ciudades con items 2001–2016, ranchos venden 800/801 = caballos).

## 3. Qué se hace dentro de una ciudad (`AECityScene`, 68 métodos)

Las pantallas/pantallitas del bucle urbano (escenas `.csb` y cajas nativas):

| Lugar | Clase nativa / escena | Qué pasa |
|---|---|---|
| Taberna/recluta | `AEPartyScene`, `AECharactorScene` | hablar con personajes, reclutar héroes/vasallos |
| Cuartel | `BarracksScene.csb`, `AEUpgradeUnitBox` | reclutar y **mejorar tropas** (`pre_unit`) |
| Mercado | `AETradeBox`, `AEStoreScene` | comprar/vender según tablas `trade`/`grocer` |
| Inventario | `AEInventoryScene` | equipo del héroe (`pl.dat`) |
| Prisión | `AEPrisonBox` | prisioneros de guerra (capturados en batalla) |
| Guarnición | `AEGarrisonScene` | tropas dejadas a defender el sitio |
| Territorio | `TerritoryBox.csb` | administración del sitio (impuestos, torres) |
| Presupuesto | `WeeklyBudget.csb`, `AEWeeklyBudget` | liquidación semanal de ingresos |
| Guardado | `AECityScene::onCtlCmdsPanelSaveGame` | punto de guardado en ciudad |

## 4. Conquista y cambio de manos

- Cada sitio pertenece a un reino (`init_datas.dat`) con guarnición inicial
  (`sites` = `sitio,chars…`).
- Atacar un sitio hostil → preparación de batalla (`AEBattlePrepare`) → batalla
  (`SGBattleScene`) → si gana el atacante, sitio cambia de dueño con su prosperidad y
  defensa actuales; las aldeas dependientes (`belong`) caen con el castillo.
- Guaridas de ladrones (tipo 9) son sitios-hostil sin economía: misiones de limpieza.

## 5. Decisión para Valcoria — poblares con vida, no con números secos

| Aspecto | BoC | Valcoria |
|---|---|---|
| Taxonomía | 9 tipos fijos en una tabla | misma tabla JSON + tipos ampliables; jerarquía aldea→castillo conservada |
| Prosperidad/defensa | dos números por sitio | mismos dos números **+ memoria de eventos** (saqueos, ferias, hambrunas visibles en el sitio) |
| Construcción | solo `tower_slot` (3/2 huecos) | heredar torres como defensa ligera **y** añadir la capa "aforo/obra" ya diseñada en `docs/sistemas/` (si el dueño quiere AoE-lite se decide en fase B) |
| Mercado | tablas de probabilidad por sitio | mismas tablas JSON + precios vivos por oferta/demanda y estación |
| Herrería | fabricación por probabilidad | mismo sistema transparente al jugador (recetas visibles) |
| Visual | UI 2D estática | vistas de sitio con paralaje, NPCs con rutina, faroles de noche — "mucho más bonito a primera vista" |
| Economía semanal | `AEWeeklyBudget` opaco | liquidación semanal **explicada al jugador** línea a línea (ingresos, gastos, sueldos) |
