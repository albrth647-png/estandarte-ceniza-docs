# 12 · Niveles — héroe (1 … 60), unidades y zonas

**Estado:** ✅ **aprobado por el dueño (aprobación en bloque, 2026-09-30). Documento final.**
**Enmienda 2026-10-01:** el dueño fija **nivel máximo del héroe = 60** y pide que **todo** (aforo,
habilidades, tropas, enemigos y zonas) **escale según el nivel del héroe**. Este documento es la
**casa única de la escala**; `05_PROGRESION.md` apunta aquí. Las **estadísticas** del héroe, en
`13_ESTADISTICAS_DEL_HEROE.md`; el balance del campo, en `../batalla/01_CIFRAS.md`.

> **Decisión:** nivel máximo **60** (2026-10-01). La constante vivirá en el módulo de guardado cuando exista. **La demo
> llega hasta el nivel 15**; los niveles 16-60 son del juego completo (§8).

> Regla de oro: **una sola escala (1 … 60) para todos** (héroe, tropa, compañero, capitán y
> enemigo). Lo que cambia es **quién sube por qué** y **qué zona te lo pone delante**.

---

## 1. La escala (1 … 60)

- **Nivel máximo del héroe: 60.** El resto de unidades usa la misma escala, con techo propio.

| Quién | Sube por | Techo |
|---|---|---|
| **Héroe** | Cerrar encargos, ganar batallas y **resolver deudas** | **60** |
| **Tropa / compañero** | **Veteranía**: batallas ganadas y supervivencia | nivel de zona **+ 2** |
| **Capitán / némesis** | **Sobrevivir con testigos** → rango propio | **60** |
| **Enemigo de zona** | No sube: **lo pone la zona** (§3) | — |

- **El XP solo lo lleva el héroe** (campo previsto `nivel_personaje` del guardado); el resto sube por **hechos**.
- **Nadie pasa de su techo:** un enemigo de zona 12 no se convierte en nivel 40 solo porque tú
  llegues arriba; el mundo tiene su propio nivel.

---

## 2. Nivel del héroe (tabla completa 1 … 60)

- **XP para subir del nivel `n` al `n+1`: `60 × n`.** Del 1 al 60 hay **106 200** de XP acumulada.
- **Vida:** `120 + 10 × (n − 1)` → nivel 60 = **710**.
- **Aforo:** `6 + 2 × (n − 1)`, **techo 40** (se alcanza en el nivel **18**).
- **Puntos de juramento:** **1 cada 6 niveles** (6 · 12 · … · 60) → **10** en toda la partida.
- **Ataque y defensa:** `../batalla/01_CIFRAS.md` §2 (28/18 en nivel 1 → **164/177** en nivel 60).
  **Habilidades:** requisitos en `../contenido/06_HABILIDADES.md` §4.4.

