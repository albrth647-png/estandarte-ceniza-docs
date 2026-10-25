# 04 · Ítems y equipo — lo que llevas encima

**Estado:** ✅ **aprobado por el dueño (aprobación en bloque, 2026-09-30). Documento final.**
**Enmienda 2026-10-02:** entra el **tipo `joya`** con **2 ranuras de anillo + 1 de amuleto** y **8
piezas**, y las **4 armas nuevas** que fabrica el herrero. Catálogo y reglas en
`../sistemas/15_FABRICACION_Y_RECETAS.md` §7 y §8.

> En Valcoria **el equipo no te hace héroe: te hace aguantar** (Pilar 5, `../VISION_JUEGO_COMPLETO.md`).
> Aquí están las **armas, armaduras, herramientas y su rareza**, cómo se **mejoran** y cuánto cabe
> en la **mochila**. Los precios y flujos, en `../sistemas/06_ECONOMIA.md`; los stats base de
> combate, en `../batalla/01_CIFRAS.md`; las piezas únicas, en `07_ARTEFACTOS.md`.
>
> **Rarezas, ids y cifras de este catálogo son propuesta de diseño** (cambiables →
> `../DECISIONES.md`).

---

## 1. La regla del equipo

1. **El arma manda, la rareza matiza:** el **tipo** de arma fija alcance y cadencia
   (`../batalla/01_CIFRAS.md` §3); la rareza sube stats, nunca cambia el rol.
2. **Nada de números infinitos:** el techo de mejora no rompe `../batalla/01_CIFRAS.md` (§7).
3. **El equipo se pierde:** al caer (`../sistemas/02_PRISIONEROS.md` §7) o al ser saqueado puedes
   quedarte sin él; por eso el equipo común se repone.
4. **Cada tropa lleva su equipo:** las armas no son solo del héroe (`00_TROPAS.md` §6).

---

## 2. Rarezas (4)

| Rareza | id | Ajuste de stats | Mejoras | Se encuentra |
|---|---|---|---|---|
| **Común** | `comun` | ×1,00 | **no** se mejora | Mercado, botín corriente |
| **Buena** | `buena` | ×1,10 | hasta **+1** | Mercado de ciudad, botín de capitán |
| **Rara** | `rara` | ×1,25 | hasta **+2** | Recompensa, casa, hallazgo |
| **Nombrada** | `nombrada` | ×1,45 | hasta **+3** | Única; piezas de trama (`07_ARTEFACTOS.md`) |

- **El ajuste multiplica** el ataque (armas) o la defensa (armaduras) **base del tipo**: nunca
  cambia vida, alcance ni cadencia.
- Una pieza **nombrada** siempre tiene **dueño anterior y rastro narrativo** (`07_ARTEFACTOS.md`).

---

## 3. Tipos y stats base

### 3.1 Armas

| id | Arma | Rol (`00_TROPAS.md`) | Alcance | Ataque base | Nota |
|---|---|---|---|---|---|
| `w_lanza` | Lanza | Línea | 3,5 m | 16 | Aguanta la carga |
| `w_espada` | Espada y escudo | Línea | 2,5 m | 16 | Mejor Guardia |
| `w_hacha` | Hacha | Línea | 2,5 m | 18 | Rompe escudos y empalizadas |
| `w_ballesta` | Ballesta | Distancia | 18 m | 16 | Recarga lenta |
| `w_arco` | Arco | Distancia | 18 m | 13 | Cadencia alta |
| `w_honda` | Honda | Distancia | 14 m | 11 | Barata; puede aturdir |
| `w_daga` | Daga | — | 1,8 m | 12 | Ligera; la del prólogo |
| `w_asta` | Asta y bandera | Apoyo | 2,5 m | 12 | La del portaestandarte |

- El **ataque base** entra en la fórmula de daño `ataque × 80 / (defensa + 80)`
  (`../batalla/01_CIFRAS.md` §2).
- **El héroe empieza con una espada alquilada** (`../sistemas/06_ECONOMIA.md` §2); es común y
  pertenece a Doña Sira hasta que la reclamas (`../sistemas/11_DEUDAS_DEL_JUGADOR.md`).

### 3.1b Las 4 armas nuevas del herrero ✅ 2026-10-02

**No son del catálogo**: son **armas nuevas que fabrica el héroe** con la profesión de herrero. Cada
una tiene **3 apariencias** distintas (12 modelos en total); la apariencia **no cambia** stats,
alcance ni cadencia. Detalle en `../sistemas/15_FABRICACION_Y_RECETAS.md` §7.

| id | Arma | Rol | Alcance | Ataque base | Apariencias |
|---|---|---|---|---|---|
| `w_martillo` | **Martillo de guerra** | Línea | 2,5 m | 17 | 3 |
| `w_alabarda` | **Alabarda** | Línea | 3,5 m | 15 | 3 |
| `w_hoz` | **Hoz de guerra** | Línea | 2,0 m | 13 | 3 |
| `w_mandoble` | **Mandoble** | Línea | 2,5 m | 19 | 3 |

