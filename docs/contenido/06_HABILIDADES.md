# 06 · Habilidades — lo que sabes hacer

**Estado:** ✅ **aprobado por el dueño (aprobación en bloque, 2026-09-30). Documento final.**
**Enmienda 2026-10-01:** se **descartan los talentos** (confirmado) y entra un **árbol de
habilidades** con **activas y pasivas** (§4). El resto del documento no cambia.

> El campo ya tiene **3 botones del héroe** (Golpe · Guardia · Desvío) y **3 órdenes de tropa**
> (Cargar · Seguirme · Defender) (`../batalla/00_REGLAS.md` §5–§6). Aquí viven la **cuarta tecla
> (Habilidad)**, las **acciones propias de las tropas** y el **árbol de habilidades** del héroe:
> cuántas hay, qué cuestan, cómo se aprenden y cómo se eligen. La presentación, en
> `../batalla/04_PRESENTACION.md`; los costes de aliento, en `../batalla/01_CIFRAS.md` §3.
>
> **Habilidades, ids y cifras son propuesta de diseño** (cambiables → `../DECISIONES.md`).

---

## 1. Lo que ya está cerrado (no se toca)

| Acción | Coste | Efecto | Fuente |
|---|---|---|---|
| **Golpe** | 0 | Ataque con tu arma; cadencia **1,2 s** | `../batalla/01_CIFRAS.md` §3 |
| **Guardia** | 0 | Ventana **0,5 s**; reduce daño **75 %** | idem |
| **Desvío** | **15 de aliento** | **0,35 s** de invulnerabilidad | idem |
| **Aliento** | — | **100**, regenera **5/s** fuera de acción | idem |
| **Cargar / Seguirme / Defender** | — | Órdenes globales de tropa | `../batalla/00_REGLAS.md` §6 |

- **Regla dura:** las habilidades nuevas son **aditivas**; **no** cambian los 3 botones ni las 3
  órdenes, que ya están aprobados (regla 6 de `../../AGENTS.md`).

---

## 2. La cuarta tecla: Habilidad

- El botón **Habilidad** abre una **tira corta de habilidades** (no un menú anidado,
  `../interfaz/00_CONTROLES.md` §1). Un toque elige; el juego **sigue** (el reloj no se para,
  `../batalla/00_REGLAS.md` §3).
- **Todas las habilidades cuestan aliento** (`../batalla/01_CIFRAS.md` §3) o son **de una vez por
  batalla**. No hay maná ni cooldowns largos: hay **aliento** y **decisión**.
- **Ninguna habilidad sube un número pelado.** Cada **activa** cambia lo que haces en el momento
  y cada **pasiva** cambia una **decisión de campo**  (cuántas veces puedes Desviar, si te empujan,
  a quién llega tu voz), no una estadística suelta. El **techo de daño** de
  `../batalla/01_CIFRAS.md` §2 (90 héroe / 45 tropa) **no se pasa nunca**.
- **Acordes al tipo de juego:** todas son **medievales y terrenales** — lo que haría un humano con
  una espada, una voz y aguante. **Sin magia, sin proyectiles mágicos, sin combos, sin «ultimates»
  ni botones** que ganen solos. Si una habilidad no cabría en un campo de batalla real de hace
  siglos, **no entra** (Pilares 1–6 de `../VALCORIA_DEUDA_DE_SANGRE.md`). Los 12 nodos del árbol
  (§4) pasan ese filtro.

---

## 3. El tronco: las 4 habilidades del héroe (no se eligen)

| id | Habilidad | Coste | Efecto | Se aprende |
|---|---|---|---|---|
| `hab_estocada` | **Estocada** | 30 aliento | Golpe cargado: **+50 %** de daño, rompe Guardia | Nivel 3 |
| `hab_grito` | **Grito de mando** | — | **1 vez/batalla**: +10 de moral en 8 m | Nivel 12 |
| `hab_aguante` | **Aguantar** | 40 aliento | 3 s sin moverte: daño recibido **−50 %** | Nivel 26 |
| `hab_reagrupe` | **Llamada** | — | **1 vez/batalla**: reagrupa a los que huyeron a 10 m (`../batalla/03_IA_Y_ORDENES.md` §6) | Nivel 42 |

