# 01 · La Firma — cómo peleas es cómo te llaman

**Estado:** ✅ **aprobado por el dueño (aprobación en bloque, 2026-09-30). Documento final.**

> Pilar 2 del juego. Describe el **juego completo** y cierra con su sección de demo.
> Cierra el pendiente nº 4 de `../DECISIONES.md` (qué acciones suman y bajan la Firma, con
> qué medidas y tope). La base narrativa está en `../VALCORIA_DEUDA_DE_SANGRE.md`.
> El eslogan tiene cuatro sentidos: la **Firma** es el público — *cada enemigo se acuerda de ti*.

---

## 1. Qué es

La Firma es **lo que el reino dice de ti cuando no estás delante**. No mide lo que has
conquistado, sino **cómo** lo has hecho: si perdonaste, si ejecutaste, si peleaste delante de
tu gente o te escondiste detrás de ellas.

Dos reglas de entrada, y de ellas sale todo lo demás:

1. **Si no lo ve nadie, no cuenta.** Un hecho solo mueve la Firma si tuvo **testigos**
   (enemigos vivos, aldeanos, Escribanos, tu propia tropa). Lo que solo lo viste tú mueve la
   memoria de los presentes (`00_MEMORIA_Y_DEUDA.md`), no la Firma.
2. **La Firma no caduca.** No hay decay: lo que te persigue, te persigue. La única forma de
   subirla es hacer cosas a la vista (§7 · La enmienda).

La Firma y la memoria son dos sistemas distintos: la **memoria** es personal (cada uno te
guarda tu rango), la **Firma** es un dato único, público y guardado.

---

## 2. Su valor

- Entero de **−100 a +100**, en el campo `firma` del `SaveState`.
- **No se muestra el número en pantalla**: el HUD y el mundo dicen el **nombre de la banda**
  (§3). El número exacto se lee en la Crónica y, más tarde, en el Libro Mayor.
- Empezamos la partida en **0 · Sin nombre**.

---

## 3. Las siete bandas

| Banda | Rango | Puerta que abre | Trampa que pone |
|---|---|---|---|
| **Palabra dada** | +60 … +100 | Casas y Escribanos te fían y te dan los encargos de honor; los honorables te siguen | Los mercachifles sin escrúpulos **no** tratan contigo (ni trampas ni artes negras) |
| **Honrado** | +30 … +59 | Descuentos, avisos y buenos reclutas | — |
| **Correcto** | +10 … +29 | Trato normal y mejor | — |
| **Sin nombre** | −9 … +9 | Nadie habla de ti | Los tablones no te cuelgan los mejores encargos |
| **Duro** | −10 … −29 | Te temen en las posadas | Recargo **+10 %** y testigos en tu contra |
| **Fiera** | −30 … −59 | Los enemigos **huyen antes** (se rompen con la moral en 10, en vez de 0); los bandidos te venden | Guardias y casas te cierran la puerta; recargo **+25 %** |
| **Hiena** | −60 … −100 | Los débiles se rinden antes y la moral enemiga **se rompe al llegar a 10** (como Fiera) | **Todos** cobran **+40 %**, nadie te fía y los honorables no te siguen |

Cada banda tiene su puerta y su trampa: **no hay una Firma «buena»**, hay la que quieres jugar.

---

## 4. Qué la mueve

Pesos: leve **±1** · medio **±3** · grave **±6** · capital **±10** (clases orientativas: el peso exacto de cada hecho manda en la tabla §4). Todo a la vista de
testigos (regla 1).

| Hecho | Peso | Dónde ocurre |
|---|---|---|
| Aceptaste una rendición | +3 | Fin de batalla |
| Perdonaste a un capitán | +5 | Fin de batalla |
| Devolviste un prisionero sin cobrar | +4 | Después de la batalla |
| Cumpliste tu rescate pagándolo | +3 | Cuando caes |
| Devolviste botín robado a aldeanos | +4 | Mundo |
| Peleaste en primera línea (tu héroe en contacto) | +2 | Batalla |
| Enmienda pública ante Escribano | +10 | Mundo (§7) |
| Tu héroe se escondió mientras caían los suyos | −4 | Batalla |
| Cargaste contra quienes ya huían | −6 | Batalla |
| Robaste o despojaste a aldeanos | −7 | Mundo |
| Ejecutaste a un rendido | −8 | Fin de batalla |
| Caíste y dejaste morir a tu gente | −6 | Cuando caes |
| Mataste a un capitán ya rendido | −10 | Fin de batalla |
| Usaste a un rehén como escudo | −10 | Batalla |

