# 14 · Profesiones del héroe — en qué te has ganado el pan

**Estado:** ✅ **aprobado por el dueño (aprobación en bloque, 2026-09-30). Documento final.**
**Enmienda 2026-10-01 (cerrada):** el dueño confirma el **núcleo de 6 profesiones**, el **maestro
por profesión repartido en las plazas**, los **rangos** y el coste de **cambiar**. Se añaden las
**cadenas de oficio (derivados)** con sus **recursos en el mapa** (§5) y la profesión
**Equitación** que se desbloquea **después de la demo** (§4b).
**Enmienda 2026-10-02 (cerrada):** los **rangos los abre el XP de oficio, no el nivel del héroe**;
cada oficio **fabrica** cosas y el maestro reparte **encargos de oficio** (clase 11). Todo eso
vive en [`15_FABRICACION_Y_RECETAS.md`](15_FABRICACION_Y_RECETAS.md).

> **Qué es una profesión:** un **oficio** del héroe (herrero, sanador, guía…) que **no** es una
> clase ni un árbol: es **una forma de ganarte la vida** que cambia lo que haces **entre**
> batallas y te da **una ventaja corta dentro**. El combate sigue siendo 3 botones + el árbol de
> habilidades (`../contenido/06_HABILIDADES.md`); la profesión **no** añade botones.
>
> **Aviso de balance:** ninguna ventaja de combate supera el **daño máximo por golpe** de
> `../batalla/01_CIFRAS.md` §2 (90/45) ni cambia los 3 botones/órdenes (regla 6 de
> `../../AGENTS.md`).

---

## 1. Cómo funcionan

- **Solo el héroe** tiene profesiones; las tropas, compañeros y capitanes se quedan con su
  **rol** (campo) y su **oficio narrativo** (`../contenido/03_COMPANEROS.md`).
- **Una profesión activa a la vez.** Aprender la primera es tu **origen**; las demás se aprenden
  con el **maestro de su oficio** (§2).
- **Cambiar de profesión:** cuesta **3 días de oficio** (no oro): el mundo nota que cambiaste
  (`../sistemas/09_TIEMPO_Y_MUNDO_VIVO.md`). ✅ **Cerrado 2026-10-01.** La barra de XP de oficio de
  la que dejas **se pierde** (`15_FABRICACION_Y_RECETAS.md` §2).
- **Dos familias de ventaja:**
  - **Fuera del combate** (el grueso): recursos, precios, cura, viaje, trato, puertas de Firma.
  - **Dentro del combate** (corta y honesta): una ventaja **situacional**, nunca un botón nuevo.
- **Aprender una profesión abre su recurso base en todo el mapa** y **sus recetas**
  (`15_FABRICACION_Y_RECETAS.md` §3 y §5). Eso es lo que hace la profesión **utilizable**, no solo
  decorativa.

---

## 2. Rangos, XP de oficio y quién enseña

- **Cada profesión tiene 3 rangos:** **Aprendiz · Oficial · Maestro**. ✅ **Cerrado.**
- **Los rangos los abre el XP de oficio**, no el nivel del héroe (**cambia lo de 2026-10-01**):
  | Rango | XP de oficio | lo que abre |
  |---|---|---|
  | **Aprendiz** | **0** | 3 recetas, ventaja de fuera y de dentro |
  | **Oficial** | **150** | +3 recetas, techo **buena** y `+1` de mejora |
  | **Maestro** | **450** | +3 recetas, techo **rara** y `+1` de mejora |

  Las cifras y sus fuentes están en [`15_FABRICACION_Y_RECETAS.md`](15_FABRICACION_Y_RECETAS.md) §2.
- **Un maestro por profesión**, **repartido entre las plazas** del reino (nadie enseña dos oficios):

  | Profesión | Maestro en | Zona |
  |---|---|---|
  | **Herrero** | Taller de forja del **Patio del Cadalso** (la ciudad) | La Marca del Sur |
  | **Sanador** | Capilla de la Marca del Sur (aldea de la demo) | La Marca del Sur |
  | **Tratante** | Mercado fluvial de la **villa de la Ribera** | La Ribera |
  | **Cazador** | **Villa de la Serranía** (pastos y hayedos) | La Serranía |
  | **Escribano** | **Villa de los Altos de Altamir** | Los Altos |
  | **Guía** | Refugio/villa de la **Tierra del Paso** | La Tierra del Paso |
  | **Equitación** | Establo de la Ribera (post-demo, §4b) | La Ribera |

