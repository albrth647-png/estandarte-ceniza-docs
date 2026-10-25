# 02 · Audio — sonido 100 % offline

**Estado:** ✅ **aprobado por el dueño (aprobación en bloque, 2026-09-30). Documento final.**

> Decidido (regla 8 de `../../AGENTS.md`): el audio **no puede depender de nada externo**. Todo
> suena desde el propio juego. Hoy **no hay ficheros de audio** (`../../THIRD_PARTY.md`), así que
> este documento fija **cómo se hace** y qué se elige. Desde 2026-10-02 hay un **tercer camino**:
> la **voz hablada pre-generada** (§1).

---

## 1. La regla: offline y con ficha

- **Tres caminos, y solo tres:**
  1. **Síntesis Web Audio** (gratis, sin archivos, generada en el momento).
  2. **Voz hablada pre-generada** (nuevo 2026-10-02): se genera **en producción**, en el equipo
     del desarrollador, con un motor TTS **local** (Kokoro) a partir de las claves `txt_*` →
     `art/audio/voz/<clave>_<idioma>.ogg`. El juego **solo lee** esos ficheros.
  3. **Ficheros propios o libres con ficha** (autor, licencia, enlace, fecha) en `art/AUTORES.md`.
- **En ejecución no cambia nada:** el juego **no lleva motor de voz embebido** ni red; sigue
  sonando 100 % offline desde el propio paquete (la voz se genera **fuera**, una vez).
- **Prohibido:** streaming, CDN, o audio de terceros sin licencia (regla 7).
- **Fallback obligatorio:** si el dispositivo no tiene audio o el jugador lo silencia, **el juego
  arranca igual** (nunca un error de consola por audio).

---

## 2. Qué suena (catálogo)

| Familia | Sonidos | Cómo se hacen |
|---|---|---|
| **Pasos** | tierra, hierba, piedra, agua | Síntesis (ruido filtrado + envolvente) |
| **Hierro** | golpe, bloqueo, desvío, impacto de flecha | Síntesis (impulso + metal) |
| **Mundo** | cuervos, campanas, viento, fuego | Síntesis ambiente + ficheros libres si aparecen |
| **Órdenes y voces** | órdenes habladas, gritos de choque/miedo, llamada de capitán | **Voz pre-generada** (Kokoro) + síntesis/mezcla breve |
| **Música** | camino, posada, batalla, asamblea | Ficheros propios/libres con ficha (≥ 4 piezas) |
| **Interfaz** | toque, aceptar, cancelar | Síntesis muy corta |

- **Modelo de voz (opción 1-C, híbrido): «lo que importa se habla, lo generativo se lee».**
  - **Se habla** (voz pre-generada con Kokoro, **en ES y EN**): prólogo, escenas fijas, las
    **órdenes de batalla**, las frases de **memoria/Firma** y el habla de los **PNJ con memoria
    completa** (elenco relevante).
  - **Se lee** (texto + sonido de mundo): encargos, rumores y bocadillos que el sistema compone
    por plantilla — **nunca se doblan**.
  - **Quién habla:** los personajes más relevantes (elenco fijo + órdenes y unidades en campo);
    el resto del mundo, gritos sintetizados **sin idioma**.
  - La herramienta TTS y sus modelos se fichan en `art/AUTORES.md` **antes** de commitear.

---

## 3. Mezcla y volúmenes

- **3 buses:** música · efectos · interfaz. Volúmenes ya existentes en Opciones
  (`../../js/core/options.js`), **fuera del guardado de partida**.
- **Ducking:** al entrar una voz/orden, la música baja **−6 dB** y vuelve en 0,4 s.
- **El silencio cuenta:** en momentos de deuda y muerte, **calla la música** para que pese
  (`../batalla/04_PRESENTACION.md` §3).

---

## 4. Rendimiento y límites

- **Voces simultáneas:** máximo **16** en el campo; por encima, se recorta por **prioridad**
  (orden > impacto > ambiente).
- **Sin descarga:** todo se genera o se lee de `art/audio/` local (si hay ficheros).
- **Presupuesto de audio:** ≤ **20 MB** de ficheros en la demo (voz ×2 idiomas incluida),
  **dentro** de los ~90 MB del total de la demo (`01_ASSETS.md` §3). Antes era 4 MB sin voz.

---

## 5. QA

- **Arranque sin audio permitido:** el juego no falla si el `AudioContext` no arranca.
- **0 errores en consola** por audio en los 10 minutos de prueba.
- **Paridad de opciones:** los volúmenes persisten y se restauran.

---

## 6. Datos, tipos y validación

- **Datos:** `data/audio.json` — `{ id, familia, fuente ("sintesis" | "fichero"), fichero?, ficha? }`.
- **Voz:** una clave **hablada** tiene **dos ficheros** (uno por idioma, `voz/<clave>_es` y
  `_en`); el validador exige que **ambos existan** si la clave está marcada como hablada.
- **Tipos:** `Sonido` en `js/data/game_types.js`.
- **Validación:** todo `fichero` referenciado **existe** y **tiene ficha** en `art/AUTORES.md`
  (`tools/validate_data.js`); una referencia sin licencia **falla**.
- **Sistema/escena:** la reproducción vive en `js/scenes/*`; la simulación **no** conoce el audio
  (regla 11 de `../../AGENTS.md`).
- **Tests:** `tests/audio.test.js`: sin audio no hay excepción; los volúmenes se aplican; no se
  superan 16 voces.

---

## 7. Cifras que fija este documento

| Cifra | Valor |
|---|---|
| Caminos de audio | **3** (síntesis · voz pre-generada · fichero con ficha) ✅ 2026-10-02 |
| Buses | **3** (música · efectos · interfaz) |
| Voces simultáneas | ≤ 16 |
| Ducking | −6 dB · retorno 0,4 s |
| Memoria de audio (demo) | ≤ **20 MB** (incluida en los ~90 MB de la demo) ✅ 2026-10-02 |
| Red | **0** (en ejecución: sin motor de voz embebido) |
| Voz hablada | **elenco relevante + órdenes** (pre-generada ×2 idiomas); el resto, texto/gritos |

---

## 8. Qué entra en la demo (Fase 1) — y qué sigue

> **Hasta aquí la demo.** Pasos, hierro, interfaz, 2 piezas de música (camino y batalla), las
> **órdenes habladas** y la voz del **prólogo y del elenco relevante** (Kokoro pre-generado, ES y
> EN), con síntesis de arranque y **sin dependencias**.

> **Y sigue el juego completo.** Más piezas (posada, asamblea, estaciones) y ambientes por zona se
> añaden **con la misma regla** (síntesis o ficha); las opciones y los buses **no cambian**.

---

## 9. Fuera de este documento

- Estilo visual → `00_ESTILO.md`
- Efectos y su ritmo → `04_EFECTOS_Y_PARTICULAS.md`
- Avisos sonoros → `../interfaz/07_AVISOS_Y_RUMORES.md`
- Fichas y licencias → `../../art/AUTORES.md`, `../../THIRD_PARTY.md`
