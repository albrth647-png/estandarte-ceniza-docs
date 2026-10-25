# 03 · Estado final del descifrado de los ZIP — registro del ataque

> Registro completo del intento de descifrado de los 18 ZIP con contraseña de
> `assets/datas/`. Resultado: **no descifrables con las vías disponibles y, a efectos del
> proyecto, irrelevantes** — el binario del juego nunca los lee (ver dossier 02 §1-§2).

---

## 1. Qué se intentó y en qué orden

| # | Vía | Resultado |
|---|---|---|
| 1 | Diccionario de contraseñas (20 candidatos obvios: paquete, email del estudio, cocos2dx…) | ❌ nada |
| 2 | Caza de la contraseña en `libMyGame.so` (Ghidra: xrefs de `unzOpenCurrentFilePassword`) | ❌ **cero llamadores** — el juego no llama nunca a las funciones de unzip (ARM + Thumb-2, binario completo) |
| 3 | Diccionario total: 231.677 candidatos (todas las cadenas ASCII 4-24 del .so y del DEX + variantes), validación por check-byte ZipCrypto | 874 falsos positivos (tasa esperada 1/256), **0 reales** (validación CRC con descompresión) |
| 4 | Constantes ZipCrypto (`0x12345678`, `0x08088405`) en el binario | ❌ ausentes — minizip compilado sin criptografía: **el binario no puede descifrar ZipCrypto ni siquiera si quisiera** |
| 5 | bkcrack (Biham-Kocher, texto plano conocido) — hipótesis XML **con BOM**: `EF BB BF <?xml version="1.0"?>\r\n<ROOT>\r\n\t` (35 bytes) | Espacio agotado al 100 % (278.848 valores Z) → **claves no encontradas** |
| 6 | bkcrack — hipótesis XML **sin BOM**: `<?xml version="1.0"?>\r\n<ROOT>\r\n\t` (32 bytes) | Espacio agotado al 100 % (317.754 valores Z, reanudado con `--continue-attack` en 6 trozos) → **claves no encontradas** |

## 2. Conclusión técnica

- El contenido interior de los ZIP **no es XML con los prologs del juego**. Lo más probable:
  volcados binarios del editor PC de Kevin Tien (el mismo que produce `mesh1.dat` ASCII).
- Sin texto plano conocido (mínimo 8 contiguos + 12 totales para Biham-Kocher), ZipCrypto con
  contraseña aleatoria es indescifrable en la práctica. Ataque por fuerza bruta pura:
  inviable (2^128 del estado interno; el check-byte da solo 8 bits por fichero).
- Los ZIP eran **contenedores de trabajo del desarrollador** (creados con
  `AEZipUtility::addFileToZip`/`addFileToZipWithMemory` en el PC de build), subidos al APK
  como residuo. La contraseña vivía en la máquina de build, no en el juego.

## 3. Por qué no importa (para Valcoria)

1. **El runtime no los lee** (dossier 02 §1): la data viva del juego está compilada dentro de
   `libMyGame.so` y en los 5 ficheros legibles (`mmi`, `sitespos`, `mesh1/2`, `tips`, `sw`, `pdl`).
2. Las **cifras de gameplay** (unidades, habilidades, economía) se extraen por descompilación
   de las funciones que las consumen — dossier 04.
3. Las **cadenas de UI y mecánicas** ya están extraídas al 100 % vía `Rc.plist` (488 claves) —
   dossier 02 §5, con el mapa de linaje BoC → Valcoria.
4. Coste/beneficio: cada fichero ZIP exigiría ~35 min de ataque sin garantía (sin texto plano).
   El valor histórico no justifica las horas de cómputo.

## 4. Referencias técnicas del proceso

- bkcrack 1.8.1 (kimci86/bkcrack), ataque de texto plano conocido sobre ZipCrypto.
- `--continue-attack <n>` permite reanudar un ataque interrumpido (punto = índice del valor Z[6]).
- Ranuras de reanudación usadas: 0→144620→278848 (con BOM); 0→72038→143728→150000→223665→
  287132→296558→304317→317754 (sin BOM).
- Escáner propio de llamadas BL/BLX ARM+Thumb-2 en Python (`scripts/blscan.py`) tras corregir
  la endianidad de decodificación ARM y el mapeo de segmentos PT_LOAD del ELF.
- El APK completo y sus herramientas de análisis viven fuera del repo (`rea_targets/`).
