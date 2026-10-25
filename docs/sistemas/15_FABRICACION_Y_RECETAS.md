# 15 · Fabricación y recetas — lo que haces con tus manos

**Estado:** ✅ **aprobado por el dueño (2026-10-02). Documento final.**
**Enmienda 2026-10-02:** el dueño decide que **la profesión sube practicando la profesión**, que
**el maestro reparte encargos de oficio** y que **cada oficio fabrica cosas** (armas nuevas con
distintas apariencias, armaduras, anillos, amuletos). Este documento fija **XP de oficio, recetas,
materiales, rareza, coste y joyería**.

> **Qué es esto:** el hermano de `14_PROFESIONES.md`. Allí vive **qué** profesión es (ventajas,
> rangos, maestros). Aquí vive **qué fabricas con ella**: recetas, materiales, precio y resultado.
>
> **Regla dura:** fabricar **no rompe** la economía. El mercado sigue teniendo lo caro
> (`../contenido/05_RECURSOS_Y_MERCADO.md` §4) y el tope de daño de
> `../batalla/01_CIFRAS.md` §2 se respeta.

---

## 1. La regla del oficio

- **Solo el héroe fabrica** y **solo con su profesión activa**: la tropa y los compañeros compran o
  reparan, no entran en la cadena de oficio.
- **Se fabrica en el taller del sitio** (herrería, capilla, mercado, escribanía, refugio, establo):
  **cuesta oro** (§6) y **tarda 0 días de juego** — no hay espera real.
- **Aprender una profesión abre su recurso base en cualquier lugar** del mapa: no hace falta ir al
  maestro ni al otro extremo del reino para extraerlo (§3).
- **Fabricar da XP de oficio** y **cerrar un encargo de oficio también** (§2).

---

## 2. XP de oficio (la barra propia)

El oficio tiene **barra propia**, separada del nivel del héroe. **Los rangos los abre el XP de
oficio, no el nivel del héroe.**

| Fuente | XP de oficio |
|---|---|
| **Práctica en el mapa** (recolectar el recurso de la profesión) | **+5** |
| **Fabricar una pieza** | **+10** |
| **Encargo de oficio completado** (el del maestro, `../misiones/00_TIPOS_DE_ENCARGO.md` §1) | **+40** |

| Rango | XP de oficio acumulado | Techo de rareza de lo fabricado |
|---|---|---|
| **Aprendiz** | **0** | **común** |
| **Oficial** | **150** | **buena** |
| **Maestro** | **450** | **rara** |

- **El rango no depende del nivel del héroe**: cambia lo que se había aprobado (niveles 6/24/48) en
  `14_PROFESIONES.md` §2. El nivel del héroe **no abre ni cierra** oficios.
- **Cambiar de profesión** sigue costando **3 días de oficio** (`14_PROFESIONES.md` §1). La barra de
  la profesión que dejas **se pierde** (no hay dos barras): por eso volver cuesta.
- **Olvidar una rama** da **oro + 1 día** en la escribanía (decisión 8-B,
  `14_PROFESIONES.md` §3).

---

## 3. Materiales: dos niveles por recurso

- **Recurso de nivel 1 → desde el nivel 1 del héroe**, en cuanto aprendes la profesión. Son los
  **7 recursos** actuales (`../contenido/05_RECURSOS_Y_MERCADO.md` §1).
- **Recurso de nivel 2 → desde el nivel 30 del héroe**. Son los **4 nuevos** de la tabla.
- **A partir del nivel 30**, el recurso de nivel 1 **rinde +50 %**.

| id | Recurso de nivel 2 | De dónde sale | Para qué | Precio base |
|---|---|---|---|---|
| `plata` | **Plata** | Vetas de plata de la Serranía y los Altos | Joyas, hebillas, varillas | **15 oro** |
| `piedra` | **Piedra tallada** | Canteras y rocas (`../mundo/07_PROPS_Y_VEGETACION.md`) | Moldes, percutores y piedras de afilar | **4 oro** |
| `cuerda` | **Cuerda** | Cáñamo de los prados y riberas | Ataduras, arreos (`../contenido/13_MONTURAS_Y_TRANSPORTE.md`) | **5 oro** |
| `resina` | **Resina** | Pinos y tocones resinados | Pegamento de mango y de adorno | **6 oro** |

- **Total: 11 recursos** (7 de nivel 1 + 4 de nivel 2) ✅ (`05_RECURSOS_Y_MERCADO.md` §1).
- **Cada uno tiene su yacimiento en el mapa** (`../mundo/03_LUGARES.md` §2) y su prop recolectable;
  el validador (regla 5) cruza `recursos.json` ↔ `props.json` ↔ `lugares.json`.
