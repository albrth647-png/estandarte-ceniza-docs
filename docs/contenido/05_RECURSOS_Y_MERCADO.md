# 05 · Recursos y mercado — las cosas que se compran y se gastan

**Estado:** ✅ **aprobado por el dueño (aprobación en bloque, 2026-09-30). Documento final.**
**Enmienda 2026-10-02:** los **4 recursos de nivel 2** (`plata`, `piedra`, `cuerda`, `resina`) entran
como recursos oficiales; el total pasa de **7** a **11** (`../sistemas/15_FABRICACION_Y_RECETAS.md` §3).

> El **marco** del dinero (moneda, salarios, recargos, deuda como producto) vive en
> `../sistemas/06_ECONOMIA.md`. Aquí está **qué bienes existen, cuánto valen, qué mueve su precio y
> cómo se guardan**. El equipo, en `04_ITEMS_Y_EQUIPO.md`; la comida, en `14_COMIDAS_Y_BEBIDAS.md`.
>
> **Precios, ids y stocks de este documento son propuesta de diseño** (cambiables →
> `../DECISIONES.md`).

---

## 1. Los recursos

Una sola divisa jugable (**oro**, `../sistemas/06_ECONOMIA.md` §1) y **siete bienes** que se
compran, se venden, se gastan o se pierden.

| id | Recurso | Para qué | Se estropea | Notas |
|---|---|---|---|---|
| `oro` | **Oro** | Todo; es la moneda | No | Fracciones de plata/cobre son de sabor |
| `hierro` | **Hierro** | Mejoras y reparaciones (`04_ITEMS_Y_EQUIPO.md` §4) | No | Sube de precio en guerra |
| `grano` | **Grano** | Comida de la compañía | Sí, despacio | **1 saco = 10 raciones** |
| `lena` | **Leña** | Fuego de camino y campamento | No | Se **recolecta** (`../mundo/07_PROPS_Y_VEGETACION.md` §4) |
| `cuero` | **Cuero** | Reparar equipo ligero, arreos | No | Barato; trueque de aldea |
| `hierbas` | **Hierbas** | Sanados, vendas y oficio del **Sanador** (`../sistemas/14_PROFESIONES.md` §5) | No | Se **recolecta** en prados y riberas ✅ (2026-10-01) |
| `carne` | **Carne** | Caza y raciones del **Cazador** (`../sistemas/14_PROFESIONES.md` §5) | **Sí, rápido** | Sale del cazo; se seca o se pierde ✅ (2026-10-01) |

### 1b. Los 4 recursos de nivel 2 (desde el nivel 30 del héroe) ✅ 2026-10-02

Son los que usa la **fabricación** cuando ya dominas el oficio
(`../sistemas/15_FABRICACION_Y_RECETAS.md` §3). **No se recogen hasta el nivel 30** y **no se
compran en la aldea**: solo en mercado de ciudad.

| id | Recurso | Para qué | Se estropea | Notas |
|---|---|---|---|---|
| `plata` | **Plata** | Joyas, hebillas y varillas del herrero | No | Vetas de la Serranía y los Altos |
| `piedra` | **Piedra tallada** | Moldes, percutores y piedras de afilar | No | Canteras y rocas |
| `cuerda` | **Cuerda** | Ataduras y arreos (`../contenido/13_MONTURAS_Y_TRANSPORTE.md`) | No | Cáñamo de prados y riberas |
| `resina` | **Resina** | Pegamento de mango y de adorno | No | Pinos y tocones resinados |

- **Nivel 1 vs nivel 2:** los **7** de §1 son los de nivel 1 (desde el nivel 1 del héroe, en cuanto
  aprendes la profesión); estos **4** son los de nivel 2 (desde el **nivel 30**).
- **A partir del nivel 30**, el recurso de nivel 1 **rinde +50 %**.
- **Cada uno tiene su yacimiento en el mapa** (`../mundo/03_LUGARES.md` §2) y su prop recolectable
  (`../mundo/07_PROPS_Y_VEGETACION.md`); el validador (regla 5) lo cruza.

- **El grano es comida, no moneda:** alimenta sin pasar por el mercado
  (`../mundo/10_SUPERVIVENCIA_Y_DESCANSO.md` §1).
- **La leña no se compra casi nunca:** se recoge. El mercado solo la vende en ciudad.

---

## 2. Precios base (propuesta)

