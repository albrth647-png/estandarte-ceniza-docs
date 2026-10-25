# Visión del juego completo — de la demo (Acto I) al horizonte de campaña

> **Qué es este documento.** La teoría de longevidad del juego completo. La demo del Acto I
> («La Ceniza», en diseño, `produccion/00_ALCANCE.md`) será una **vista previa**: un trozo
> jugable del sistema. Aquí se cuenta de qué **lecciones del prototipo anterior** parte el
> diseño y qué tipos de mecánicas podrían seguir, sin cerrar todavía ninguna cifra.
>
> **Documento autónomo:** no depende de ni enlaza a otros textos del proyecto (usa sus nombres en
> `código` como referencia, no como enlace).
>
> **Estado:** 🟡 **Idea, no diseño**. Nada de esto está implementado ni decidido. Aquí **no hay
> cifras cerradas**: cuántos capitanes, cuántas entradas de diario, cuántas horas de campaña,
> multiplicadores o plazos son **preguntas** (§9), no decisiones. Las cifras concretas salen de
> su documento de diseño cuando el dueño las apruebe, en el orden de siempre (datos → código →
> tests → documentación).

---

## 1. De dónde partimos: las lecciones del prototipo anterior

> **Nota (2026-10-01, aclarada 2026-10-25):** la tabla de abajo describe el **primer juego**
> («Estandarte de Ceniza»), cuyo código **ya no existe** y no se conserva en este repo. Se
> conserva **solo como memoria de lo que ya se probó**; no es diseño del juego nuevo. El diseño
> vivo está en `VALCORIA_DEUDA_DE_SANGRE.md` y en `docs/`.

Esto **no es propuesta**, es lo que el prototipo anterior (Acto I) ya tenía o tenía diseñado:

| Pieza | Estado |
|---|---|
| **Historia:** Acto I completo, 7 escenas (caída de Valcoria → Puerto Ceniza → Granero → Torre → Umbria → cierre) | Hecho |
| **Mapa global:** 22 plazas (17 + 5 mazmorras), 8 interactivas en la demo, reloj de campaña (**1 día = 30 s**) | Hecho |
| **Batalla:** motor propio intacto (movimiento, mitigación, moral, Ola de choque), HUD con 4 órdenes + 4 habilidades + estandarte + pausa, despliegue por datos + 2 formaciones | Hecho |
| **Resultado de batalla:** bajas permanentes, **veteranos** (nombre + rasgo), prisioneros, botín, honor, XP de escuadrón y de personaje | Hecho |
| **Culdán:** el enemigo derrotado reaparece a los 3 días con +1 nivel (tope 15); si cae el héroe, despierta en plaza aliada | Hecho |
| **Guardado:** versionado (v2) con slots, export/import y migración compatible | Hecho |
| **Contenido:** 9 unidades, 20 misiones, 19 ítems + 9 artefactos, 8 mercancías, 3 facciones activas (de 8 reinos) | Diseñado |
| **Histórico (primer juego):** cámara, rondas de enemigos, raza neutral, IA de héroes, habilidades de escuadrón, mazmorras | ⬜ **No aplican** al juego nuevo |

**La clave:** el juego completo no repite estas piezas tal cual — el **mapa por casillas** y la
**batalla 2D** quedaron fuera con el cambio de género — pero **hereda sus lecciones**: los
escuadrones (como concepto, ahora en un campo de batalla en 1.ª persona), los veteranos, la
idea del culdán (hoy generalizada en los **capitanes con memoria**), el honor, la economía y la
campaña por días. Todo lo que sigue son **familias de mecánicas** que encajan con el juego nuevo.

---

## 2. Evidencia — por qué unos juegos duran meses o años

### 2.1 Seis familias de juegos longevos

