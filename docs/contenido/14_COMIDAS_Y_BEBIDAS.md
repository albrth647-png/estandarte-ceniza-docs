# 14 · Comidas y bebidas — lo que se come en Valcoria

**Estado:** ✅ **aprobado por el dueño (aprobación en bloque, 2026-09-30). Documento final.**

> Una compañía de deudores **come o se deshace** (`../mundo/10_SUPERVIVENCIA_Y_DESCANSO.md`). Aquí
> está **qué se come, qué alimenta y cuánto cuesta**; las reglas de consumo, hambre y descanso, en
> `../mundo/10_SUPERVIVENCIA_Y_DESCANSO.md`; los precios del grano, en `05_RECURSOS_Y_MERCADO.md`;
> el clima que encarece, en `../mundo/09_CLIMA_Y_ESTACIONES.md`.
>
> **Platos, ids y precios son propuesta de diseño** (cambiables → `../DECISIONES.md`).

---

## 1. Los alimentos

| id | Comida | Qué es | Raciones | Nota |
|---|---|---|---|---|
| `pan` | **Pan** | Hogaza de la aldea | 1 | Barato, no se guarda mucho |
| `racion` | **Ración de campaña** | Pan, tocino, queso | 1 | La unidad de `10_SUPERVIVENCIA` §1 |
| `grano` | **Grano** | Saco | **10** | Se compra por saco (`05_RECURSOS_Y_MERCADO.md` §1) |
| `tocino` | **Tocino** | Carne salada | 1 | Se conserva |
| `queso` | **Queso** | De oveja o cabra | 1 | Aguanta el viaje |
| `potaje` | **Potaje caliente** | Guiso de posada | 1 | **+5 de moral** la primera del día |
| `salazon` | **Salazón** | Pescado de río | 1 | Ribera barata |
| `fruta` | **Fruta** | Del árbol del camino | 1 | Recogible (`../mundo/07_PROPS_Y_VEGETACION.md`) |

- **La ración es la unidad de juego** (`../mundo/10_SUPERVIVENCIA_Y_DESCANSO.md` §1): 1 por tropa y
  día. Todo lo demás **es una ración con nombre**; el potaje y el salazón solo cambian el **efecto
  extra**, no la cuenta diaria.
- **La caza** da carne (raciones) sin pasar por el mercado
  (`08_ANIMALES_Y_CRIATURAS.md` §4).

---

## 2. Las bebidas

| id | Bebida | Efecto | Coste |
|---|---|---|---|
| `agua` | **Agua** | Nada; obligatoria con la ración | 0 |
| `vino` | **Vino** | **+5 de moral** de campaña; una vez por día | 3 oro la jarra |
| `cerveza` | **Cerveza** | **+3 de moral**; barata | 2 oro |
| `aguardiente` | **Aguardiente** | **+8 de moral** pero **−10 % de sigilo** al día siguiente | 5 oro |

- **El alcohol sube la moral de campaña, no la de combate** (`../sistemas/08_LUTO_Y_MORAL.md` §3):
  la moral del campo empieza en 100 siempre (`../batalla/01_CIFRAS.md` §5).
- **Borracho no es gratis:** el aguardiente baja el sigilo (`../mundo/01_EXPLORACION.md` §3) — sirve
  para celebrar, no para infiltrarse.
- **Nunca incapacita al héroe:** un día de resaca cuesta, no bloquea (Pilar 3).

---

## 3. Energía, moral y descanso

| Comer / beber | Efecto | Límite |
|---|---|---|
| **Ración del día** | Evita el hambre (−5 moral/día, `../mundo/10_SUPERVIVENCIA` §1) | 1 por tropa |
| **Potaje caliente** | **+5 de moral** | 1ª del día |
| **Vino / cerveza** | +5 / +3 de moral de campaña | 1 por día |
| **Cena de posada** | Recupera **vida y moral completas** | 1 noche (`§2`) |
| **Banquete** | **Funeral**: +10 de moral (`../sistemas/08_LUTO_Y_MORAL.md` §3) | 1 por luto |

- **La comida no cura heridas graves:** eso es el **barbero** (`00_TROPAS.md` §3.3) o el descanso
  (`../mundo/10_SUPERVIVENCIA_Y_DESCANSO.md` §3).
- **El hambre no mata:** debilita y baja moral, nunca acaba la partida (`../mundo/10_SUPERVIVENCIA` §3).

---

## 4. Comer con la tropa

