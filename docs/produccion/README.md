# produccion — para que el juego salga vivo y a tiempo

> Índice de la carpeta. Regla de la casa (`docs/README.md`): solo se escribe lo aprobado;
> lo demás queda 🟡 y no se rellena inventando.

**Estado:** **13 de 13 documentos aprobados** (10 el 2026-09-30 + 3 el 2026-10-01).

| Doc | Qué contendrá | Estado |
|---|---|---|
| [`00_ALCANCE.md`](00_ALCANCE.md) | Qué entra en la primera versión jugable y qué espera | ✅ aprobado |
| [`01_FASES.md`](01_FASES.md) | Orden de implementación con hitos verificables | ✅ aprobado |
| [`02_GUARDADO_Y_DATOS.md`](02_GUARDADO_Y_DATOS.md) | `SaveState`, versionado, topes y JSON del juego | ✅ aprobado |
| [`03_RIESGOS.md`](03_RIESGOS.md) | Rendimiento, móvil, 5 MB, texto ×2, controles táctiles | ✅ aprobado |
| [`04_QA.md`](04_QA.md) | Plan de pruebas por sistema y umbrales | ✅ aprobado |
| [`05_MERCADO_Y_LANZAMIENTO.md`](05_MERCADO_Y_LANZAMIENTO.md) | Demo, precio y dónde se publica | ✅ aprobado |
| [`06_LEGAL_Y_AUTORIA.md`](06_LEGAL_Y_AUTORIA.md) | Licencias, fichas y derechos | ✅ aprobado |
| [`07_RELEASES_Y_VERSIONES.md`](07_RELEASES_Y_VERSIONES.md) | Numeración, entregas y compatibilidad de guardados | ✅ aprobado |
| [`08_PLATAFORMAS_Y_MINIMOS.md`](08_PLATAFORMAS_Y_MINIMOS.md) | Navegador, APK, escritorio y mínimos | ✅ aprobado |
| [`09_PRIVACIDAD_Y_DATOS.md`](09_PRIVACIDAD_Y_DATOS.md) | Qué se recoge (nada) y qué se declara | ✅ aprobado |
| [`10_BUILD_Y_FIRMA_APK.md`](10_BUILD_Y_FIRMA_APK.md) | Build y firma de la APK: keystore, secretos, tamaño | ✅ aprobado (2026-10-01) |
| [`11_PLAYTEST_Y_BETA.md`](11_PLAYTEST_Y_BETA.md) | Guion de prueba con gente y criterios de salida | ✅ aprobado (2026-10-01) |
| [`12_LOGROS_Y_ESTADISTICAS.md`](12_LOGROS_Y_ESTADISTICAS.md) | 12 logros, 14 estadísticas y export de la Crónica | ✅ aprobado (2026-10-01) |

**Planes de trabajo (no cuentan en los 13):**

| Plan | Qué es | Estado |
|---|---|---|
| [`PLAN_FASE1.md`](PLAN_FASE1.md) | **El plan de construcción de la Fase 1**: los 88 documentos, los JSON, `js/systems/*`, las costuras de test y el gate de cada paso | ✅ 2026-10-02 |
| [`../PLAN_MIGRACION_3D.md`](../PLAN_MIGRACION_3D.md) | La capa de dibujo (fases 0-6): escena, cámara, niebla, LOD, pooling y reserva 2D | ✅ 2026-10-02 |

**Lo que está previsto:** `npm run qa` (check + lint + validate + docs + test con cobertura ≥ 90 %
+ humo en Chromium), guardado versionado con migración y respaldo de corruptos, validadores de
datos, i18n con paridad ES/EN y un árbol del repo de 287 ficheros (46 de test).