- Sus ataques base (13-19) quedan **un punto por encima del techo del catálogo** (11-18):
  es la ventaja de fabricar. No rompen `../batalla/01_CIFRAS.md` §3.
- **Las 8 armas del catálogo** (§3.1) siguen siendo **solo de mercado o botín**: el herrero no las
  fabrica.

### 3.2 Armaduras y escudos

| id | Pieza | Defensa base | Nota |
|---|---|---|---|
| `a_cota` | Cota de malla | +8 | General |
| `a_cuero` | Peto de cuero | +4 | Barato, ligero |
| `a_casco` | Casco | +3 | Reduce un crítico a la mitad 1 vez |
| `a_escudo` | Escudo | +5 | Solo con espada; mejora Guardia |

### 3.3 Joyas (4 anillos + 4 amuletos: 8 piezas) ✅ 2026-10-02

**8 piezas**, todas de la herrería. Los efectos son **pequeños** y entran en la mitigación normal
(`../batalla/01_CIFRAS.md` §2): **no hay golpe extra**. Materiales y receta en
`../sistemas/15_FABRICACION_Y_RECETAS.md` §8.

| id | Joya | Ranura | Efecto |
|---|---|---|---|
| `j_anillo_hierro` | Anillo de hierro | Anillo | **+1 ataque** |
| `j_anillo_plata` | Anillo de plata | Anillo | **+2 ataque** |
| `j_anillo_cuero` | Anillo de cuero | Anillo | **+1 defensa** |
| `j_anillo_piedra` | Anillo de piedra tallada | Anillo | **+2 defensa** |
| `j_amuleto_vida` | Amuleto de vida | Amuleto | **+10 vida** |
| `j_amuleto_coraje` | Amuleto de coraje | Amuleto | **+5 vida** |
| `j_amuleto_piedra` | Amuleto de piedra | Amuleto | **+1 defensa** |
| `j_amuleto_plata` | Amuleto de plata | Amuleto | **+1 ataque** |

- **Ranuras del héroe:** `arma` · `armadura` · `escudo` · `anillo_1` · `anillo_2` · `amuleto`.
  Los dos anillos son intercambiables; el amuleto es una ranura aparte.
- **Verificación obligatoria:** anillo de plata (+2) + arma `rara` +1 en nivel 30 no puede pasar de
  **90 de daño por golpe** (test de borde por escribir).

### 3.4 Herramientas (no combaten)

| id | Herramienta | Para |
|---|---|---|
| `t_pico` | Pico | Abrir derrumbes y empalizadas (`12_TRAMPAS_Y_OBSTACULOS.md`) |
| `t_hacha_lena` | Hacha de leña | Leña y puertas (`../mundo/07_PROPS_Y_VEGETACION.md`) |
| `t_yesca` | Yesca y pedernal | Encender fuego de campamento (`../mundo/10_SUPERVIVENCIA_Y_DESCANSO.md`) |
| `t_vendas` | Vendas de barbero | Curar fuera de combate 1 vez |

- Una herramienta **no da stats**: da **puertas** (lo que se puede abrir o hacer).
- El **zapador** (`00_TROPAS.md` §3.3) ya trae pico y hacha: no hace falta comprarlas para él.
- Las **4 armas nuevas** y las **8 joyas** se fabrican, no se compran: son de la herrería del sitio
  (`../sistemas/15_FABRICACION_Y_RECETAS.md` §7 y §8).

---

## 4. Mejoras (el herrero)

- **3 niveles** (`+1` / `+2` / `+3`): cada nivel **×1,10** sobre la base de la pieza (acumulativo,
  redondeado hacia abajo). Una común **no se mejora** (§2).
- **Dónde:** en cualquier **herrería** (aldea o ciudad, `09_EDIFICIOS_Y_ESTRUCTURAS.md`).
- **Coste:** oro + **hierro** (`05_RECURSOS_Y_MERCADO.md`); sube por nivel y por rareza.
  Reparar un arma sin mejora, `10-25 oro` (`../sistemas/06_ECONOMIA.md` §4).
- **Puertas de nivel:** `+2` exige **nivel 8** del héroe; `+3`, **nivel 12**
  (`../sistemas/05_PROGRESION.md` §1).
- **Quién la hace:** el **herrero** de la plaza; el **armero de casa** puede hacer las raras. **Y el
  héroe con profesión de herrero fabrica en el taller del sitio**
  (`../sistemas/15_FABRICACION_Y_RECETAS.md` §4): lo que sale de sus manos **nunca pasa de `rara`
  ni de `+1`**.
- **Techo:** una `nombrada` `+3` no pasa del **daño máximo por golpe** de `../batalla/01_CIFRAS.md`
  (90 héroe / 45 tropa).

---

## 5. La mochila (carga limitada)

