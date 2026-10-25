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
