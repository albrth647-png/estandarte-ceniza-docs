# 00 · Resumen del blanco — Blade of Conquest v1.1.1

> **Proyecto:** Valcoria — Deuda de Sangre · Línea de ingeniería inversa.
> **Propósito de este dossier:** documentar TODO lo extraído de Blade of Conquest con REA +
> Ghidra para revivir el juego mejorado. Nada de esto se copia literal: se extrae **conocimiento**
> (arquitectura, datos, fórmulas) y Valcoria lo re-implementa desde cero, mejorado.

---

## 1. Identificación del blanco

| Campo | Valor |
|---|---|
| **Nombre comercial** | Blade Of Conquest (征服之刃, «Zhengfu Zhi Ren» = Hoja de Conquista) |
| **Paquete** | `com.wmstudio.games.boc` |
| **Versión analizada** | 1.1.1 (última publicada, 9-feb-2018) |
| **SHA256 del APK** | `f7ab6c3b4d0278f93451c3b1b184540cc36d29cdcdded3362e0c17ee6d12782f` |
| **Origen del archivo** | CDN de Farsroid vía droidcove.com; hash idéntico al publicado por Uptodown (APK limpio, sin mods) |
| **Firma del certificado** | MD5 `a8205999599b83ebf725eb110769acb9` (Uptodown) |
| **Desarrollador** | 田坤 (Tian Kun), estudio wmstudio — contacto `wmstudiogame@163.com` |
| **Equipo real** | **Una sola persona**: Kevin Tien hizo planificación, programación, arte y pruebas (`pdl.dat`) |
| **Historia comercial** | Lanzado ~2016 en Google Play; **220.000 instalaciones**; 3,85★ (7.425 votos); última actualización 25-nov-2017; **retirado de Google Play el 6-ene-2020**; monetización: anuncios de 5 s tras cada batalla, sin compras |
| **Requisitos** | Android 2.3.3+ (v1.1.1: 4.0.3+); APK único de 53,35 MB (55.940.905 bytes) |
| **Recepción** | «Mount & Blade en un teléfono» + «sistema de combate tipo Dragon Force (Sega Saturn)» (reseñas de la comunidad) |

## 2. Por qué este blanco es la base de Valcoria

- Es el **esqueleto probado**: mundo abierto con cientos de sitios, ejército reclutable, combate
  en tiempo real con control de héroe, captura de pueblos y comercio urbano. Ya funcionó y ya
  convenció (220 mil instalaciones con desarrollo de una persona y cero marketing).
- Es un **juego abandonado**: sin sucesor desde 2020. Revivirlo con producción moderna es
  territorio libre de competencia directa.
- Valcoria hereda el esqueleto y reemplaza la piel: 1.ª persona, identidad de deuda/sangre,
  memoria de los enemigos, paridad ES/EN, guardado versionado — todo lo decidido en los 98 docs.

## 3. Identificación técnica rápida (pre-Ghidra)

| Pieza | Hallazgo |
|---|---|
| **Motor** | Cocos2d-x (C++ nativo): `libMyGame.so` (nombre del template por defecto del motor) |
| **Lib nativa** | `lib/armeabi/libMyGame.so` — ARM 32-bit EABI5, ELF compartido, con símbolos de minizip y `AECrypto::MD5` |
| **Java** | Un solo `classes.dex` de arranque (sin lógica de juego en Java) |
| **Datos** | `assets/datas/*.dat` — **ZIPs con contraseña** (extraíbles al obtener la clave de `libMyGame.so`) |
| **Mapas** | `assets/game_maps/*.tmx` — 43 mapas Tiled XML (rejilla mundial 5×5 de celdas de 50×50 tiles de 32 px) |
| **UI** | 31 escenas `.csb` de Cocos Studio 2.1.0.0 (BattlePrepare, Barracks, Party, Inventory, FaceGenerator…) |
| **Textos** | `Rc.plist` / `Rc_cn.plist` (par EN/CN — el equivalente BoC de nuestro i18n ES/EN), `tips.dat` con pares EN/CN |
| **Cifrado** | `AECrypto::MD5` + `AEZipUtility` (creación/lectura de ZIP con contraseña) — utilidades propias del estudio |

