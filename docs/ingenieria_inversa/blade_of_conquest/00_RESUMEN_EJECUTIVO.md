# 00 · RESUMEN EJECUTIVO — Anatomía de Blade of Conquest

> Dossier de ingeniería inversa. Fuente: APK v1.0.2 (`com.wmstudio.games.boc`, 36,79 MB,
> SHA-256 `d2c42d5febbd1623e09ff2517641711ef0fcda6a3b61af12d66cb3a49949d2a9`), desempaquetado
> y analizado con Ghidra 12.2 + análisis estático. Fecha: 2026-10-25.
> Propósito: revivir el juego como **Valcoria / Estandarte de Ceniza** — mismo esqueleto, carne nueva.
> **Nada del código o assets originales se copia a Valcoria**: se documenta el diseño y se reconstruye desde cero.

## Qué es Blade of Conquest

RPG estratégico en tiempo real estilo "Mount & Blade de bolsillo" (la propia comunidad de
Google Play lo describió así: *"This game is effectively Mount & Blade on a phone"*).
El jugador crea un príncipe del reino de Casadoria, recorre el continente de Atmora con su
hueste, recluta de entre 20+ tipos de tropa, conquista cientos de poblados y castillos,
comercia, captura prisioneros y sube de nivel con árbol de habilidades y talentos.
Desarrollado por 田坤 (Kevin_Tien86, "wmstudio") en 2017; retirado de Google Play en enero
de 2020 con ~220.000 instalaciones y 3,85 estrellas. Abandonado desde entonces.

## Veredicto tecnológico (lo primero que hay que saber)

| Capa | Tecnología | Dónde vive la lógica |
|---|---|---|
| Motor | **Cocos2d-x 3.x (C++)** | 100 % del juego |
| Binario del juego | `lib/armeabi/libcocos2dcpp.so` — ELF ARM32, 27,6 MB | Motor propio "AE" + juego "SG" sobre Cocos2d-x |
| Base de datos | **19 archivos XML en claro** en `assets/datas/*.dat` | TODO el contenido (unidades, skills, items, mapas, reinos…) |
| Mapas | **TMX de Tiled** en `assets/game_maps/world_X_Y.tmx` | Geografía del mundo en cuadrícula 5×5 |
| Escenas/UI | **CocoStudio `.csb`** (binario flatbuffers) en `assets/Scenes/` | Maquetación de pantallas |
| Capa Android | `classes.dex` — glue estándar Cocos2d-x + AdMob/Umeng/Firebase | **Ninguna lógica de juego** |
| Guardado | `UserDefault.xml` (preferencias XML de Cocos) + puntos de guardado en escena | — |

**Consecuencia clave para Valcoria:** el juego no necesita "descompilar" para entenderse.
Su base de datos entera es XML legible y sus mapas son TMX estándar; el binario conserva
16.782 símbolos de funciones C++ que nombran casi toda la arquitectura. La ingeniería
inversa profunda (Ghidra) se reserva para las fórmulas del motor de batalla, la IA y el
formato de guardado, que sí viven compiladas en el `.so`.

## Los cuatro subsistemas que hay que revivir

1. **Mundo-continente (SandTable)** — mapa mundial en cuadrícula de celdas, grafo de
   caminos entre poblados, bandas errantes con respawn, reinos con reyes/vasallos y
   lealtades iniciales. Dossier: `02_MAPA_MUNDIAL.md`, `09_ENEMIGOS_Y_RESPAWN.md`.
2. **Poblados y economía (City)** — ciudades/aldeas/castillos con prosperidad, defensa,
   huecos de torre, mercado con tablas de probabilidad, herrería, comercio e impuestos
   semanales (`AEWeeklyBudget`). Dossier: `03_POBLADOS_Y_CONSTRUCCION.md`, `08_ECONOMIA.md`.
3. **Tropas y héroe (Party/Units)** — 23 unidades con árbol de mejora por `pre_unit`,
   stats base + crecimiento por nivel, coste de recluta y mejora, botín; héroe con
   32 habilidades en árbol + talentos. Dossier: `04_UNIDADES_TROPAS.md`, `05_HABILIDADES.md`.
4. **Batalla en tiempo real (Battle)** — formaciones, campo de batalla, órdenes a
   compañías, control directo del héroe con skills. Dossier: `07_BATALLA.md`.

## Estado del análisis

| Pieza | Estado | Método |
|---|---|---|
| Base de datos XML (19 .dat) | ✅ 100 % extraída y tabulada | Parseo directo |
| Mapas TMX + malla de caminos | ✅ estructura completa | Parseo directo |
| Arquitectura de clases nativa | ✅ 183 clases de juego mapeadas | Símbolos del .so |
| Motor de batalla (fórmulas) | 🔶 en curso | Ghidra headless |
| IA de reinos/bandas | 🔶 en curso | Ghidra headless |
| Formato de guardado | 🔶 en curso | Ghidra headless |

Los dossiers 02–10 detallan cada subsistema con sus tablas originales decodificadas.
El dossier `11_CODIGO_NATIVO.md` recoge el mapa de clases y los hallazgos de Ghidra.