- **Se aprenden por nivel** (`../sistemas/05_PROGRESION.md` §1): al llegar al nivel, la habilidad
  está disponible; no se compra con oro.
- Estas cuatro son el **tronco**: llegan **solas** y **no** se eligen ni se reparten. El árbol (§4)
  crece **por encima** del tronco, con habilidades que **sí** se eligen.
- **Techo:** ninguna habilidad supera el **daño máximo por golpe** de `../batalla/01_CIFRAS.md`
  (90 héroe). **Contramedida justa:** la IA puede **Guardia** contra `hab_estocada`; el enemigo
  también puede reagrupar (`../batalla/03_IA_Y_ORDENES.md` §3.2). No hay botón que gane solo.

---

## 4. El árbol de habilidades (activas y pasivas)

**Descartado el árbol de talentos; entra el árbol de habilidades.** No sube números: **elige qué
deudas de combate sabes pagar**. Es corto y se lee de un vistazo (Pilar 6).

### 4.1 Cómo se abre

- **3 ramas** — **FILO** (cómo pegas), **MURO** (cómo aguantas), **VOZ** (cómo mandas).
- **4 nodos por rama** = **12 nodos**; **5 activas** y **7 pasivas**.
- Cada nodo pide un **nivel mínimo** y el **nodo anterior de su misma rama** (el primero no pide
  padre). No hay nodos cruzados entre ramas: la rama entera es un camino. **Niveles de los pisos:
  3 · 15 · 30 · 48** (escala del héroe 1-60, `../sistemas/12_NIVELES_DEL_HEROE.md`).
- Se reparte en la **pausa de campamento / escribanía**, **nunca en caliente**: en batalla la tira
  del botón **Habilidad** solo muestra lo ya elegido (`../batalla/00_REGLAS.md` §5).
- **No se puede tener todo:** hay **más nodos que puntos** (abajo), así que cada partida elige un
  héroe distinto **con las mismas reglas**.

### 4.2 Puntos de juramento (lo que se reparte)

| Fuente | Cuánto | Nota |
|---|---|---|
| **Nivel** | **1 cada 6 niveles** (6 · 12 · 18 · 24 · 30 · 36 · 42 · 48 · 54 · 60) | Total por nivel: **10** |
| **Deuda mayor saldada** | **+1** cada una | No sube el tope: **llega antes** al máximo (tope +3) |
| **Máximo** | **10** puntos (el total nunca lo pasa) | Para **12** nodos: **siempre faltan 2** |

- **Coste de un nodo:** **1 punto**, siempre. La estructura la marca el **nivel** (§4.1), no el precio.
- **Sin resparto gratis:** los puntos una vez gastados, gastados están (la Firma y la Crónica los
  recuerdan). **✅ Decidido (2026-10-01): sí se puede olvidar una rama**, pagando **oro y 1 día**
  en la escribanía (`../contenido/09_EDIFICIOS_Y_ESTRUCTURAS.md`). Los nodos gastados **no
  devuelven** el punto: recuerdan que cambiaste de oficio de armas.
- **Todo es aditivo en el guardado:** el reparto vive en `SaveState.juramento`
  (**SAVE_VERSION 3**, §8); migrar rellena vacío, nunca borra.

### 4.3 Las 3 ramas y sus 12 nodos

**Rama FILO — cómo pegas** (activas ofensivas + 2 pasivas)

| id | Tipo | Nivel | Efecto |
|---|---|---|---|
| `arb_filo_1` | **pasiva** | 3 | **Plantado** (1 s sin moverte): tu golpe lleva **+15 %** de daño (techo 90) |
| `arb_filo_2` | **activa** | 15 | **Barrido** (35 aliento): golpe en **180°** a 2,5 m que **aparta** a los de delante; daño de un golpe normal |
| `arb_filo_3` | **pasiva** | 30 | Guardia en el **primer 0,15 s**: devuelve **25 %** del daño bloqueado |
| `arb_filo_4` | **activa** | 48 | **Tajo de juramento** (**1/batalla**): rompe la Guardia y **hace temblar** 3 m; **sin daño extra** |

