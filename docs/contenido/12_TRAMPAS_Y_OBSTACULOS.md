# 12 · Trampas y obstáculos — lo que corta el paso

**Estado:** ✅ **aprobado por el dueño (aprobación en bloque, 2026-09-30). Documento final.**

> Ni el camino ni el campo son lisos: hay **troncos, derrumbes, portones con cerrojo, fosos y
> empalizadas**. Aquí está **qué corta el paso, quién lo pone y cómo se pasa**. Los edificios, en
> `09_EDIFICIOS_Y_ESTRUCTURAS.md`; los puntos de interés del campo, en `../batalla/02_TERRENO.md` §9;
> las herramientas, en `04_ITEMS_Y_EQUIPO.md` §3.4.
>
> **Trampas, ids y cifras son propuesta de diseño** (cambiables → `../DECISIONES.md`).

---

## 1. Obstáculos de mundo (en el camino)

| id | Obstáculo | Qué hace | Se supera con |
|---|---|---|---|
| `tronco` | **Tronco caído** | Corta el paso hasta que lo apartas | Fuerza (tiempo) o **hacha de leña** |
| `derrumbe` | **Derrumbe** | Bloquea un paso de montaña | **Pico** o un favor de casa |
| `seto` | **Seto / zarzal** | Corta la visión y el paso | Fuego (riesgo) o rodeo |
| `valla` | **Valla** | Marca un límite; salta bajo | Salto corto o puerta |
| `cadena` | **Cadena / argolla** | Cierra un portón o un puente | Llave, favor o **pico** |
| `porton` | **Portón con cerrojo** | Cierra ciudad, aldea o refugio | Favor, soborno o esperar |
| `vado` | **Paso de agua** | Frena y resbala | Ya es terreno (`../mundo/06_TERRENO_DEL_MUNDO.md`) |
| `lodo` | **Barro profundo** | Frena la carreta | Tablones o esperar a que seque |

- **Ningún obstáculo bloquea la partida:** siempre hay **rodeo, herramienta o favor**
  (Pilar 3: *el fallo nunca atasca*).
- Se ve **por material y forma** (§5), sin leyenda.

---

## 2. Trampas del campo de batalla

| id | Trampa | Efecto | Punto de interés |
|---|---|---|---|
| `foso` | **Foso** | Frena, expone; quien cae pierde 0,5 s | Sí |
| `red` | **Red caída** | Enreda 2 s (no mata) | Sí |
| `empalizada` | **Empalizada** | Cobertura 2; se rompe a hachazos | Sí (`09_*`) |
| `carro_volcado` | **Carro volcado** | Cobertura 3; se empuja para cerrar un paso | Sí |
| `fuego` | **Fuego / hogar** | **5 de daño/s** al pisar; avisa con humo | Sí (`../batalla/02_TERRENO.md` §7) |
| `atranco` | **Atranco de puerta** | Cuello de botella de 1,5 m | Sí |

- Máximo **4 puntos de trampa** por campo (`../batalla/02_TERRENO.md` §9).
- **Toda trampa es esquivable:** nunca cierra la única salida (`../batalla/02_TERRENO.md` §9).
- **Ninguna trampa mata sola:** el fuego hace daño pero deja margen de 1 m
  (`../batalla/02_TERRENO.md` §7).

---

## 3. Cómo se superan

| Vía | Cuándo | Coste |
|---|---|---|
| **Fuerza** | Tronco, derrumbe, valla | Tiempo (segundos) |
| **Herramienta** | Pico, hacha de leña | La herramienta (`04_ITEMS_Y_EQUIPO.md` §3.3) |
| **Tiempo** | Barro, lodo, río que baja | Medio día de juego |
| **Favor** | Portón, cadena, puerta de ciudad | Un favor (`../sistemas/03_FAVORES.md`) |
| **Orden a las tropas** | Empalizada, atranco, carro | El **zapador** abre paso (`00_TROPAS.md` §3.3) |
| **Soborno** | Guardia, ronda | 20-50 oro (`../sistemas/06_ECONOMIA.md` §3) |

- **El zapador es la respuesta del campo:** con él, la empalizada deja de ser un muro y pasa a ser
  un botón (pero solo él, no cualquiera).
- **Sin herramienta ni favor, siempre queda el rodeo:** pagar en tiempo, nunca en partida.

---

## 4. Quién las pone

| Quién | Qué trampa | Motivo |
|---|---|---|
| **Bandidos de camino** | Foso, red, tronco | Tienden emboscada (`01_ENEMIGOS.md` §3) |
| **Cuadrilla de casa** | Empalizada, atranco | Defender una plaza |
| **Patrulla de Altamir** | Cadena, portón | Cobrar peaje sin derecho |
| **La aldea** | Valla, seto, foso | Defenderse de los bandidos |
| **La guerra entre casas** | Derrumbe, puente cortado | Cerrar un tramo (`09_*` §2) |
| **Tú** | Fuego (incendio) | Cobrar rápido; **Firma −7** (`../sistemas/01_FIRMA.md` §4) |

