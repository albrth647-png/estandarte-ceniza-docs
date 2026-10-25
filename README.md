# Valcoria — Deuda de Sangre · documentación de diseño

> **Qué es:** la documentación de diseño de **Valcoria — Deuda de Sangre** (nombre de
> trabajo cerrado), un **RPG medieval de supervivencia y memoria**, en **1.ª persona y tiempo
> real**, **móvil primero** (APK), sin mando y **100 % offline**.
>
> **El gancho:** «Cada enemigo se acuerda de ti. Y no todos mueren.»
>
> **Este repositorio contiene solo documentación.** El código del juego **aún no existe**:
> se escribirá aquí cuando el diseño esté aprobado y empiece la Fase 1
> (`docs/produccion/PLAN_FASE1.md`). Toda la documentación está escrita en clave
> **greenfield**: describe el juego que se va a construir, no un build previo.

---

## Por dónde empezar

1. [`docs/VALCORIA_DEUDA_DE_SANGRE.md`](docs/VALCORIA_DEUDA_DE_SANGRE.md) — **la idea del
   juego**: pilares, bucle, controles, memoria, mercado, riesgos y decisiones cerradas.
   Es el documento que manda.
2. [`docs/README.md`](docs/README.md) — el **índice completo** y la jerarquía en caso de
   conflicto entre documentos.
3. [`docs/PLAN_DOCUMENTOS.md`](docs/PLAN_DOCUMENTOS.md) — la **checklist del proyecto**
   completo, con casillas ✅/🟡 y el orden de trabajo.

---

## Estructura

| Ruta | Qué hay |
|---|---|
| `docs/` | **98 documentos de diseño aprobados** (la idea, la visión, las decisiones y las 9 áreas de diseño) más índices y documentos de trabajo |
| `AGENTS.md` | reglas de trabajo del proyecto (el contrato de ingeniería del futuro build) |
| `CHANGELOG.md` | historial de cambios de la documentación |

**Las 9 áreas de `docs/`** (cada una con su propio `README.md` como índice):

| Área | Contenido |
|---|---|
| `historia/` | premisa, estructura, actos, finales, personajes, códice y bestiario |
| `mundo/` | mapa, exploración, viajes, lugares, PNJ, clima y ciudades |
| `contenido/` | los catálogos jugables: tropas, enemigos, capitanes, ítems, mercado, habilidades… |
| `misiones/` | encargos, tablones, cadenas, rumores y pagos |
| `sistemas/` | memoria y deuda, prisioneros, favores, crónica, progresión, economía, luto |
| `batalla/` | reglas, cifras, terreno, IA y presentación del campo de batalla |
| `interfaz/` | controles, pantallas, HUD, tono/i18n, accesibilidad y tutorial |
| `arte/` | estilo visual, assets, audio, animaciones y efectos (100 % offline) |
| `produccion/` | alcance, fases, guardado, riesgos, QA, mercado, legal, build y playtest |

---

## Reglas del proyecto (resumen)

- **Lo pendiente va 🟡.** Nada se escribe como decidido si no lo está: no se rellena
  inventando.
- **Los números viven en un solo sitio**; el resto de documentos enlazan, no duplican.
- **Documentación actualizada en la misma tarea** que cambia el diseño.
- **Un documento de diseño no se escribe** hasta que el dueño aprueba su contenido.

El detalle está en [`docs/README.md`](docs/README.md) §«Reglas de mantenimiento».

---

## Estado

🟡 **Diseño cerrado en borrador completo, código por empezar.** Los 98 documentos de diseño
están escritos y aprobados (con 🟡 internos donde falta una cifra del dueño). **No existe
ningún código, ningún asset ni ningún build del juego**: la primera entrega será la demo del
Acto I («La Ceniza», `docs/produccion/00_ALCANCE.md`) y su plan de construcción está en
`docs/produccion/PLAN_FASE1.md`.

---

## Licencia

Contenido **propietario**. Sin licencia de uso: todos los derechos reservados.