| Familia | Ejemplos | Qué lo sostiene |
|---|---|---|
| **MMO** | World of Warcraft, Final Fantasy XIV, Elder Scrolls Online | Curva vertical lenta + **endgames apilados** (mazmorras, raids, PvP, reputaciones, profesiones) + temporadas que reabren el ciclo. |
| **Sandbox medieval** | Mount & Blade Warband / Bannerlord, Kenshi, Battle Brothers, Starsector | Metas autoimpuestas y un **mundo vivo que avanza sin ti**; no hay final, hay horizontes. |
| **Grand strategy** | Crusader Kings 3, Total War | El tiempo **es** el contenido: siglos de sucesiones, muertes, guerras. Perder también genera historia. |
| **Emergente** | Dwarf Fortress, RimWorld | Sistemas que se combinan entre sí → historias irrepetibles que nadie escribió a mano. |
| **Idle offline** | Melvor Idle, Tideward, NGU Idle | Progresión por **timestamp**: al reabrir, el juego simula lo que pasó mientras no estabas. |
| **Ascensión / NG+** | Elden Ring, Diablo, Path of Exile, prestige de los idle | Reinicio **voluntario** que se conserva como desbloqueo permanente y dificultad nueva. |

### 2.2 Datos concretos (externos, no de este proyecto)

- **WoW (vanilla):** ~**400 horas** para llevar un personaje de nivel 1 a 60. El endgame no nació
  porque hubiera demasiado contenido, sino porque —palabras de uno de sus diseñadores, Andy
  Gavin— *«no hay forma de crear contenido al ritmo al que los jugadores lo consumen»*.
- **Consecuencia de esa cita:** cuando no puedes producir más rápido, diseñas **contenido más
  lento de consumir**: lockouts semanales, reputaciones de larga duración, escalones de equipo.
  Es lo contrario de lo que queremos: aquí el límite lo debe poner tu tiempo de juego, no un muro
  de espera real.
- **Offline real (Melvor / Tideward):** la simulación se cierra con un **cap de 24 horas a tasa
  completa**. El tope existe por **retención diaria** y **coste de simulación**; la resolución es
  matemática y barata (**O(acciones)**, cientos de ms).
- **Contraste de ritmo:** en un sandbox como Mount & Blade no importa "terminarlo"; el jugador se
  pone sus propias metas y el mundo le pone las sorpresas.

### 2.3 La lección común

Ninguno de estos juegos dura porque tenga un final lejano, sino porque **no tiene final**: tiene
horizontes que se van retirando.

---

## 3. Teoría destilada

### 3.1 Las 3 formas de endgame

1. **Fijo.** Un contenido final lineal: sirve una vez y se agota.
2. **Escalado / endless.** Los mismos contenidos con números más grandes. Es **un truco**: sube
   la cifra, pero el jugador no cambia *cómo* juega.
3. **Ascensión / prestige.** Reinicio voluntario con desbloqueo permanente: el único que añade
   **una decisión nueva** al final de cada ciclo.

**Regla:** el escalado puede existir, pero **nunca como única capa**.

### 3.2 Las 3 curvas de poder

| Curva | Qué es | Problema / virtud |
|---|---|---|
| **Poder del enemigo** | El rival se vuelve más fuerte. | Si es lo único, la partida es una cuesta arriba. |
| **Poder escalado** | El jugador sube números (ataque, PV). | Cómodo al principio; **aburre al final** porque no cambia el juego. |
| **Mejoras duras** | Desbloqueos que **cambian cómo juegas**, limitados y combinables como un *deck*. | El motor de longevidad real. |

**Objetivo:** que el poder a largo plazo venga de **mejoras duras** (artefactos únicos, rasgos,
doctrinas, afijos), con los números como acompañamiento.

### 3.3 Los 7 motores destilados

1. **No hay final, hay horizontes.** Cada meta resuelta destapa la siguiente.
2. **Agentes con memoria.** Modelo de referencia: el *Nemesis System* (Shadow of Mordor / War):
   capitanes con nombre, rango, rencor y rasgos que recuerdan al jugador y vuelven. **Está
   patentado**: hay que diseñar una versión **propia**, no copiarlo.
3. **Mejoras duras > números.** Ver §3.2.
4. **Reloj propio.** Lo que pasa mientras no juegas es **contenido gratis**.
5. **Capas apiladas.** Mantener 2–3 objetivos activos de distinta escala (misión → región →
   campaña).
6. **Repetición con variación.** Semillas + afijos convierten pocos escenarios en contenido
   casi infinito.
