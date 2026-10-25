# 00 · Memoria y deuda — el corazón de Valcoria

**Estado:** ✅ **aprobado por el dueño (2026-09-30). Documento final.**

> Este es el sistema del que cuelgan casi todos los demás. Describe el **juego completo** y
> cierra con su sección de demo. Cierra el pendiente nº 3 de `../DECISIONES.md` (rangos de
> relación, deuda, precios de rescate y topes de guardado).

---

## 1. Por qué existe (Pilar 3)

La Ordenanza de la Sangre dice que **la sangre derramada se paga**. Si el mundo no recuerda,
no hay deuda que cobrar ni nada que perdonar. De aquí salen tres promesas que este sistema
tiene que cumplir:

1. **Memoria universal**: *todo* PNJ recuerda lo que le hiciste — también el aldeano más
   humilde. Nadie es decorado.
2. **La deuda viaja**: se paga, se hereda, se perdona o se quema. Nunca desaparece sola.
3. **La derrota no bloquea**: si caes, el mundo cobra (rescate/rehén) y el juego sigue.

Base narrativa: `../historia/00_PREMISA.md` (la Ordenanza, los Escribanos, el Libro Mayor).

---

## 2. Dos capas de memoria

### 2.1 Memoria ligera — todos los PNJ

Una ficha compacta por persona que te ha visto o te ha hablado. **Coste mínimo, se guarda
siempre.** Campos (claves cortas a propósito, es JSON en el guardado):

| Campo | Tipo | Qué es |
|---|---|---|
| `id` | string | id del PNJ (`snake_case`, único) |
| `r` | entero −100…100 | **rango de relación** (§3) |
| `d` | entero | deuda **firmada**: `> 0` te debe · `< 0` le debes (§5) |
| `f` | 0 \| 1 | deuda blanca activa: te debe **un favor** (§6) |
| `u` | entero 0…15 | tipo del último hecho relevante (enum de §4) |
| `dia` | entero | día de juego en que ocurrió |
| `rw` | 0 \| 1 | tiene rencor activo (§7) |

### 2.2 Memoria completa — los «relevantes»

Personajes con historia propia: los de `../historia/02_PERSONAJES.md`, los **capitanes y
cabecillas**, posaderos, portavoces y remendones que te dan encargos. Se marcan en su ficha de
datos con `relevante: true`. Además de la ficha ligera, guardan una **lista de hechos**:

| Campo | Tipo | Qué es |
|---|---|---|
| `d` | entero | día de juego |
| `t` | entero 0…15 | tipo de hecho (enum de §4) |
| `p` | entero | peso aplicado al rango (−15…+15) |

- **Tope: 32 hechos por persona.** Al desbordar, los **4 últimos son intocables** y de los 28
  restantes se descarta el de menor peso absoluto (a empates, el más antiguo). **Nunca** se
  descarta un hecho de tipo *capital* de los últimos 7 días.
- Se guardan **enums, no texto**: ahorra bytes, la traducción es gratis (`txt_mem_*`) y la
  `04_CRONICA.md` los redacta en prosa cuando el jugador los lee.

---

## 3. Rangos de relación

De −100 a +100, con **bandas**. Un PNJ en una banda se comporta según ella; el rango no
caduca jamás por pasar el tiempo (solo cambia por hechos).

| Banda | Rango | Cómo te trata |
|---|---|---|
| **Verdugo** | −100 … −60 | Te ataca o llama a los suyos. No negocia. |
| **Enemigo** | −59 … −30 | Te cobrá mal, testificará contra ti, no te deja comprar. |
| **Hostil** | −29 … −10 | Te apura, descuenta tu descuento y aprieta el precio. |
| **Desconocido** | −9 … +9 | Trato neutral. |
| **Conocido** | +10 … +29 | Te da hora, avisa de peligro, te fía poco. |
| **Amigo** | +30 … +59 | Te abre su casa, te sigue en la batalla, baja precios. |
| **Hermano de sangre** | +60 … +100 | Va contigo, arriesga por ti y **rescata** si caes. |

Dos estados laterales, que conviven con la banda:

- **Deudor / acreedor** (campo `d`): cambia el trato *al margen* de la banda (quien te debe
  cobra menos; quien le debes te aprieta).
- **Rencor activo** (campo `rw`): **techo duro** — mientras dure, el rango no puede pasar de
  −20 hacia arriba, por mucho que hagas (§7).

---

## 4. Hechos: qué mueve el rango

