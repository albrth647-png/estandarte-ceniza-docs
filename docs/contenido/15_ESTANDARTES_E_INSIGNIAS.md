# 15 · Estandartes e insignias — de quién es cada bandera

**Estado:** ✅ **aprobado por el dueño (aprobación en bloque, 2026-09-30). Documento final.**

> En el campo, **una bandera se lee antes que una cara**. Aquí está la **heráldica de cada casa**,
> el **estandarte de tu compañía** (que cambia con tu Firma) y las **insignias** de la Ordenanza y
> de los Marcados. Las casas, en `../historia/05_CASAS_Y_FACCIONES.md`; el portaestandarte, en
> `00_TROPAS.md` §3.3; cómo se pinta, en `../arte/00_ESTILO.md` §5.
>
> **Toda la heráldica es original** (regla 8 de `../../AGENTS.md`): ningún símbolo, color ni lema
> copia a otro juego. **Nombres, colores y símbolos son propuesta de diseño** (cambiables →
> `../DECISIONES.md`).

---

## 1. Cómo se lee una bandera en el campo

- **Silueta primero:** forma y símbolo se reconocen a **60 m** (`../arte/00_ESTILO.md` §4); el color
  es **refuerzo**, no información (`../interfaz/04_ACCESIBILIDAD.md` §2).
- **Colores de casa:** cada facción tiene **2 colores + contorno** (regla de iconos,
  `../arte/05_ICONOS.md` §4).
- **La bandera fija el bando:** tu bando, el de la casa o el sin ley (bandidos no llevan enseña).
- **Nunca solo color:** un daltoniano distingue las banderas por **forma** (`§4`).

---

## 2. Heráldica de las casas (original)

| Facción | Campo | Símbolo | Lema (prop.) |
|---|---|---|---|
| **Casa Altamir** | Óxido + oro | **Puente almenado con una moneda** | «Quien cruza, paga» |
| **La Escribanía** | Hierro + sebo | **Pluma sobre un sello** | «La cuenta cuadra» |
| **La otra ribera** | Verde agua + ceniza | **Barca partida por una ola** | «El libro no cruza» |
| **Doña Sira** | Sebo + sangre | **Libro abierto con una espada** | «Reclamo la espada» |
| **Los Marcados** | Harapo + hierro | **La marca del cadalso, tosca** | (nace en el Acto I, §3) |
| **Casas menores** | A elegir entre 4 paletas | Molino, maza, llave de gremio, haz de trigo | «Su parte del peaje» |

- **Toda bandera de casa lleva una parte lisa** (donde se ve la insignia) y una **borla o rapacejo**
  que la distingue a distancia.
- **La heráldica de casa se gana en `data/estandartes.json`** y se cruza con `data/facciones.json`
  (`../historia/05_CASAS_Y_FACCIONES.md` §5).

---

## 3. El estandarte de tu compañía

- **Cómo nace:** en el cadalso, con un **harapo** y la marca del cadalso encima
  (`../historia/00_PREMISA.md`). Es la primera bandera que llevas.
- **Cambia con tu Firma** (`../sistemas/01_FIRMA.md` §3): no cambia de forma por comprar, sino por
  **lo que haces**. Propuesta de **5 estados**:

| Estado | Firma | Cómo se ve |
|---|---|---|
| **Harapo** | Sin nombre | Tela cruda y sucia; la marca a la vista |
| **Paño** | Correcto / Honrado | Tela remendada, ya con tu símbolo |
| **Enseña** | Palabra dada | Tela limpia, símbolo bordado, **oro** |
| **Sombra** | Duro / Fiera | Tela oscura, símbolo tachado |
| **Grillete** | Hiena | Tela negra con **hierro** de cadalso |

- **Tu símbolo lo eliges tú en la primera bandera** (una forma simple: cuervo, espada rota, cruz,
  puente, sello…). **Original y tuyo**, no de ninguna casa (`§1`).
- **Cambiar de estado es automático** con la Firma (sin coste), pero el **rastro queda** en la
  Crónica (`../sistemas/04_CRONICA.md`).

---

## 4. Insignias de la Ordenanza y de los Marcados

- **El sello del Escribano:** la **marca de pluma y sello** en los documentos y carteles
  (`../historia/08_TEXTO_DEL_MUNDO.md`). Un documento **sin sello no vale** (`../sistemas/01_FIRMA.md` §7).
- **La marca del cadalso:** la señal en la piel que **todos los Marcados llevan**
  (`../sistemas/07_CICATRICES.md` §1). No es bandera: es **crédito y condena**.