7. **Crónica / legado.** Un registro del paso del jugador por el mundo: convierte números en
   recuerdos.

### 3.4 Los 3 de mejor relación impacto/esfuerzo

1. **Agentes con memoria + diario** (dos capas puras, aditivas al guardado).
2. **Bloques de campaña que rotan** (reutilizan el reloj).
3. **Repetición escalada con variación** (reutiliza las mazmorras ya diseñadas).

---

## 4. Principios de adaptación a Valcoria

Todo lo que se añada tiene que respetar la naturaleza del proyecto:

- **100 % offline y estático.** No hay servidor: lo que "rota" se deriva **del propio guardado**.
- **Nada de esperas reales.** Prohibido el "vuelve en 24 h". El gating debe ser **en días de
  juego acelerables jugando**.
- **Determinismo.** Misma partida = mismo mundo (sin azar fuera de la simulación).
- **Guardado aditivo y versionado.** Nunca romper un guardado existente.
- **Nada de `localStorage` sin capar.** Todo lo que crezca (diario, agentes) va **acotado**.
- **El reloj entra inyectado.** Las capas puras reciben el tiempo; nunca lo consultan solas.
- **Paridad de textos ES/EN** desde el primer commit.
- **Motor de batalla estable.** El motor se diseña una vez: lo nuevo entra por datos,
  despliegues o capas puras por encima, sin tocar el motor.

---

## 5. Familias de mecánicas candidatas (concepto, sin cifras)

Ninguna está decidida. Cada una dice **de qué pieza de la demo sería continuación**.

| Familia | Idea | Continúa de... |
|---|---|---|
| **Agentes enemigos con memoria** | Oficiales enemigos con nombre propio y recuerdo de lo que les hiciste; si escapan vuelven peores. | El **culdán** (reaparición) y los **veteranos** (nombre + rasgo), en espejo. |
| **Diario autoescrito** | Un registro que pone texto a lo que la partida ya calcula (batallas, bajas, veteranos, plazas). | El **resultado de batalla** y el **mapa**. |
| **Bloques de campaña que rotan** | Cada cierto tiempo de juego, un puñado de objetivos y modificadores; al cerrar, **se conserva todo**. | El **reloj de campaña** y las **misiones** ya diseñadas. |
| **Repetición escalada** | Los escenarios de mazmorra repetibles con **afijos** (niebla, hambruna, asedio) y recompensa creciente. | Las **mazmorras** y sus batallas de dificultad ya diseñadas. |
| **Encargos en el tiempo** | Mandas a un compañero/veterano a un encargo; se resuelve **en días de juego**. | El **roster de compañeros** y el reloj. |
| **Ciudad productiva** | Los edificios producen **mientras no juegas**, con tope al reabrir. | La **ciudad**, los **edificios** y los **impuestos** ya diseñados. |
| **Legado / nuevo ciclo** | Al tope de nivel, reinicio voluntario que **conserva** artefactos y personajes. | El **tope de nivel** y el **equipo/artefactos**. |
| **Reputación y mundo vivo** | Las facciones cambian de actitud según pasan los días; el honor abre aliados y equipo. | El **honor**, los **8 reinos** y la IA de héroes prevista. |
| **Hazañas y bestiario** | Contadores con texto de completado. | El contenido **ya listado** (unidades, artefactos, plazas). |

**Nota de honestidad:** en el chat anterior yo propuse cifras concretas para varias de estas
(cuántos agentes, cuántos registros de diario, multiplicadores, horas de campaña, plazos). **No
tenían base en los documentos del proyecto y quedan retiradas**: van en §9 como preguntas.

---

## 6. Lo que NO hay que copiar

1. **Endgame solo escalado** (Diablo III, Destiny, The Division): "los mismos números más altos"
   aburre en semanas.
2. **Time-gating real** (lockouts, "vuelve en 24 h"): choca con la promesa offline.
3. **El *treadmill* que borra progreso**: en un single-player estático sienta fatal; la
   traducción correcta es **"conservar todo + dificultad opcional"**.
4. **Copiar el Némesis al detalle**: está patentado; el diseño es propio.