| Bien | Precio base | Unidad | Nota |
|---|---|---|---|
| **Ración** | **2 oro** | 1 comida | `../sistemas/06_ECONOMIA.md` §4 |
| **Saco de grano** | **12 oro** | 10 raciones | Rendimiento 10 (`§1`) |
| **Hierro** | **8 oro** | 1 pieza | Sube en guerra (§3) |
| **Leña** | **2 oro** | 1 haz | Recolectable gratis |
| **Cuero** | **4 oro** | 1 pieza | Barato |
| **Hierbas** | **3 oro** | 1 manojo | Recolectable; del Sanador ✅ |
| **Carne** | **3 oro** | 1 pieza | Del cazo; se estropea rápido ✅ |
| **Sal** | **6 oro** | 1 pieza | Conserva grano (opcional, sabor) |
| **Plata** | **15 oro** | 1 pieza | Recurso de nivel 2 ✅ 2026-10-02 |
| **Piedra tallada** | **4 oro** | 1 pieza | Recurso de nivel 2 ✅ 2026-10-02 |
| **Cuerda** | **5 oro** | 1 pieza | Recurso de nivel 2 ✅ 2026-10-02 |
| **Resina** | **6 oro** | 1 pieza | Recurso de nivel 2 ✅ 2026-10-02 |

- Los precios del **equipo** viven en `04_ITEMS_Y_EQUIPO.md` §6 y los de **posada**, en
  `../sistemas/06_ECONOMIA.md` §4.
- **Todo precio de tabla es entero** (los céntimos no existen, `../sistemas/06_ECONOMIA.md` §1).

---

## 3. Qué mueve el precio

| Factor | Efecto | Referencia |
|---|---|---|
| **Firma** | Duro **+10 %** · Fiera **+25 %** · Hiena **+40 %** · Amigo **−10 %** | `../sistemas/01_FIRMA.md` §3 |
| **Guerra abierta** | Hierro y equipo **suben** | `../sistemas/09_TIEMPO_Y_MUNDO_VIVO.md` |
| **Sequía / invierno** | Grano y comida **suben** | `../mundo/09_CLIMA_Y_ESTACIONES.md` |
| **Puerto y ribera** | Trato **más barato** | `../mundo/08_AGUA_RIOS_Y_PUENTES.md` |
| **Serranía** | Trato **más caro** (aislamiento) | `../mundo/00_MAPA.md` |
| **Memoria del vendedor** | Banda y `d` ajustan al margen | `../sistemas/00_MEMORIA_Y_DEUDA.md` §3 |

- **Los recargos por Firma se aplican sobre el precio base**, después la memoria del vendedor.
- **La curva de venta** (`../sistemas/06_ECONOMIA.md` §7): vender mucho **hunde el precio**, para
  que el mercado no sea un pozo sin fondo.

---

## 4. El mercado, la tienda y el trueque

- **Stock finito por sitio** (`../sistemas/06_ECONOMIA.md` §7): cada plaza tiene reserva y se
  repone cada **3-7 días** de juego (`../misiones/01_TABLONES_Y_PORTAVOCES.md` §6).
- **Qué se vende dónde:**

| Sitio | Ofrece | Compra |
|---|---|---|
| **Aldea** | Grano, leña, cuero, raciones | Poco; trueque |
| **Posada / cruce** | Raciones, cama, rumores | Botín menudo |
| **Mercado de ciudad** | Hierro, equipo, sal, rarezas buenas, **plata, piedra, cuerda y resina** | Casi todo |
| **Casa / armero** | Equipo raro y nombradas | No compra basura |

- **Fiado:** solo entre banda **Amigo o mejor** (`../sistemas/00_MEMORIA_Y_DEUDA.md` §3) y con
  tope de **100 oro** (`../sistemas/03_FAVORES.md` §4).
- **Trueque:** se cambia bien por bien sin oro; el valor lo fija la tabla de §2, ajustada por §3.
  Es la salida del que no tiene bolsa (Pilar 3: *el fallo nunca atasca*).

---

## 5. Reservas y topes

| Cota | Valor | Motivo |
|---|---|---|
| Stock por recurso y sitio | **60** unidades (grano, hierro) | Reserva finita |
| Reposición | cada **3-7 días** | Mundo vivo |
| Carga de la compañía | la mochila + carreta | `04_ITEMS_Y_EQUIPO.md` §5, `13_MONTURAS_Y_TRANSPORTE.md` |
| Fiado | ≤ **100 oro** | `../sistemas/03_FAVORES.md` §4 |
| Precio mínimo de venta | **50 %** del base | La curva no baja de ahí |

