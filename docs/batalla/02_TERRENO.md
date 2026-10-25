# 02 · Terreno — el campo lo pone el mundo

**Estado:** ✅ **aprobado por el dueño (aprobación en bloque, 2026-09-30). Documento final.**

> El campo de batalla **no se inventa**: se forma con el terreno del sitio donde te encontraste
> (`../mundo/02_VIAJE_Y_ENCUENTROS.md` §4 y `../mundo/06_TERRENO_DEL_MUNDO.md`). Es **el mismo
> JSON** (`data/terreno.json`) y el mismo tipo de terreno con **dos efectos**: al caminar y al
> pelear. Aquí se fija el **efecto de combate**; las cifras generales están en `01_CIFRAS.md`,
> las reglas del campo en `00_REGLAS.md` y el catálogo de campos concretos en
> `05_CATALOGO_DE_CAMPOS.md`.

---

## 1. Una sola lista de terrenos

Los **9 tipos** son los de `../mundo/06_TERRENO_DEL_MUNDO.md` §1 — ni uno más. Un solo campo
nunca mezcla dos terrenos en el mismo metro cuadrado; puede haber **manchas** (un rodal de
bosque dentro de una llanura), y eso son dos zonas del campo, no un tipo nuevo.

| Tipo | Lectura en el campo |
|---|---|
| **Camino real** | Suelo firme y despejado; la carga manda |
| **Tierra / rodada** | Como el camino, algo más blando |
| **Rocío / pastizal** | Hierba alta: cubre las piernas y esconde a los que se agachan |
| **Barro** | Lento y pegajoso; el que corre se queda rezagado |
| **Roca / pedral** | Pedrizas y lajas: cobertura dura y paso malo |
| **Bosque espeso** | Poca vista, mucha cobertura, nadie carga en formación |
| **Arboleda clara** | Bosque que se cruza: cobertura ligera, se puede cargar |
| **Vado / orilla** | Agua por los tobillos: resbala, corta la carrera y es un cuello de botella |
| **Muralla / escalera** | Piedra construida: cobertura alta y pasos obligados |

---

## 2. Qué hace cada terreno en el campo

Se leen los mismos campos del JSON que al caminar (`velocidad`, `visibilidad`, `cobertura`),
más dos derivados del combate: **carga** y **riesgo**.

| Terreno | Freno (`velocidad`) | Cobertura | ¿Carga? | Visibilidad | Riesgo propio |
|---|---|---|---|---|---|
| **Camino real** | ×1,0 | 0 | **Sí** | alta (60 m) | — |
| **Tierra / rodada** | ×0,95 | 0 | **Sí** | alta (60 m) | — |
| **Rocío / pastizal** | ×0,9 | 1 | Sí | media (40 m) | Agacharse esconde |
| **Barro** | ×0,7 | 1 | **No** | media (40 m) | Correr no gana distancia |
| **Roca / pedral** | ×0,8 | 2 | No | alta (60 m) | La caída cuesta 0,5 s |
| **Bosque espeso** | ×0,75 | **3** | **No** | **baja (25 m)** | Se puede empezar rodeado |
| **Arboleda clara** | ×0,9 | 1 | Sí | media (40 m) | — |
| **Vado / orilla** | ×0,6 | 1 | No | media (40 m) | Resbalón; Desvío al doble |
| **Muralla / escalera** | ×0,8 | 2 | No | alta (60 m) | Cuello de botella |

- **Freno:** multiplica la velocidad de **todo el que pisa esa zona** (héroe, aliados y
  enemigos), igual que al caminar. El que huye (5,5 m/s) también lo sufre.
- **Cobertura:** de 0 a 3 (§3).
- **¿Carga?:** si el terreno permite la **ventaja de carga** (§5).
- **Visibilidad:** la distancia a la que una unidad **detecta** a otra (§6).
- **Riesgo propio:** el precio de pelear ahí (§7).

---

## 3. Cobertura: la cifra que más se nota

La cobertura es un **nivel 0–3** y hace dos cosas:

1. **Encoge el daño a distancia** (flechas, hondas, venablos):

| Nivel | Daño a distancia recibido |
|---|---|
| 0 | 100 % |
| 1 | **−25 %** |
| 2 | **−40 %** |
| 3 | **−55 %** |

2. **Esconde a quien se agacha** (opción de control de la exploración): con cobertura ≥ 1,
   agachado, la unidad **no es elegida como objetivo** por la IA a distancia si hay otro
   objetivo a menos de 10 m.

- La cobertura **no reduce el daño cuerpo a cuerpo**: para eso está la Guardia.
- La cobertura del terreno y la de los **props** (`../mundo/07_PROPS_Y_VEGETACION.md` §4) se
  suman pero **nunca pasan de 3**: un tronco en terreno de bosque espeso no da nivel 5.

