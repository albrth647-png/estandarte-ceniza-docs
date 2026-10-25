# 03 · IA y órdenes — quién decide qué

**Estado:** ✅ **aprobado por el dueño (aprobación en bloque, 2026-09-30). Documento final.**

> Decidido: **órdenes globales para tus tropas + IA propia de cada unidad**, sin micromando
> (`00_REGLAS.md` §6–§7). Aquí se detalla **cómo decide cada bando y qué cuesta cambiar de
> idea**. Las cifras generales están en `01_CIFRAS.md`; las de este documento (§9) son las de
> decisión, reacción y castigo por cambio de orden.

---

## 1. Las dos capas

Toda unidad obedece a **dos capas a la vez**:

1. **La orden global** (la tuya, para todo tu bando): Cargar · Seguirme · Defender.
2. **La IA propia** (de la unidad): elige objetivo y se defiende sola cada **0,5 s**.

La orden global **inclina** la IA, no la anula: con Defender nadie persigue; con Cargar nadie se
queda atrás. Nadie espera tu permiso para defenderse — y nadie obedece si su moral está rota.

---

## 2. La IA de tus tropas

### 2.1 Cómo elige objetivo (cada 0,5 s)

1. **Enemigo dentro de su alcance** (`01_CIFRAS.md` §3): el más cercano.
2. Si hay varios, el **de menor vida** y luego el **que ya la está atacando**.
3. Si no hay nadie a alcance: se mueve hacia el enemigo más cercano **que pueda ver** (según la
   visibilidad del terreno, `02_TERRENO.md` §6).
4. **Nunca** elige a un enemigo que solo está herido y huyendo si hay otro delante: rematar al
   que huye es una **decisión tuya**, no suya.

### 2.2 Qué hace con cada orden

| Orden | Cómo la ejecuta tu tropa |
|---|---|
| **Cargar** | Avanza hacia el enemigo más cercano que vea; +30 % de velocidad 5 s y +10 de moral (`01_CIFRAS.md` §4–§5). Persigue si el enemigo retrocede |
| **Seguirme** | Se forma en torno a ti (radio 6 m) y se mueve a la velocidad de **tu tropa más lenta**; no persigue fuera de 12 m de ti |
| **Defender** | Mantiene posición en un radio de 4 m; −40 % de velocidad; +20 % de defensa; **no persigue** aunque el enemigo huya |

### 2.3 Cuándo huye (tu tropa)

- Con moral **0** (o **10** contra una Firma Fiera/Hiena), la unidad **rompe** y huye a 5,5 m/s.
- No vuelve al combate aunque la orden cambie: hay que **reagruparla** (§6).
- Si huye **un tercio** del bando, se dispara el **pánico en cadena** (`00_REGLAS.md` §8).

---

## 3. La IA enemiga

### 3.1 Cómo pelea por familia

La forma de pelear sale de `../contenido/01_ENEMIGOS.md`; la IA lee **el rasgo de la familia**:

| Familia (rasgo) | Cómo decide |
|---|---|
| **Bandidos / hostigadores** | Atacan y se apartan; huyen antes que nadie (rompen al llegar a 10, `01_CIFRAS.md` §5) |
| **Cuadrilla disciplinada** | Mantiene formación, protege al capitán, no se dispersa |
| **Patrulla de casa** | Cobra y avisa antes de pelear; se retira en orden si pierde a su capitán |
| **Fanáticos / feudo** | No se rinde hasta que la moral se rompe; busca al jugador (memoria/Firma) |

- La IA enemiga **también** lee la Firma y la memoria: los que te odian **te buscan a ti**
  (`../sistemas/01_FIRMA.md` §6) y no huyen tan pronto.

### 3.2 Cuándo se rinde o se desbanda

- **Unidad con moral 0** → huye (o se rinde si no tiene salida física: acorralada y sin aliados
  a 8 m).
- **Un tercio del bando roto** → pánico: la mitad huye, el resto se rinde (`00_REGLAS.md` §9).
- Ahí empiezan las **4 salidas** del prisionero (`../sistemas/02_PRISIONEROS.md`).

---

## 4. El capitán enemigo (unidad con nombre)

El capitán **no es una tropa con más vida**: decide distinto.

1. **Percibe el campo cada 2 s** (los demás, cada 0,5 s): piensa, no reacciona.
2. **Reagrupa una vez por batalla:** si la moral media de su bando cae por debajo de **40**,
   llama a sus hombres (radio 15 m, +15 de moral a los que lo oigan, solo una vez).
3. **Contextura:** mientras vive, su gente recupera **+1/s de moral extra** (sobre el +2/s de
   `01_CIFRAS.md` §5); su ruptura pesa **×2** en los suyos.
4. **Rendición con nombre:** un capitán se puede **voltear, rescatar o ejecutar** tras la
   batalla; su decisión de rendirse depende de su memoria de ti (banda y rencor).
5. **Vuelve:** el capitán que huye o se rinde no desaparece — regresa con su casa
   (`../contenido/01_ENEMIGOS.md` §3).

---

## 5. Cambiar de orden a media batalla

Cambiar de idea **cuesta**, para que la orden sea una decisión y no un botón de pánico:

