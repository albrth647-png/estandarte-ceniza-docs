# 10 · Voces y gritos — lo que se oye en el campo

**Estado:** ✅ **aprobado por el dueño (aprobación en bloque, 2026-09-30). Documento final.**

> Valcoria **habla poco y golpea mucho**: las órdenes suenan **cortas** y **lo que importa se
> habla** con voz pre-generada (opción 1-C, `../arte/02_AUDIO.md` §2), mientras el mundo
> generativo lanza **frases sueltas** por bocadillo **en texto**. Aquí están **qué
> se dice, cómo se escribe y cuándo se calla**. El tono general, en `../interfaz/03_I18N_Y_TONO.md`;
> los avisos, en `../interfaz/07_AVISOS_Y_RUMORES.md`.
>
> **Frases y ids son propuesta de diseño** (cambiables → `../DECISIONES.md`).

---

## 1. Las familias de frases

| Familia | Prefijo | Cuándo | Quién |
|---|---|---|---|
| **Grito de orden** | `txt_grito_orden_*` | Al recibir Cargar / Seguirme / Defender | Tu tropa, tu capitán |
| **Grito de choque** | `txt_grito_choque_*` | Primer contacto de la batalla | Ambos bandos |
| **Grito de miedo** | `txt_grito_miedo_*` | Moral quebrándose o unidad rota | El que huye |
| **Rendición** | `txt_grito_rinde_*` | Unidad acorralada sin aliados a 8 m | El rendido |
| **Victoria** | `txt_grito_victoria_*` | Moral enemiga rota | Tu bando |
| **Saludo** | `txt_npc_saludo_*` | Al enfocar a un PNJ y hablar | PNJ del mundo |
| **Amenaza / precio** | `txt_npc_precio_*` | Trato hostil, peaje, deuda | Mercader, patrulla |
| **Lamento** | `txt_npc_lamento_*` | Tras una baja o un funeral | Aldeanos, deudos |
| **Habladuría** | `txt_rumor_*` | Posada, tablón | Posadero, portavoz |

- Una familia es **un conjunto pequeño** de variantes (3-5), para no repetir la misma frase.
- **`txt_rumor_*` ya vive** en `../misiones/03_CADENAS_Y_RUMORES.md`: no se duplica aquí.

---

## 2. Reglas de escritura (duras)

1. **Corto:** ≤ 2 líneas y **≤ 90 caracteres** como todo bocadillo (`../interfaz/03_I18N_Y_TONO.md` §4).
2. **Sin acentos raros ni comillas tipográficas:** se escribe lo que se puede pintar en la fuente
   del juego (nada de comillas «angulares» fuera de este documento de diseño).
3. **Clave `txt_*` con paridad ES/EN obligatoria** (regla 10 de `../../AGENTS.md`): una frase nace
   en los dos idiomas a la vez.
4. **La ley está en la boca de todos:** se habla de **deudas, cuentas y marcos**, no de épica
   (`../interfaz/03_I18N_Y_TONO.md` §1).
5. **Sin nombres traducidos:** Valcoria, Altamir, Doña Sira no se traducen; los títulos sí.

---

## 3. Cómo suenan (100 % offline)

- **Gritos de orden / choque:** **voz hablada pre-generada** (Kokoro, fuera de la ejecución) para
  las órdenes y los gritos fijos de campo; las variantes raras, síntesis corta. Nunca doblaje de
  estudio, que multiplicaría el trabajo (`../arte/02_AUDIO.md` §1-§2).
- **Bocadillos de PNJ (1-C):** **los del elenco relevante sí se hablan** (PNJ con memoria
  completa, escenas fijas); **lo generativo no** — encargos, rumores y frases con huecos se leen
  con sonido de mundo.
- **Idioma:** la voz existe **en ES y EN** con la misma clave que el texto
  (`../interfaz/03_I18N_Y_TONO.md` §3).
- **Volumen:** bus **efectos**; la voz de orden hace **ducking −6 dB** a la música
  (`../arte/02_AUDIO.md` §3).
- **Límite:** ≤ **16 voces simultáneas**, se recorta por prioridad (orden > impacto > ambiente)
  (`../arte/02_AUDIO.md` §4).
- **Fallback:** sin audio, el juego arranca igual; los bocadillos se leen (`../arte/02_AUDIO.md` §1).

---

## 4. Cuándo NO hablar (para que no se gasten)