- **Poner una trampa no es gratis:** deja **memoria** del que la sufre (`../sistemas/00_MEMORIA_Y_DEUDA.md` §4)
  y puede encender rencor si humilla.

---

## 5. Cómo se ven y se oyen (sin leyenda)

- **Por material:** madera (tronco, valla, empalizada), piedra (derrumbe, portón), tierra (foso,
  lodo), agua (vado), fuego (llama y humo) — coherente con `../arte/00_ESTILO.md` §4.
- **Por forma:** un foso es una zanja; una red, un tejido; un atranco, una puerta estrecha.
- **Por sonido:** madera que cruje, cadena que golpea, agua que corre, fuego que chisporrotea
  (`../arte/02_AUDIO.md`).
- **Aviso, no tutorial:** al acercarte, el HUD deja una línea de **3 s** («El foso te frenará»,
  «La cadena aguanta»), nunca una explicación.
- **Nunca solo color** (`../interfaz/04_ACCESIBILIDAD.md` §2).

---

## 6. Coste de arte y reutilización

- **Piezas modulares:** tronco, valla, empalizada, portón, foso y red se recombinan
  (`../arte/00_ESTILO.md` §5).
- **Presupuesto por pieza:** ≤ **0,2 MB**; animaciones cortas (puerta que gira, carro que vuelca)
  `../arte/03_ANIMACIONES.md` §3.
- **Props de campo:** ≤ 4 puntos por campo, comparten modelos con el mundo
  (`../mundo/07_PROPS_Y_VEGETACION.md`).
- **Nada de física real de derrumbe:** el derrumbe es un **cambio de estado** (paso abierto/cerrado),
  no simulación (`../arte/03_ANIMACIONES.md` §4).

---

## 7. Datos, tipos y validación

- **Datos (por crear):** `data/trampas.json` — `{ id, tipo (mundo/campo), pone, superacion, coste, punto,
  modelo, letal }`.
- **Tipos:** `Trampa` en `js/data/game_types.js` (una sola vez, regla 4).
- **Validación:** esquema en `js/data/schemas.js` + cruce del `modelo` con `data/assets.json`, del
  `punto` con `data/campos.json` (`../batalla/05_CATALOGO_DE_CAMPOS.md`) y de `letal` (**nunca**
  `true` solo) en `tools/validate_data.js`.
- **Sistema puro:** `js/systems/trampas.js` — estado, superación y coste; sin DOM, sin reloj, RNG
  inyectado.
- **Tests (por escribir):** `tests/trampas.test.js`, mínimo 3 casos (normal, borde, error): el fuego no es letal
  solo; una trampa no cierra la única salida; el zapador abre la empalizada que otro no abre.

---

## 8. Cifras que fija este documento

| Cifra | Valor |
|---|---|
| Obstáculos de mundo | **8** |
| Trampas de campo | **6** |
| Puntos de trampa por campo | ≤ 4 |
| Ancho de atranco | **1,5 m** |
| Fuego | 5 daño/s · margen 1 m · **nunca letal solo** |
| Peso por pieza | ≤ 0,2 MB |
| Bloqueo de partida | **0** (siempre hay rodeo) |

---

## 9. Qué entra en la demo (Fase 1) — y qué sigue

> **Hasta aquí la demo.** El **tronco**, la **valla**, el **portón**, la **empalizada** y el
> **carro volcado** del tramo y de la aldea; la **puerta atrancada** del campo de puerta/aldea; el
> **fuego** del hogar de aldea. El zapador abriendo paso, funcionando.

> **Y sigue el juego completo.** Fosos, redes, derrumbes, cadenas y puentes cortados se añaden
> **con estas mismas reglas y estas mismas piezas**: crecer = más filas en `trampas.json`, no otra
> física.

---

## 10. Fuera de este documento

- Edificios y empalizadas → `09_EDIFICIOS_Y_ESTRUCTURAS.md`
- Puntos de interés del campo → `../batalla/02_TERRENO.md` §9
- Campos concretos → `../batalla/05_CATALOGO_DE_CAMPOS.md`
- Herramientas → `04_ITEMS_Y_EQUIPO.md`
- Favor y soborno → `../sistemas/03_FAVORES.md`, `../sistemas/06_ECONOMIA.md`
- Props del mundo → `../mundo/07_PROPS_Y_VEGETACION.md`
- Estilo y color → `../arte/00_ESTILO.md`