- **El maestro reparte encargos de oficio** (clase 11, `../misiones/00_TIPOS_DE_ENCARGO.md` §1):
  **3 por rango**, y cada uno trae **1 receta** (`15_FABRICACION_Y_RECETAS.md` §9).
- **No bloquea nada:** la profesión **no** es una puerta social; eso es la **Firma** y la
  **memoria** (`../sistemas/01_FIRMA.md`). La profesión **ayuda**, no manda.

---

## 3. Análisis de candidatas (12) — veredicto cerrado

| # | Profesión | Fuera del combate | Dentro del combate | Veredicto |
|---|---|---|---|---|
| 1 | **Herrero** | Mejoras de equipo más baratas y mejor techo | Reparar tu armadura una vez en campaña | ✅ **Núcleo** |
| 2 | **Sanador / Barbero** | Cura heridas de campaña; vende/compra vendas | Venda rápida (evita 1 baja) | ✅ **Núcleo** |
| 3 | **Guía / Rastreador** | Atajos, evita emboscadas, lee el tiempo | Detecta enemigos ocultos antes | ✅ **Núcleo** |
| 4 | **Escribano** | Puertas de Firma, Crónica más rica, precios | Reagrupa un poco más rápido | ✅ **Núcleo** |
| 5 | **Tratante / Mercader** | Mejores precios, trueque, fiado | Soborno en el campo (una vez) | ✅ **Núcleo** |
| 6 | **Cazador** | Comida y cueros; rastrea bestias | Daño a distancia con lo que haya | ✅ **Núcleo** |
| 7 | **Cocinero / Tabernero** | Cocina raciones; banquete de moral | — | ⬜ No (se solapa con Sanador y con `14_COMIDAS_Y_BEBIDAS.md`) |
| 8 | **Trovador / Juglar** | Rumores, Firma, canciones | Aura de moral corta | ⬜ No (se solapa con Escribano) |
| 9 | **Ladrón / Ganzúa** | Ganzúa, sigilo, roba | Ataque por la espalda | ⬜ No (no hay sigilo diseñado) |
| 10 | **Contrabandista** | Mercado negro, salta peajes | — | ⬜ No (se solapa con Tratante) |
| 11 | **Caballerizo** | Cuida bestias y carretas | — | ⬜ No (**Equitación** lo sustituye, §4b) |
| 12 | **Sacerdote / Capellán** | Consuela, funerales, Firma | Última oración (moral) | ⬜ No (sin magia; solapa con Escribano) |

**Criterios:** originalidad (nada de otro juego), que **quepa en el armazón** (sistemas puros, sin
sigilo ni magia), que **cambie decisiones** y no solo números, y que **no duplique** otro sistema.

---

## 4. Núcleo confirmado (6 profesiones) ✅

| Profesión | Maestro (§2) | Fuera del combate (Aprendiz → Maestro) | Dentro del combate (1 ventaja corta) |
|---|---|---|---|
| **Herrero** | Patio del Cadalso | −10 % / −20 % / −30 % en mejoras; abre el techo +1 al Maestro | **Reparar** tu armadura una vez por batalla |
| **Sanador** | Capilla de la Marca del Sur | Cura 1 / 2 / 3 heridas de campaña por descanso | **Venda** que evita 1 baja (se acumula con el barbero) |
| **Guía** | Tierra del Paso | Atajo 1 / 2 / 3 veces por viaje; −emboscada | **Ojo**: enemigos ocultos a 40 / 50 / 60 m |
| **Escribano** | Villa de los Altos | Puertas de Firma más fáciles; Crónica con más voz | **Orden clara**: reagrupe 20 % más rápido |
| **Tratante** | Villa de la Ribera | −10 % / −15 % / −20 % al comprar; +5 % / +10 % / +15 % al vender | **Soborno**: neutralizas 1 unidad una vez |
| **Cazador** | Villa de la Serranía | +1 / +2 / +3 raciones por caza; cueros | **Tiro** a distancia con arco improvisado |

- **Se gana el pan, no la gloria:** ninguna profesión sube stats pelados; cambian **recursos,
  precios, viaje y una acción corta** de campo.
- **Lo que se fabrica con cada una** está en
  [`15_FABRICACION_Y_RECETAS.md`](15_FABRICACION_Y_RECETAS.md) §5 y §7 (9 recetas por profesión).
