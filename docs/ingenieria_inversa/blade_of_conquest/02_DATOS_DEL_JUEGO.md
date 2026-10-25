# 02 · Datos del juego — inventario, cifrado y contenido legible — BoC v1.1.1

> Dossier de extracción de datos. Complementa a `01_ARQUITECTURA_DEL_APK.md` con lo aprendido
> al INTENTAR descifrar la base de datos y lo que de hecho ya es legible.

---

## 1. El hallazgo clave: el juego NUNCA lee los ZIP cifrados

Verificado de dos formas independientes sobre `libMyGame.so`:

1. **Escaneo completo de llamadas** (BL/BLX ARM + Thumb-2, 148.546 + 71.241 instrucciones de
   llamada decodificadas con mapeo de segmentos ELF correcto): **cero llamadas** a
   `AEZipUtility::unzipOpenFile`, `unzipFile`, `unzipFileToMemory`, `unzipTagFileToMemory` ni
   `unzOpenCurrentFilePassword`.
2. **Constantes ZipCrypto ausentes**: `0x12345678` y `0x08088405` (inicialización de claves del
   cifrado ZIP) no aparecen en ningún byte del binario — el minizip embebido fue compilado
   **sin soporte de criptografía**.

Consecuencia: los 18 ZIP con contraseña de `assets/datas/` son **restos del empaquetado del
desarrollador** (Kevin Tien los creaba en PC con `AEZipUtility::addFileToZip` y los subía con
la clave puesta; en el móvil nunca se abren). Por eso el ataque de diccionario contra la
contraseña era una calle sin salida: **la contraseña no existe en el binario**.

## 2. Los 5 ficheros que el juego SÍ lee

Referencias de cadena encontradas en `.rodata`:

| Fichero | Referencia en binario | Estado |
|---|---|---|
| `datas/mmi.dat` | `@0x00ae1589` (junto a claves `mp_id`, `mtype`) | ✅ XML plano — metadatos del mapa mundial |
| `datas/sitespos.dat` | (cargado vía `mmi.dat` §`site_pos_file`) | ✅ XML plano — posiciones de sitios |
| `datas/mesh1.dat` / `mesh2.dat` | (cargados vía `mmi.dat` §`mesh_file`) | ✅ ASCII — mallas de terreno |
| `datas/tips.dat` | `@0x00ada2b8` | ✅ XML plano — consejos EN/CN |
| `datas/sw.dat` | `@0x00ada7d7` (junto a `words_count=%d`) | ✅ texto GBK — **filtro de palabras censuradas** |
| `datas/pdl.dat` | `@0x00add7cc` (junto a `txt_pdl_thanks`) | ✅ XML plano — créditos |
| `datas/tmp_datas.dat` | `@0x00ada8b1` (junto a `1.2.8`, `r+b`, `%02x`) | ⚠️ blob de alta entropía — ver §4 |

## 3. `sw.dat` no es contenido de juego: es el filtro de censura

Decodificado como GBK: lista de **nombres políticos y personas reales** (毛泽东, 周恩来,
孙中山, 邓小平…) — el filtro que impide usar nombres sensibles al crear el héroe (requisito de
las tiendas chinas de 2016). Interesante para el dossier histórico; **sin valor de diseño**.

## 4. `tmp_datas.dat` — la pista del «caché temporal»

- 118.904 bytes de alta entropía (sin cabecera PK/zlib).
- El binario lo abre con modo **`r+b`** (lectura/escritura) y hay un `%02x` y una versión
  `1.2.8` en las cadenas contiguas — patrón de *caché binario que el juego genera y relee*.
- Hipótesis de trabajo: es un **caché** que el juego reconstruye; el contenido real (unidades,
  habilidades, economía) está **compilado dentro de `libMyGame.so`** (coherente con las cifras
  del .rodata: 568 KB de constantes + 202 KB de `.data.rel.ro`).
