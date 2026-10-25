# Pendientes — todo lo que sigue abierto (2026-10-02, tras las rondas 5 y 6)

**Estado:** 🧪 **documento de trabajo** (no es un documento de diseño y **no cuenta** en los 98).

> Qué es: el barrido de **lo que queda abierto (🟡)** después de cerrar, hasta el **2026-10-02**,
> todas las decisiones del dueño. Qué NO es: una lista inventada; solo lo que el propio diseño deja 🟡.
> La lista maestra vive en `DECISIONES.md` (§Pendientes).

---

## 1. Lo que sigue abierto

| # | Documento | Pendiente | Quién lo cierra |
|---|---|---|---|
| 1 | `batalla/01_CIFRAS.md` · `batalla/03` | **Cifras del campo** (moral hasta qué punto rompe, coste y aforo de recluta, qué hace cada terreno, reparto de 10+) | Fase 2 (opción B elegida) |
| 2 | `produccion/05` | URL final de la página y fecha de lanzamiento | Cuando exista |

> **Cerrados el 2026-10-01 (última ronda):** `hierbas` y `carne` como **recursos oficiales**
> (2-A → `hierbas` y `carne` son recursos oficiales (3 / 3 oro); con los 4 de nivel 2, el total llega a **11**), **Equitación** a **400 oro + 5 días** (3-B) y
> **los 7 documentos** de la lista (4-A → **ya redactados**: `produccion/10`, `11`, `12`,
> `interfaz/10`, `11`, `historia/09` y `COBERTURA_REQUISITOS.md`; el diseño sube a **98**).
> Todo lo demás quedó cerrado en las rondas anteriores (ver §3).

---

## 2. Cerrado en esta ronda (para que no se reabra)

| Decisión | Resultado |
|---|---|
| XP por fuente | ✅ encargo `20+4×zona` · enemigo `10+2×nivel` · capitán `60` · deuda `40/100` · tu deuda `120` |
| Escalado por nivel | ✅ **+5 % / +4 % / +3 %** (vida/ataque/defensa) |
| Atributos | ✅ **AGI** +0,5/s aliento y −1 Desvío cada 3 · **INT** +5 % XP y −2 % precio |
| Profesiones | ✅ núcleo de **6**; 1 activa; cambio **3 días**; **1 maestro por profesión repartido en las plazas**; rangos por **XP de oficio (150/450)** desde 2026-10-02 |
| Fabricación de oficios | ✅ XP de oficio propio; **63 recetas**; clase de encargo **11 `oficio`**; 4 armas nuevas ×3 apariencias; 8 joyas; taller del sitio (`sistemas/15_FABRICACION_Y_RECETAS.md`) |
| Casas y cuartos (rehenes) | ✅ **5 oro/día** de renta; **1 cuarto en la demo** (+ por zona después); **solo capitanes** se retienen; rédito **rescate ÷ 10/día** (tope 10); come 1 ración/día; campo `alquiler` del guardado (aditivo); el jugador **alquila**, no cobra peaje |
| Derivados | ✅ cada oficio declara su recurso y **el mapa lo trae**; validador cruza `profesiones.json` con los datos del mapa |
| Recursos de oficio | ✅ **2-A**: `hierbas` y `carne` → **recursos oficiales**; y **4 de nivel 2** (`plata`, `piedra`, `cuerda`, `resina`) desde el nivel 30 → **11 en total** (2026-10-02) |
| Precio de Equitación | ✅ **3-B**: **400 oro + 5 días de oficio** |
| Equitación | ✅ 7.ª profesión, **se compra tras el Capítulo 1**; el héroe va a pie en la demo |
| Vidas de Fase 4 | ✅ montado 80/100 · perro 35 · mercenario 55 · bestias 25/30/90/10 |
| Flashback del Paso | ✅ **escena recuerdo** (no jugable) |
| Criatura `cri_animas` | ✅ **4 unidades que matan** |
| Olvidar una rama | ✅ sí, **oro + 1 día** en la escribanía |
| Comida → lealtad | ✅ **Fase 4** |
| Compañeros | ✅ **4** (1 en la demo) |
| Canales | ✅ **web estática + APK local** (tiendas fuera) |
| Precio | ✅ **19 USDT (TRC20), pago único** |
| Edad | ✅ **16+** |
| Exploración | ✅ **«la mirada lleva»** |
| `strings_*` | ✅ el catálogo de claves se depura al cerrar esta ronda de diseño |
| Memoria y Firma | ✅ **cerrados** como están |

---

## 3. Lista maestra `DECISIONES.md` (hoy)

Abiertos: **1** (cifras del campo, Fase 2) y **2** (URL/fecha).
**Cerrados:** todo lo anterior, incluidos `hierbas`/`carne` (2-A), **Equitación 400 oro + 5 días**
(3-B), **los 7 documentos redactados** (4-A), **la fabricación de oficios** (ronda 5) y
**las casas y cuartos para rehenes** (ronda 6) → **98 docs**.

---

## 4. Marcadores 🟡 obsoletos — **limpiados (2026-10-01)**

Se quitaron **40** marcadores en **16 documentos** que citaban como «pendiente» a un documento ya
✅ (`contenido/00`, `contenido/01`, `sistemas/02`, `04`, `06`, `mundo/04`, `05`, `09`, `10`, `11`,
`misiones/01`, `03`, `04`, `historia/05`, `batalla/03`, `arte/00`). **Se conservan** los que marcan
un pendiente real (§1).

También se limpiaron **documentos base**:

- **`VALCORIA_DEUDA_DE_SANGRE.md` §10-§11** → reescritos: los 8 puntos ya vivían en `docs/` y el
  «próximo paso» ya no es el duelo 1v1 (superado 2026-09-30).
- **`VISION_JUEGO_COMPLETO.md` §1** → marcado como **histórico del primer juego**; su fila
  «Pendiente de la Fase 3» queda **⛔ no aplica**.
- **`DATOS.md`** → añadida la aclaración de qué está diseñado vs. qué falta por implementar.

---

## 5. Huecos aprobados (lista externa)

`ANALISIS_COBERTURA_DOCUMENTOS.md` §3 → **los 7 aprobados el 2026-10-01** y **dados de alta en
`PLAN_DOCUMENTOS.md`**: `produccion/10_BUILD_Y_FIRMA_APK.md` (Alta), `produccion/11_PLAYTEST_Y_BETA.md`,
`interfaz/10_TUTORIAL_Y_FIRST_RUN.md`, `historia/09_CODEX_Y_BESTIARIO.md`,
`produccion/12_LOGROS_Y_ESTADISTICAS.md`, `docs/COBERTURA_REQUISITOS.md`,
`interfaz/11_AVISOS_DE_CONTENIDO.md`.
