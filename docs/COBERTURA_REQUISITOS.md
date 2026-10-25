# Cobertura de requisitos — requisito ↔ documento ↔ test

**Estado:** ✅ **aprobado por el dueño (2026-10-01, ronda 4-A). Documento final.**

**🧪 También es el índice de trazabilidad:** cada regla dura, cada requisito no funcional y cada
decisión fuerte apunta a **dónde está escrito** y a **cómo se comprueba**. Si una fila no tiene
destino, el proyecto tiene un hueco; si el destino no existe, esta tabla se corrige el mismo día.

> **Cómo se lee:** *Requisito → Dónde se diseña → Cómo se verifica*. «Verificación» = comando de
> `npm run qa` o test de `tests/`. **Este documento no inventa requisitos:** son los de
> `../AGENTS.md`, de `VALCORIA_DEUDA_DE_SANGRE.md` y de los propios documentos enlazados.

---

## 1. Reglas duras de `AGENTS.md` (11)

| # | Regla | Dónde se diseña | Cómo se verifica |
|---|---|---|---|
| 1 | `js/**` solo globals de navegador | `produccion/08_PLATAFORMAS_Y_MINIMOS.md` | `npm run lint` (sin `process`/`require`) |
| 2 | Sistemas puros (sin DOM/reloj/fetch) | `batalla/00_REGLAS.md` §10 + cada doc con su «sistema puro» | `npm run lint` + `tests/*` por sistema |
| 3 | Rutas relativas `data/*.json` | `produccion/08_PLATAFORMAS_Y_MINIMOS.md` §5 | `npm run lint` + `npm run validate` |
| 4 | Tipos una sola vez (`game_types.js`) | `produccion/02_GUARDADO_Y_DATOS.md` | `npm run check` (tsc estricto) |
| 5 | Datos validados o no arranca | `DATOS.md` (checklist por JSON) | `npm run validate` |
| 6 | Guardado versionado + backup corrupto | `produccion/02_GUARDADO_Y_DATOS.md` | `tests/save.test.js`, `tests/save_slots.test.js` |
| 7 | Originalidad (0 activos de terceros) | `produccion/06_LEGAL_Y_AUTORIA.md` | `arte/AUTORES.md` + `THIRD_PARTY.md` |
| 8 | Offline y sin esperas reales | `produccion/05_MERCADO_Y_LANZAMIENTO.md`, `10_BUILD_Y_FIRMA_APK.md` | `npm run smoke` (sin red) + modo avión (§6 del doc 10) |
| 9 | Determinismo (tiempo inyectado) | `batalla/00_REGLAS.md`, `mundo/02_VIAJE_Y_ENCUENTROS.md` | `tests/rng.test.js` + tests de batalla |
| 10 | Paridad ES/EN | `interfaz/03_I18N_Y_TONO.md` | `npm run validate` (0 claves sin pareja) |
| 11 | Presentación solo en escenas | `batalla/04_PRESENTACION.md`, `arte/04_EFECTOS_Y_PARTICULAS.md` | `npm run lint` + `tests/scene_*.test.js` |

---

## 2. Pilares de `VALCORIA_DEUDA_DE_SANGRE.md` (6)

| Pilar | Dónde se diseña | Cómo se verifica |
|---|---|---|
| 1 — Controles táctiles propios | `interfaz/00_CONTROLES.md` | `tests/input.test.js` + `npm run smoke` |
| 2 — La Firma | `sistemas/01_FIRMA.md` | `tests/` del sistema de Firma (al implementar) |
| 3 — Deuda de Sangre (memoria y rescate) | `sistemas/00_MEMORIA_Y_DEUDA.md`, `sistemas/02_PRISIONEROS.md` | tests de memoria/prisioneros (al implementar) |
| 4 — Explorar a pie | `mundo/01_EXPLORACION.md`, `contenido/13_MONTURAS_Y_TRANSPORTE.md` | revisión de diseño + `npm run validate` |
| 5 — Encuentro libre | `mundo/02_VIAJE_Y_ENCUENTROS.md` | tests con RNG inyectado (al implementar) |
| 6 — El campo de batalla | `batalla/00_REGLAS.md` → `batalla/06_BATALLAS_DE_LA_HISTORIA.md` | `tests/` del campo (al implementar) + `npm run smoke` |

---

## 3. Requisitos no funcionales (los del QA)

