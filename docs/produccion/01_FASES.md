# 01 · Fases — el plan completo, de la demo al juego completo

**Estado:** ✅ **Aprobado por el dueño (2026-09-30). Reescrito completo el 2026-10-02** (enmienda
en `../DECISIONES.md`).

**Documentos que viven junto a este:**
- `00_ALCANCE.md` — **el alcance de la demo (Acto I, 2-3 h) y MANDA sobre todo lo demás.**
- **`PLAN_FASE1.md`** — **el plan de construcción de la Fase 1**: documentos, datos, código,
  costuras de test y gate de cada paso. **Aquí abajo solo está el resumen**; la ejecución vive allí.

> **La Fase 1 ES el Acto I de la demo, y se hace completo.** No se publica nada a medias ni se
> abre la Fase 2 con la demo coja. Las Fases 2-5 son la **continuación** hasta el juego completo.

---

## 1. Reglas del método (no se negocian)

1. **Una fase a la vez.** No se abre la siguiente hasta que la anterior cierra.
2. **Nada se construye sin su documento ✅.** Si la fase necesita un documento 🟡, primero se
   escribe y se aprueba (regla del dueño: documentos **completos y finales** y del **juego
   completo** — dentro de cada doc se marca qué entra en la demo y qué es continuación).
3. **Orden de trabajo dentro de la fase:** documento → datos → código → tests → documentación.
4. **Un bug ALTA bloquea avanzar** (`../BUGS.md`).
5. **Cada paso cierra con `npm run qa` en verde** (check + lint + validate + docs + tests con
   cobertura ≥ 90 % + humo) y con su **hito jugable** cumplido.
6. **El guardado nunca se rompe**: lo que toque `SaveState` actualiza migración y pruebas
   (`02_GUARDADO_Y_DATOS.md`).
7. **El fallo nunca atasca**: si un paso añade derrota, siempre hay salida.

---

# 2. FASE 1 — Acto I de la demo

**Qué es:** el **Acto I** de la demo entero, 2-3 horas, jugable de principio a fin: del cadalso al
giro de las páginas arrancadas. 6 sitios, 6 encargos, 3 batallas, 3 tipos de tropa, 3 familias
enemigas, 5 sistemas núcleo (memoria, Firma, prisioneros, favores, Crónica).

**Cierra cuando:** alguien ajeno al proyecto la juega 2-3 horas, entiende que **las deudas y la
memoria** son el juego, y no encuentra ni un atasco. Criterio completo en `00_ALCANCE.md` §6.

**Criterio de esta fase: la mejor impresión.** Reglas **I1..I7** en `PLAN_FASE1.md` §1 — *nada a
medias* · *el núcleo se ve* · *los 30 minutos cumplen* · *la promesa literal manda* ·
*presentación en cada paso* · *presupuesto de impresión* (60 fps, avisos ≤ 3 s, iconos ≥ 48 px) ·
*aspecto de película* (luz/niebla/paleta, cuerpos de proporción humana, retratos de los 16 clave).

### Los 8 pasos (resumen; el detalle está en `PLAN_FASE1.md`)

| Paso | Hito | Docs | Esfuerzo |
|---|---|---|---|
| **1.1** | Caminas en 1.ª persona, entras y sales de un sitio y **el juego guarda** | 7 | **M** |
| **1.2** | Un PNJ al que perdonas **te recuerda**; tu Firma sube o baja y **queda guardada** | 4 | **S** |
| **1.3** | Recorres los **6 sitios**, con viaje por días y encuentros | 9 | **M** |
| **1.4** | Ganas **rompiendo la moral**; tres huyen; esgrimes en 1.ª persona | 18 | **L** |
| **1.5** | Capturas a un capitán, lo **volteas**; si caes, **no te atascas** | 11 | **M** |
| **1.6** | La demo **se juega del cadalso al giro final**, con Registro simple | 18 | **L** |
| **1.7** | Demo presentable: **se ve, se oye y se siente** como juego | 10 | **M** |
| **1.8** | Alguien que no eres tú la descarga y juega **2-3 horas** | 11 | **S** |