1. **No hay locución de relleno:** nadie comenta cada paso ni cada golpe.
2. **Un grito por unidad y por evento**, no por segundo.
3. **Nada de voz durante la ayuda contextual de 3 s** (`../batalla/04_PRESENTACION.md`) ni durante
   un aviso de sistema (`../interfaz/07_AVISOS_Y_RUMORES.md`: 1 aviso a la vez).
4. **En los momentos de deuda y muerte, se calla la música** y baja el parloteo a cero
   (`../batalla/04_PRESENTACION.md` §3): el silencio es parte del tono.
5. **Un PNJ que te teme no saluda:** el silencio (o el gesto) es su frase.

---

## 5. Cuántas líneas entran

| Bloque | Líneas (propuesta) | Idiomas |
|---|---|---|
| Gritos de campo (5 familias × 3) | **~15** | ×2 |
| Saludos (por banda de memoria, 7) | **~21** | ×2 |
| Amenazas / precio / trato | **~12** | ×2 |
| Lamentos y funeral | **~9** | ×2 |
| **Total nuevo estimado** | **~57** | **×2 = ~114 claves** |

- El **presupuesto de `txt_*`** del alcance (300-450 ×2, `../produccion/00_ALCANCE.md` §3) ya cuenta
  estas claves; se ajustan al escribir, no se reescriben.
- **Audio:** las frases del **elenco relevante** y las órdenes se pre-generan además en voz
  (×2 idiomas, dentro de los ≤ 20 MB de audio, `../arte/02_AUDIO.md` §4); el resto de las ~57
  líneas **solo existe como texto**.
- **Toda frase con huecos** (`{nombre}`, `{casa}`, `{oro}`) se compone desde plantilla
  (`../interfaz/03_I18N_Y_TONO.md` §6): nunca se escribe dos veces.

---

## 6. Datos, tipos y validación

- **Datos:** `data/voces.json` — `{ id, familia, clave_txt, banda_min, banda_max, prioridad }`.
- **Tipos:** `Voz` en `js/data/game_types.js` (una sola vez, regla 4).
- **Validación:** esquema en `js/data/schemas.js` + `validateStringsPair` (toda `clave_txt` tiene
  pareja ES/EN) + cruce de `familia` con §1 en `tools/validate_data.js`.
- **Sistema/escena:** el **sistema emite un evento** («orden recibida», «unidad rota») y la
  **escena** elige la frase y la pinta/reproduce; el motor puro no conoce bocadillos
  (regla 11 de `../../AGENTS.md`).
- **Tests:** `tests/voces.test.js`, mínimo 3 casos (normal, borde, error): toda clave tiene pareja
  ES/EN; una frase de más de 90 caracteres falla; una banda de memoria sin saludo cae al neutral.

---

## 7. Cifras que fija este documento

| Cifra | Valor |
|---|---|
| Familias de frases | **9** (§1) |
| Variantes por familia | 3-5 |
| Longitud | ≤ 2 líneas · ≤ 90 caracteres |
| Líneas nuevas (propuesta) | **~57 ×2** |
| Voz hablada | **elenco relevante + órdenes** (pre-generada ×2); el resto, texto/gritos |
| Voces simultáneas | ≤ 16 |
| Idiomas | **2** con paridad |

---

## 8. Qué entra en la demo (Fase 1) — y qué sigue

> **Hasta aquí la demo.** Los **gritos de orden, choque, miedo, rendición y victoria** de las 3
> familias del Acto I (`01_ENEMIGOS.md`) — **hablados** —, y los **saludos/amenazas** de los PNJ
> de los 6 sitios (**hablados** los del elenco relevante, en texto los del mundo), con paridad
> ES/EN al 100 % **en texto y en voz**.

> **Y sigue el juego completo.** Las frases de las familias y bandas restantes y los lamentos de
> funerales se añaden **con estas mismas reglas**: crecer = más filas en `voces.json`, no otro
> sistema de voz.

---

## 9. Fuera de este documento

- Tono y claves `txt_*` → `../interfaz/03_I18N_Y_TONO.md`
- Audio, buses y ducking → `../arte/02_AUDIO.md`
- Avisos y rumores → `../interfaz/07_AVISOS_Y_RUMORES.md`
- Rumores jugables → `../misiones/03_CADENAS_Y_RUMORES.md`
- Diálogo de trama → `../historia/04_GUION.md`
