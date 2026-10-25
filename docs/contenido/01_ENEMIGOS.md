# 01 · Enemigos — contra quién peleas

**Estado:** ✅ **aprobado por el dueño (aprobación en bloque, 2026-09-30). Documento final.**

> El eslogan manda: *«Cada enemigo se acuerda de ti. Y no todos mueren.»* Hay enemigos fijos
> (los que la historia pone) y enemigos **que nacen de lo que haces** (venganzas, deudas, los
> que huyeron y volvieron). Describe el **juego completo**. Cómo pelean por dentro está en
> `../batalla/03_IA_Y_ORDENES.md` §3; las stats de sus tropas, en `../batalla/01_CIFRAS.md`.
> **Nombres e ids son propuesta de diseño** (cambiables → `../DECISIONES.md`).

---

## 1. De dónde salen los enemigos

Dos fuentes, y las dos se mezclan en el campo:

1. **Fijos (historia):** los que el guion pone en el camino — la cuadrilla de una casa, la
   patrulla que cobra peaje, los del Paso (`../historia/01_ESTRUCTURA.md`).
2. **Generados (sistemas):** los que **se ganan** jugando —
   - el que **huyó** de un campo y vuelve con su casa (`../batalla/00_REGLAS.md` §9),
   - el que tiene **rencor activo** contigo (`../sistemas/00_MEMORIA_Y_DEUDA.md` §7),
   - el que **cobra una deuda blanca** como aviso o puerta (`../sistemas/03_FAVORES.md`),
   - la casa que se queda sin rostro y pone precio a tu cabeza (`../historia/05_CASAS_Y_FACCIONES.md`).

> **Regla dura:** ningún enemigo generado es anónimo. Todo el que te busca tiene **una razón
> escrita en tu memoria** — lo que hiciste, o lo que dejaste de pagar.

---

## 2. Las familias enemigas

Toda unidad empieza en **moral 100** (`../batalla/01_CIFRAS.md` §5): lo que cambia entre familias es **cuándo rompen** y cómo huyen, nunca el punto de partida.

| id | Familia | Rasgo | Quién la manda | Ruptura |
|---|---|---|---|---|
| `cuervos_del_camino` | **Bandidos de camino** | Hostigadores | Un cabecilla (rara vez capitán) | Rompen a **10** (pelean con miedo, `01_CIFRAS.md` §5) |
| `cuadrilla_de_casa` | **Cuadrilla de una casa** | Disciplinada | Un capitán con nombre | Rompen a **0** |
| `patrulla_de_altamir` | **Patrulla de Altamir** | Patrulla de casa | Un teniente de Altamir | Rompen a **0** |
| `riberenos_de_la_orilla` | **Gente de la otra ribera** | Fanáticos | Un caudillo de ribera | Rompen a **0** y no salen del campo: se repliegan y vuelven |
| `rencorosos` | **Los que te señalan** | Vengativos | El que tiene tu nombre | Rompen a **0**; buscan tu unidad, no la victoria |

- **`rencorosos`** no es una banda de plantilla: es la **familia generada** por la memoria y la
  Firma. Su composición la decide **quién te busca** (una casa, una aldea, un capitán viejo).
- Los rasgos los lee la IA (`../batalla/03_IA_Y_ORDENES.md` §3.1): hostigadores huyen antes;
  disciplinados no se dispersan; la patrulla avisa antes de pelear; los vengativos no se rinden
  hasta romperse y **te buscan a ti**.