- **El brazalete de Marcado:** una cinta con la marca del cadalso que distingue a tu tropa del
  enemigo en el campo (lectura a distancia, `§1`).
- **La insignia de casa:** un **broche** o **cinta** del color de la casa; el que la lleva responde
  por ella.

---

## 5. Portar la bandera (y qué pasa si cae)

- **La lleva el portaestandarte** (`00_TROPAS.md` §3.3): mientras está **en pie**, el bando tiene
  **+5 de moral** (se suma a la contextura del capitán, `../batalla/03_IA_Y_ORDENES.md` §4).
- **Si cae el abanderado:** el bando **pierde el +5**; la bandera queda en el suelo y **cualquiera**
  puede recogerla (**una** unidad de tu bando, con el toque de «Seguirme» cerca).
- **La bandera caída es un momento, no una derrota:** no cambia la moral de golpe, solo deja de
  sumar (ninguna trampa mortal, Pilar 3).
- **Bandera de casa tomada:** es **trofeo** (`07_ARTEFACTOS.md` §4): vale oro y respeto, y su casa
  la reclama.

---

## 6. Arte: cómo se pinta sin coste alto

- **Atlas de símbolos:** todos los emblemas viven en **una sola textura** (o pocas) y las banderas se
  hacen **tela + símbolo + color** por shader/pintura, no con un modelo por casa
  (`../arte/00_ESTILO.md` §5).
- **Recoloreo:** la misma tela sirve para Altamir (óxido) y la ribera (verde) cambiando paleta.
- **Bandera animada:** un clip corto de **viento** (`../arte/03_ANIMACIONES.md` §3); los props
  instanciados no se animan.
- **Presupuesto:** ≤ **0,15 MB** por bandera base; el atlas de símbolos ≤ **0,5 MB**.
- **Sin texto en la bandera:** el lema va en `txt_*` al enfocar, no bordado
  (`../interfaz/03_I18N_Y_TONO.md`).

---

## 7. Datos, tipos y validación

- **Datos:** `data/estandartes.json` — `{ id, faccion, campo, simbolo, lema_txt, estados, modelo,
  atlas }`.
- **Tipos:** `Estandarte` y `EstandarteCompania` en `js/data/game_types.js` (una sola vez, regla 4).
- **Validación:** esquema en `js/data/schemas.js` + cruce de `faccion` con `data/facciones.json`
  (`../historia/05_CASAS_Y_FACCIONES.md` §5) y del `modelo`/`atlas` con `data/assets.json` en
  `tools/validate_data.js`.
- **Sistema puro:** `js/systems/estandartes.js` — elige el estado por Firma y aplica el +5 de moral
  mientras el abanderado esté en pie; sin DOM ni reloj.
- **Tests:** `tests/estandartes.test.js`, mínimo 3 casos (normal, borde, error): el estado cambia con
  la Firma; sin abanderado se pierde el +5; una facción sin heráldica rompe la carga.

---

## 8. Cifras que fija este documento

| Cifra | Valor |
|---|---|
| Facciones con heráldica | **6** |
| Colores por bandera | **2 + contorno** |
| Estados del estandarte del jugador | **5** (harapo → grillete) |
| Moral por portaestandarte | **+5** al bando mientras esté en pie |
| Lectura a distancia | **60 m** (silueta, sin depender del color) |
| Peso por bandera / atlas | ≤ 0,15 MB / ≤ 0,5 MB |
| Texto bordado | **0** (lema en `txt_*`) |

---

## 9. Qué entra en la demo (Fase 1) — y qué sigue

> **Hasta aquí la demo.** El **harapo** inicial y el **paño** (2 de los 5 estados), la heráldica de
> **Altamir** y de **los Marcados** y el **brazalete de Marcado**, con el portaestandarte sumando
> **+5**. La bandera caída y el trofeo, funcionando.

> **Y sigue el juego completo.** Los estados **Enseña**, **Sombra** y **Grillete**, y las heráldicas
> de la **Escribanía**, **Sira** y **las casas menores**, se añaden **con estas mismas reglas**: más
> filas en `estandartes.json` y el mismo atlas, no un modelo por casa.

---

## 10. Fuera de este documento

- Casas y facciones → `../historia/05_CASAS_Y_FACCIONES.md`
- Portaestandarte y moral → `00_TROPAS.md`, `../batalla/01_CIFRAS.md` §5
- Cómo se ve el campo → `../batalla/04_PRESENTACION.md`
- La marca del cadalso → `../sistemas/07_CICATRICES.md`
- Estilo, color y reutilización → `../arte/00_ESTILO.md`
- Iconos → `../arte/05_ICONOS.md`
- Trofeos → `07_ARTEFACTOS.md`