- **Sinergias:** Herrero ↔ equipo (`../contenido/04_ITEMS_Y_EQUIPO.md`); Sanador ↔ luto
  (`08_LUTO_Y_MORAL.md`); Guía ↔ viaje (`../mundo/02_VIAJE_Y_ENCUENTROS.md`); Escribano ↔ Firma
  (`01_FIRMA.md`); Tratante ↔ economía (`06_ECONOMIA.md`); Cazador ↔ bestias
  (`../contenido/08_ANIMALES_Y_CRIATURAS.md`).

### 4b. Equitación (la 7.ª, se compra tras la demo) ✅

- **Cuándo:** se desbloquea **después del Capítulo 1** (es decir, **después de la demo**).
- **Cómo:** **se compra** como cualquier otra profesión (en el **establo de la Ribera**) por
  **400 oro + 5 días de oficio** ✅ (cerrado 2026-10-01).
- **Qué da:** te montas (galope en el mapa, sin cambio de cámara de batalla) y montas mejor que
  los demás: la barca/establo te sale más barato y los caballos de otros se ganan antes.
- **Dónde vive también:** `../contenido/13_MONTURAS_Y_TRANSPORTE.md` §1 (montura del héroe).
- **En la demo no existe**: el Acto I es **a pie** (Pilar 4).

---

## 5. Cadenas de oficio y lo que el mapa tiene que tener

**Regla de diseño (2026-10-01):** toda profesión tiene **derivados** (qué necesita para existir) y
**el mapa tiene que traer todo lo que esa profesión consume o explota**. Si el recurso no está en
el mapa, **la profesión no entra**.

| Profesión | Derivado (qué necesita) | Dónde está en el mapa | Recurso requerido |
|---|---|---|---|
| **Herrero** | **Minería → hierro** + **leña** (carbón) | Vetas y escombreras de la Serranía y los Altos; leñador en bosque y arboleda | ✅ `hierro`, `leña` (`../contenido/05_RECURSOS_Y_MERCADO.md`) · `plata`, `piedra`, `resina` de nivel 2 ✅ |
| **Sanador** | **Herbolario → hierbas** + **cuero** (vendas) | Prados, riberas y campos de grano | ✅ `cuero` · ✅ `hierbas` (**recurso oficial**, 2026-10-01) |
| **Guía** | **Señales → refugios y cruces** | Nodos del grafo: refugios y cruces (`../mundo/00_MAPA.md` §2) | ✅ · `cuerda` de nivel 2 ✅ |
| **Escribano** | **Curtido → cuero/pergamino** | Curtidores y talabarteros de plaza | ✅ `cuero` |
| **Tratante** | **Mercado → los 11 recursos** | Plazas y mercados de las 5 zonas | ✅ (oro, hierro, grano, leña, cuero, hierbas, carne, plata, piedra, cuerda, resina) |
| **Cazador** | **Caza → cuero y carne** | Bosques, arboledas y prados (`../contenido/08_ANIMALES_Y_CRIATURAS.md`) | ✅ `cuero` · ✅ `carne` (**recurso oficial**, 2026-10-01) |
| **Equitación** | **Caballería → caballos y mulas** | Establos, praderas y dehesas (`../mundo/03_LUGARES.md`) | ✅ · `cuerda` (arreos) de nivel 2 ✅ |

- **Dónde se mapea:** cada recurso de la tabla se definirá como **fila de `lugares.json`** (por crear),
  como **prop del campo** (`../mundo/07_PROPS_Y_VEGETACION.md`) o como **fila de
  `recursos.json`**. Es decir: **mineral para la herrería, hierbas para el sanador, cuero para el
  escribano y el cazador, prado/establo para la equitación** — no pueden faltar.
- **Validación (regla 5):** `data/profesiones.json` lleva `recurso: [...]` y
  `tools/validate_data.js` **cruza cada recurso** con `recursos.json` / `props.json` /
  `lugares.json`. Una profesión con un recurso que no existe en el mapa **no arrancará** el juego (regla 5).
- ✅ **Cerrado (2026-10-01): `hierbas` y `carne` son recursos oficiales** — entran en
  `data/recursos.json` (precios en `../contenido/05_RECURSOS_Y_MERCADO.md` §2).
- ✅ **Cerrado (2026-10-02): 4 recursos de nivel 2 más** — `plata`, `piedra`, `cuerda`, `resina`
  (`15_FABRICACION_Y_RECETAS.md` §3). **Total: 11.**