- **Los 4 nuevos no se compran en la aldea**: solo en mercado de ciudad
  (`05_RECURSOS_Y_MERCADO.md` §4).

---

## 4. Cómo se fabrica (rareza, coste y tiempo)

1. En el taller del sitio eliges **receta** desbloqueada (§5) y **cuánto material extra** echas.
2. **El rango pone el techo de rareza; los materiales deciden si llegas.**
3. **El coste en oro es el que pone la receta** (§6). No hay porcentaje automático.
4. Sale **0 días de juego**: la acción es inmediata.

| Rango | Rareza alcanzable | Ajuste de stats | Mejoras | Material extra para llegar |
|---|---|---|---|---|
| **Aprendiz** | **común** | ×1,00 | **ninguna** | los mínimos de la receta |
| **Oficial** | **buena** | ×1,10 | **+1** | **+1** unidad del material principal |
| **Maestro** | **rara** | ×1,25 | **+1** | **+2** unidades del material principal |

- **Ejemplo (`r_anillo_hierro`, material `hierro ×2`):** con rango **Aprendiz** sale **común** (+1
  ataque, sin mejora). Con rango **Oficial** y `hierro ×3` sale **buena** (+1 ataque, +1 mejora).
  Con rango **Maestro** y `hierro ×4` sale **rara** (+1 ataque, +1 mejora).
- **Lo `nombrada` no se fabrica**: se compra, se saquea o viene con la trama
  (`../contenido/07_ARTEFACTOS.md`). Ningún oficio da pieza única.
- **El tope de daño (90 / 45)** se comprueba **después** de aplicar rareza, mejora y escalado por
  nivel (`../batalla/01_CIFRAS.md` §2). Verificable en `tests/recetas.test.js`.

---

## 5. Recetas: 9 por profesión

- **3 recetas al aprender** + **3 por rango** que subas → **9 por profesión**.
- **7 profesiones × 9 = 63 recetas** en el juego completo.
- **Receta** = `{ id, profesion, item, cantidad, coste_oro, materiales[], extra_por_rango, nivel_min }`.
- **Cada encargo del maestro trae 1 receta** que se desbloquea al cerrarlo (§9): los 9 encargos y
  las 9 recetas son la misma cuenta.

| Profesión | Receta base (3) | +3 al ser Oficial | +3 al ser Maestro |
|---|---|---|---|
| **Herrero** | 2 armas nuevas + 1 anillo | 2 armas nuevas + 1 armadura | 1 amuleto + 1 anillo + 1 armadura |
| **Sanador** | 1 venda + 1 ungüento + 1 tintura | 3 curas mayores | 3 antídotos y elaboraciones |
| **Guía** | 1 señal + 1 cebo + 1 cuerda guía | 3 herramientas de campo | 3 trampas y mapas |
| **Escribano** | 1 carta + 1 copia + 1 sello | 3 documentos oficiales | 3 contratos y actas |
| **Tratante** | 1 ración + 1 saco + 1 fardo | 3 arneses de carga | 3 paquetes de viaje |
| **Cazador** | 1 cebo + 1 ogual + 1 preparativo | 3 señuelos | 3 trampas de caza |

> **Nota de alcance:** la **tabla de arriba fija el reparto** (3 + 3 + 3, qué tipo de pieza entra en
> cada tramo). Los **nombres y el coste exacto** de las 63 recetas son **datos** y entran uno a uno
> en `data/recetas.json` **con su test** al implementarse (regla 5); aquí no se inventan.
> La tabla completa de §6 fija los **rangos de precio** por tipo de pieza.

---

## 6. Coste en oro de las recetas

- **Cada receta trae su precio en la propia receta** (decisión 2026-10-02). No es un porcentaje del
  precio del ítem: se balancea pieza a pieza y el validador lo cruza contra `precio_base` de
  `../contenido/04_ITEMS_Y_EQUIPO.md` §6.

| Tipo de pieza | Coste en oro | Nota |
|---|---|---|
| **Arma nueva** (herrero) | **40-60** | Materiales aparte |
| **Armadura o escudo** (herrero) | **30-50** | Rehacer una pieza de `04_ITEMS` §3.2 |
| **Joya** (anillo o amuleto) | **25-40** | Con su material principal |
| **Consumible de Sanador** | **8-15** | Venda, ungüento, tintura |
| **Herramienta de Guía** | **10-20** | Señal, cebo, cuerda |
| **Documento de Escribano** | **5-12** | Carta, copia, sello |
| **Envolvente de Tratante** | **10-18** | Ración, saco, fardo |
| **Pieza de Cazador** | **8-16** | Cebo, señuelo, preparativo |