**88 documentos** repartidos entre los 8 pasos (de los 97 de diseño); **9 diferidos** a las
Fases 2-5 (§3-§6). **Camino crítico: 1.1 → 1.4 → 1.6 → 1.8.**

Cada paso cierra con **`npm run qa` verde + hito jugable + presentación mínima**. Documentos, JSON,
`js/systems/*`, costuras de test y gates paso a paso: **`PLAN_FASE1.md` §2-§8**.

> **Al cerrar la Fase 1 (Acto I de la demo):** la demo queda congelada (solo bugs). Todo lo nuevo
> va a la Fase 2.

---

# 3. FASE 2 — Acto II: el libro de todos

- **Objetivo:** el reino grande: casas rivales, cobranzas largas y la investigación del Teniente.
- **Entra:** **Libro Mayor completo**, **cicatrices**, **mundo vivo** (hoy en la demo solo
  «apagado»), **minimapa**, **códice**, **logros**, capitanes y némesis con memoria completa,
  economía completa. **Ampliación de lo ya construido:** más sitios, más familias, más encargos.
- **Documentos diferidos a esta fase:** `../sistemas/07_CICATRICES.md` ·
  `../sistemas/09_TIEMPO_Y_MUNDO_VIVO.md` · `../interfaz/06_MINIMAPA.md` ·
  `../historia/09_CODEX_Y_BESTIARIO.md` · `../produccion/12_LOGROS_Y_ESTADISTICAS.md`.
- **Hito:** una partida larga en la que el mundo **se mueve sin ti** y tú puedes **leer tu libro**.
- **Riesgo:** la memoria completa dispara el guardado → subir «relevantes» con cuidado y probar
  los topes en partidas largas.

# 4. FASE 3 — Acto III: la deuda mayor

- **Objetivo:** el final que elige el jugador y sus consecuencias.
- **Hito:** los **tres finales** jugables (pagar / cobrar / quemar), con epílogo que cambia según
  tu Firma y tus Marcados.
- **Docs ✅:** `../historia/03_RECORRIDO.md` (asamblea, en su parte del Acto III) ·
  `../sistemas/11_DEUDAS_DEL_JUGADOR.md` (la asamblea; la deuda del Acto I ya está en la Fase 1).
- **Riesgo:** tres finales se comen el calendario → se escriben primero los cierres y luego los
  epílogos variables.

# 5. FASE 4 — Escalado a juego completo

- **Objetivo:** subir todo lo que la demo dejó fuera **sin rehacer nada**: **10+ por bando**,
  más mundo y más contenido.
- **Entra:** luto y moral, lealtad y deserción, supervivencia completa, clima y estaciones
  completos, monturas (Equitación), animales y criaturas, trampas completas, comidas completas,
  estandartes completos, recursos completos, más campos y más familias enemigas.
- **Documentos diferidos a esta fase:** `../sistemas/08_LUTO_Y_MORAL.md` ·
  `../sistemas/10_LEALTAD_Y_DESERCION.md` · `../contenido/08_ANIMALES_Y_CRIATURAS.md`
  (la decoración barata de aldea sí entra en la demo).
- **Hito:** partida de 10+ horas con 10+ unidades por bando y el guardado aún sano.
- **Riesgo:** el rendimiento con 10+ → simplificar campos y terrenos **antes** que bajar unidades.

# 6. FASE 5 — Horizontes y lanzamiento

- **Objetivo 1 — el juego no se acaba:** mejoras **duras** (que cambian cómo juegas, no solo
  números), capitanes generados que vuelven con sus casas, **campañas que rotan** reutilizando el
  reloj y —si el dueño lo aprueba— un reinicio voluntario con desbloqueo permanente
  (base: `../VISION_JUEGO_COMPLETO.md`).
- **Objetivo 2 — producto:** versión 1.0 **de pago único** en las plataformas, con guardados
  compatibles, changelog para el jugador y su parte legal.
- **Documentos diferidos a esta fase:** `../contenido/07_ARTEFACTOS.md` (en la demo solo los 2
  ítems de historia, como objetos corrientes de `../contenido/04_ITEMS_Y_EQUIPO.md`).
