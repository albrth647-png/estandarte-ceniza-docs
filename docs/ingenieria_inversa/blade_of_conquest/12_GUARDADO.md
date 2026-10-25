# 10 · GUARDADO Y DATOS DEL JUGADOR — Cómo BoC guarda tu partida

> Dossier 10. Lo visible del sistema de guardado antes del análisis Ghidra profundo
> (que se recoge en `13_CODIGO_NATIVO.md`). Enlaza con el contrato de guardado v1 de
> Valcoria (`docs/produccion/02_GUARDADO_Y_DATOS.md`).

## 1. Qué sabemos del guardado de BoC

| Pista | Fuente | Lectura |
|---|---|---|
| `UserDefault.xml` | strings del `.so` (uso estándar de Cocos) | preferencias ligeras (opciones, último slot) en XML del sandbox de la app |
| `AECityScene::onCtlCmdsPanelSaveGame` | símbolo | guardar desde el panel de comandos **estando en ciudad** |
| `AESandTableScene::onCtlCmdsPanelSaveGame` | símbolo | guardar desde el panel **estando en el mapa mundial** |
| `save_count` | string | contador de partidas guardadas |
| `cm_alert_savegame`, `cm_msg_savegame`, `txt_sys_savegame.png` | strings/atlases | UI de confirmación de guardado |
| `AECreateFileScene` (32), `AESelectGameScene` (27) | clases | creación de personaje y **selector de ranuras de partida** |

Conclusiones: guardado **manual en puntos concretos** (mapa/ciudad), múltiples ranuras
(escena de selección), estado del mundo serializado desde `AEPlayerData` (116 métodos —
el agregador de estado del jugador). No hay autosave visible salvo el contador.

## 2. Cómo Valcoria lo hará mejor (contrato ya escrito)

El diseño de Valcoria ya fija (ver `docs/produccion/02_GUARDADO_Y_DATOS.md`):
- `SAVE_VERSION = 1` **con el esquema demo completo desde el día uno** (nada de esquemas
  provisionales), migración documentada para versiones futuras.
- Guardado local (IndexedDB + exportación de fichero), autosave por capítulo + manual,
  y **texto de la Crónica dentro del save** — la partida guarda también su historia.
- Datos sensibles del mundo (memoria de capitanes) versionados con el mismo esquema.

## 3. Checklist de paridad con BoC

- [x] Múltiples ranuras con nombre (`AESelectGameScene` ↔ pantalla de partidas)
- [x] Guardar en mapa y en ciudad (mismos dos contextos)
- [x] Estado completo del mundo (reinos, lealtades, bandas, prosperidades)
- [x] Opciones separadas del save (`UserDefault` ↔ `localStorage` de opciones)
- [ ] Autosave — Valcoria añade lo que BoC no tenía
- [ ] Crónica en el save — añadido propio de Valcoria