| Nivel | XP | Vida | Aforo | Juramento | Se abre |
|---|---|---|---|---|---|
| 1 | 60 | 120 | 6 | 0 | — |
| 2 | 120 | 130 | 8 | 0 | — |
| **3** | 180 | 140 | 10 | 0 | **`hab_estocada`** · **piso 1** del árbol |
| 4 | 240 | 150 | 12 | 0 | — |
| 5 | 300 | 160 | 14 | 0 | — |
| **6** | 360 | 170 | 16 | **1** | — |
| 7 | 420 | 180 | 18 | 1 | — |
| 8 | 480 | 190 | 20 | 1 | — |
| 9 | 540 | 200 | 22 | 1 | — |
| 10 | 600 | 210 | 24 | 1 | — |
| 11 | 660 | 220 | 26 | 1 | — |
| **12** | 720 | 230 | 28 | **2** | **`hab_grito`** |
| 13 | 780 | 240 | 30 | 2 | — |
| 14 | 840 | 250 | 32 | 2 | — |
| **15** | 900 | 260 | 34 | 2 | **piso 2** del árbol |
| 16 | 960 | 270 | 36 | 2 | — |
| 17 | 1020 | 280 | 38 | 2 | — |
| **18** | 1080 | 290 | **40** | **3** | Aforo al techo |
| 19 | 1140 | 300 | 40 | 3 | — |
| 20 | 1200 | 310 | 40 | 3 | — |
| 21 | 1260 | 320 | 40 | 3 | — |
| 22 | 1320 | 330 | 40 | 3 | — |
| 23 | 1380 | 340 | 40 | 3 | — |
| **24** | 1440 | 350 | 40 | **4** | — |
| 25 | 1500 | 360 | 40 | 4 | — |
| **26** | 1560 | 370 | 40 | 4 | **`hab_aguante`** |
| 27 | 1620 | 380 | 40 | 4 | — |
| 28 | 1680 | 390 | 40 | 4 | — |
| 29 | 1740 | 400 | 40 | 4 | — |
| **30** | 1800 | 410 | 40 | **5** | **piso 3** del árbol |
| 31 | 1860 | 420 | 40 | 5 | — |
| 32 | 1920 | 430 | 40 | 5 | — |
| 33 | 1980 | 440 | 40 | 5 | — |
| 34 | 2040 | 450 | 40 | 5 | — |
| 35 | 2100 | 460 | 40 | 5 | — |
| **36** | 2160 | 470 | 40 | **6** | — |
| 37 | 2220 | 480 | 40 | 6 | — |
| 38 | 2280 | 490 | 40 | 6 | — |
| 39 | 2340 | 500 | 40 | 6 | — |
| 40 | 2400 | 510 | 40 | 6 | — |
| 41 | 2460 | 520 | 40 | 6 | — |
| **42** | 2520 | 530 | 40 | **7** | **`hab_reagrupe`** |
| 43 | 2580 | 540 | 40 | 7 | — |
| 44 | 2640 | 550 | 40 | 7 | — |
| 45 | 2700 | 560 | 40 | 7 | — |
| 46 | 2760 | 570 | 40 | 7 | — |
| 47 | 2820 | 580 | 40 | 7 | — |
| **48** | 2880 | 590 | 40 | **8** | **piso 4** del árbol |
| 49 | 2940 | 600 | 40 | 8 | — |
| 50 | 3000 | 610 | 40 | 8 | — |
| 51 | 3060 | 620 | 40 | 8 | — |
| 52 | 3120 | 630 | 40 | 8 | — |
| 53 | 3180 | 640 | 40 | 8 | — |
| **54** | 3240 | 650 | 40 | **9** | — |
| 55 | 3300 | 660 | 40 | 9 | — |
| 56 | 3360 | 670 | 40 | 9 | — |
| 57 | 3420 | 680 | 40 | 9 | — |
| 58 | 3480 | 690 | 40 | 9 | — |
| 59 | 3540 | 700 | 40 | 9 | — |
| **60** | — | **710** | 40 | **10** | Techo |

- **Habilidades y sus requisitos** (tronco a 3 · 12 · 26 · 42; pisos del árbol a 3 · 15 · 30 · 48):
  `../contenido/06_HABILIDADES.md` §4.4. **El nivel no se salta con oro.**
- **Cómo se reparten los atributos** (FUE/AGI/INT) y el origen: `13_ESTADISTICAS_DEL_HEROE.md`.

### 2.1 De dónde sale el XP (toda unidad y encargo da) ✅

**Todo da experiencia y recompensa:** cada encargo, cada enemigo derrotado y cada deuda
resuelta. Nada «solo da oro».

| Fuente | XP | Recompensa (además) |
|---|---|---|
| **Encargo cumplido** | `20 + 4 × nivel de la zona` | Pago en `../misiones/04_PAGOS_Y_RECOMPENSAS.md` + botín del contenedor |
| **Enemigo derrotado en batalla** | `10 + 2 × nivel del enemigo` | Botín de cuerpo/arcón (`../contenido/11_TABLAS_DE_BOTIN.md`) |
| **Capitán o némesis vencido** | `60` | Botín de capitán + una pieza buena |
| **Deuda resuelta** | `40` (menor) · `100` (mayor) | Firma/memoria; la mayor da **+1 punto de juramento** |
| **Deuda tuya pagada** | `120` | Baja tu deuda y sube tu Firma (`../sistemas/11_DEUDAS_DEL_JUGADOR.md`) |
| **Oficio (práctica, fabricación, encargo del maestro)** | **no da XP de héroe** | Da **XP de oficio** en su propia barra: +5 / +10 / +40 (`15_FABRICACION_Y_RECETAS.md` §2) |
| **Tropa o compañero superviviente** | **veteranía** (no XP del héroe) | Sube su nivel hasta «zona + 2» (§4) |

- **Se sube por cerrar y cobrar, no por matar a lo bruto** (`05_PROGRESION.md` §1): el XP de
  encargos y deudas es mayor que el de matar.