---

## 7. Armas nuevas y apariencias

- **4 armas nuevas**, cada una con **3 apariencias distintas** → **12 modelos**. Al fabricar, el
  juego elige **una de las 3** (RNG sembrado, determinista).
- **Son armas nuevas, no las 8 del catálogo** de `../contenido/04_ITEMS_Y_EQUIPO.md` §3.1. Las del
  catálogo **siguen siendo solo de mercado o botín**; el herrero fabrica **estas cuatro**.

| id | Arma nueva | Rol | Alcance | Ataque base | Apariencias |
|---|---|---|---|---|---|
| `w_martillo` | **Martillo de guerra** | Línea | 2,5 m | 17 | 3 |
| `w_alabarda` | **Alabarda** | Línea | 3,5 m | 15 | 3 |
| `w_hoz` | **Hoz de guerra** | Línea | 2,0 m | 13 | 3 |
| `w_mandoble` | **Mandoble** | Línea | 2,5 m | 19 | 3 |

- **Los ataques base** están **dentro del rango del catálogo** (11-19): no rompen
  `../batalla/01_CIFRAS.md` §3.
- **Las apariencias son solo arte**: no cambian stats, alcance ni cadencia.
- Los **12 modelos** entran **dentro del presupuesto de 100 MB** de la demo
  (`../produccion/10_BUILD_Y_FIRMA_APK.md` §5, decisión 2026-10-02).

---

## 8. Joyas: dos anillos y un amuleto

- **2 ranuras de anillo** (`anillo_1`, `anillo_2`) y **1 ranura de amuleto** (`amuleto`). Los anillos
  son intercambiables entre sí; el amuleto cuelga del cuello.

| id | Joya | Material | Efecto |
|---|---|---|---|
| `j_anillo_hierro` | Anillo de hierro | `hierro ×2` | **+1 ataque** |
| `j_anillo_plata` | Anillo de plata | `plata ×2` | **+2 ataque** |
| `j_anillo_cuero` | Anillo de cuero | `cuero ×3` | **+1 defensa** |
| `j_anillo_piedra` | Anillo de piedra tallada | `piedra ×3` | **+2 defensa** |
| `j_amuleto_vida` | Amuleto de vida | `hierbas ×3` + `cuero ×1` | **+10 vida** |
| `j_amuleto_coraje` | Amuleto de coraje | `cuero ×4` | **+5 vida** |
| `j_amuleto_piedra` | Amuleto de piedra | `piedra ×2` + `resina ×1` | **+1 defensa** |
| `j_amuleto_plata` | Amuleto de plata | `plata ×2` + `cuerda ×1` | **+1 ataque** |

- **Son 8 piezas y todas son de la herrería** (§5).
- **Los efectos son pequeños y no hay daño directo**: entran en la mitigación normal
  (`../batalla/01_CIFRAS.md` §2), no hay golpe extra.
- **Verificación obligatoria:** anillo de plata (+2) + arma `rara` +1 en nivel 30 no puede pasar de
  **90 de daño por golpe**. Es un test de borde de `tests/recetas.test.js`.

---

## 9. Encargos de oficio (la clase 11)

- **`oficio` es una clase de encargo nueva** (`../misiones/00_TIPOS_DE_ENCARGO.md` §1): la reparte
  **el maestro** de la profesión, no el tablón. **3 encargos por rango**, 9 en total.
- **Pagan en XP de oficio** (**+40**) **+ oro**, no en XP del héroe
  (`12_NIVELES_DEL_HEROE.md` §2.1).

| Rango | Encargos del maestro | XP de oficio | Oro |
|---|---|---|---|
| **Aprendiz** | 3 (para llegar a Oficial) | **+40** cada uno | **20-40** |
| **Oficial** | 3 (para llegar a Maestro) | **+40** cada uno | **40-60** |
| **Maestro** | 3 (las mejores piezas) | **+40** cada uno | **60-90** |

- **Son encargos normales** (`../misiones/02_ESTRUCTURA_DE_ENCARGO.md`): plazo, fallo, testigos y
  memoria. **Fallo blando** si se pasa el plazo; **nunca bloquea** (Pilar 3).
- **Cada encargo trae 1 receta** que se desbloquea al cerrarlo (§5).