---

## 4. Freno: moverse dentro del campo

- La velocidad de combate de `01_CIFRAS.md` §4 se multiplica por el **freno** de la zona que se
  pisa. Un soldado de línea (4,5 m/s) en vado (×0,6) corre a **2,7 m/s**.
- El freno **cambia al cruzar la frontera** de una zona: no se arrastra.
- La **orden Defender** (−40 % de `01_CIFRAS.md` §4) y el freno se multiplican: en bosque
  espeso defendiendo, se pelea casi parado. Es intencional: ahí no se persigue.
- La **unidad huyendo** no puede quedar atrapada por el freno: si su velocidad efectiva baja de
  1,5 m/s, recupera 1,5 m/s mínimos para poder salir del campo.

---

## 5. Ventaja de carga

- Requiere **terreno con carga = sí** y venir **corriendo en línea recta ≥ 2 s** hacia el
  objetivo.
- Efecto: el **primer golpe** hace **+25 % de daño** y la unidad recibe **+10 de moral**
  (se suma al +10 de la orden Cargar de `01_CIFRAS.md` §5, no lo sustituye).
- Se pierde al: recibir un golpe antes de conectar, girar (cambiar de dirección), estar en
  cobertura ≥ 1, o salir del terreno con carga.
- **Nadie carga en bosque espeso, barro, vado, roca ni muralla**: ahí se pelea a pie firme.

---

## 6. Visibilidad y detección

- La **visibilidad** de la tabla §2 es la distancia a la que la IA **detecta** a otra unidad
  (la niebla del render es aparte, `../mundo/01_EXPLORACION.md` §7).
- Cifras: **alta = 60 m · media = 40 m · baja = 25 m**.
- A **media distancia y menos**, la detección cuenta igual para los dos bandos: no hay IA
  tramposa que vea a través del bosque.
- El jugador **ve** lo que el render pinta (60 m con niebla), pero solo **enfoca** a lo que está
  dentro de su visibilidad de terreno: en bosque espeso hay que acercarse para distinguir a
  quien ya te está mirando.

---

## 7. Riesgos propios del terreno

| Riesgo | Dónde | Qué pasa |
|---|---|---|
| **Resbalón** | rocío, vado, barro | El **Desvío** cuesta el **doble de aliento** (30 en vez de 15) y corre menos 0,2 s |
| **Caída** | roca, muralla | Correr tiene un 10 % de "tropiezo": pierdes **0,5 s** sin poder golpear (nunca daño letal) |
| **Rodeo** | bosque espeso | Si el encuentro sale por **emboscada**, empiezas **sin despliegue y en semicírculo** |
| **Fuego** | aldea, ruina | Las zonas incendiadas hacen **5 de daño/s** a quien las pisa; se ven de lejos |
| **Cuello** | puerta, vado, escalera | Ancho de paso de **1,5 m**: quien defiende ahí pelea de uno en uno |

- **Ningún riesgo mata solo** (regla: *el fallo nunca atasca*). El fuego avisa con humo antes de
  hacer daño y deja 1 m de margen para salir.

---

## 8. Cómo se genera el campo

**Plantilla por terreno + puntos de interés con semilla.** Ni a mano (caro) ni aleatorio puro
(injusto):

1. Se toma el **terreno dominante** del tramo donde saltó el encuentro
   (`../mundo/02_VIAJE_Y_ENCUENTROS.md` §4).
2. Se elige la **plantilla** de ese terreno: llanura de camino, bosque, aldea, vado/orilla,
   puerta de ciudad o ruina.
3. Se **siembran** los puntos de interés (§9) con el **RNG de la partida** → misma semilla,
   mismo campo (determinismo).
4. Se colocan **manchas** del terreno vecino (un rodal, un charco) sin superar el 20 % del campo.

- **6 plantillas** cubren las 9 lecturas de terreno; el **catálogo** con sus variantes y su
  tamaño está en `05_CATALOGO_DE_CAMPOS.md`.
- El campo **nunca** introduce un terreno que no esté en el tramo: si peleas en camino real, no
  aparece un vado que no existía.

---

## 9. Puntos de interés del campo

| Punto | Cobertura | Se puede usar |
|---|---|---|
| **Puerta / portón** | 2 | Abrir, cerrar o atrancar (cuello de botella) |
| **Carro volcado** | 3 | Cobertura alta; se puede empujar para cerrar un paso |
| **Árbol caído** | 2 | Cobertura; al terminar, se recolecta leña (`../contenido/11_TABLAS_DE_BOTIN.md`) |
| **Empalizada** | 2 | Aguanta golpes; se rompe a hachazos y abre paso |
| **Fuego / hogar** | 0 | Daña al pisarlo (§7); de noche ilumina como punto de referencia |
| **Vado / puente** | 1 | Paso obligado; el puente no tiene resbalón, el vado sí |
| **Mojón o señal** | 0 | Texto de mundo (`../historia/08_TEXTO_DEL_MUNDO.md`) |

