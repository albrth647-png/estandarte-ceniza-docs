# 02 · Prisioneros — rescatar, retener, voltear, ejecutar

**Estado:** ✅ **aprobado por el dueño (aprobación en bloque, 2026-09-30). Documento final.**

> El fin de batalla no es un botín: es una **decisión con nombre y cara** (`00_REGLAS.md` §9).
> La Ordenanza reconoce **cinco salidas** para el que se rinde, y las cinco se pagan de una
> forma u otra (`../historia/00_PREMISA.md`). Aquí viven sus **reglas y precios**; los efectos
> sobre la reputación, en `01_FIRMA.md`, y sobre la memoria, en `00_MEMORIA_Y_DEUDA.md`.

---

## 1. Dónde y cuándo se decide

- Salta al romperse la moral enemiga (`00_REGLAS.md` §9): **la mitad huye, el resto se rinde**.
- Se te presentan los prisioneros **con nombre**: capitanes y cabecillas, uno a uno. La **tropa
  rasa** se resuelve en bloque (§8).
- **La derrota no bloquea** (Pilar 3): si **caes tú**, se aplica la misma mecánica desde el otro
  lado (§7). Nunca hay pantalla de muerte sin salida.

---

## 2. Las cinco salidas

| Salida | Qué haces | Qué ganas | Qué te cuesta |
|---|---|---|---|
| **Rescatar** | Lo sueltas (con o sin fianza) | Firma y memoria buenas; quizá una **deuda blanca** | El botín que no cobras |
| **Retener** | Lo guardas como **rehén** | Palanca: su casa paga o se doblega | Su casa te señala; si abusas, memoria en contra |
| **Voltear** | Lo pones a tu servicio | Una tropa o **capitán** contigo | Su **deuda** o tu oro; no todos aceptan |
| **Ejecutar** | Le quitas la vida | Botín, miedo, menos enemigos hoy | Firma **mucho** más baja y **rencores** que crecen |
| **Canjear** | Lo cambias por algo perdido (un prisionero propio, un rehén, una prueba) | Recuperas lo que cuesta encontrar | Creas una **deuda** con su bando (Pilar 3) |

- **Cinco salidas, ni una más** (`../produccion/00_ALCANCE.md` §2.1; el canje, del Pilar 3 de `../VALCORIA_DEUDA_DE_SANGRE.md`). Ninguna es «la buena»:
  cada una abre una puerta y cierra otra.
- **Solo se retiene a un nombre:** los que se guardan como **rehén** son **capitanes y cabecillas**
  (§1), los únicos que ocupan **cuarto** (§3.1). La **tropa rasa** nunca se retiene: se resuelve en
  bloque — **liberar · reclutar · saquear** (§8).

---

## 3. Precios y fianzas

- **Rescate del prisionero** (lo que paga su casa por él):
  - **Capitán / cabecilla con nombre:** **(nivel + 10) × 10 oro** (misma fórmula que tu rescate,
    `00_MEMORIA_Y_DEUDA.md` §5).
  - **Tropa rasa:** **(nivel + 5) × 4 oro**.
- **Rescatar sin cobrar:** gratis, pero renuncias a la fianza (§4).
- **Fianza (retener):** no cuesta; su casa paga el **rescate ×1,5** o te debe un favor de casa.
- **Voltear:** cuesta su **deuda de sangre** si la tienes (la pagas tú y pasa a tu favor) o, si no,
  **(nivel + 10) × 12 oro** en mano.
- **Ejecutar:** gratis; el coste es la **Firma** y la **memoria** (§5), no el oro.

*Precios ajustables en `06_ECONOMIA.md`; la fórmula y su forma no cambian.*

### 3.1 · Los cuartos: dónde vive un rehén

- **Retener exige sitio.** Un rehén se guarda en una **casa alquilada**
  (`../contenido/09_EDIFICIOS_Y_ESTRUCTURAS.md` §1), nunca «en el bolsillo»: **sin cuarto libre no
  puedes retener** (te quedan rescatar, voltear o ejecutar).