**Rama MURO — cómo aguantas** (pasivas defensivas + 1 activa)

| id | Tipo | Nivel | Efecto |
|---|---|---|---|
| `arb_muro_1` | **pasiva** | 3 | **Desvío cuesta 10** (de 15) |
| `arb_muro_2` | **pasiva** | 15 | Con la **Guardia en alto** no te empujan ni te rodean |
| `arb_muro_3` | **activa** | 30 | **Plantar los pies** (20 aliento): **4 s** sin poder andar, inmune a empuje; el aliento **no** regenera |
| `arb_muro_4` | **pasiva** | 48 | **Último aliento** (**1/batalla**): un golpe que te tumbaría te deja a **1** de vida y te regala un **Desvío** |

**Rama VOZ — cómo mandas** (pasivas de mando + 2 activas)

| id | Tipo | Nivel | Efecto |
|---|---|---|---|
| `arb_voz_1` | **pasiva** | 3 | **Grito** y **Llamada** alcanzan **+50 %** (8→12 m; 10→15 m) |
| `arb_voz_2` | **pasiva** | 15 | Los que reagrupas **no vuelven a huir** durante **20 s** |
| `arb_voz_3` | **activa** | 30 | **Rodilla en tierra** (25 aliento): tus tropas a 12 m **defienden 5 s** sin gastar la orden |
| `arb_voz_4` | **activa** | 48 | **Última orden** (**1/batalla**): tus tropas a 15 m **no huyen 8 s** aunque su moral esté rota |

- **Ejemplos de reparto** (con 7 puntos de nivel): cerrar **FILO** entera + `arb_muro_1` +
  `arb_voz_1`; o ir a mitades de **MURO** y **VOZ**. Nunca las 3 enteras: eso son 12 puntos y el
  techo por nivel es 7 (10 con todas las deudas mayores).
- **Sin micromando:** ninguna habilidad **selecciona unidades** ni abre menús; **Rodilla en tierra**
  es una orden local con temporizador, no un control de escuadrón (`../batalla/03_IA_Y_ORDENES.md`).
- **Contramedida justa:** los capitanes juegan con las **mismas reglas** (`02_CAPITANES_Y_NEMESIS.md`);
  si pueden romper tu Guardia, **tú también** puedes romper la suya.

### 4.4 Requisito de nivel de **todas** las habilidades del héroe

**Ninguna habilidad se aprende ni se usa sin cumplir su requisito de nivel.** El nivel no se salta
con oro: el árbol solo **añade** el gasto de puntos, nunca sustituye el nivel. Cuadro completo
(tronco + árbol), en una página:

| Habilidad | Vía | Requisito de nivel | Requisito además |
|---|---|---|---|
| `hab_estocada` | tronco | **Nivel 3** | — |
| `hab_grito` | tronco | **Nivel 12** | — |
| `hab_aguante` | tronco | **Nivel 26** | — |
| `hab_reagrupe` | tronco | **Nivel 42** | — |
| `arb_filo_1` · `arb_muro_1` · `arb_voz_1` | árbol (piso 1) | **Nivel 3** | — |
| `arb_filo_2` · `arb_muro_2` · `arb_voz_2` | árbol (piso 2) | **Nivel 15** | nodo **1** de su rama |
| `arb_filo_3` · `arb_muro_3` · `arb_voz_3` | árbol (piso 3) | **Nivel 30** | nodo **2** de su rama |
| `arb_filo_4` · `arb_muro_4` · `arb_voz_4` | árbol (piso 4) | **Nivel 48** | nodo **3** de su rama |

- **Reglas del requisito:** se comprueba **al repartir** (pantalla del árbol) y **al usar** (en
  batalla); un nodo con el nivel justo pero **sin su padre** sigue bloqueado; el nivel y el punto
  se gastan **a la vez**. La validación vive en `js/systems/habilidades.js` y en
  `tools/validate_data.js` (§8).