- **Tope:** −100 … +100.
- **Conservación:** los **últimos 16 hechos** de Firma se guardan con su día para que la
  Crónica pueda redactarlos (`{d, t, p}`), igual que la memoria.

---

## 5. Cómo se enlaza con la memoria

Cuando un PNJ **desconocido** te conoce por primera vez, no arranca en 0: arranca con su
**rango inicial = Firma ÷ 10** (redondeado, y siempre acotado a ±10).

- Eres **Hiena (−80)** → el aldeano que nunca te vio ya te mira con **−8**.
- Eres **Palabra dada (+70)** → el mismo aldeano empieza en **+7**.

Así la Firma **siembra** la memoria personal: el mundo ya llega con una idea formada, y
después cada uno te guarda tu rango aparte. Nunca al revés: un rango personal altísimo no te
sube la Firma si nadie lo vio.

---

## 6. Quién lee la Firma

| Quién | Qué hace con ella |
|---|---|
| Bandos enemigos | Con Fiera/Hiena **huyen antes** y te buscan a ti; con Palabra dada, los nobles no huyen |
| Mercaderes y posadas | Recargos por banda (§3) |
| Tablones y portavoces | Los encargos de honor exigen banda ≥ Correcto |
| Reclutas | Los honorables solo se unen a Firma ≥ Honrado; los crítos, a Firma ≤ Fiera |
| Casas nobles y Escribanos | Solo negocian contigo desde Correcto hacia arriba |
| `02_PRISIONEROS.md` | Los rendidos ante una Firma baja esperan lo peor: se rinden más pronto |
| `04_CRONICA.md` | Redacta tus últimos 16 hechos públicos con el nombre de tu banda |
| `11_DEUDAS_DEL_JUGADOR.md` | La asamblea del Acto III lee tu Firma pública |

---

## 7. La enmienda

Para que una Firma baja **no sea una condena eterna** (la derrota nunca bloquea):

- **Máximo 3 enmiendas por partida.**
- Cuesta **100 oro** y **1 día** con un Escribano de la Sangre.
- Efecto: **+10** de Firma, a la vista de toda la plaza.
- **No sirve para bajar** la Firma: solo sube.
- Cada enmienda queda registrada como hecho público y la Crónica la narra.

---

## 8. Datos, tipos y validación

- **Guardado:** `firma` (entero), `enmiendas` (0…3) y `firmaHechos` (máx 16) en `SaveState`
  → aditivo, junto con `memoria` (`00_MEMORIA_Y_DEUDA.md` §10).
- **Tipos:** `FirmaEstado` y `HechoFirma` en `js/data/game_types.js` (una sola vez).
- **Validación:** esquema en `js/data/schemas.js`; los enums de hechos, cruzados en
  `tools/validate_data.js`.
- **Sistema puro:** `js/systems/firma.js` — sin DOM, sin reloj (el día entra en `dt`/día de juego),
  RNG inyectado; las escenas solo **emiten hechos** y pintan la banda.
- **Tests (por escribir):** `tests/firma.test.js`, mínimo 3 casos (normal, borde, error).

---

## 9. Qué entra en la demo (Fase 1)

- La Firma **se ve desde la primera batalla** (banda de 4 palabras en el HUD: Sin nombre,
  Correcto, Duro, Fiera son alcanzables en el Acto I).
- **1 enmienda** disponible (la de la plaza del cadalso, si la gastas).
- Los 4 hechos de batalla de §4 que ya ocurren en la demo: rendición, perdón, ejecución y
  carga contra huidos.
- Recargos y reclutas por banda **activos** en los 6 sitios.
- **Mismas cifras que en el juego completo.**

---

## 10. Cifras que fija este documento

| Cifra | Valor |
|---|---|
| Valor | −100 … +100, sin decay |
| Bandas | 7 (Palabra dada → Sin nombre → Hiena) |
| Pesos | ±1 / ±3 / ±6 / ±10 |
| Rango inicial de un desconocido | Firma ÷ 10 (±10) |
| Enmiendas | 3 por partida · 100 oro · +10 |
| Hechos guardados | últimos 16 |
| Recargos | Duro +10 % · Fiera +25 % · Hiena +40 % |
| Efecto moral en batalla | Fiera/Hiena: la moral rota llega a 10 en vez de a 0 |

---

## 11. Fuera de este documento

- Rangos personales y memoria → `00_MEMORIA_Y_DEUDA.md`
- Los actos concretos del fin de batalla → `02_PRISIONEROS.md`
- Cómo se redacta y se lee → `04_CRONICA.md`
- Reclutas y precios → `../contenido/00_TROPAS.md`, `06_ECONOMIA.md`
- Pantalla que la enseña → `../interfaz/02_HUD.md`