- **Renta:** la casa cuesta **5 oro/día** (`06_ECONOMIA.md` §3) y se paga como la posada.
- **Cuartos:** **1 en la demo**; el juego completo da **más según la zona** que cruzas
  (`../mundo/00_MAPA.md`). **Un cuarto = un rehén**; lleno, no entra otro.
- **Rédito:** un rehén **rinde oro al día** = **rescate ÷ 10** (§3), con **tope 10 días**.
  Ejemplo: capitán de nivel 10 → rescate 200 → **20 oro/día** hasta 200.
- **Coste de boca:** consume **1 ración/día** (`../mundo/10_SUPERVIVENCIA_Y_DESCANSO.md` §1).
- **Neto:** retener solo compensa si el rédito cubre renta + ración; si no, pierdes oro (y el rehén
  sigue siendo palanca política, §4).

---

## 4. Qué decide cada prisionero

| Salida | Firma (`01_FIRMA.md` §4) | Memoria (`00_MEMORIA_Y_DEUDA.md` §4) |
|---|---|---|
| Aceptar la rendición | **+3** | — |
| Rescatar (volver a casa) | **+4** | Hecho **4 · Perdonado** (+10) si le debías algo → **deuda blanca** (`f=1`) |
| Retener (rehén) | 0 | Hecho **8 · Cobro por la fuerza** (−6) si aprietas |
| Voltear | 0 | Hecho **1/2** (trato/encargo) si cumple |
| Ejecutar a un rendido | **−8** | Hecho **12 · Ejecución** (−12) |
| Ejecutar a un **capitán** rendido | **−10** | Hecho 12 + **rencor** si tiene parientes (hecho 13) |
| Usar a un rehén **como escudo** | **−10** | Hecho 11 · Humillación pública (−10) |

- **Un nombre pesa más que un número:** ejecutar a un capitán no baja lo mismo que ejecutar a un
  villano, y su casa lo hereda (`00_MEMORIA_Y_DEUDA.md` §7).

---

## 5. Voltear a un capitán (la salida más cara)

- **Requisitos** (por su rango personal, `00_MEMORIA_Y_DEUDA.md` §3–§9):
  - **Amigo o mejor (+30):** se viene **voluntario** (sin oro, se le paga con servicio).
  - **Conocido / Hostil (−29 … +29):** solo **comprando** su lealtad (§3).
  - **Enemigo o peor (−30 …):** **no se volta** — se rescata, se retiene o se ejecuta.
- **Su deuda:** si debía sangre, la pagas tú y **pasa a tu favor**; si tenía rencor activo, este
  **no se borra** al servirte (te sirve con el rencor dentro).
- **Ficha propia:** un capitán volteado pasa al catálogo de `../contenido/02_CAPITANES_Y_NEMESIS.md`
  y **recuerda** por qué cambió de bando.

---

## 6. Ejecutar: lo que se gana y lo que se pierde

- **Ganas:** su botín (arma, arreos, oro), **miedo** (su gente se rinde antes la próxima vez) y
  un enemigo menos hoy.
- **Pierdes:** Firma pública (−8 / −10), memoria de todos los que lo vieron, y **rencores**
  heredados por su casa (verdugo mínimo). El que mata por costumbre acaba sin quien le fíe.
- **No hay ejecución «limpia»:** siempre hay testigos (tus tropas, al menos) y la Firma
  **solo cuenta lo que se ve** (`01_FIRMA.md` §1).

---

## 7. Si caes tú (Pilar 3, lado B)

Misma mecánica, desde el otro lado. El mundo decide, y **siempre hay salida**:

| Situación | Qué pasa |
|---|---|
| **Tienes oro** | Pagas tu **rescate** = (nivel + 10) × 10 (`00_MEMORIA_Y_DEUDA.md` §5) · Firma +3 al cumplirlo |
| **No tienes oro** | **Servicio:** la deuda cambia de forma; haces un encargo para quien te capturó y sigues |
| **Te quieren retener** | **Cautiverio:** puedes esperar rescate (un Amigo) o comprar una puerta |
| **Hay un Amigo a < 10 m** | Te **arrastra** malherido fuera del campo: sin deuda nueva, vida mínima |
| **Banda Hermano de sangre** | **Rescata** él mismo (`00_MEMORIA_Y_DEUDA.md` §3) |