- **Las acciones de las tropas no tienen nivel propio:** salen de su **rol** (§5), no del nivel del
  héroe. Las habilidades del **enemigo** no se copian (`01_ENEMIGOS.md` §2).

---

## 5. Acciones de las tropas (3)

Las tropas **no tienen botones propios** (no hay micromando): sus acciones salen de su **rol** y
de la **orden** vigente.

| Rol | Acción | Cuándo | Efecto |
|---|---|---|---|
| **Portaestandarte** (`00_TROPAS.md` §3.3) | **Bandera en alto** | Siempre en pie | **+5 de moral** al bando |
| **Zapador** | **Abrir paso** | Ante puerta o empalizada | Rompe el obstáculo (`12_TRAMPAS_Y_OBSTACULOS.md`) |
| **Ballestero / arquero** | **Descarga** | Orden **Defender** | Primer disparo **+25 %** si no se ha movido |

- **Del barbero:** su **venda** evita 1 baja de campaña por batalla (`00_TROPAS.md` §3.3).
- **De la familia enemiga:** sus rasgos son su «habilidad» (`01_ENEMIGOS.md` §2): no se copian.

---

## 6. Qué se compra, qué se aprende y qué se elige

| Vía | Qué da | Dónde |
|---|---|---|
| **Se aprende (nivel)** | El **tronco**: las 4 habilidades del héroe (§3) | `../sistemas/05_PROGRESION.md` |
| **Se elige (juramento)** | Los **12 nodos** del árbol (§4), con **puntos** | Este documento §4 |
| **Se compra** | Mejoras de equipo (`04_ITEMS_Y_EQUIPO.md` §4) y **entrenamiento** de tropa | Herrería / plaza |
| **Se hereda** | Un **artefacto** que cambia una regla (`07_ARTEFACTOS.md`) | Trama |
| **Se gana con un compañero** | Su **aporte de oficio** (`03_COMPANEROS.md` §4) | Nodos `une` |

- **Las mejoras duras** (que cambian cómo juegas, no solo números) llegan en la **Fase 5**
  (`../sistemas/05_PROGRESION.md` §4). **Nunca** rompen el guardado: son aditivas y acotadas. El
  **árbol de habilidades es de antes** (Fase 3): es donde el dueño pide **elección**, no potencia.
- **Entrenar una tropa** cuesta oro y un día, y sube su **veteranía** (`00_TROPAS.md` §6): +2
  ataque o +4 vida, a elegir por rol. Techo = el balance de `../batalla/01_CIFRAS.md`.

---

## 7. Cómo se enseñan sin tutorial

- **La primera batalla enseña sola** (`../batalla/04_PRESENTACION.md` §7): el botón **Golpe** se
  ilumina al primer contacto; la orden **Cargar** produce el «Tres huyen» que explica la victoria.
- **La ayuda es de una línea y 3 s** (`../interfaz/02_HUD.md`) y **se puede desactivar entera**
  (`../interfaz/04_ACCESIBILIDAD.md`).
- **Cada habilidad nueva se aprende usándola** en una pelea fácil del camino, no con un muro de
  texto: misma filosofía del Pilar 6.
- **El árbol se enseña al abrirse:** al ganar el **primer punto de juramento** (nivel 2), se ve una
  vez la pantalla de las **3 ramas** con **una línea cada una**; a partir de ahí, silencio.
- **Sin árbol de talentos de estadísticas:** el héroe es **un deudor con espada**
  (`../sistemas/05_PROGRESION.md` §1); el árbol no le da **poder**, le da **elección** entre pocas
  y claras habilidades.

---

## 8. Datos, tipos y validación

- **Datos:** `data/habilidades.json` — `{ id, tipo (heroe/tropa), coste, efecto, aprende_en,
  una_vez }` para el tronco, **más** `{ rama (filo/muro/voz), padre, nivel, pasiva }` para los
  **nodos del árbol** (§4.3). Un solo fichero, dos familias de fila.