| Requisito | Dónde se diseña | Cómo se verifica |
|---|---|---|
| Cobertura ≥ **90 %** | `produccion/04_QA.md` §2 | `npm run test:cov` (falla si baja) |
| **0** errores de consola / 10 min | `produccion/04_QA.md` §2 | `npm run smoke` + prueba manual §4 |
| Humo en **2** tamaños | `produccion/04_QA.md` §1 | `npm run smoke` (960×683 y 915×555) |
| ≥ 3 casos por módulo (normal/borde/error) | `../AGENTS.md` §Convenciones | revisión + cobertura |
| Objetivos ≥ **48 px**, sin solo-color | `interfaz/00_CONTROLES.md`, `arte/05_ICONOS.md` | revisión de diseño + smoke visual |
| Texto ≤ **90** caracteres por clave | `interfaz/03_I18N_Y_TONO.md` | `npm run validate` |
| Presupuesto assets demo ≤ **8 MB** | `produccion/03_RIESGOS.md` | revisión al añadir assets |
| Guardado ≤ **5 MB**, 3 slots | `produccion/02_GUARDADO_Y_DATOS.md` | `tests/save.test.js` |
| Parpadeo ≤ **3 Hz** | `interfaz/04_ACCESIBILIDAD.md` | revisión de efectos (`arte/04`) |
| Enlaces de docs **0 rotos** | `README.md` §Reglas | `npm run docs` |

---

## 4. Decisiones fuertes del dueño (log en `DECISIONES.md`)

| Decisión | Dónde vive hoy | Verificación |
|---|---|---|
| Nivel máximo **60** (demo, hasta 15) | `sistemas/12_NIVELES_DEL_HEROE.md`, `js/core/save.js` | `tests/save.test.js` (60 válido / 61 rechazado) |
| Árbol de habilidades 3×4 (sin talentos) | `contenido/06_HABILIDADES.md` §4 | al implementar: `tests/habilidades.test.js` |
| **7** profesiones, 1 activa, Equitación post-demo | `sistemas/14_PROFESIONES.md` | al implementar: `tests/profesiones.test.js` |
| **XP de oficio propio** (umbrales 150 / 450) y 9 encargos del maestro | `sistemas/14_PROFESIONES.md` §2 | al implementar: `tests/profesiones.test.js` |
| **Fabricación**: 63 recetas, 4 armas nuevas ×3 apariencias, 8 joyas, taller del sitio | `sistemas/15_FABRICACION_Y_RECETAS.md` | al implementar: `tests/recetas.test.js` |
| **Casa alquilada y cuartos de rehenes** (5 oro/día; 1 cuarto en demo; solo capitanes; rédito rescate ÷ 10/día) | `sistemas/02_PRISIONEROS.md` §3.1 | al implementar: `tests/prisioneros.test.js` |
| Recursos oficiales: **11** (7 de nivel 1 + 4 de nivel 2 desde el 30) | `contenido/05_RECURSOS_Y_MERCADO.md` §1-§1b | `npm run validate` (al existir el JSON) |
| Joyas: 2 anillos + 1 amuleto, sin romper el tope 90/45 | `contenido/04_ITEMS_Y_EQUIPO.md` §3.3 | al implementar: `tests/recetas.test.js` |
| APK **~100 MB** (subió desde 15 MB) | `produccion/10_BUILD_Y_FIRMA_APK.md` §5 | al construir |
| Precio **19 USDT TRC20** · web + APK · **16+** | `produccion/05`, `06`, `09` | revisión de la ficha pública al lanzar |
| XP por fuente y escalado +5/+4/+3 | `sistemas/12` §2.1 y §5 | al implementar: `tests/progresion.test.js` |
| Vidas de Fase 4 (montados, perro, bestias) | `batalla/01_CIFRAS.md` §1 | al implementar (Fase 4) |

---

## 5. Cómo se mantiene esta tabla

1. **Un documento nuevo** → una fila nueva aquí (misma tarea, mismo commit).
2. **Una regla de `../AGENTS.md` cambia** → esta tabla se corrige **antes** que el código.
3. **«Al implementar»** significa: el test **se escribe con el sistema**, no se deja para luego
   (DoD de `produccion/04_QA.md` §5).
4. **Nada se da por cubierto solo por estar enlazado:** la columna «Cómo se verifica» es la que
   manda; si no hay comando ni test, la fila está **en mora**.

---

## 6. Cifras que fija este documento

| Cifra | Valor |
|---|---|
| Reglas duras trazadas | **11 / 11** |
| Pilares trazados | **6 / 6** |
| Requisitos no funcionales | **10** |
| Decisiones fuertes trazadas | **8** |
| Filas «en mora» (sin verificación) | **0** |

---

## 7. Qué entra en la demo (Fase 1) — y qué sigue

> **Hasta aquí la demo.** Las 35 filas de §1-§4 con sus verificaciones de `npm run qa`; los
> sistemas de las Fases 2-5 aparecen con su marca «al implementar».

> **Y sigue el juego completo.** Cada sistema nuevo de las Fases 2-5 **gana su fila y su test** en
> la misma tarea; esta tabla es la que se revisa en cada release (`../produccion/07_RELEASES_Y_VERSIONES.md`
> §4) para que «falta el test» no pueda esconderse.

---

## 8. Fuera de este documento

- El QA como proceso (pasos, umbrales, DoD) → `produccion/04_QA.md`
- El mapa completo de tipos de documento externos → `ANALISIS_COBERTURA_DOCUMENTOS.md` (🧪)
- Las reglas mismas → `../AGENTS.md`
- Las decisiones con su fecha → `DECISIONES.md`
- Qué JSON existe y quién lo valida → `DATOS.md`