---

## 10. Datos, tipos y validación

- **Datos:**
  - `data/profesiones.json` — `{ id, rangos, maestro, recurso, xp_por_rango }`
  - `data/recetas.json` (nuevo) — `{ id, profesion, item, cantidad, coste_oro, materiales[],
    extra_por_rango, nivel_min }`
  - `data/recursos.json` sube a **11** (`../contenido/05_RECURSOS_Y_MERCADO.md` §1).
  - `data/items.json` suma el tipo `joya` y las 4 armas nuevas (`04_ITEMS_Y_EQUIPO.md` §3).
- **Tipos:** `Receta`, `MaterialReceta` y `Joya` en `js/data/game_types.js` (una sola vez, regla 4).
- **Validación (regla 5):** cada fila de `recetas.json` cruza su `item` con `items.json`, sus
  `materiales` con `recursos.json` y su `profesion` con `profesiones.json` (rango alcanzado);
  `tools/validate_data.js` falla si algo no cuadra.
- **Sistema puro:** `js/systems/fabricacion.js` — rareza, coste, mejora y carga; sin DOM, sin reloj,
  RNG inyectado.
- **Guardado:** `SaveState.profesion = { id, rango, xp, recetas: [] }` → **SAVE_VERSION 4**
  (`../produccion/02_GUARDADO_Y_DATOS.md`); `migrateSave()` rellena vacío.
- **Tests:** `tests/recetas.test.js` y `tests/profesiones.test.js`, mínimo 3 casos (normal, borde,
  error): sin material suficiente no se fabrica; el rango pone el techo de rareza; una receta con
  material inexistente se rechaza; el daño de una joya respeta el tope 90/45.

---

## 11. Cifras que fija este documento

| Cifra | Valor |
|---|---|
| XP de oficio por práctica en el mapa | **+5** |
| XP de oficio por fabricar | **+10** |
| XP de oficio por encargo del maestro | **+40** |
| Umbrales de rango | **150** (Oficial) · **450** (Maestro) |
| Recursos | **11** (7 de nivel 1 + **4 de nivel 2 desde el nivel 30**) |
| Recetas | **9 por profesión** (3 + 3 + 3) → **63** |
| Techo de rareza por rango | común → buena → **rara** |
| Mejoras de lo fabricado | **+1** como mucho |
| Coste en oro | el de cada receta (§6) |
| Armas nuevas | **4** × **3 apariencias** = **12 modelos** |
| Ranuras de joya | **2 anillos + 1 amuleto** |
| Piezas de joya | **8** |
| Taller | el del sitio · cuesta oro · **0 días** |
| Encargos de oficio | clase **11** · **9** en total (3 por rango) |

---

## 12. Qué entra en la demo (Fase 1) — y qué sigue

> **Hasta aquí la demo.** Una profesión (la del origen) en **Aprendiz**: sus **3 recetas base**, el
> recurso de nivel 1 recolectable en el mapa y el taller de Herreruela con **+1**
> (`../mundo/03_LUGARES.md` §2). La herrería sigue haciendo reparaciones. **Sin** joyería completa,
> **sin** armas nuevas, **sin** recursos de nivel 2 (nivel 30) y **sin** la clase `oficio` completa.

> **Y sigue el juego completo.** Las **6** del núcleo con sus 3 rangos y 9 recetas, la clase `oficio`
> con sus 9 encargos, los **4 recursos de nivel 2** desde el nivel 30, las **4 armas nuevas × 3
> apariencias**, la **joyería** completa y **Equitación** tras el Capítulo 1. Todo con **las mismas
> reglas**: crecer = más filas en `recetas.json`, no otro sistema.

---

## 13. Fuera de este documento

- Qué es una profesión y sus ventajas → `14_PROFESIONES.md`
- Niveles y XP del héroe → `12_NIVELES_DEL_HEROE.md`
- Catálogo base de armas y armaduras → `../contenido/04_ITEMS_Y_EQUIPO.md`
- Recursos y precios → `../contenido/05_RECURSOS_Y_MERCADO.md`
- Tope de daño y mitigación → `../batalla/01_CIFRAS.md`
- Las 11 clases de encargo → `../misiones/00_TIPOS_DE_ENCARGO.md`
- Pagos → `../misiones/04_PAGOS_Y_RECOMPENSAS.md`
- Piezas con historia → `../contenido/07_ARTEFACTOS.md`
- Presupuesto de APK → `../produccion/10_BUILD_Y_FIRMA_APK.md`
