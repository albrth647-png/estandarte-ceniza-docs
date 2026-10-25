# 11 · Playtest y beta — probar con gente de verdad

**Estado:** ✅ **aprobado por el dueño (2026-10-01, ronda 4-A). Documento final.**

> **Nada se publica sin jugar delante de alguien que no es el autor.** Aquí está cómo se prueba
> con gente: con quién, qué guion sigue, qué se mide, con qué acuerdo y **qué hay que ver para
> decir «sale»**. **Cifras de este documento son propuesta de diseño** (cambiables →
> `../DECISIONES.md`).

---

## 1. Los tres puntos de prueba

| Punto | Cuándo | Con quién | Qué busca |
|---|---|---|---|
| **Alpha** | al cerrar cada hito de `01_FASES.md` | el autor + 1 persona de confianza | ¿se rompe algo? |
| **Beta** | antes de publicar la demo | **5 jugadores** | ¿se entiende sin explicación? |
| **Verificación final** | tras arreglar la beta | los mismos 5 (o 3 de ellos) | ¿se cumplen los criterios de salida? |

- **No hay telemetría** (`09_PRIVACIDAD_Y_DATOS.md`): todo lo que se mide se **observa y se anota
  a mano**. El juego no recoge datos de uso, ni en beta.

---

## 2. Con quién (beta)

- **5 jugadores** que **no** hayan visto el juego ni el repositorio.
- Personas que jueguen con **dedos en móvil** (el juego es táctil, `../interfaz/00_CONTROLES.md`).
- **0 exigencia de experiencia previa** en el género: si solo lo entienden los tácticos, el
  onboarding ha fallado (`../interfaz/10_TUTORIAL_Y_FIRST_RUN.md`).

---

## 3. El acuerdo (una página)

Antes de jugar, cada jugador lee y acepta un acuerdo de **una sola página**:

1. **No comparte** capturas, vídeo ni el enlace hasta la fecha de salida.
2. **Dice la verdad** delante («no lo entiendo» es el mejor regalo del test).
3. **Sus notas son anónimas** en el registro de bugs.
4. **No paga nada** y no recibe nada a cambio (ni código ni dinero).

- Es un acuerdo **entre particulares**; no sustituye nada legal de tienda (que hoy no hay,
  `05_MERCADO_Y_LANZAMIENTO.md`).

---

## 4. Guion de la sesión (60 minutos)

| Min | Qué pasa | Quién habla |
|---|---|---|
| 0-5 | El jugador abre y crea partida **sin ayuda** | nadie; se observa |
| 5-30 | Juega libre: primer sitio, primer encargo, primera batalla | nadie; se anota dónde se atasca |
| 30-45 | Se le piden **3 tareas concretas** (§5) | el guion las pide, no se enseña el camino |
| 45-55 | **5 preguntas fijas** (§6), en ese orden | habla el jugador |
| 55-60 | Cierre: «¿algo más?» y despedida | ambos |

- **Ni una sola pista durante la sesión.** Si el jugador se atasca más de 5 minutos en un punto,
  se anota como fallo de diseño y **se le saca del paso** para continuar (no se enseña).
- Se juega en **su dispositivo** siempre que se pueda; si no, en el del autor con su tamaño de UI.

---

## 5. Las 3 tareas concretas

1. **Consigue y cobra un encargo** del tablón (crear, leer, completar, cobrar).
2. **Gana una batalla** usando al menos una orden a la tropa (`../batalla/03_IA_Y_ORDENES.md`).
3. **Guarda, sale y vuelve a cargar** la partida (comprueba slots y migración).

- Cada tarea se marca **hecha sin ayuda / hecha tras pista / no hecha**. El resultado es el dato,
  no la opinión.

---

## 6. Las 5 preguntas fijas (escala 1-5 + comentario)

1. ¿La primera media hora te **enganchó** o te **costó arrancar**?
2. ¿Entendiste **los tres botones** sin que te los explicaran?
3. ¿Qué momento te **costó más**? (punto exacto, si lo recuerda)
4. ¿Notaste que el mundo **recuerda** lo que hiciste?
5. ¿Lo seguirías jugando mañana? **¿Pagarías 19 USDT por ello?** (`05_MERCADO_Y_LANZAMIENTO.md`)

- **Nunca se pregunta «¿te gustó?»**: gustó no arregla nada; las 5 anteriores sí.

---

## 7. Registro y criterios de salida («sale» solo si…)

| Criterio | Umbral |
|---|---|
| Tareas **sin ayuda** | **3 / 3** en al menos **4 de 5** jugadores |
| Bugs **ALTA** abiertos | **0** (`../BUGS.md`) |
| Errores de consola en la sesión | **0** |
| Pregunta 1 (enganche) | media **≥ 3,5 / 5** |
| Pregunta 5 (pagaría) | media **≥ 3 / 5** |
| `npm run qa` | **verde** el día del cierre |

- **Si algo falla:** bug en `../BUGS.md` con su formato (ID, pasos, severidad) → se arregla →
  **beta de verificación** con los mismos criterios. No se publica «con fallos conocidos».
- **Las notas crudas se archivan** como apéndice fechado de este documento (tabla de sesiones).

---

## 8. Datos, tipos y validación

- **Sin JSON y sin telemetría:** el feedback vive en el registro fechado de este documento y los
  bugs, en `../BUGS.md` (formato duro de `../../AGENTS.md`).
- **No se toca el guardado:** la beta juega con el `SaveState` normal (el formato de guardado
  vigente en esa versión); así se prueba de verdad la migración (`02_GUARDADO_Y_DATOS.md`).
- **Los hallazgos que cambian diseño** se anotan en `../DECISIONES.md` con su fecha; los que no,
  solo son bugs.

---

## 9. Cifras que fija este documento

| Cifra | Valor |
|---|---|
| Puntos de prueba | **3** (alpha · beta · verificación) |
| Jugadores en beta | **5** |
| Duración de la sesión | **60 min** |
| Tareas concretas | **3** |
| Preguntas fijas | **5** (escala 1-5) |
| Tolerancia a errores de consola | **0** |
| Bugs ALTA abiertos para salir | **0** |
| Acuerdo | **1 página**, anónimo, sin pago |

---

## 10. Qué entra en la demo (Fase 1) — y qué sigue

> **Hasta aquí la demo.** Beta completa de **5 jugadores** con su guion de 60 minutos y sus
> criterios de salida, **antes** de publicar la demo del Acto I.

> **Y sigue el juego completo.** Cada entrega mayor de las Fases 2-5 repite **al menos una ronda
> de verificación** con el mismo guion y **los mismos umbrales**: crece el juego, no baja la barra.

---

## 11. Fuera de este documento

- Qué significa «terminado» (QA técnico) → `04_QA.md`
- Qué se publica y a qué precio → `05_MERCADO_Y_LANZAMIENTO.md`
- Errores y su ciclo → `../BUGS.md`
- Hitos en los que se prueba → `01_FASES.md`
- Privacidad (sin telemetría) → `09_PRIVACIDAD_Y_DATOS.md`
- Avisos de contenido que el jugador verá → `../interfaz/11_AVISOS_DE_CONTENIDO.md`