- **Cada tropa come 1 ración/día** (el héroe, 1) — la cuenta de `../mundo/10_SUPERVIVENCIA` §1.
- **La reserva se guarda** en la mochila/carreta (`04_ITEMS_Y_EQUIPO.md` §5, `13_MONTURAS_Y_TRANSPORTE.md` §3).
- **Sin reserva ni oro:** la compañía pierde **−5 de moral/día** y puede desertar
  (`../sistemas/10_LEALTAD_Y_DESERCION.md` §2). La salida siempre existe: cazar, pedir fiado o
  aceptar un encargo de `escoltar` (`../misiones/00_TIPOS_DE_ENCARGO.md`).
- **Repartir de más** (banquete) sube moral **una vez por botín** (`../sistemas/08_LUTO_Y_MORAL.md` §3).

---

## 5. Mercados, posadas y temporada

- **Dónde se compra:** granero y mercado de aldea; posada y cruce (raciones); mercado de ciudad
  (todo) (`05_RECURSOS_Y_MERCADO.md` §4).
- **Precio por zona:** puerto y ribera **abaratan** el pescado y el grano; la serranía **encarece**
  (aislamiento) (`05_RECURSOS_Y_MERCADO.md` §3).
- **Precio por estación:** sequía e invierno **encarecen** el grano (`../mundo/09_CLIMA_Y_ESTACIONES.md`);
  el hambre de una aldea quemada lo dispara (`09_EDIFICIOS_Y_ESTRUCTURAS.md` §2).
- **Precios de referencia:** ración **2 oro** · saco de grano **12 oro** · noche de posada **5 oro**
  (+ cena **7 oro**) (`../sistemas/06_ECONOMIA.md` §4).

---

## 6. Comida para el luto y para los favores

- **Funeral:** un **banquete** pagado da **+10 de moral** tras el luto
  (`../sistemas/08_LUTO_Y_MORAL.md` §3). Sin banquete, la semana de luto pesa entera.
- **Favor de mesa:** dar techo y cena una noche es un **favor de hasta 100 oro**
  (`../sistemas/03_FAVORES.md` §4): se puede **cobrar** o **conceder**.
- **La mesa como disculpa:** invitar a un enemigo a comer no borra el rencor, pero abre una
  reconciliación (`../sistemas/00_MEMORIA_Y_DEUDA.md` §4, hecho 15 · +15).

---

## 7. Datos, tipos y validación

- **Datos:** `data/comidas.json` — `{ id, tipo (alimento/bebida), raciones, efecto, coste_base,
  moral, se_conserva }`.
- **Tipos:** `Comida` y `Bebida` en `js/data/game_types.js` (una sola vez, regla 4).
- **Validación:** esquema en `js/data/schemas.js` + cruce con `data/economia.json` (precios) y con
  `data/supervivencia.json` (ración/día) en `tools/validate_data.js`.
- **Sistema puro:** `js/systems/comida.js` — consumo, efecto y conservación; sin DOM, sin reloj
  (día por `save.day`), RNG inyectado.
- **Tests:** `tests/comida.test.js`, mínimo 3 casos (normal, borde, error): sin raciones la moral
  baja; el vino no sube la moral de campo; el hambre no mata.

---

## 8. Cifras que fija este documento

| Cifra | Valor |
|---|---|
| Alimentos | **8** |
| Bebidas | **4** |
| Ración por unidad y día | **1** |
| Ración / saco de grano | 2 oro / 12 oro (10 raciones) |
| Potaje | +5 de moral (1ª del día) |
| Vino / cerveza / aguardiente | +5 / +3 / +8 (−sigilo) |
| Banquete funeral | +10 de moral |
| Noche de posada (+ cena) | 5 (+2) oro |

---

## 9. Qué entra en la demo (Fase 1) — y qué sigue

> **Hasta aquí la demo.** **Ración, grano, pan, potaje y agua/vino**, con el consumo diario de la
> compañía, el potaje de posada y el banquete de los 3 funerales del Acto I. Precios simples, sin
> temporada.

> **Y sigue el juego completo.** Tocino, queso, salazón, fruta, cerveza y aguardiente, y la
> **variación por zona y estación**, se añaden **con estas mismas reglas**: crecer = más filas en
> `comidas.json`, no otro sistema de hambre.

---

## 10. Fuera de este documento

- Consumo, hambre y descanso → `../mundo/10_SUPERVIVENCIA_Y_DESCANSO.md`
- Precios y grano → `05_RECURSOS_Y_MERCADO.md`, `../sistemas/06_ECONOMIA.md`
- Clima y estaciones → `../mundo/09_CLIMA_Y_ESTACIONES.md`
- Moral y luto → `../sistemas/08_LUTO_Y_MORAL.md`
- Favores de mesa → `../sistemas/03_FAVORES.md`
- Caza → `08_ANIMALES_Y_CRIATURAS.md`
