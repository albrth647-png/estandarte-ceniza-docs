# Fase A — Inventario exhaustivo de referencias a juegos reales

> **Task ID:** 2-a · **Fecha:** 2026-11-06 · **Alcance:** `/home/z/my-project/repos/estandarte-ceniza-docs/docs/` (98 fichas + raíz del repo para cruces).
> **Método:** greps case-insensitive por nombre de juego + patrones genéricos («como en», «estilo», «inspirado», «referencia», «género», «endgame», «idle», «prestige», «videojuego») + lectura completa de `docs/VISION_JUEGO_COMPLETO.md`, `docs/VALCORIA_DEUDA_DE_SANGRE.md` (§5) y fichas ancla. Verificación negativa (0 hits) para: Age of Empires, Wee Warriors, Dark Souls, Bloodborne, Sekiro, Skyrim, Witcher, Kingdom Come, Wartales, XCOM, Civilization, Frostpunk, Stellaris, Zelda, Hades, Minecraft, Valheim, Godot/Unity/Unreal, Kenney, OpenGameArt.

---

## Resumen

| Métrica | Valor |
|---|---|
| **Juegos reales distintos citados** | **20** (17 dentro de las 6 familias del §2.1 + 3 huérfanos) |
| **Referencias no-lúdicas** | 1 (película *El Señor de los Anillos*) |
| **Paquetes de assets citados** | 4 (KayKit + City Builder Bits, Quaternius MegaKit, Modular Castle Kit, zorro «Fox») |
| **Fichas de docs/ con referencias** | 10 de 98 (+2 fichas de raíz: `THIRD_PARTY.md`, `art/AUTORES.md`) |
| **Juegos huérfanos (fuera de §2.1)** | **3**: Shadow of Mordor/War, Destiny, The Division |
| **Ancla del proyecto** | «Blade of Conquest» **no aparece escrita en ninguna parte del repo**; el juego original se llama siempre «el prototipo anterior» / «el primer juego» (el APK real vive en `/home/z/my-project/rea/blade_of_conquest/`) |
| **Concentración** | El 90 % de las citas de juegos están en **una sola ficha**: `docs/VISION_JUEGO_COMPLETO.md` (§2, §3.3, §6, §10) |

---

## 1. Referencias dentro del §2.1 (las 6 familias, 17 juegos)

### 1.1 World of Warcraft (MMO — lección negativa)

| Ficha | Línea | Cita | Qué aporta a Valcoria |
|---|---|---|---|
| docs/VISION_JUEGO_COMPLETO.md | 53 | «**MMO** \| World of Warcraft, Final Fantasy XIV…» | Familia de referencia: endgames apilados |
| docs/VISION_JUEGO_COMPLETO.md | 62 | «**WoW (vanilla):** ~400 horas… nivel 1 a 60» | Dato de longevidad: el endgame nace de la escasez de contenido |
| docs/VISION_JUEGO_COMPLETO.md | 63-64 | «palabras de… Andy Gavin — "no hay forma de crear contenido"» | Anti-patrón: contenido más lento de consumir → prohibido aquí |
| docs/VISION_JUEGO_COMPLETO.md | 228-229 | «Andy Gavin — "WOW Endgames – Vanilla" (blog)» | Fuente citada con URL |
| docs/VISION_JUEGO_COMPLETO.md | 237 | «observación directa de World of Warcraft…» | Base de evidencia del §2 |

Se apoyan en ella: `sistemas/09_TIEMPO_Y_MUNDO_VIVO.md` (reloj por acciones, no esperas reales), `sistemas/05_PROGRESION.md`, `VISION` §4 («Nada de esperas reales», prohibido el «vuelve en 24 h»).

### 1.2 Final Fantasy XIV (MMO)

| Ficha | Línea | Cita | Qué aporta a Valcoria |
|---|---|---|---|
| docs/VISION_JUEGO_COMPLETO.md | 53 | «MMO \| World of Warcraft, Final Fantasy XIV, Elder…» | Lección negativa MMO: lockouts, temporadas |
| docs/VISION_JUEGO_COMPLETO.md | 237 | «observación directa de… Final Fantasy XIV» | Base de evidencia |