---

## 7. Cómo encaja cada familia en la arquitectura (sin nombres de ficheros decididos)

La regla del proyecto es clara y aplica a todo lo de §5:

- **Datos primero:** cualquier pool (agentes, tipos de registro, afijos) entra con su validador.
- **Capa pura:** la lógica vive en módulos de simulación sin DOM, sin `fetch` y sin reloj; el día
  entra por parámetro (los nombres exactos se deciden al implementar).
- **Escenas:** el mapa y el resultado dibujan y llaman a esas capas; no simulan.
- **Guardado:** lo nuevo es **aditivo** (migración compatible) y **acotado**.
- **Motor:** el motor de campo y el pathfinding (por construir) se diseñan estables; lo nuevo
  los llama, no los toca.

**Orden propuesto (sujeto a tu decisión):** primero las dos piezas más baratas y que más
reutilizan lo ya hecho (**agentes con memoria** + **diario**), luego el reloj de campaña y los
bloques que rotan, después la repetición escalada, y al final lo que toca economía/legado.

---

## 8. Riesgos técnicos (todos reales, ninguno inventado)

| Riesgo | Mitigación |
|---|---|
| **`localStorage` pequeño (≈ 5 MB).** Un diario o una lista de agentes podrían crecer sin control. | **Capar** cada estructura (tope explícito) y validarlo. |
| **Dependencia del reloj del sistema.** Una capa pura que lea el reloj deja de ser testeable y rompe el determinismo. | El tiempo **siempre** entra inyectado. |
| **Textos incompletos en un idioma.** | Toda `txt_*` nueva nace en ES **y** EN. |
| **Datos sin validar.** | Validador en el esquema + cruce de datos antes de usarlos. |
| **Guardados antiguos rotos.** | Migración aditiva y versionada; corrupto → copia de seguridad. |
| **Tocar el motor de batalla.** | Todo entra por datos, despliegues o capas puras. |

---

## 9. Preguntas abiertas (decisiones del dueño — NO rellenar inventando)

- **Alcance:** ¿qué familias de §5 entran en el **juego completo** y cuáles (si alguna) en la
  demo?
- **Agentes con memoria:** ¿cuántos? ¿cuántos rangos? ¿qué es el rencor y qué lo cambia? ¿se
  puede reclutar al enemigo vencido?
- **Diario:** ¿cuántos registros se conservan? ¿qué tipos? ¿panel en el mapa o pantalla propia?
- **Bloques que rotan:** ¿qué duración en días de juego? ¿qué conservan?
- **Reloj de campaña:** el prototipo anterior usó **1 día = 30 s**. ¿Se mantiene o se recalibra
  para el juego completo?
- **Repetición escalada:** ¿qué afijos? ¿con o sin tope de recompensa?
- **Duración objetivo** de la campaña completa (**a decidir**; yo propuse cifras en el chat sin
  base, retiradas).
- **Persistencia:** ¿todo lo nuevo entra en la misma fase de guardado (aditivo)?

---

## 10. Fuentes consultadas

- Andy Gavin — «WOW Endgames – Vanilla» (blog del desarrollador):
  <https://all-things-andy-gavin.com/2012/10/29/wow-endgames-vanilla/>
- Gamedeveloper.com — «Ending on a High Note — The 3 Forms of Endgame Design» (Josh Bycer):
  <https://www.gamedeveloper.com/design/ending-on-a-high-note-the-3-forms-of-endgame-design>
- Game-Wisdom — «The 3 Forms of Power Curves in Game Design» (Josh Bycer):
  <https://game-wisdom.com/critical/3-forms-power-curves-game-design>
- Tideward — comparativa de progresión offline:
  <https://tideward.app/offline-progression/>

Además, observación directa de World of Warcraft, Final Fantasy XIV, Elder Scrolls Online,
Mount & Blade Warband/Bannerlord, Kenshi, Battle Brothers, Starsector, Crusader Kings 3,
Total War, Dwarf Fortress, RimWorld, Melvor Idle, NGU Idle, Elden Ring, Diablo, Path of Exile y
del *Nemesis System* de Shadow of Mordor/War.