- Desencriptar los ZIP es por tanto **importante pero no urgente**: la data viva está en el
  binario y se extrae por descompilación (dossier 04).

## 5. Lo que ya sabemos del contenido por las cadenas (Rc.plist, 488 claves)

Vocabulario completo del juego agrupado por prefijo:

| Prefijo | Nº | Sistema |
|---|---|---|
| `cm_` | 234 | UI común (botones, títulos) |
| `txt_` | 76 | textos generales |
| `td_` | 54 | **encuentros en el mapa**: bandidos que piden oro (pagar/pelear/huir con éxito/fallo), bestias |
| `krl_` | 33 | unidades/roles |
| `sk_` | 16 | habilidades: **4 clases** (Combate, Magia, Divina, Disparo), activas/pasivas, rango `X/Y` |
| `talk_` | 10 | **retención de generales**: recompensar en oro / despedir; la lealtad se queja («quizá sea hora de irme») |
| `captalk_` | 10 | **cautivos**: persuadir / liberar / nada / matar; persuasión **1 intento por semana**; el ransom de un capturado llega por diplomacia |
| `dip_` | 6 | **diplomacia**: tributo, tregua, alianza, rescate de cautivo con oro |
| `slave_` | 5 | **venta de cautivos** al tratante |
| `persuade_` / `release_` | 3 | resultados de captación/liberación |
| `bs_` / `sg_` / `rs_` / `free_` / `dlorder_` / `map_` / `info_` | 37 | batalla, guardado, versión, descargas, mapa, info |

### El «árbol genealógico» de los sistemas de Valcoria

Estas cadenas demuestran que los sistemas estrella de Valcoria ya estaban **germinados** en BoC:

| BoC (2017) | Valcoria (diseño 2026) |
|---|---|
| `captalk_` persuadir/liberar/matar + rescate semanal | `sistemas/02_PRISIONEROS.md` (4 salidas) + canje |
| `talk_` recompensar/despedir a generales descontentos | `sistemas/10_LEALTAD_Y_DESERCION.md` |
| `dip_` tributo/tregua/alianza/rescate | Facciones con memoria de casa (`historia/05`) |
| `td_` bandidos y bestias en el mapa | Encargos y emboscadas (`misiones/`) |
| `WeeklyBudget` (escena) | Salarios diarios y renta (`sistemas/06_ECONOMIA.md`) |
| `TerritoryBox` (escena) | Conquista de sitios (`mundo/`) |
| Moral → daño (tips.dat) | Moral de campo (`batalla/01_CIFRAS.md` §5) |
| Lanza vs caballería (tips.dat) | Anti-clase por arma (batalla) |

## 6. Escenas de UI (22 ficheros `.csb`) — el flujo completo

HomeScene → SelectGame / CreateFile → FaceGenerator → CharactorScene → mundo →
PartyScene · BarracksScene · UpgradeUnit · InventoryScene · StoreScene · TradeScene ·
PrisonScene · TerritoryBox · TalentBox · SkillBox/SkillSelBox · WeeklyBudget · GiftBoxScene →
BattlePrepareScene → batalla → VictoryScene → CompletedRewards.

(+ `TestUI.csb` — residuo de desarrollo del propio Kevin Tien.)

## 7. Estado del descifrado de los ZIP (CERRADO — ver dossier 03)

- Contraseña NO está en el binario (verificado: 231.677 candidatos de strings del .so y del
  dex contra el ZipCrypto, 874 falsos positivos del check de cabecera, 0 reales).
- bkcrack (Biham-Kocher): **espacio agotado al 100 %** con las dos hipótesis de cabecera XML
  (con BOM y sin BOM) — claves no encontradas. El interior no es XML: son volcados binarios
  del editor PC del desarrollador.
- **Caso cerrado y documentado** (`03_ESTADO_DEL_DESCIFRADO.md`): los ZIP son residuos de
  build, el runtime nunca los lee, y la data viva está en el binario (dossier 04).