- **El nivel lo pone la zona:** cada familia aparece con el **nivel de la zona** donde estás
  (ajuste −1/0/**+1** para el capitán); **no escala contigo**. Tabla de bandas y fórmula en
  `../sistemas/12_NIVELES_DEL_HEROE.md` §3. El nivel **no** cambia la ruptura de moral ni la
  familia: cambia sus números.

---

## 3. Composición y forma de pelear

Cada familia lleva **una mezcla de los roles** de `../contenido/00_TROPAS.md` §2, con su propio
sesgo:

| Familia | Línea | Distancia | Apoyo | Capitán | Forma de pelear |
|---|---|---|---|---|---|
| Bandidos de camino | Poca, ligera | Ballesteros de emboscada | — | 1 cabecilla | Tienden emboscada, hostigan y huyen antes de perder |
| Cuadrilla de casa | Sí, con escudo | Sí | Sí (bandera de casa) | **1 capitán** | Formación, protegen al capitán, se retiran en orden |
| Patrulla de Altamir | Sí | Sí | Sí | **1 teniente** | Cobran peaje primero, pelean después; se repliegan si pierden al jefe |
| Gente de la otra ribera | Sí, sin escudo | Hondas | — | 1 caudillo | Pelean en su vado, no cruzan; no se rinden hasta romperse |
| Los que te señalan | Según quién te busca | Ídem | Ídem | A veces | Buscan **tu** unidad; no huyen hasta muy abajo |

- **El botín** de cada familia (oro, hierro, armas, rehenes) vive en
  `../contenido/11_TABLAS_DE_BOTIN.md`.
- **Los capitanes** con nombre, sus rasgos y sus némesis viven en
  `../contenido/02_CAPITANES_Y_NEMESIS.md`.

---

## 4. Qué hacen fuera del campo

Un enemigo no solo existe cuando peleas:

| Fuera del campo | Qué es |
|---|---|
| **Patrullar** | Recorren un tramo y te **detectan** según la visibilidad del terreno (`../batalla/02_TERRENO.md` §6) |
| **Cobrar** | Exigen peaje o deuda en un cruce; puedes pagar, negociar o pelear |
| **Sitiar / cerrar** | Cortan un camino o una puerta hasta que resuelvas la deuda |
| **Esconderse** | El que huye se refugia en un sitio; volver a buscarlo es un encargo |
| **Avisar** | La patrulla que te ve avisa a su casa: sube su peso en la tabla de encuentros (`../mundo/02_VIAJE_Y_ENCUENTROS.md` §2) |

- **El mundo se mueve sin ti:** quién patrulla dónde y quién cobra a quién lo decide
  `../sistemas/09_TIEMPO_Y_MUNDO_VIVO.md`.

---

## 5. Voltear, rescatar o comprar (y lo que no)

- **Voltear:** al enemigo rendido con banda Enemigo o peor **no** se le volta; con banda Amigo,
  se viene contigo (`../sistemas/02_PRISIONEROS.md`).
- **Rescatar:** un capitán prisionero puede pagar su rescate o pagarlo con servicio — y volver
  siendo tu deudor.
- **Comprar:** a un cabecilla se le paga para que cambie de bando una vez; el que se vende se
  acuerda, y su casa también.
- **Lo que no se puede:** ningún enemigo es «fácil» por ser generado. Un aldeano con rencor es
  tan peligroso como una cuadrilla si le das tiempo.

---

## 6. Datos, tipos y validación

- **Datos (por crear):** `data/enemigos.json` — `{ id, familia, rasgo, composicion, moral_base, capitan,
  botin, fuera_de_campo }`.
- **Tipos:** `FamiliaEnemiga` en `js/data/game_types.js` (una sola vez, regla 4).
- **Validación:** esquema en `js/data/schemas.js` + cruce con `data/tropas.json` (roles válidos)
  en `tools/validate_data.js`.
- **Sistema puro:** la composición y el retorno de los que huyeron viven en
  `js/systems/enemigos.js`; sin DOM, sin reloj, RNG inyectado.

---

## 7. Cifras que fija este documento

| Cifra | Valor |
|---|---|
| Familias enemigas | **5** (4 fijas + los generados por memoria/Firma) |
| Rasgos de IA | 4 (hostigador · disciplinado · patrulla · fanático/vengativo) |
| Moral inicial | **100** para toda familia (`../batalla/01_CIFRAS.md` §5) |
| Nivel | el de la **zona** (−1/0/+1) · `../sistemas/12_NIVELES_DEL_HEROE.md` §3 |
| Ruptura | bandidos a **10** (miedo) · el resto a **0** |
| Capitán | 1 por cuadrilla y patrulla; cabecilla en bandidos |
| Retorno de huidos | todo el que huye puede volver con su casa |
| Botín y capitanes | `11_TABLAS_DE_BOTIN.md` y `02_CAPITANES_Y_NEMESIS.md` |

---

## 8. Qué entra en la demo (Fase 1) — y qué sigue

> **Hasta aquí la demo.** **3 familias** (`../produccion/00_ALCANCE.md` §3): bandidos de camino,
> cuadrilla de una casa y patrulla de Altamir, con sus capitanes (4+ con memoria) y sus
> encuentros en los 2 campos. Fijos y generados funcionando igual que en el juego completo.

> **Y sigue el juego completo.** La gente de la otra ribera y los `rencorosos` (la familia que
> genera tu propia memoria) se añaden **con estas mismas reglas**: más filas en
> `enemigos.json`, los mismos rasgos y la misma IA. La cifra no cambia al escalar.

---

## 9. Fuera de este documento

- Rasgos y decisiones de la IA → `../batalla/03_IA_Y_ORDENES.md`
- Stats de combate → `../batalla/01_CIFRAS.md`
- Capitanes y némesis → `02_CAPITANES_Y_NEMESIS.md`
- Tropas que te siguen → `00_TROPAS.md`
- Botín → `../contenido/11_TABLAS_DE_BOTIN.md`
- Prisioneros y las 4 salidas → `../sistemas/02_PRISIONEROS.md`
- Lo que te hace enemigos (memoria, Firma) → `../sistemas/00_MEMORIA_Y_DEUDA.md`,
  `../sistemas/01_FIRMA.md`