Se apoyan en ella: `VISION` §6.2 (time-gating real prohibido), `interfaz/11_AVISOS_DE_CONTENIDO.md` (sin FOMO).

### 1.3 Elder Scrolls Online (MMO)

| Ficha | Línea | Cita | Qué aporta a Valcoria |
|---|---|---|---|
| docs/VISION_JUEGO_COMPLETO.md | 53 | «…Final Fantasy XIV, Elder Scrolls Online» | Tercer ejemplo MMO de endgame apilado |
| docs/VISION_JUEGO_COMPLETO.md | 237 | «observación directa de… Elder Scrolls Online» | Base de evidencia |

**Nota:** el enunciado de la tarea describe el §2.1 como «MMO: WoW/FFXIV/Diablo/PoE», pero el fichero real lista WoW/FFXIV/**ESO** en la fila MMO. ESO no es huérfano (está en la tabla), pero sí diverge del resumen del encargo.

### 1.4 Mount & Blade: Warband / Bannerlord (sandbox medieval)

| Ficha | Línea | Cita | Qué aporta a Valcoria |
|---|---|---|---|
| docs/VISION_JUEGO_COMPLETO.md | 54 | «Sandbox medieval \| Mount & Blade Warband / Bannerlord…» | Familia ancla: mundo vivo que avanza sin ti |
| docs/VISION_JUEGO_COMPLETO.md | 72 | «en un sandbox como Mount & Blade no importa "terminarlo"» | Metas autoimpuestas; no hay final, hay horizontes |
| docs/VISION_JUEGO_COMPLETO.md | 238 | «Mount & Blade Warband/Bannerlord, Kenshi…» | Observación directa |

Se apoyan en ella: `mundo/09_TIEMPO_Y_MUNDO_VIVO.md` (el mundo sigue sin el jugador), `batalla/*` (batalla táctica de tropas), `contenido/00_TROPAS.md` (alistar tropa por oro), `mundo/02_VIAJE_Y_ENCUENTROS.md` (campaña por días).

### 1.5 Kenshi (sandbox medieval)

| Ficha | Línea | Cita | Qué aporta a Valcoria |
|---|---|---|---|
| docs/VISION_JUEGO_COMPLETO.md | 54 | «Mount & Blade Warband / Bannerlord, Kenshi, Battle…» | Mundo indiferente al jugador; horizontes |
| docs/VISION_JUEGO_COMPLETO.md | 238 | «…Kenshi, Battle Brothers, Starsector…» | Observación directa |

Se apoyan en ella: `mundo/00_MAPA.md` (Tierra de Ninguno, autoridad que no llega), `sistemas/00_MEMORIA_Y_DEUDA.md` (el mundo no espera al héroe).

### 1.6 Battle Brothers (sandbox medieval)

| Ficha | Línea | Cita | Qué aporta a Valcoria |
|---|---|---|---|
| docs/VISION_JUEGO_COMPLETO.md | 54 | «…Kenshi, Battle Brothers, Starsector» | Escuadrón mercenario con bajas permanentes |
| docs/VISION_JUEGO_COMPLETO.md | 238 | «…Battle Brothers, Starsector…» | Observación directa |

Se apoyan en ella: `contenido/00_TROPAS.md` (tropa con nombre/miedo), `VISION` §1 (veteranos: nombre + rasgo), `batalla/00_REGLAS.md` (moral como condición de victoria).

### 1.7 Starsector (sandbox medieval)

| Ficha | Línea | Cita | Qué aporta a Valcoria |
|---|---|---|---|
| docs/VISION_JUEGO_COMPLETO.md | 54 | «…Battle Brothers, Starsector» | Campaña simulada con reloj propio |
| docs/VISION_JUEGO_COMPLETO.md | 238 | «…Starsector, Crusader Kings 3…» | Observación directa |

Se apoyan en ella: `mundo/05_TIEMPO_DEL_MUNDO.md` (días por acciones), `VISION` §3.3 motor 4 («Reloj propio: lo que pasa mientras no juegas es contenido gratis»).

### 1.8 Crusader Kings 3 (grand strategy)

| Ficha | Línea | Cita | Qué aporta a Valcoria |
|---|---|---|---|
| docs/VISION_JUEGO_COMPLETO.md | 55 | «Grand strategy \| Crusader Kings 3, Total War» | El tiempo ES el contenido; sucesiones |
| docs/VISION_JUEGO_COMPLETO.md | 238 | «…Crusader Kings 3, Total War…» | Observación directa |

Se apoyan en ella: `sistemas/00_MEMORIA_Y_DEUDA.md` §7 (herencia de deuda: hijo 100 %, casa 50 %), `historia/05_CASAS_Y_FACCIONES.md` (casas que se extinguen), `sistemas/09_TIEMPO_Y_MUNDO_VIVO.md`.

### 1.9 Total War (grand strategy)

| Ficha | Línea | Cita | Qué aporta a Valcoria |
|---|---|---|---|
| docs/VISION_JUEGO_COMPLETO.md | 55 | «Crusader Kings 3, Total War» | Perder también genera historia |
| docs/VISION_JUEGO_COMPLETO.md | 239 | «Total War, Dwarf Fortress, RimWorld…» | Observación directa |

Se apoyan en ella: `batalla/06_BATALLAS_DE_LA_HISTORIA.md` («si el jugador pierde, la historia sigue»), formaciones por datos (`batalla/00_REGLAS.md`).

### 1.10 Dwarf Fortress (emergente)

| Ficha | Línea | Cita | Qué aporta a Valcoria |
|---|---|---|---|
| docs/VISION_JUEGO_COMPLETO.md | 56 | «Emergente \| Dwarf Fortress, RimWorld» | Sistemas que se combinan → historias irrepetibles |
| docs/VISION_JUEGO_COMPLETO.md | 239 | «Dwarf Fortress, RimWorld, Melvor Idle…» | Observación directa |

Se apoyan en ella: `sistemas/04_CRONICA.md` (registro de lo que pasó), `MECANICAS.md` §3 (Red de rencores: grafo emergente), `sistemas/00_MEMORIA_Y_DEUDA.md` (memoria universal de PNJ).

### 1.11 RimWorld (emergente)

| Ficha | Línea | Cita | Qué aporta a Valcoria |
|---|---|---|---|
| docs/VISION_JUEGO_COMPLETO.md | 56 | «Dwarf Fortress, RimWorld» | Historias que nadie escribió a mano |
| docs/VISION_JUEGO_COMPLETO.md | 239 | «RimWorld, Melvor Idle, NGU Idle…» | Observación directa |

Se apoyan en ella: `sistemas/04_CRONICA.md`, `contenido/02_CAPITANES_Y_NEMESIS.md` (rasgos y rencor generados), `sistemas/07_CICATRICES.md` (secuelas permanentes).

### 1.12 Melvor Idle (idle offline)

| Ficha | Línea | Cita | Qué aporta a Valcoria |
|---|---|---|---|
| docs/VISION_JUEGO_COMPLETO.md | 57 | «Idle offline \| Melvor Idle, Tideward, NGU Idle» | Progresión por timestamp al reabrir |
| docs/VISION_JUEGO_COMPLETO.md | 69 | «Offline real (Melvor / Tideward): cap de 24 horas» | Tope de simulación offline (retención + coste) |
| docs/VISION_JUEGO_COMPLETO.md | 239 | «Melvor Idle, NGU Idle, Elden Ring…» | Observación directa |

Se apoyan en ella: `mundo/09_TIEMPO_Y_MUNDO_VIVO.md` §3 (qué pasa con lo dejado a medias) — **pero con la regla propia de `VISION` §4: nada de esperas reales; el cap de 24 h de Melvor/Tideward se rechaza como muro de tiempo real**.

### 1.13 Tideward (idle offline)

| Ficha | Línea | Cita | Qué aporta a Valcoria |
|---|---|---|---|
| docs/VISION_JUEGO_COMPLETO.md | 57 | «Melvor Idle, Tideward, NGU Idle» | Progresión por timestamp |
| docs/VISION_JUEGO_COMPLETO.md | 69 | «(Melvor / Tideward): la simulación se cierra…» | Cap 24 h a tasa completa |
| docs/VISION_JUEGO_COMPLETO.md | 234-235 | «Tideward — comparativa de progresión offline» | Fuente citada con URL |

Se apoyan en ella: ídem Melvor.

### 1.14 NGU Idle (idle offline)

| Ficha | Línea | Cita | Qué aporta a Valcoria |
|---|---|---|---|
| docs/VISION_JUEGO_COMPLETO.md | 57 | «Melvor Idle, Tideward, NGU Idle» | Referencia del género idle |
| docs/VISION_JUEGO_COMPLETO.md | 239 | «Melvor Idle, NGU Idle, Elden Ring…» | Observación directa |

Se apoyan en ella: `VISION` §3.1.3 (ascensión/prestige) y §5 (Legado / nuevo ciclo). Ojo: los greps de «NGU» sin sufijo dan falsos positivos con «ninguna/ninguno».

### 1.15 Elden Ring (ascensión / NG+)

| Ficha | Línea | Cita | Qué aporta a Valcoria |
|---|---|---|---|
| docs/VISION_JUEGO_COMPLETO.md | 58 | «Ascensión / NG+ \| Elden Ring, Diablo, Path of Exile» | Reinicio voluntario con desbloqueo permanente |
| docs/VISION_JUEGO_COMPLETO.md | 239 | «NGU Idle, Elden Ring, Diablo…» | Observación directa |

Se apoyan en ella: `VISION` §5 «Legado / nuevo ciclo» (conserva artefactos y personajes), `sistemas/12_NIVELES_DEL_HEROE.md` (tope de nivel como disparador).

### 1.16 Diablo / Diablo III (ascensión + anti-patrón)

| Ficha | Línea | Cita | Qué aporta a Valcoria |
|---|---|---|---|
| docs/VISION_JUEGO_COMPLETO.md | 58 | «Elden Ring, Diablo, Path of Exile, prestige» | NG+ / temporada como capa opcional |
| docs/VISION_JUEGO_COMPLETO.md | 169 | «Endgame solo escalado (Diablo III, Destiny…)» | **Anti-patrón**: mismos números más altos aburre |
| docs/VISION_JUEGO_COMPLETO.md | 239 | «Elden Ring, Diablo, Path of Exile y…» | Observación directa |

Se apoyan en ella: `VISION` §3.2 (mejoras duras > números), `contenido/07_ARTEFACTOS.md` (desbloqueos que cambian cómo juegas), afijos de repetición escalada (`VISION` §5).

### 1.17 Path of Exile (ascensión / NG+)

| Ficha | Línea | Cita | Qué aporta a Valcoria |
|---|---|---|---|
| docs/VISION_JUEGO_COMPLETO.md | 58 | «Elden Ring, Diablo, Path of Exile, prestige…» | Prestige que se conserva como desbloqueo |
| docs/VISION_JUEGO_COMPLETO.md | 239 | «Diablo, Path of Exile y del *Nemesis System*…» | Observación directa |

Se apoyan en ella: `VISION` §5 (Legado / nuevo ciclo, afijos), `sistemas/05_PROGRESION.md`.

---

## 2. Juegos HUÉRFANOS (citados pero fuera de las 6 familias del §2.1)

### 2.1 Shadow of Mordor / Shadow of War (Nemesis System) — huérfano clave

| Ficha | Línea | Cita | Qué aporta a Valcoria |
|---|---|---|---|
| docs/VISION_JUEGO_COMPLETO.md | 108-110 | «el *Nemesis System* (Shadow of Mordor / War): capitanes…» | Modelo de referencia de los agentes con memoria |
| docs/VISION_JUEGO_COMPLETO.md | 174 | «Copiar el Némesis al detalle: está patentado» | Restricción legal: diseñar versión propia |
| docs/VISION_JUEGO_COMPLETO.md | 240 | «del *Nemesis System* de Shadow of Mordor/War» | Observación directa |
| docs/contenido/02_CAPITANES_Y_NEMESIS.md | 83, 88, 100, 125 | «**Némesis** de su familia, con refuerzos» / «Némesis heredada» | El nombre del sistema Valcoria homenajea al juego **sin citarlo nunca** |

Es la referencia estructural más importante del diseño (culdán generalizado → capitanes con nombre, rango, rencor y rasgos que vuelven; `sistemas/00_MEMORIA_Y_DEUDA.md`, `sistemas/09_TIEMPO_Y_MUNDO_VIVO.md`), y **no está en la tabla del §2.1**: solo aparece en §3.3, §6 y §10 de VISION.

### 2.2 Destiny

| Ficha | Línea | Cita | Qué aporta a Valcoria |
|---|---|---|---|
| docs/VISION_JUEGO_COMPLETO.md | 169 | «(Diablo III, Destiny, The Division): "los mismos…"» | Anti-patrón de endgame escalado (§6 «Lo que NO hay que copiar») |

Refuerza `VISION` §3.2: el poder a largo plazo debe venir de mejoras duras, no de números.

### 2.3 The Division

| Ficha | Línea | Cita | Qué aporta a Valcoria |
|---|---|---|---|
| docs/VISION_JUEGO_COMPLETO.md | 169 | «Diablo III, Destiny, The Division): "los mismos números…"» | Ídem: treadmill que borra progreso (§6.3) |

Refuerza la traducción «conservar todo + dificultad opcional» (`sistemas/11_DEUDAS_DEL_JUGADOR.md`, epílogo por Firma).

---

## 3. Referencia no-lúdica: *El Señor de los Anillos* (película)

| Ficha | Línea | Cita | Qué aporta a Valcoria |
|---|---|---|---|
| docs/VALCORIA_DEUDA_DE_SANGRE.md | 210 | «referencia: *El Señor de los Anillos* como dirección, no…» | Dirección de fotografía (luz, niebla, paleta), no presupuesto |
| docs/DECISIONES.md | 85 | «referencia *El Señor de los Anillos* como dirección» | Decisión ronda 10: estilo película medieval |
| docs/arte/00_ESTILO.md | 6-7 | «fotografía de referencia: *El Señor de los Anillos*» | Base de la dirección de arte aprobada |

Sostiene: `arte/00_ESTILO.md` completo (ACES, sol oblicuo, niebla 60 m), `produccion/01_FASES.md` (hito 1.7), `produccion/PLAN_FASE1.md` I7.

---

## 4. Paquetes de assets citados (no son juegos, pero son referencias de terceros)

### 4.1 KayKit (paquete CC0 — el más citado de todo el repo)

| Ficha | Línea | Cita | Qué aporta a Valcoria |
|---|---|---|---|
| docs/arte/01_ASSETS.md | 15-19 | «u_knight.glb \| KayKit \| CC0 1.0» | 5 humanos de prototipo (héroe, bandido, explorador, aldeano, escribano) |
| docs/arte/01_ASSETS.md | 20 | «u_skeleton_warrior/minion/rogue/mage.glb (4) \| KayKit» | 4 esqueletos en reserva (criaturas/leyenda) |
| docs/arte/01_ASSETS.md | 25 | «los 5 humanos KayKit pasan a reserva de…» | Enmienda 2026-10-02: cuerpos de proporción humana en pantalla |
| docs/arte/01_ASSETS.md | 40, 142 | «Sustituyen al cartoon de KayKit» | Estado de sustitución de assets |
| docs/VALCORIA_DEUDA_DE_SANGRE.md | 219 | «los modelos KayKit pasan a reserva de prototipo» | Pilar §5: nada de cartoon en pantalla |
| docs/VALCORIA_DEUDA_DE_SANGRE.md | 229-230 | «Quaternius MegaKit, Modular Castle Kit, KayKit City Builder Bits» | Paquetes CC0 identificados, no descargados |
| docs/DECISIONES.md | 85 | «de "low-poly tipo KayKit" a dirección de fotografía» | Enmienda de estilo (ronda 10) |
| docs/DECISIONES.md | 86 | «el cartoon de KayKit pasa a reserva de prototipo» | Decisión ronda 11: personas realistas |
| docs/produccion/06_LEGAL_Y_AUTORIA.md | 24 | «CC0 1.0 (KayKit) · CC0 + CC-BY 4.0 (Fox)» | Licencias de los 10 modelos .glb |
| docs/produccion/00_ALCANCE.md | 108 | «cartoon KayKit → reserva ✅ 2026-10-02» | Alcance demo |
| docs/arte/README.md | 18 | «(KayKit CC0 / Fox CC-BY), Three.js r186…» | Stack de arte |
| docs/mundo/07_PROPS_Y_VEGETACION.md | 25 | «KayKit CC0 ya incorporado; ficha en…» | Props con licencia |
| THIRD_PARTY.md (raíz) | 13 | «Modelos KayKit (reserva de prototipo: 5 humanos)» | Compromiso de licencias |
| art/AUTORES.md (raíz) | 12-13 | «u_knight \| KayKit \| CC0» | Ficha de autoría |

Se apoya en ella: todo el pipeline de arte (`arte/01_ASSETS.md`), el gate de peso (`produccion/10_BUILD_Y_FIRMA_APK.md` §5) y la reserva de prototipo. **En el enunciado de la tarea KayKit figuraba como fila «especiales» del §2.1; en el fichero real esa fila no existe.**

### 4.2 Quaternius MegaKit, Modular Castle Kit, KayKit City Builder Bits

| Ficha | Línea | Cita | Qué aporta a Valcoria |
|---|---|---|---|
| docs/VALCORIA_DEUDA_DE_SANGRE.md | 229-230 | «paquetes CC0 de castillo/interiores… identificados pero no descargados» | Reserva de assets de arquitectura/interiores |

Única mención en todo el repo (estado ⏳ pendiente de descarga).

### 4.3 Modelo «Fox» (zorro CC0 + CC-BY)

| Ficha | Línea | Cita | Qué aporta a Valcoria |
|---|---|---|---|
| docs/produccion/06_LEGAL_Y_AUTORIA.md | 24, 77 | «CC0 + CC-BY 4.0 (Fox)» | Fauna; crédito CC-BY obligatorio |
| docs/arte/README.md | 18 | «Fox CC-BY» | Stack de arte |
| THIRD_PARTY.md (raíz) | 14 | «Modelo de zorro (reserva de fauna)… CC0 + CC-BY» | Crédito en créditos del juego |
| art/AUTORES.md (raíz) | 14 | «u_fox (zorro) \| autor libre \| CC0 + CC-BY» | Ficha de autoría |

Se apoya en ella: `contenido/08_ANIMALES_Y_CRIATURAS.md` (fauna de reserva).

---

## 5. El ancla: «Blade of Conquest» y el prototipo anterior

- **0 menciones literales** de «Blade of Conquest» en TODO el repo (verificado por grep sobre docs/ + raíz). El juego original se nombra siempre como **«el prototipo anterior»** o **«el primer juego»**.
- Su memoria vive en `docs/VISION_JUEGO_COMPLETO.md` §1 (tabla de piezas heredadas: escuadrones, veteranos, culdán, honor, economía, campaña por días, 1 día = 30 s) y en la nota 2026-10-01/25 que aclara que su código ya no existe.
- Términos que de ahí hereda el diseño nuevo: **culdán** (reaparición del enemigo, hoy generalizado a «capitanes con memoria» — `sistemas/09_TIEMPO_Y_MUNDO_VIVO.md`), **veteranos** (nombre + rasgo — `contenido/00_TROPAS.md`), **honor** y **resultado de batalla**.
- El APK físico del juego original está en `/home/z/my-project/rea/blade_of_conquest/` (blade_of_conquest_1.0.2.apk, jadx_out, unpacked), fuera del repo de docs.
- **Riesgo de trazabilidad:** sin el nombre en la documentación, la cadena «juego abandonado → prototipo anterior → Valcoria» solo existe en el worklog y en el enunciado del proyecto. Si se quiere preservar el ancla, habría que añadirla (p. ej. como nota histórica en VISION §1).

---

## 6. Fuentes externas citadas (no juegos)

| Fuente | Ficha | Línea | Cita |
|---|---|---|---|
| Andy Gavin — «WOW Endgames – Vanilla» | docs/VISION_JUEGO_COMPLETO.md | 228-229 | blog del desarrollador, con URL |
| Gamedeveloper.com — «Ending on a High Note» (Josh Bycer) | docs/VISION_JUEGO_COMPLETO.md | 230-231 | 3 formas de endgame |
| Game-Wisdom — «The 3 Forms of Power Curves» (Josh Bycer) | docs/VISION_JUEGO_COMPLETO.md | 232-233 | curvas de poder |
| Tideward — comparativa de progresión offline | docs/VISION_JUEGO_COMPLETO.md | 234-235 | tideward.app/offline-progression |

---

## Hallazgos y huérfanos

1. **Concentración extrema:** 17 de 20 juegos viven en una sola ficha (`VISION_JUEGO_COMPLETO.md`). Las 97 fichas de diseño restantes **no citan juegos reales por nombre** — coherente con la regla de originalidad (`AGENTS.md` regla 7, `THIRD_PARTY.md` §2: «Cero activos, nombres o textos de juegos de terceros»), pero convierte a VISION en punto único de fallo si se pierde la teoría de longevidad.
2. **Huérfanos confirmados (3 juegos):** *Shadow of Mordor/War* (Nemesis System — §3.3/§6/§10 de VISION; el sistema «Némesis» de `contenido/02_CAPITANES_Y_NEMESIS.md` lleva su nombre sin citar el juego), *Destiny* y *The Division* (solo en §6 como anti-patrones). Los ejemplos del enunciado **Age of Empires y Wee Warriors NO aparecen en el repo** (0 hits).
3. **Discordancia del enunciado con el fichero real:** el §2.1 actual no tiene fila «especiales» (Blade of Conquest / KayKit) y su fila MMO lista ESO, no Diablo/PoE (que están en la fila Ascensión). El enunciado de la tarea describe una versión del inventario más antigua o de otra fuente.
4. **«Blade of Conquest» es fantasma:** el ancla del proyecto jamás se escribe en la documentación. Todo se refiere a «el prototipo anterior». Recomendación: nota de trazabilidad en VISION §1 o en el README del proyecto.
5. **El Nemesis System es la referencia estructural #1 y está bien tratada legalmente:** se cita como modelo, se marca «está patentado» y se ordena diseñar versión propia (`VISION` 108-110 y 174; `DECISIONES.md` registra la generalización a «capitanes con memoria»).
6. **Los idle se citan para rechazar su mecánica de tiempo real:** Melvor/Tideward aportan el patrón timestamp + cap 24 h, pero `VISION` §4 lo prohíbe explícitamente («Nada de esperas reales», «vuelve en 24 h» prohibido) — la referencia es dialéctica, no de copia.
7. **WoW aporta la cita fundacional** (Andy Gavin: «no hay forma de crear contenido al ritmo al que los jugadores lo consumen»), de la que sale la teoría de «contenido más lento de consumir» que Valcoria invierte en «el límite lo pone tu tiempo de juego».
8. **Assets:** KayKit es la referencia más citada del repo (≈20 líneas en 10 ficheros) pero quedó **degradada a reserva de prototipo** (decisión 2026-10-02, rondas 10-11); Quaternius MegaKit / Modular Castle Kit / City Builder Bits están «identificados pero no descargados» (⏳). Cualquier uso futuro exige ficha en `THIRD_PARTY.md`.
9. **Higiene de búsqueda:** los patrones «NGU» (falso positivo con «ninguna») y «Idle» (estado de animación en `arte/03_ANIMACIONES.md`) dan ruido; «victoria» y «pilar/pillars» también son falsos positives en español.
10. **Cero referencias a motores u otras tiendas de assets** (Godot/Unity/Unreal/Kenney/OpenGameArt: 0 hits) — el stack es Three.js r186 vendorizado + assets propios generados fuera de ejecución.