- **Nunca** se pierde la partida por caer: se pierde oro, tiempo o libertad, no el juego.

---

## 8. La tropa rasa (resolución en bloque)

- Al acabar, la tropa sin nombre se agrupa: eliges **liberar**, **reclutar** (si hay cupo de
  aforo, `../contenido/00_TROPAS.md` §4) o **saquear** (botín, con memoria en contra del lugar).
- **Los que huyeron no se resuelven aquí:** vuelven con su casa (`../contenido/01_ENEMIGOS.md` §3).

---

## 9. Datos, tipos y validación

- **Guardado:** campo `prisioneros` en `SaveState` (aditivo, aditivo) y campo
  `alquiler` = `{ sitio, dias_restantes, cuartos[] }` (aditivo), junto a
  `memoria` y `firma`.
- **Tipos:** `Prisionero` y `Salida` en `js/data/game_types.js` (una sola vez, regla 4).
- **Validación:** esquema en `js/data/schemas.js` + cruce con `data/tropas.json` en
  `tools/validate_data.js`.
- **Sistema puro:** `js/systems/prisioneros.js` — calcula precios y aplica hechos a memoria y
  Firma; sin DOM, sin reloj, RNG inyectado.
- **Tests (por escribir):** `tests/prisioneros.test.js`, mínimo 3 casos (normal, borde, error): una salida
  imposible (voltear a un Enemigo) se rechaza; ejecutar deja rencor; el rescate nunca deja sin
  salida; **un cuarto lleno rechaza retener**.

---

## 10. Cifras que fija este documento

| Cifra | Valor |
|---|---|
| Salidas | **4** (rescatar · retener · voltear · ejecutar) |
| Rescate de capitán | (nivel + 10) × 10 oro |
| Rescate de tropa | (nivel + 5) × 4 oro |
| Fianza (rehén) | rescate ×1,5 o un favor de casa |
| Renta de la casa alquilada | **5 oro/día** |
| Cuartos | **1 en la demo** · +1 por zona en el juego completo |
| Quién se retiene | **solo capitanes y cabecillas** (la tropa rasa, en bloque) |
| Rédito de un rehén | **rescate ÷ 10 por día** · tope 10 días |
| Boca del rehén | 1 ración/día |
| Voltear (comprando) | (nivel + 10) × 12 oro · o su deuda pagada por ti |
| Voltear voluntario | rango personal ≥ **+30** (Amigo) |
| Tu rescate al caer | (nivel + 10) × 10 oro · sin oro = servicio |
| Efecto Firma | rescatar +4 · rendirse/aceptar +3 · ejecutar −8 · capitán −10 · rehén-escudo −10 |

---

## 11. Qué entra en la demo (Fase 1) — y qué sigue

> **Hasta aquí la demo.** Las **4 salidas** con sus precios y consecuencias, jugables tras las 3
> batallas del Acto I; el **rescate** al caer con la fórmula de §7; la tropa rasa en bloque; y la
> **casa alquilada** con **1 cuarto** para retener (§3.1). Los personajes fijos de esta tanda y
> **4+ capitanes** con memoria (`../produccion/00_ALCANCE.md`).

> **Y sigue el juego completo.** Todos los capitanes y cabecillas de las **5 familias**
> (`../contenido/01_ENEMIGOS.md`) y sus cortes se añaden **con estas mismas reglas y precios**.
> Crecer = más filas de datos, no una mecánica nueva.

---

## 12. Fuera de este documento

- Reputación y hechos públicos → `01_FIRMA.md`
- Memoria, bandas y rencores → `00_MEMORIA_Y_DEUDA.md`
- Favores y deuda blanca → `03_FAVORES.md`
- Precios y flujos de oro → `06_ECONOMIA.md`
- Capitanes que vuelven → `../contenido/02_CAPITANES_Y_NEMESIS.md`
- Moral y fin de batalla → `../batalla/00_REGLAS.md`