- Como máximo **4 puntos de interés** por campo: más es un laberinto, no un campo de batalla.
- Todo punto de interés es **esquivable**: nunca cierra la única salida del campo.

---

## 10. Cómo lo lee el jugador de un vistazo (sin leyenda)

- **Se camina y se siente:** el barro frena, el vado resbala, la hierba tapa. La primera vez
  que lo pisas, lo sabes.
- **Se ve el material:** piedra, agua, hierba, lodo y bosque tienen **color y textura propios**
  (`../arte/00_ESTILO.md`); no hace falta un cartel.
- **Cobertura:** lo que te tapa, te tapa también a ti; la misma roca sirve para los dos bandos.
- **Aviso de riesgo, no de regla:** cuando entras en una zona con riesgo propio, el HUD deja
  una línea de **3 s** («El vado te frenará»), nunca un tutorial.

---

## 11. Datos, tipos y validación

- **Un solo fichero:** `data/terreno.json` — `{ id, nombre_txt, velocidad, visibilidad,
  encuentro, cobertura, carga, riesgo, ancho_paso }`. Los campos `cobertura`, `carga`, `riesgo`
  y `ancho_paso` los añade el combate; `velocidad` y `visibilidad` los comparte con el mundo.
- **Tipos:** `Terreno` y `EfectoTerreno` en `js/data/game_types.js` (una sola vez, regla 4).
- **Validación:** esquema en `js/data/schemas.js` + cruce con `lugares.json` y
  `../mundo/06_TERRENO_DEL_MUNDO.md` en `tools/validate_data.js`: **todo terreno del mundo
  tiene su ficha de combate y al revés**.
- **Sistema puro:** `js/systems/terreno.js` — lee la zona por la que se mueve una unidad y
  devuelve freno, cobertura y detección. Sin DOM, sin reloj.
- **Tests (por escribir):** `tests/terreno.test.js`, mínimo 3 casos (normal, borde, error): la cobertura nunca
  pasa de 3; el freno no atrapa a un huido; el fuego no es letal solo.

---

## 12. Cifras que fija este documento

| Cifra | Valor |
|---|---|
| Tipos de terreno | **9** (la lista de `../mundo/06_TERRENO_DEL_MUNDO.md`) |
| Freno en el campo | ×0,6 (vado) … ×1,0 (camino real) |
| Cobertura | nivel 0–3 · daño a distancia −25 % / −40 % / −55 % |
| Cobertura y props | se suman, **tope 3** |
| Ventaja de carga | +25 % al primer golpe · +10 moral · solo terreno con carga |
| Detección | alta 60 m · media 40 m · baja 25 m |
| Riesgos | resbalón (Desvío ×2) · caída 10 %/0,5 s · fuego 5/s · cuello 1,5 m |
| Puntos de interés | máximo **4** por campo |
| Plantillas | **6** (catálogo en `05_CATALOGO_DE_CAMPOS.md`) |
| Manchas de terreno vecino | ≤ 20 % del campo |

---

## 13. Qué entra en la demo (Fase 1) — y qué sigue

> **Hasta aquí la demo.** Los **5 terrenos** de `../mundo/06_TERRENO_DEL_MUNDO.md` §4 (camino
> real, tierra, rocío, bosque espeso y barro) y los **3 campos** del alcance
> (`../produccion/00_ALCANCE.md` §2.5): llanura de camino, aldea y bosque. Ventaja de carga,
> cobertura, fuego y puerta, funcionando con estas mismas cifras.

> **Y sigue el juego completo.** Los 4 terrenos restantes (roca, arboleda, vado, muralla) y sus
> 4 plantillas (vado/orilla, puerta de ciudad, ruina, pedral) se añaden **con estas mismas
> reglas**: crecer es añadir filas a `terreno.json` y plantillas a `05_CATALOGO_DE_CAMPOS.md`,
> nunca rehacer el motor. La cifra no cambia al escalar.

---

## 14. Fuera de este documento

- Reglas del campo y las 5 fases → `00_REGLAS.md`
- Cifras generales (vida, daño, moral, ritmo) → `01_CIFRAS.md`
- Órdenes globales e IA → `03_IA_Y_ORDENES.md`
- Cómo se ve y se toca → `04_PRESENTACION.md`
- El catálogo de campos concretos → `05_CATALOGO_DE_CAMPOS.md`
- El terreno al caminar y al viajar → `../mundo/06_TERRENO_DEL_MUNDO.md`
- Estructuras y trampas del campo → `../contenido/09_EDIFICIOS_Y_ESTRUCTURAS.md`,
  `../contenido/12_TRAMPAS_Y_OBSTACULOS.md`