Todo hecho tiene un **peso**: leve **±2**, medio **±5**, grave **±10**, capital **±15** (clases orientativas: el peso exacto de cada hecho manda en su tabla §4).
El rango se acota a [−100, +100]; los pesos se aplican en el día en que ocurren.

| Hecho (`t`) | Peso | Notas |
|---|---|---|
| 0 · Desconocido | 0 | Primera vez que le hablas |
| 1 · Trato cumplido | +2 | Compraste, pagaste, cumpliste hora |
| 2 · Encargo completado | +5 | Le resolviste lo que pedía |
| 3 · Salvado de morir | +10 | Le salvaste la vida en batalla o en el camino |
| 4 · Perdonado | +10 | Podías ejecutarlo y no lo hiciste → además §6 |
| 5 · Deuda pagada | +8 | Le saldaste lo que le debías |
| 6 · Favor cobrado | 0 | Consumir un favor no mueve el rango |
| 7 · Robo o despojo | −7 | |
| 8 · Cobro por la fuerza | −6 | |
| 9 · Incumplimiento | −5 | Dejaste un encargo a medias |
| 10 · Herido en pelea | −4 | |
| 11 · Humillación pública | −10 | Delante de testigos |
| 12 · Ejecución | −12 | Muerte que tú ordenaste |
| 13 · Muerte de un pariente | −15 | *Capital*: enciende rencores (§7) |
| 14 · Deuda heredada | −5 | Nace con la deuda de su padre |
| 15 · Reconciliación | +15 | Paga o perdona tras un rencor |

**Todo lo demás no mueve el rango.** Mirar, pasar, comprar al precio de tabla: 0.

---

## 5. La deuda: tres formas y una regla

| Forma | Se paga con | Heredable |
|---|---|---|
| **Oro** (componenda) | monedas | Sí |
| **Servicio** | hacerle un trabajo equivalente | Sí (si no, se convierte en oro) |
| **Sangre** (feudo) | una marca, un miembro de la casa o un duelo | Sí |

Reglas cerradas:

- La deuda **no caduca ni genera intereses**. Simplemente está.
- `d > 0` = te debe · `d < 0` = le debes. Cantidades enteras, en oro equivalente.
- **Herencia:** hijo/a directo hereda el **100 %**; si no hay, la casa o familia el **50 %**;
  si no queda nadie con su apellido, se extingue (por eso los Escribanos marcan la piel).
- **Rescate (si caes tú):** precio = **(nivel del héroe + 10) × 10** oro. Ej.: nivel 1 → 110;
  nivel 15 → 250. Si no lo pagas, no hay Game Over: sales **por servicio** (misma deuda, otra
  forma) y la partida sigue. Detalle y variantes en `02_PRISIONEROS.md`.

---

## 6. Deuda blanca (el perdón)

- Un **perdón** (hecho 4) convierte la deuda pendiente en **deuda blanca**: el campo `f` pasa
  a 1 y la cantidad `d` se pone a 0.
- Es **un favor, cobrable una sola vez**: se consume al usarlo (hecho 6, peso 0).
- **No se hereda**: es cosa suya, no de sus hijos.
- **Caduca** a los **90 días de juego** si no lo usas; al caducar simplemente desaparece (sin
  castigo adicional: ya perdonaste).

---

## 7. Rencores

- **Cómo nace:** un hecho *capital* (13 · muerte de pariente, 11 · humillación pública,
  12 · ejecución fallida, 7 · despojo) o varias ofensas graves seguidas (3 de peso ≤ −7).
- **Cuánto dura:** **no caduca nunca.** Solo se apaga con la sección 15 · Reconciliación
  (+15) o con la muerte del que lo lleva.
- **Efecto:** techo de rango en **−20** mientras esté activo (§3).
- **Herencia:** el rencor **de sangre** se transmite a los parientes directos con la mitad de
  su fuerza y marca a toda la casa (la casa queda, para ti, **Enemigo** mínimo).
- **Topes:** 1 rencor por PNJ ligero, **3** por relevante, **60 rencores activos** en toda la
  partida. Al llegar al tope, el más antiguo y de menor peso se cierra con un aviso.

---

## 8. Topes y tamaño del guardado (≤ 5 MB)

| Cota | Valor | Motivo |
|---|---|---|
| Fichas ligeras por **lugar** | **25** | El lugar no acuerda más gente de la que se ve |
| Fichas ligeras totales | **400** | Techo de la partida completa |
| Relevantes con memoria completa | **60** | Los que tienen historia |
| Hechos por relevante | **32** | §2.2 |
| Rencores activos | **60** | §7 |
| **Memoria total en el guardado** | **≤ 400 KB** | Deja ~4,5 MB al resto del `SaveState` |

