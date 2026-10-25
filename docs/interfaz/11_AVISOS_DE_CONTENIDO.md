# 11 · Avisos de contenido y fotosensibilidad — avisar sin estropear

**Estado:** ✅ **aprobado por el dueño (2026-10-01, ronda 4-A). Documento final.**

> El juego es **16+** (`../produccion/06_LEGAL_Y_AUTORIA.md` §4) y su tono es **sobrio, sin gore**
> (`../arte/04_EFECTOS_Y_PARTICULAS.md` §1). Este documento cierra dos cosas: **qué se avisa antes
> de jugar** (contenido sensible y opciones de confort) y **cómo se cumple el techo fotosensible**
> que ya fija `04_ACCESIBILIDAD.md` (parpadeo ≤ 3 Hz). **Cifras de este documento son propuesta de
> diseño** (cambiables → `../DECISIONES.md`).

---

## 1. Dónde se avisa (y dónde nunca)

| Aviso | Dónde vive | Cuándo se ve |
|---|---|---|
| **Ficha de contenido** | pantalla de **Crear partida** (debajo de las opciones, en una línea) | antes de la **primera** partida |
| **Recordatorio** | Opciones → «Avisos de contenido» (consultable siempre) | cuando el jugador quiera |
| **Aviso puntual de escena** | aviso de sistema de 3 s (`07_AVISOS_Y_RUMORES.md`) | **antes** de una escena de golpe, nunca durante |

- **Nunca** se avisa *durante* una batalla o un diálogo (rompería el tono y taparía la acción,
  `02_HUD.md` §1).
- **Nada de popup con «OK»**: la ficha de Crear partida es **texto de una línea**; el detalle está
  en Opciones (`01_PANTALLAS.md` §4).
- **Aviso = información, no testimonio:** no asusta ni sermonea; dice lo que hay.

---

## 2. La ficha de contenido (texto fijo, 4 líneas)

Se muestra **una sola vez**, en Crear partida, en una línea de resumen con las 4 etiquetas de §2.
El texto completo vive en Opciones. Contenido (propuesta, ES/EN, claves `txt_aviso_*`):

| # | Etiqueta (1 línea) | Cubre |
|---|---|---|
| 1 | **Violencia medieval sin gore** — espadas, sangre sobria, sin desmembramientos | combate (`../arte/04_EFECTOS_Y_PARTICULAS.md`) |
| 2 | **Muerte de personajes y animales**; tema del luto | `../sistemas/08_LUTO_Y_MORAL.md`, `../contenido/08_ANIMALES_Y_CRIATURAS.md` |
| 3 | **Temas adultos**: condena falsa, deudas heredables, ejecuciones, traición | `../historia/00_PREMISA.md` |
| 4 | **Opciones de confort**: texto grande, daltonismo, sacudidas y parpadeo reducibles | `04_ACCESIBILIDAD.md` |

- **4 líneas, 4 etiquetas.** No se lista cada escena; se lista cada **tipo**.
- Si el contenido de una fase futura añade un tipo nuevo, **se añade una etiqueta** (el molde no
  cambia).

---

## 3. El techo fotosensible (cómo se cumple)

`04_ACCESIBILIDAD.md` §3 fija **parpadeo ≤ 3 Hz**; aquí está la **comprobación**:

| Regla | Cómo se cumple | Dónde se mira |
|---|---|---|
| Ningún elemento **nuevo** parpadea a > 3 Hz | todo destello (crítico, aviso, marca) usa el mismo temporizador de la escena | `arte/04_EFECTOS_Y_PARTICULAS.md` |
| **Modo «Poco destello»** en Opciones: sustituye destellos por **cambio de brillo suave** | 1 interruptor, efecto inmediato | `04_ACCESIBILIDAD.md` §3 |
| **Sacudida de pantalla: 0 al máximo** (8 niveles) está previsto | el nivel 0 es el por defecto en la ficha de contenido | `04_ACCESIBILIDAD.md` §3 |
| Transiciones entre pantallas **sin fundido blanco** | solo fundido a negro corto (≤ 0,3 s) | `08_TRANSICIONES_Y_CARGAS.md` |
| **Verificación manual** antes de cada entrega | guion de 5 comprobaciones (§5) | `../produccion/04_QA.md` |

