# Fase B — Tabla de decisiones: qué se revive, qué se transforma, qué se sustituye

> Entregable de la Fase B pedida por el dueño: cruzar **juego real (BoC) ↔ documentación
> Valcoria ↔ referencias** y dejar en una tabla qué tomamos de cada uno.
> Basada en: inventario de Fase A (`fase_A_inventario_referencias.md`), anatomía BoC
> (dossiers 00–11 de esta carpeta) y las 98 fichas del repo.
> **Cada fila con 💬 es una decisión que el dueño debe confirmar.**

## 1. El esqueleto: Blade of Conquest, sistema por sistema

| # | Sistema de BoC | Veredicto | Cómo queda en Valcoria | Dónde se decide/define |
|---|---|---|---|---|
| 1 | Mundo por sectores (5×5 TMX + grafo de 209 nodos) | **Revive mejorado** | misma estructura de sectores+grafo, render WebGL con paralaje/día-noche/nombres, niebla de guerra | `02_MAPA_MUNDIAL.md` §7 |
| 2 | 88 sitios de 9 tipos, jerarquía aldea→castillo (`belong`) | **Revive igual mejorado** | misma taxonomía en JSON; vistas de sitio con vida | `03_POBLADOS_Y_CONSTRUCCION.md` §5 |
| 3 | Prosperidad + defensa por sitio, inversión en 3 pilares | **Revive igual mejorado** | mismos dos números + memoria de eventos y liquidación explicada | `03` §5, `08_ECONOMIA` §5 |
| 4 | Construcción: solo torres en huecos (3/2) | 💬 **Decisión abierta** | (a) conservar torres como construcción ligera; (b) ampliar a capa "obra" estilo AoE-lite; (c) nada de construcción | abajo §3 |
| 5 | 23 tropas, árbol `pre_unit`, `base + growth×nv` | **Revive igual mejorado** | mismo árbol y fórmula, JSON versionado, veteranía por actos | `04_UNIDADES_TROPAS.md` §5 |
| 6 | 32 skills (4 escuelas, ramas 5+5+3, prerrequisitos OR) | **Revive transformado** | mismos árboles con recurso **aliento** (no mana) y desbloqueos narrativos | `05_HABILIDADES_TALENTOS.md` §4 |
| 7 | 17 talentos por atributo | **Revive igual mejorado** | mismos perfiles ligados a Deuda y capitanes | `05` §2 |
| 8 | Personajes con STR/AGI/INT, lealtad 75–100, honor | **Revive transformado** | mismos stats + **capitanes con memoria** (lazos, rencores, deudas) | `06_PERSONAJES_Y_REINOS.md` §4 |
| 9 | Reinos con rey/vasallos/sitios en `init_datas` | **Revive igual mejorado** | mismo arranque declarativo JSON | `06` |
| 10 | Batalla: formaciones 20 huecos, órdenes, héroe controlado, auto-batalla | **Revive mejorado** | idéntico esqueleto + vista 1.ª persona, pausa táctica, informe de Crónica | `07_BATALLA.md` §5 |
| 11 | Fórmula de daño `atk_ef −2×def`, suelo 25 %, crit ×1,0–1,5, var ±10 %, bloqueo anula | **Revive con ajuste** | misma fórmula con bloqueo que mitiga y penetración explícita, constantes publicadas | `11_CODIGO_NATIVO.md` §1, §7 |
| 12 | Bandas errantes: respawn `rs_time`, patrulla, botín anidado | **Revive igual mejorado** | igual + cabecillas con nombre y memoria | `09_ENEMIGOS_Y_RESPAWN.md` §3 |
| 13 | Economía: botín 2 niveles, mercados por probabilidad, presupuesto semanal por personaje | **Revive mejorado** | mismos flujos + precios vivos + liquidación explicada; **sin IAP** | `08_ECONOMIA_Y_COMERCIO.md` §5 |
| 14 | Guardado clave-valor plano + puntos de guardado | **Revive transformado** | esquema versionado `SAVE_VERSION=1`, autosave, Crónica dentro del save | `10_GUARDADO.md` §2 |
| 15 | Prisioneros (`AEPrisonBox`), honor, mercader de esclavos | **Revive transformado** | captura y rescates con coste moral narrativo (decisión de tono del dueño) | `docs/contenido/` |
| 16 | Monetización (IAP `sl.dat`, AdMob, Umeng, anti-cheat) | **Se sustituye** | fuera; solo tienda local de comercio y telemetría local opcional | `01_TECNOLOGIA` §7 |