- **Hito:** tras terminar la historia, el mundo sigue ofreciendo deudas nuevas.

---

## 7. Verificación común a todos los pasos y fases

- **`npm run qa` en verde** (cobertura ≥ 90 %, validadores de datos, enlaces y humo en Chromium).
- **Hito jugable cumplido**: se juega lo que el paso promete (no vale «casi»).
- **Guardado**: guardar, cargar, migrar y slots funcionando; corrupto siempre respaldado.
- **Paridad ES/EN** y **cero enlaces rotos**.
- **Documento actualizado** en la misma tarea que cambia el diseño.
- **Presentación mínima por paso**: el paso nuevo tiene su aviso, su icono y su sonido.

---

## 8. Riesgos del calendario (y plan B)

| Riesgo | Cuándo se nota | Plan B |
|---|---|---|
| Los controles táctiles no convencen | 1.1 | Probar variantes de palanca y enfocar con pulgares reales antes de 1.2 |
| La memoria universal infla el guardado | 1.2 | Recortar **topes**, nunca la mecánica |
| El mapa crece sobre el alcance | 1.3 | Manda `00_ALCANCE`: **6 sitios** |
| El campo con 5-6 no se siente | 1.4 | Subir a 8 antes de 1.5; si aún no, reducir el campo |
| Rendimiento en móvil (60 fps) | 1.4 | Fusión de geometrías, LOD y pooling; simplificar terreno antes que bajar unidades |
| El guardado se rompe al subir de versión | 1.2 / 1.4 / 1.5 | `migrateSave()` probado en cada subida (regla 6) |
| Demasiadas decisiones post-batalla | 1.5 | Máximo **4** |
| El guion se desborda | 1.6 | Recortar secundario, no la columna vertebral |
| La demo pasa de 2-3 h | 1.6-1.7 | Cortar en el **giro** (ya fijado como final de la demo) |
| Pulir antes de que el bucle funcione | 1.7 | **Prohibido**: el pulido va después de 1.6 |
| El estilo de película pesa en un gama media | 1.7 | Gate de MB: si la primera escena no corre a 60 fps, se baja textura/resolución, **nunca la escena** |
| Publicar sin demostrar la promesa | 1.8 | Revisar `00_ALCANCE.md` §4 y pasar el playtest de `11_PLAYTEST_Y_BETA.md` |
| El escalado a 10+ rompe el rendimiento | Fase 4 | Simplificar campos antes que bajar unidades |
| Tres finales comien el calendario | Fase 3 | Cierres primero, epílogos variables después |

---

## 9. Qué documentos se **usan** antes de cada paso

> Antes decía «qué documentos se **escriben**»: los **97 documentos de diseño están ✅**. La lista
> completa por paso está en **`PLAN_FASE1.md` §2**; los JSON, en **§3**; los test, en **§5**.

| Antes de | Se necesita leído y aprobado |
|---|---|
| **1.1** | `PLAN_FASE1.md` §2 (fila 1.1) + `00_ALCANCE.md` + `02_GUARDADO_Y_DATOS.md` |
| **1.2** | fila 1.2 + `../PLAN_MIGRACION_3D.md` (capa de dibujo) |
| **1.3** | fila 1.3 |
| **1.4** | fila 1.4 + `../batalla/01_CIFRAS.md` (cifras cerradas) |
| **1.5** | fila 1.5 |
| **1.6** | fila 1.6 + `../historia/04_GUION.md` (claves cerradas) |
| **1.7** | fila 1.7 + `../arte/01_ASSETS.md` (estilo película, retratos y cuerpos; presupuesto 🟡 a revisar con la primera escena) |
| **1.8** | fila 1.8 + `04_QA.md` + `11_PLAYTEST_Y_BETA.md` |
| **Fases 2-5** | los 9 documentos diferidos + los ampliados de §3-§6 |

> **Regla de oro:** los documentos se escriben **uno o dos pasos antes** de la fase que los
> necesita. Ni antes (se quedan viejos), ni después (se improvisa). Hoy ya están todos escritos:
> esta regla protege el **orden de construcción**, no el de redacción.