- **No hay estroboscopia intencional en ningún sitio del diseño**: si aparece un efecto nuevo que
  la pida, **se rechaza en diseño**, no en revisión.

---

## 4. Qué NO es esto

- **No es control parental ni bloqueo por edad:** la edad 16+ es una **ficha de tienda/página**
  (`../produccion/06_LEGAL_Y_AUTORIA.md` §4); el juego no pregunta ni verifica.
- **No es un filtro de violencia:** no se apaga la sangre ni se cambia el tono; solo se **avisa** y
  se ofrecen las opciones de confort que están previstos.
- **No sustituye al tono:** el diseño sobrio (sin gore) es el de `../arte/00_ESTILO.md` y
  `../arte/04_EFECTOS_Y_PARTICULAS.md`; el aviso lo recuerda, no lo crea.

---

## 5. Guion de verificación (antes de cada entrega)

5 comprobaciones manuales, en este orden (caben en los 10 minutos de `../produccion/04_QA.md` §4):

1. **Crear partida** muestra la línea de aviso **solo la primera vez**.
2. Opciones → **Avisos de contenido** abre las 4 líneas completas (ES y EN).
3. **Poco destello** activo: una batalla completa con críticos **sin destellos rápidos**.
4. **Sacudida 0**: una batalla completa sin movimiento de cámara.
5. **Parpadeo:** ningún aviso, marca ni HUD parpadea visiblemente (> 3 Hz) durante 2 minutos de
   juego variado.

- Si una falla → bug en `../BUGS.md` con su severidad (**fotosensible = ALTA**: tapa jugar a
  parte del público).

---

## 6. Datos, tipos y validación

- **Datos:** **sin JSON nuevo.** Las 4 etiquetas son claves `txt_aviso_contenido_1..4` con
  paridad ES/EN (regla 10); la opción es un ajuste de Opciones como los están previstostes.
- **Persistencia:** «ya vi la ficha» va en `SaveState` (bandera aditiva,
  `../produccion/02_GUARDADO_Y_DATOS.md`); una partida vieja sin la bandera **la ve una vez** y no
  se pierde nada.
- **Sistema puro:** no hace falta: es texto y una bandera. Si se quisiera un aviso por escena
  (§1), sería `js/systems/avisos.js` están previstoste por diseño, con sus tests.
- **Tests (por escribir):** `tests/i18n.test.js` (las 4 claves en ambos idiomas) + `tests/save.test.js` (la
  bandera aditiva no rompe partidas existentes).

---

## 7. Cifras que fija este documento

| Cifra | Valor |
|---|---|
| Etiquetas de contenido | **4** |
| Ficha visible | **1** vez (primera Crear partida) |
| Avisos de escena | ≤ **3 s**, solo **antes** (canal de `07`) |
| Parpadeo máximo | **3 Hz** (techo de `04`) |
| Sacudida por defecto | **0** (niveles 0-8 existentes) |
| Fundido entre pantallas | negro, **≤ 0,3 s** |
| Comprobaciones previas a entrega | **5** |
| JSON nuevo | **0** |

---

## 8. Qué entra en la demo (Fase 1) — y qué sigue

> **Hasta aquí la demo.** La ficha de 4 etiquetas en Crear partida, su texto en Opciones, la
> bandera de «ya vista», el modo «Poco destello» de `04_ACCESIBILIDAD.md` y las 5 comprobaciones
> del guion §5 en cada entrega.

> **Y sigue el juego completo.** Si un acto nuevo añade un **tipo** de contenido sensible, se
> añade **una etiqueta** (§2) y se actualiza la ficha; los techos de parpadeo, sacudida y tono
> **no se tocan**. Crecer = una línea más de texto, no un sistema nuevo.

---

## 9. Fuera de este documento

- Accesibilidad completa (texto, daltonismo, subtítulos) → `04_ACCESIBILIDAD.md`
- Avisos y rumores en juego → `07_AVISOS_Y_RUMORES.md`
- Tono de los textos → `03_I18N_Y_TONO.md`
- Sangre y efectos (el diseño sobrio) → `../arte/04_EFECTOS_Y_PARTICULAS.md`
- Edad y ficha legal → `../produccion/06_LEGAL_Y_AUTORIA.md` §4
- QA (dónde entran las 5 comprobaciones) → `../produccion/04_QA.md` §4
- Primer arranque → `10_TUTORIAL_Y_FIRST_RUN.md`