Cálculo real: ficha ligera ≈ 60 B (400 → 24 KB) + relevante ≈ 32 × 36 B ≈ 1,2 KB
(60 → 70 KB) ≈ **94 KB**. El tope de 400 KB deja margen para partidas largas con muchos
hechos.

**Si se supera la cota:** olvido **por orden de peso** (se caen los hechos y fichas de menor
peso absoluto). **Nunca** se pierde el rango (`r`), la deuda (`d`), el favor (`f`) ni un
rencor (`rw`). La memoria se apaga, la deuda no.

---

## 9. Quién usa este sistema

| Sistema | Qué le pide a la memoria |
|---|---|
| `01_FIRMA.md` | Lee los rangos de los relevantes: cómo te ven los que te ven a menudo |
| `02_PRISIONEROS.md` | El prisionero con banda Enemigo o peor no se volta; con Amigo, se va contigo |
| `03_FAVORES.md` | Lee y consume `f` |
| `04_CRONICA.md` | Redacta los hechos de los relevantes en prosa legible |
| `06_ECONOMIA.md` | Descuentos y recargos según banda y `d` |
| Encargos y tablones | Quién te da trabajo depende de su banda |
| `../historia/05_CASAS_Y_FACCIONES.md` | La casa hereda la memoria de sus miembros (media ponderada) |
| IA de batalla y moral | Los que te odian **no huyen tan pronto** y te buscan a ti |
| `11_DEUDAS_DEL_JUGADOR.md` | La asamblea lee tu deuda total y tu rango medio en el reino |

---

## 10. Datos, tipos y validación

- **Guardado:** campo nuevo `memoria` en el guardado (aditivo:
  la migración rellena `memoria` vacío en partidas de versiones anteriores; nunca borra nada).
- **Tipos:** `FichaMemoria` y `HechoMemoria` en `js/data/game_types.js` (una sola vez, regla 4).
- **Validación:** esquema en `js/data/schemas.js` + cruce de `id` de PNJ en
  `tools/validate_data.js`; sin eso, `loadData()` no arranca (regla 5).
- **Sistema puro:** la memoria vivirá en `js/systems/memoria.js` — sin DOM, sin fetch, sin
  reloj: todo se mide en días de juego y los RNG se inyectan (regla 2).
- **Tests (por escribir):** `tests/memoria.test.js`, mínimo 3 casos (normal, borde, error).

---

## 11. Qué entra en la demo (Fase 1)

- **6 sitios** × cupo 25 = **150 fichas ligeras**.
- **12 relevantes** con memoria completa (los del Acto I y sus capitanes).
- **3 rencores de historia** (la casa que abrió la puerta, un aldeano de la aldea de la
  marca, un capitán que sobrevive).
- **Rescate** jugable tras caer, con la fórmula de §5.
- **Deuda blanca** visible en el primer perdón.
- **Cifras idénticas a las del juego completo**: no hay nada que rehacer al escalar.

---

## 12. Cifras que fija este documento

| Cifra | Valor |
|---|---|
| Rango | −100 … +100 (7 bandas, §3) |
| Pesos de hecho | ±2 / ±5 / ±10 / ±15 |
| Topes de rango | ±100; rencor = techo −20 |
| Hechos por relevante | 32 (4 intocables) |
| Favor (deuda blanca) | 1 uso · caduca a 90 días · no se hereda |
| Herencia de deuda | hijo 100 % · casa 50 % · sin herederos se extingue |
| Rescate | (nivel + 10) × 10 oro · sin oro = servicio |
| Topes de guardado | 25/lugar · 400 fichas · 60 relevantes · 60 rencores · ≤ 400 KB |
| Demo | 150 fichas · 12 relevantes · 3 rencores |

---

## 13. Fuera de este documento

- Cómo se **mide** tu reputación global → `01_FIRMA.md`
- Las **4 salidas** del fin de batalla → `02_PRISIONEROS.md`
- Variantes de rescate y rehén → `02_PRISIONEROS.md`
- Cómo se **redacta** en pantalla → `04_CRONICA.md`
- Precios y flujos de oro → `06_ECONOMIA.md`
- Cómo se guarda todo → `../produccion/02_GUARDADO_Y_DATOS.md`