- **Tipos:** `Habilidad` y `NodoArbol` en `js/data/game_types.js` (una sola vez, regla 4).
- **Guardado:** `SaveState.juramento = { puntos, gastados: [] }` — **aditivo** (**SAVE_VERSION 3**,
  `../produccion/02_GUARDADO_Y_DATOS.md`); `migrateSave()` rellena vacío, nunca borra.
- **Validación:** esquema en `js/data/schemas.js` + cruce del `coste` con el **aliento** de
  `../batalla/01_CIFRAS.md` §3, del `aprende_en`/`nivel` con `NIVEL_MAX` de `save.js` y del
  `padre`/`rama` dentro de sí mismo, en `tools/validate_data.js`. **12 nodos / ≤10 puntos**.
- **Sistema puro:** `js/systems/habilidades.js` — tronco + coste, efecto y «una vez» del árbol;
  sin DOM, sin reloj, RNG inyectado.
- **Tests:** `tests/habilidades.test.js`, mínimo 3 casos (normal, borde, error): una habilidad sin
  aliento no lanza; el «una vez por batalla» no vuelve; un nodo **sin nivel o sin padre** no se
  compra; el reparto **no pasa** de 10 puntos; **ningún efecto supera el tope de daño**
  (`../batalla/01_CIFRAS.md` §2); `hab_reagrupe`/`arb_voz_4` no superan el tope de reagrupación de
  `../batalla/03_IA_Y_ORDENES.md` §9.

---

## 9. Cifras que fija este documento

| Cifra | Valor |
|---|---|
| Botones del héroe | **3** (Golpe · Guardia · Desvío) + tecla **Habilidad** |
| Órdenes de tropa | **3** (Cargar · Seguirme · Defender) |
| Tronco (se aprenden solas) | **4** (niveles 3 · 12 · 26 · 42) |
| Árbol | **3 ramas × 4 nodos = 12** (**5 activas · 7 pasivas**) |
| Puntos de juramento | **1 cada 6 niveles** (10; tope total **10**), +1 por deuda mayor |
| Coste de nodo | **1 punto**; nivel mínimo 3 · 15 · 30 · 48 + padre de la rama |
| Requisito de nivel | **Obligatorio y no se salta con oro** (§4.4) |
| Acciones de tropa | **3** (bandera · abrir paso · descarga) |
| Coste en batalla | aliento (100, +5/s) o **1 vez por batalla** |
| Entrenamiento | oro + 1 día · veteranía +2 ataque o +4 vida |

---

## 10. Qué entra en la demo (Fase 1) — y qué sigue

> **Hasta aquí la demo.** Los **3 botones** y las **3 órdenes** con sus reglas (ya cerrados), la
> tecla **Habilidad** con **1** habilidad del tronco en el Acto I (`hab_estocada`, nivel 3), las
> acciones del portaestandarte y el zapador, y el **árbol abierto por su primer piso**: los **3
> nodos de nivel 3** (`arb_filo_1`, `arb_muro_1`, `arb_voz_1`) con **1 punto** ganado al nivel 6.
> En la demo el héroe **no pasa del nivel 15** (tope de la demo).

> **Y sigue el juego completo.** Los pisos 6 · 9 · 12 de las tres ramas y el resto del tronco se
> añaden **con estas mismas reglas**: crecer = más filas en `habilidades.json`, no botones ni
> sistemas nuevos. Las **mejoras duras** siguen llegando en la Fase 5 sin cambiar el guardado.

---

## 11. Fuera de este documento

- Botones, órdenes y moral → `../batalla/00_REGLAS.md`, `../batalla/01_CIFRAS.md`
- IA y reagrupe → `../batalla/03_IA_Y_ORDENES.md`
- Cómo se ve y se enseña → `../batalla/04_PRESENTACION.md`
- Roles y rasgos de tropa → `00_TROPAS.md`
- Subida de nivel y puntos de juramento → `../sistemas/05_PROGRESION.md`
- Guardado versionado → `../produccion/02_GUARDADO_Y_DATOS.md`
- Mejoras de equipo → `04_ITEMS_Y_EQUIPO.md`
