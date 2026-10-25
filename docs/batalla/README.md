# batalla — el campo de batalla

> Índice de la carpeta. Regla de la casa (`docs/README.md`): solo se escribe lo aprobado;
> lo demás queda 🟡 y no se rellena inventando.

**Estado:** 7 de 7 documentos aprobados (2026-09-30).
El **diseño** del Pilar 6 ya está cerrado (`../VALCORIA_DEUDA_DE_SANGRE.md` §Pilar 6); aquí
falta lo que no se decidió en la conversación: **las reglas finas, las cifras y los escenarios**.

| Doc | Qué contendrá | Estado |
|---|---|---|
| [`00_REGLAS.md`](00_REGLAS.md) | El campo paso a paso: semi-tiempo real, moral, tú como unidad | ✅ aprobado |
| [`01_CIFRAS.md`](01_CIFRAS.md) | Los números: vida, daño, moral, tope de unidades | ✅ aprobado |
| [`02_TERRENO.md`](02_TERRENO.md) | Qué hace cada terreno dentro del campo | ✅ aprobado |
| [`03_IA_Y_ORDENES.md`](03_IA_Y_ORDENES.md) | La IA de tus tropas y del enemigo; las órdenes globales | ✅ aprobado |
| [`04_PRESENTACION.md`](04_PRESENTACION.md) | HUD, barra de órdenes, botones y cámara en 1.ª persona | ✅ aprobado |
| [`05_CATALOGO_DE_CAMPOS.md`](05_CATALOGO_DE_CAMPOS.md) | Los escenarios concretos que pueden abrirse | ✅ aprobado |
| [`06_BATALLAS_DE_LA_HISTORIA.md`](06_BATALLAS_DE_LA_HISTORIA.md) | Las batallas fijas de la trama (incluido el flashback del Paso) | ✅ aprobado |

**Regla técnica:** la simulación vivirá en `js/systems/*` **puro** (determinista, con RNG
inyectado); la escena solo dibuja y presenta (AGENTS.md).