- **Lo que se pierde al viajar:** nada por el viaje en sí; el **grano se estropea despacio**
  (`../mundo/10_SUPERVIVENCIA_Y_DESCANSO.md` §1) y el **asalto** puede quitarte carga
  (`12_TRAMPAS_Y_OBSTACULOS.md`).

---

## 6. Productos que son deudas

- **Rescates y fianzas** se compran y se venden como un bien: pagar el rescate de otro y pasar a
  ser su acreedor es **comprar su deuda** (`../sistemas/06_ECONOMIA.md` §6).
- **Componenda** (20 marcos = 200 oro, `../sistemas/06_ECONOMIA.md` §4): el precio de un hombre
  libre; se paga en el mercado de la Escribanía.
- **Cobranza por encargo:** el encargo de clase `cobrar` convierte grano, cuero o hierro de un
  moroso en oro para ti (`../misiones/04_PAGOS_Y_RECOMPENSAS.md` §1).
- **La deuda no genera intereses** (`../sistemas/06_ECONOMIA.md` §6): comprarla no la hace crecer.

---

## 7. Datos, tipos y validación

- **Datos:** `data/recursos.json` — `{ id, nombre_txt, unidad, precio_base, se_estropea, stock }`;
  los precios de compra/venta se cruzan con `data/economia.json`.
- **Tipos:** `Recurso` y `Mercado` en `js/data/game_types.js` (una sola vez, regla 4).
- **Validación:** esquema en `js/data/schemas.js` + cruce con `data/lugares.json` (stocks) y con
  `data/economia.json` (recargos) en `tools/validate_data.js`.
- **Sistema puro:** `js/systems/mercado.js` — aplica precio, recargos, curva y stock; sin DOM, sin
  reloj (día por `save.day`), RNG inyectado.
- **Tests:** `tests/mercado.test.js`, mínimo 3 casos (normal, borde, error): el recargo de Hiena es
  +40 %; vender en masa baja el precio sin bajar del 50 %; un stock agotado no rompe la tienda.

---

## 8. Cifras que fija este documento

| Cifra | Valor |
|---|---|
| Recursos | **11** (7 de nivel 1 + **4 de nivel 2** desde el nivel 30) ✅ |
| Ración / saco de grano | **2 oro** / 12 oro (10 raciones) |
| Hierro / leña / cuero | 8 / 2 / 4 oro |
| Hierbas / carne | 3 / 3 oro ✅ |
| Plata / piedra / cuerda / resina | **15 / 4 / 5 / 6** oro ✅ (nivel 2) |
| Recargos por Firma | los de `../sistemas/01_FIRMA.md` §3 |
| Stock por recurso y sitio | **60** · reposición 3-7 días |
| Fiado | ≤ 100 oro · banda ≥ Amigo |
| Precio mínimo de venta | 50 % del base |
| Curva de venta | `../sistemas/06_ECONOMIA.md` §7 |

---

## 9. Qué entra en la demo (Fase 1) — y qué sigue

> **Hasta aquí la demo.** **Oro, grano, leña y hierro** con sus precios y el **trueque**; el
> mercado del Patio del Cadalso y los puestos de aldea; el fiado entre Amigos. **Sin** sal, sin
> curva de venta fina, sin compra de deudas ajenas y **sin los 4 recursos de nivel 2** (nivel 30).

> **Y sigue el juego completo.** El **mercado completo** (cuero, sal, curva de venta, compra de
> deudas) llega con la Fase 2/Fase 4; los **precios base y los recargos no cambian**: crecer = más
> filas en `recursos.json`, no otra economía.

---

## 10. Fuera de este documento

- El marco económico (marco, salarios, recargos) → `../sistemas/06_ECONOMIA.md`
- Equipo y mejoras → `04_ITEMS_Y_EQUIPO.md`
- Comida y bebida → `14_COMIDAS_Y_BEBIDAS.md`
- Recetas y qué se fabrica con cada oficio → `../sistemas/15_FABRICACION_Y_RECETAS.md`
- Rendimiento del grano y el hambre → `../mundo/10_SUPERVIVENCIA_Y_DESCANSO.md`
- Clima y estaciones → `../mundo/09_CLIMA_Y_ESTACIONES.md`
- Fichas de sitio y stocks → `../mundo/03_LUGARES.md`