- **Huecos de mochila = 12 + equipo puesto** (no ocupa). Las **carretas** la amplían
  (`13_MONTURAS_Y_TRANSPORTE.md`); sin carreta, eres tú y tu espalda.
- **Peso por pieza:** arma 3 · armadura 5 · herramienta 2 · consumible 1. **Tope de carga** = el
  que fije su mochila; con exceso, **no puedes correr** (andar sí).
- **Lo que se pierde al viajar:** nada, salvo lo que dejes o te roben (`12_TRAMPAS_Y_OBSTACULOS.md`);
  la comida se estropea despacio (`../mundo/10_SUPERVIVENCIA_Y_DESCANSO.md` §1).
- **Regla dura:** **ningún objeto único del guion** ocupa mochila de forma que bloquee la trama
  (los artefactos van a un **estante** aparte, `07_ARTEFACTOS.md` §6).

---

## 6. Dónde se encuentran

| Vía | Qué sale | Referencia |
|---|---|---|
| **Mercado** | Común y buena, precio de tabla | `05_RECURSOS_Y_MERCADO.md` |
| **Botín** | Común, buena y, rara vez, rara | `11_TABLAS_DE_BOTIN.md` |
| **Recompensa de encargo** | Buena o rara según clase | `../misiones/04_PAGOS_Y_RECOMPENSAS.md` §2 |
| **Hallazgo** | Rara, en ruinas y contenedores | `11_TABLAS_DE_BOTIN.md` |
| **Única (nombrada)** | Solo por trama o asamblea | `07_ARTEFACTOS.md` |

- **El equipo no se fabrica de la nada:** el hierro sale de `05_RECURSOS_Y_MERCADO.md` y el
  mercado tiene **stock finito** (`../sistemas/06_ECONOMIA.md` §7).

---

## 7. Datos, tipos y validación

- **Datos (por crear):** `data/items.json` — `{ id, tipo (arma/armadura/joya/herramienta/consumible), rol, rareza,
  stats, peso, mejoras_max, precio_base, donde, apariencia }`.
- **Tipos:** `Item`, `TipoItem` y `Rareza` en `js/data/game_types.js` (una sola vez, regla 4).
- **Validación:** esquema en `js/data/schemas.js` + cruce con `data/tropas.json` (rol y arma) y con
  `../batalla/01_CIFRAS.md` (stats conocidas) en `tools/validate_data.js`.
- **Sistema puro:** `js/systems/items.js` — aplica rareza, mejora y carga; sin DOM ni reloj.
- **Tests (por escribir):** `tests/items.test.js`, mínimo 3 casos (normal, borde, error): una común no se mejora;
  el `+3` respeta el techo de daño; una mochila llena no rompe el guardado.

---

## 8. Cifras que fija este documento

| Cifra | Valor |
|---|---|
| Rarezas | **4** (común · buena · rara · nombrada) |
| Ajustes de rareza | ×1,00 / ×1,10 / ×1,25 / ×1,45 |
| Mejoras | hasta **+3** · ×1,10 por nivel · común no se mejora |
| Puertas de mejora | +2 nivel 8 · +3 nivel 12 |
| Armas del catálogo | **8** |
| Armas nuevas del herrero | **4** × **3 apariencias** = **12 modelos** ✅ 2026-10-02 |
| Armaduras / escudos | **4** |
| Joyas | **8** (4 anillos + 4 amuletos) · ranuras 2 + 1 ✅ 2026-10-02 |
| Herramientas | **4** |
| Mochila | **12** huecos (+ equipo puesto) · carreta amplía |
| Reparar arma | 10-25 oro |

---

## 9. Qué entra en la demo (Fase 1) — y qué sigue

> **Hasta aquí la demo.** Las **3 armas base** (`w_lanza`, `w_ballesta`, `w_honda`/`w_arco`), la
> **cota** y el **escudo** comunes, las **vendas** y el **pico**, con la **herrería de Herreruela**
> (`../mundo/03_LUGARES.md` §2) haciendo reparaciones y `+1`. La mochila de 12 huecos, funcionando.

> **Y sigue el juego completo.** Las rarezas `rara`/`nombrada`, las armas de montado y las
> herramientas de asedio se añaden **con estas mismas reglas y la misma fórmula**: crecer = más
> filas en `items.json`, no un sistema nuevo.

---

## 10. Fuera de este documento

- Stats y fórmula de daño → `../batalla/01_CIFRAS.md`
- Precios, oro y salarios → `../sistemas/06_ECONOMIA.md`
- Recursos, hierro y trueque → `05_RECURSOS_Y_MERCADO.md`
- Piezas únicas → `07_ARTEFACTOS.md`
- Dónde y con qué probabilidad salen → `11_TABLAS_DE_BOTIN.md`
- Herrerías y talleres → `09_EDIFICIOS_Y_ESTRUCTURAS.md`
- Carretas y carga → `13_MONTURAS_Y_TRANSPORTE.md`