| Cambio | Precio |
|---|---|
| Cualquier cambio de orden | **2 s de reagrupe**: la tropa se coloca sin atacar (media velocidad) |
| De **Cargar** a **Defender** | Además **−5 de moral** (frenar en seco); una vez por batalla el bando no lo nota |
| De **Defender** a **Cargar** | Sin coste de moral (animar es fácil); cuenta el reagrupe de 2 s |

- **No hay pausa total:** abrir la barra de órdenes baja el reloj al 25 % (`00_REGLAS.md` §3);
  confirmar da 1 s al 100 % para que la orden «cuaje».
- El **computo de quién acata** que muestra el HUD sale de aquí: una unidad con moral rota no
  reagrupa.

---

## 6. Reagrupar a los que huyeron

- Una unidad rota huye hasta salir del campo o hasta que **alguien con autoridad** (tú, un
  capitán aliado a 10 m) le da **una orden de Seguirme**: recupera 30 de moral y vuelve.
- **Una sola reagrupación** por unidad y batalla: el miedo no se cobra dos veces.
- Los que salen del campo cuentan como **bajas de campaña** aunque no mueran
  (`../sistemas/08_LUTO_Y_MORAL.md`).

---

## 7. Hacer la IA más lista sin volverla tramposa

Reglas duras (no se negocian, son las que hacen justa la pelea):

1. **La IA ve lo que un hombre vería:** no lee a través de la cobertura, la niebla ni la
   visibilidad del terreno (`02_TERRENO.md` §6).
2. **No conoce tu orden antes de que la ejerzas:** reacciona a lo que **pasa** (avance, huida),
   no al botón.
3. **Mismo RNG, mismas reglas:** la IA no tiene tiradas ocultas; usa el RNG de la partida
   (determinismo).
4. **No hay ventaja por bando:** tus tropas y las suyas usan la misma cadencia (0,5 s), el mismo
   freno y la misma moral.
5. **Se mejora añadiendo decisiones, no números:** más reglas de comportamiento (cubrir, flanquear,
   reagrupar), nunca vida o daño extra escondidos.

---

## 8. Determinismo y pruebas sin navegador

- La IA vivirá en el **motor puro** `js/systems/campo.js` (y `js/systems/ia.js` si crece; por construir): sin DOM,
  sin `fetch`, sin reloj; `dt` y RNG **inyectados** (reglas 2 y 11 de `../../AGENTS.md`).
- **Determinismo:** misma semilla + mismas decisiones = **la misma batalla**, golpe a golpe.
- **Tests (por escribir)** (`tests/campo.test.js`, mínimo 3 casos):
  - normal: dos bandos iguales, con la misma semilla, empatan igual dos veces.
  - borde: una unidad sola contra diez **huye** o **se rinde**, nunca «onewipea».
  - error: una orden imposible (reagrupar dos veces) se ignora sin romper el estado.
- Prueba de **no trampa**: una unidad sin línea de visión **no** dispara aunque el objetivo esté
  a alcance de arco en línea recta estadística.

---

## 9. Cifras que fija este documento

| Cifra | Valor |
|---|---|
| Cadencia de decisión (tropa) | **0,5 s** |
| Cadencia de decisión (capitán) | **2 s** |
| Objetivo | enemigo más cercano a alcance; a igualdad, el de menos vida |
| Seguirme | radio de formación 6 m · no persigue a más de 12 m |
| Defender | radio de posición 4 m · +20 % defensa · no persigue |
| Reagrupe por cambio de orden | **2 s** sin atacar (media velocidad) |
| Volver de Cargar a Defender | **−5 de moral** (una vez por batalla sin coste) |
| Reagrupación de una unidad rota | **1** por unidad y batalla · +30 de moral |
| Reagrupar | tú o un capitán a **10 m** |
| Reagrupar el enemigo (capitán) | moral media < **40** · +15 en 15 m · 1 vez |
| Contextura del capitán | recuperación +1/s extra · ruptura ×2 |
| Rendición individual | acorralada, sin aliados a 8 m |

---

## 10. Qué entra en la demo (Fase 1) — y qué sigue

> **Hasta aquí la demo.** Las **3 órdenes** (Cargar / Seguirme / Defender), la IA propia a 0,5 s,
> la huida, la rendición y la reagrupación por construir en los **3 campos** con **4+ capitanes**
> con memoria (`../produccion/00_ALCANCE.md` §2.5). Igual que el juego completo en reglas; solo
> cambia la **cantidad** de unidades (5-6, y 8 en el cierre).

> **Y sigue el juego completo.** Los **10+ por bando**, los **rasgos de familia** completos
> (§3.1) y los capitanes de todas las casas se añaden **con esta misma IA y estas mismas
> decisiones**. Crecer = más filas en `../contenido/01_ENEMIGOS.md`, no una IA nueva.

---

## 11. Fuera de este documento

- Las 5 fases y el reloj → `00_REGLAS.md`
- Vida, daño, moral y ritmo → `01_CIFRAS.md`
- Cobertura, freno y detección → `02_TERRENO.md`
- Cómo se ve, se avisa y se toca → `04_PRESENTACION.md`
- Familias enemigas y rasgos → `../contenido/01_ENEMIGOS.md`
- Capitanes que vuelven → `../contenido/02_CAPITANES_Y_NEMESIS.md`
- Prisioneros y las 4 salidas → `../sistemas/02_PRISIONEROS.md`
