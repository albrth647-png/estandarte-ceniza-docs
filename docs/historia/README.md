# historia — la narrativa de Valcoria

> Carpeta de **la historia del juego**. Regla de la casa (`docs/README.md`): aquí solo se
> escribe lo que el **dueño aprueba**; todo lo demás está 🟡 y no se rellena inventando.

**Estado:** 10 de 10 documentos **aprobados** (9 el 2026-09-30 + 1 el 2026-10-01).

## Lo que la historia ya tiene decidido (de otros documentos)

- **El relato lo escriben los sistemas**: memoria universal (Pilar 5), La Firma (Pilar 7),
  la Crónica y la Deuda de Sangre (Pilar 3). La trama guionizada pone el **marco**;
  la partida de cada jugador escribe su historia dentro.
- **Motor de diálogo ya disponible**: `js/systems/dialogue.js` — nodos
  `habla / decision / une / batalla`, con condiciones sobre el guardado y efectos
  (oro, honor, moral, banderas, unir companero). Puro y testado.
- **Todo texto visible pasa por claves `txt_*` con paridad ES/EN** (cuesta ×2: la historia
  se dosifica, no se despilfarra).
- **1.ª persona y exploración libre**: la historia se cuenta caminando, hablando y leyendo
  (el mundo, la Crónica, las reacciones), no en cinemáticas.

## Documentos

| Doc | Qué contendrá | Estado |
|---|---|---|
| [`00_PREMISA.md`](00_PREMISA.md) | Logline, tema, el mundo de la Ordenanza, el eslogan y su encaje con el juego | ✅ aprobado |
| [`01_ESTRUCTURA.md`](01_ESTRUCTURA.md) | Prólogo, tres actos, flashbacks, giros y **los tres finales** | ✅ aprobado |
| [`02_PERSONAJES.md`](02_PERSONAJES.md) | Los 8: protagonista, viuda, Escribano Mayor, Altamir, el Teniente, los Marcados | ✅ aprobado |
| [`03_RECORRIDO.md`](03_RECORRIDO.md) | Cómo se cuenta en pantalla: primeros minutos, diálogo, Crónica, memoria | ✅ aprobado |
| [`04_GUION.md`](04_GUION.md) | Escenas y diálogos jugables con claves `txt_*` (árboles del motor) | ✅ aprobado |
| [`05_CASAS_Y_FACCIONES.md`](05_CASAS_Y_FACCIONES.md) | Casas, la otra ribera, los Escribanos: quién manda y qué quiere | ✅ aprobado |
| [`06_CRONOLOGIA.md`](06_CRONOLOGIA.md) | La línea de tiempo del mundo y de la partida | ✅ aprobado |
| [`07_LEYENDAS_Y_RUMORES.md`](07_LEYENDAS_Y_RUMORES.md) | Lo que la gente cree y lo que se dice de ti | ✅ aprobado |
| [`08_TEXTO_DEL_MUNDO.md`](08_TEXTO_DEL_MUNDO.md) | Carteles, inscripciones, cartas y coplas | ✅ aprobado |
| [`09_CODEX_Y_BESTIARIO.md`](09_CODEX_Y_BESTIARIO.md) | Códice de 5 secciones y bestiario, llenado por hecho | ✅ aprobado (2026-10-01) |

Nota: el bloque de **finales** quedó integrado en `01_ESTRUCTURA.md` (no lleva documento propio).