## 2. Las referencias: qué tomamos de cada juego (Fase A)

| Juego | Qué tomamos | Qué NO tomamos | Ficha base |
|---|---|---|---|
| **Blade of Conquest** (ancla) | el esqueleto completo: mundo por sectores, sitios, tropas con árbol, batalla en tiempo real con héroe, bandas con respawn, economía semanal, torres, deudas (`player_debts`) | sus assets, su código, su monetización, su UI de 2017 | dossiers 00–11 |
| **Mount & Blade Warband/Bannerlord** | "una hueste y un mapa vivo", reclutar/mejorar, prisioneros, señores con memoria | escala de simulación política completa (KK governorship) | VISION §2.1 |
| **Kenshi** | empezar débil y sin nombre, mundo que no te debe nada | Letrística de muertes permanentes en masa | VISION §2.1 |
| **Battle Brothers** | hermandad con nombres y cicatrices, contratos, fragilidad | estética ploma (Valcoria va colorida) | VISION §2.1 |
| **Starsector** | progresión por flota=hueste, mundo abierto con facciones | gravedad de inventario | VISION §2.1 |
| **CK3** | lealtad, intriga, rasgos que cuentan historias | profundidad de dinastías full | VISION §2.1 |
| **Total War** | legibilidad del choque de masas | gestión de ciudades en batalla | VISION §2.1 |
| **Dwarf Fortress** | simulación que genera historias | complejidad sin filtro | VISION §2.1 |
| **RimWorld** | tribulaciones narrativas de personajes | curación por "incidentes" | VISION §2.1 |
| **Melvor Idle / Tideward / NGU** | progreso offline legítimo (colas que avanzan al volver) | idle puro como género | VISION §2.1, `docs/sistemas/` |
| **Elden Ring / Diablo / PoE** | NG+ / ascensión con carries decididos | farmeo infinito como meta | VISION §2.1, cap 24 h |
| **WoW / FFXIV / ESO** | lección: 400 h de mundo contenido; zonas memorables | MMO (nada online) | VISION §2.1 |
| **Shadow of Mordor/War** (huérfana #1) | el MODELO de capitanes con memoria — cita explícita de la patente en VISION; solo modelo conceptual, sin mecánicas cubiertas por patente (11-ago-2036) | Nemesis System literal | VISION 108–110, 174, 240; `docs/contenido/02_CAPITANES_Y_NEMESIS.md` |
| **Destiny / The Division** (huérfanas 2–3) | anti-patrón: cómo NO escalar el endgame | loot shooter | VISION 169 |
| **KayKit + packs** (huérfanas técnicas) | assets base CC0 de prototipo (reserva) | como identidad visual final | `art/`, THIRD_PARTY |

**Conclusión de coherencia:** no hay contradicciones entre referencias y esqueleto —
BoC aporta la estructura, las familias aportan la dirección de mejora. Las 3 huérfanas
se integran en la tabla (recomendación: citarlas en VISION §2.1 en la próxima revisión).

## 3. Decisión abierta: construcción (legado del pitch con Age of Empires)

El pitch original hablaba de "niveles de construcción estilo Age of Empires", pero
**ni BoC tiene base-building** (solo torres en huecos) **ni el repo menciona AoE nunca**
(0 resultados en las 98 fichas — verificado en Fase A). Opciones:

| Opción | Qué significa | Coste | Recomendado |
|---|---|---|---|
| (a) Torres puras (fidelidad BoC) | invertir oro en hasta 3/2 torres por sitio | mínimo | ✔ para la **demo** |
| (b) AoE-lite | añadir 2–3 edificios por sitio (granja/mercado/muralla) con efectos en prosperidad/defensa | medio | ✔ para **post-demo** (encaja con prosperidad/defensa ya existentes) |
| (c) AoE completo | construcción libre por tile | alto | ✘ contradice la escala móvil y la visión actual |

**Recomendación registrada**: (a) en la demo, (b) como evolución natural documentada en
`docs/sistemas/` cuando la demo esté verde. Pendiente de la palabra del dueño.

## 4. Próximos pasos

1. El dueño valida esta tabla (sobre todo filas 4, 11 y §3).
2. Con la validación, Fase D: guías "cómo se construye cada cosa, pero mejor" en
   `docs/nueva_ingenieria/` y push final.