---

## 6. Datos, tipos y validación

- **Datos (por crear):** `data/profesiones.json` — `{ id, rangos: [{xp, nombre_txt, fuera, dentro}], maestro,
  recurso: [], xp_por_rango }`.
- **Tipos:** `Profesion` y `ProfesionEstado` en `js/data/game_types.js` (regla 4).
- **Guardado:** `SaveState.profesion = { id, rango, xp, recetas: [] }` — **aditivo**
  (aditivo, `../produccion/02_GUARDADO_Y_DATOS.md`); la migración rellena vacío.
- **Validación:** esquema en `js/data/schemas.js` + cruce de cada `recurso` con los datos del mapa
  (§5) y de las recetas con `items.json` (`15_FABRICACION_Y_RECETAS.md` §10).
- **Sistema puro:** `js/systems/profesiones.js` — rangos, bonus de fuera y ventaja de dentro; sin
  DOM, sin reloj, RNG inyectado. La fabricación vivirá en `js/systems/fabricacion.js`.
- **Tests (por escribir):** `tests/profesiones.test.js` y `tests/recetas.test.js`, mínimo 3 casos (normal, borde,
  error): no se sube de rango sin XP de oficio; el cambio de profesión cuesta **3 días**; ninguna
  ventaja supera el techo de daño; una profesión con un recurso **ausente del mapa** se rechaza.

---

## 7. Cifras que fija este documento

| Cifra | Valor |
|---|---|
| Titulares | **solo el héroe** |
| Profesiones activas a la vez | **1** |
| Profesiones del núcleo | **6** ✅ (+ **Equitación** post-demo) |
| Rangos | 3: Aprendiz · Oficial · Maestro |
| **XP de oficio por rango** | **150** (Oficial) · **450** (Maestro) ✅ (ya no por nivel de héroe) |
| Cambio de profesión | **3 días de oficio** ✅ |
| Maestros | **1 por profesión**, repartidos por las plazas ✅ |
| Encargos de oficio | **3 por rango** (9 en total), clase **11** ✅ |
| Precio de Equitación | **400 oro + 5 días** ✅ |
| Recursos de las cadenas | **11** oficiales (7 de nivel 1 + 4 de nivel 2) ✅ |
| Recetas | **9 por profesión** (63 en total) ✅ |
| Ventajas | fuera (grueso) + **1** corta dentro |
| Cadenas | 7 cadenas con su recurso en el mapa (§5) |

---

## 8. Qué entra en la demo (Fase 1) — y qué sigue

> **Hasta aquí la demo.** **Una** profesión (la del origen) en rango **Aprendiz**, con sus
> **3 recetas base**, su recurso recolectable en el mapa y sus ventajas de fuera y de dentro; el
> **maestro de la Marca del Sur** (Herrero o Sanador) para el cambio. Los rangos Oficial/Maestro, el
> resto de maestros, la clase `oficio` completa y **Equitación** quedan fuera.

> **Y sigue el juego completo.** Las **6** del núcleo con sus 3 rangos, sus 9 recetas y su maestro;
> **Equitación** tras el Capítulo 1; los **4 recursos de nivel 2** desde el nivel 30; y **todo lo que
> cada oficio necesita en el mapa** (§5) se añaden **con estas mismas reglas**: crecer = más filas en
> `profesiones.json` + `recetas.json` y sus recursos en `lugares.json`/`props`, no un sistema nuevo.

---

## 9. Fuera de este documento

- **Recetas, materiales, joyería y armas nuevas** → [`15_FABRICACION_Y_RECETAS.md`](15_FABRICACION_Y_RECETAS.md)
- Habilidades y árbol → `../contenido/06_HABILIDADES.md`
- Niveles y XP → `12_NIVELES_DEL_HEROE.md`
- Equipo y mejoras → `../contenido/04_ITEMS_Y_EQUIPO.md`
- Recursos comerciales → `../contenido/05_RECURSOS_Y_MERCADO.md`
- Props y recolectables → `../mundo/07_PROPS_Y_VEGETACION.md`
- Compañeros y sus oficios → `../contenido/03_COMPANEROS.md`
- PNJ y gremios → `../mundo/04_PNJ.md`
- Montura del héroe → `../contenido/13_MONTURAS_Y_TRANSPORTE.md`