- **El oficio tiene su propia barra** y **no sube el nivel del héroe**: los rangos de profesión
  (Aprendiz/Oficial/Maestro) los abre el **XP de oficio**, no el nivel
  (`14_PROFESIONES.md` §2 y `15_FABRICACION_Y_RECETAS.md` §2).
- ✅ **Cerrado (2026-10-01):** las cifras de XP por fuente están **aprobadas** (opción A).
- **Recompensas**: oro y botín se detallan en `../misiones/04_PAGOS_Y_RECOMPENSAS.md` y
  `../contenido/11_TABLAS_DE_BOTIN.md`; aquí solo se enlaza.

---

## 3. Nivel de zona y nivel de los enemigos

- **Cada zona tiene una banda de nivel** (`data/zonas.json`) que **cubre la escala hasta 60**: es
  el **tono del mundo**. El nivel de los enemigos que te salen **sale de la zona** donde estás.

| Zona | Banda de nivel | Quién la puebla |
|---|---|---|
| **La Marca del Sur** (demo) | **1 – 12** | Bandidos de camino y cuadrillas menores |
| **La Ribera** | **12 – 24** | Mercenarios, patrullas de gremio y contrabando |
| **La Serranía** | **24 – 36** | Bandidos de paso y contrabandistas |
| **Los Altos de Altamir** | **36 – 48** | Cuadrillas de casa y caballeros de Altamir |
| **La Tierra del Paso** | **48 – 60** | Veteranos sueltos, los del Paso y lo peor del reino |

- **Regla de nivel enemigo:** `nivel = nivel de la zona + ajuste`, con **ajuste −1 / 0 / +1**:
  - **+1** para el **capitán**/cabecilla que manda el grupo,
  - **0** para la tropa de plantilla,
  - **−1** para el **rezagado** o el que huye solo.
- **El nivel del héroe no sube el enemigo:** el mundo no escala contigo; si vuelves fuerte a la
  Marca del Sur, aplastas (y eso también es una decisión). **No hay rubber-banding.**
- **Determinista con la semilla** (RNG inyectado, regla 9 de `../../AGENTS.md`).
- **Enemigos fijos de la historia:** nivel **clavado**; p. ej. el **Teniente** es **nivel 40**
  siempre (`../contenido/02_CAPITANES_Y_NEMESIS.md` §5.1).
- **Quién usa esto:** familias → `../contenido/01_ENEMIGOS.md`; terreno → `../mundo/06_TERRENO_DEL_MUNDO.md`;
  tablas de encuentro → `../mundo/02_VIAJE_Y_ENCUENTROS.md` §2. Aquí solo se fija **el nivel**.

---

## 4. Nivel de las unidades y los personajes

- **Toda unidad lleva nivel:** tropas, compañeros y capitanes lo tienen en su ficha
  (`data/tropas.json`, `data/companeros.json`, `data/capitanes.json`).
- **Al reclutar, una tropa entra al nivel de la zona**, no al tuyo: la Marca del Sur da tropa de
  nivel 1-12 aunque tú vayas por el 50.
- **Cómo sube una tropa:** **veteranía** por batallas ganadas (`../contenido/00_TROPAS.md` §6);
  a los hitos, **+2 de ataque** o **+4 de vida** a elegir por rol. Techo: **nivel de zona + 2**.
- **Los compañeros pelean a tu lado** con su nivel y las **mismas reglas** que una tropa
  (`../contenido/03_COMPANEROS.md`).
- **Los capitanes** suman **rango propio** (0…+3) al nivel de zona
  (`../contenido/02_CAPITANES_Y_NEMESIS.md` §3).

---

## 5. Escalado por nivel (sin romper el balance)

- **El héroe no usa esta fórmula:** su curva es explícita (§2 y `../batalla/01_CIFRAS.md` §2).
- **Para unidades y enemigos**, el nivel escala sobre las **stats base de nivel 1** de
  `../batalla/01_CIFRAS.md` §1–§2:

| Stat | Factor por nivel `n` |
|---|---|
| **Vida** | `base × (1 + 0,05 × (n − 1))` |
| **Ataque** | `base × (1 + 0,04 × (n − 1))` |
| **Defensa** | `base × (1 + 0,03 × (n − 1))` |

- **Redondeo:** entero **hacia abajo**; nunca por debajo de la base de nivel 1.
- **Tope duro que no se escala:** el **daño máximo por golpe** de `../batalla/01_CIFRAS.md` §2
  (**90** héroe / **45** tropa) se aplica **después** de escalar; un enemigo de nivel 60 sigue sin
  poder «onewipe».