## 4. Estado del trabajo RE

| Tarea | Estado |
|---|---|
| Descarga e integridad del APK | ✅ hecho (hash verificado) |
| Desempaquetado del APK | ✅ hecho (`rea_targets/boc_unpacked/`) |
| Identificación de motor y arquitectura | ✅ hecho (Cocos2d-x, ARM32, datos ZIP cifrados) |
| Contraseña ZIP de `datas/*.dat` | 🔄 en curso (Ghidra: xrefs de `unzOpenCurrentFilePassword`) |
| Volcado de unidades/skills/chars | ⏳ bloqueado por la contraseña |
| Descompilación de combate/economía | ⏳ tras el volcado |
| Dossier «cómo hacerlo mejor» | ⏳ con los hallazgos anteriores |

## 5. Cadena de custodia y limpieza

- El APK y los volcados viven FUERA del repo (en `rea_targets/`); al repo solo entra documentación
  y datos textuales legibles (tablas/JSON) — nunca binarios del juego original.
- Fuentes consultadas para el contexto (reseñas, historia, hash): Uptodown, AppBrain, Reddit
  r/AndroidGaming (hilo original de lanzamiento 2016), foro Easytech, Sbenny.


---

## Serie de dossiers (estado del análisis 2026-10-25)

| Dossier | Contenido | Fuente |
|---|---|---|
| `01_ARQUITECTURA_DEL_APK.md` | paquete v1.1.1, assets, escenas, sistema de mapas | v1.1.1 |
| `02_DATOS_DEL_JUEGO.md` | ZIP con contraseña = restos; claves de texto legibles | v1.1.1 |
| `03_ESTADO_DEL_DESCIFRADO.md` | veredicto bkcrack y cierre del descifrado | v1.1.1 |
| `04_MAPA_MUNDIAL.md` | cuadrícula 5×5, grafo de 209 nodos, sitios, reinos | v1.0.2 |
| `05_POBLADOS_Y_CONSTRUCCION.md` | 88 sitios/9 tipos, prosperidad/defensa, torres | v1.0.2 |
| `06_UNIDADES_TROPAS.md` | 23 tropas, árbol pre_unit, stats y crecimiento | v1.0.2 |
| `07_HABILIDADES_TALENTOS.md` | 32 skills en 4 escuelas + 17 talentos | v1.0.2 |
| `08_PERSONAJES_Y_REINOS.md` | personajes, lealtades, reparto político inicial | v1.0.2 |
| `09_BATALLA.md` | formaciones, órdenes, héroe, auto-batalla | v1.0.2 |
| `10_ECONOMIA_Y_COMERCIO.md` | botín, mercados, presupuesto semanal | v1.0.2 |
| `11_ENEMIGOS_Y_RESPAWN.md` | 34 bandas errantes con respawn | v1.0.2 |
| `12_GUARDADO.md` | puntos de guardado, claves del save | v1.0.2 + binario |
| `13_CODIGO_NATIVO.md` | 5.750 funciones descompiladas; fórmula de daño | Ghidra 12.2 |
| `datos/` | 21 tablas de datos decodificadas + arquitectura de clases | v1.0.2 |

**Nota de versiones:** el esqueleto de sistemas es idéntico en v1.0.2 y v1.1.1. La
v1.0.2 (copia local, SHA-256 `d2c42d5f…`) distribuye las tablas `datas/*.dat` como XML
en claro — por eso la serie 04–13 extrae los datos completos de ella; la v1.1.1 los
empaquetó en ZIP con contraseña que el juego nunca lee (ver `02_DATOS_DEL_JUEGO.md`).
La descompilación completa de Ghidra (5.750 funciones, 23 clases) y el APK original
se conservan en el espacio local `rea/blade_of_conquest/` del proyecto.