- **A nivel 60** las cifras quedan en **×3,95 de vida · ×3,36 de ataque · ×2,77 de defensa**.
- ✅ **Cerrado (2026-10-01):** los tres factores (0,05 / 0,04 / 0,03) están **aprobados**
  (opción A); registro en `../DECISIONES.md`.

---

## 6. Datos, tipos y validación

- **Datos (por crear):** `data/zonas.json` gana `nivel_min`/`nivel_max` (bandas §3); `data/tropas.json`,
  `data/companeros.json` y `data/capitanes.json` ganan `nivel` (y `techo_extra` en tropas);
  `data/progresion.json` pasa a `{ nivel_max: 60, vida_base, incremento, veteranias }`.
- **Tipos:** `NivelPersonaje` y `NivelEscuadron` **están previstos**; se añaden `NivelZona` y el campo
  `nivel` a `Tropa`/`Companero`/`Capitan` en `js/data/game_types.js` (regla 4).
- **Constante prevista:** `NIVEL_MAX = 60` (con test de borde 60 válido /
  61 rechazado).
- **Guardado:** `nivel_personaje` y `niveles` quedan previstos en el guardado; **sin campos nuevos**
  (aditivo).
- **Validación:** esquema en `js/data/schemas.js` + cruce de bandas (`nivel_min ≤ nivel_max`), de
  los niveles de enemigo contra la banda de su zona y del `nivel` de ficha contra `NIVEL_MAX`, en
  `tools/validate_data.js`.
- **Sistema puro:** `js/systems/progresion.js` + `js/systems/enemigos.js`; sin DOM, sin reloj, RNG
  inyectado.
- **Tests (por escribir):** `tests/progresion.test.js` y `tests/capitanes.test.js`: el héroe no pasa de **60**;
  una tropa no pasa de «zona + 2»; el daño tras escalar no supera 90/45; la misma semilla da el
  mismo nivel de enemigo.

---

## 7. Cifras que fija este documento

| Cifra | Valor |
|---|---|
| Escala / nivel máximo del héroe | **1 … 60** |
| XP del héroe | `60 × n` para subir (106 200 acumulada) |
| XP por fuente | encargo · enemigo · capitán · deuda (tabla §2.1, ✅) |
| XP de oficio | **barra aparte** · +5 práctica · +10 fabricar · +40 encargo del maestro (umbrales 150 / 450) ✅ |
| Vida / aforo del héroe | `120 + 10 × (n − 1)` (710 a 60) · `6 + 2 × (n − 1)`, techo **40** (nivel 18) |
| Puntos de juramento | 1 cada 6 niveles → **10** |
| Zonas (bandas) | 5 (1-12 · 12-24 · 24-36 · 36-48 · 48-60) |
| Ajuste de nivel enemigo | −1 · 0 · **+1** (capitán) |
| Techo de tropa | nivel de zona **+ 2** |
| Rango propio de capitán | 0 … **+3** |
| Escalado (vida/ataque/defensa) | +5 % · +4 % · +3 % por nivel ✅ |
| Tope de daño | **90 / 45** tras escalar (no se rompe) |

---

## 8. Qué entra en la demo (Fase 1) — y qué sigue

> **Hasta aquí la demo.** El héroe con **niveles 1-15** (**tope de la demo**), arrancando en La
> Marca del Sur (banda 1-12), su tabla de XP y el **nivel de zona** poniendo enemigos de **nivel
> 1-13** (capitán +1). Solo el **piso 1** del árbol y el primer tramo del tronco entran aquí;
> tropas al nivel de la zona y primera veteranía.

> **Y sigue el juego completo.** Las **otras 4 zonas** (Ribera, Serranía, Altos y Paso) con sus
> **bandas hasta 60** se añaden **con estas mismas reglas**: crecer = más filas en `zonas.json`, no
> un sistema nuevo. Los factores de escalado (§5) se cierran en la Fase 2.

---

## 9. Fuera de este documento

- Estadísticas y atributos del héroe → `13_ESTADISTICAS_DEL_HEROE.md`
- Stats base del campo, daño y moral → `../batalla/01_CIFRAS.md`
- Cómo sube el héroe en detalle → `05_PROGRESION.md`
- Habilidades y sus requisitos de nivel → `../contenido/06_HABILIDADES.md` §4.4
- Tropas y veteranía → `../contenido/00_TROPAS.md`
- Familias enemigas → `../contenido/01_ENEMIGOS.md`
- Zonas del mapa → `../mundo/00_MAPA.md`
