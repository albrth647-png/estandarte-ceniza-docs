# Análisis de cobertura — lista externa vs. documentos del proyecto

**Estado:** 🧪 **documento de trabajo** (no es un documento de diseño y **no cuenta en los 98**).
Fecha: 2026-10-01.

> Qué es: el mapeo de la **lista externa de tipos de documento** (~700 títulos, de una
> plantilla genérica de producción de videojuegos) contra los **98 documentos de diseño ya
> escritos** (`PLAN_DOCUMENTOS.md`) y contra las reglas del repo (`../AGENTS.md`, `README.md`).
> Qué NO es: un plan para crear 700 documentos. La mayoría **no aplica** a este proyecto
> (un solo desarrollador, offline, estático, sin servidores, sin live-service).

---

## 0. Respuesta directa: habilidades y talentos

| Tema de la lista externa | ¿Existe en el proyecto? | Dónde / por qué |
|---|---|---|
| **Habilidades** | ✅ **Sí, cubierto** | `contenido/06_HABILIDADES.md`: **tronco** de 4 habilidades del héroe por nivel, **árbol de 3 ramas × 4 nodos** (5 activas, 7 pasivas) con **puntos de juramento**, 3 acciones de tropa y coste en **aliento**, sin micromando. Enlazado desde `batalla/00_REGLAS.md` §5 y `batalla/04_PRESENTACION.md`. |
| **Talentos** | ⛔ **Descartados (confirmado 2026-10-01)** | `sistemas/05_PROGRESION.md` §1: el héroe es un deudor con espada, **sin clases ni talentos de estadísticas**. Lo que entra en su lugar es un **árbol de habilidades** que da **elección, no potencia** (fila anterior). Las mejoras **duras** siguen en Fase 5. |
| Árbol de **habilidades** (activas y pasivas) | ✅ **Añadido 2026-10-01** | `contenido/06_HABILIDADES.md` §4 (FILO/MURO/VOZ, 12 nodos, ≤ 10 puntos, aditivo `SaveState.juramento`). Ver `DECISIONES.md` (fila 2026-10-01). |

**Conclusión:** el documento de habilidades existe y **ahora incluye el árbol activas/pasivas** que
pidió el dueño; el de **talentos** sigue sin existir (a propósito).

---

## 1. Cómo leer este análisis

Para cada bloque de la lista se da: **documento(s) del repo que lo cubren**, y el veredicto:

- ✅ **Cubierto** — ya hay documento (o regla) que lo trata.
- 🟡 **Parcial** — está dentro de otro documento, pero sin apartado propio; se puede ampliar sin
  reabrir el diseño.
- 🧩 **Hueco real** — no está y **sí aplica** al juego; candidato a documento nuevo (§3).
- ⬜ **Fuera de alcance** — no aplica (single-dev, offline, estático, sin servidores, sin
  live-service, sin equipo grande, sin monetización más allá del pago único).

Regla de oro que se respeta en todo el mapeo: **un documento de diseño describe el juego**, no
el proceso corporativo. Lo de proceso vivirá en `tools/` (por crear) y `AGENTS.md`, `CONTRIBUTING`-style o en
`produccion/`, y no infla los 98.

---

## 2. Mapeo por bloques

### Bloque 1 — Gestión, requisitos y trazabilidad

| Ítems de la lista | Veredicto | Dónde |
|---|---|---|
| Acta de constitución, plan de comunicación/recursos/presupuesto, línea base de cronograma, EDT | ⬜ | Proyecto unipersonal; el equivalente es `produccion/00_ALCANCE.md` y `01_FASES.md`. |
| Registro de interesados, matriz de responsabilidades | ⬜ | Sin equipo. |
| Product backlog, definición de listo/hecho | 🟡 | `PLAN_DOCUMENTOS.md` + `produccion/04_QA.md` (DoD de `../AGENTS.md`). |
| Matriz de trazabilidad de requisitos, SRS, requisitos no funcionales, especificación funcional | 🟡 | Repartido en `PLAN_DOCUMENTOS.md` (trazabilidad), `AGENTS.md` (no funcionales: rutas, i18n, offline) y cada doc de diseño. |
| Plan de gestión de configuración, plan de versión, plan de despliegue, plan de reversión | 🟡 | `produccion/07_RELEASES_Y_VERSIONES.md` + `produccion/02_GUARDADO_Y_DATOS.md` (migración/reversión de guardado). |
| Matriz de entornos | ⬜ | Sin staging/prod; el entorno es un navegador/APK local. |
| Registro de incidencias | ✅ | `docs/BUGS.md`. |
| Plan de respuesta a riesgos | ✅ | `produccion/03_RIESGOS.md` (15 riesgos con plan B). |
| Solicitudes de cambio | 🟡 | `DECISIONES.md` (log fechado). |
| Actas de aceptación de hitos, informes de estado, actas de reuniones | ⬜ | Un desarrollador. |
| Registro de deuda técnica | 🧩 | **Hueco menor** (§3). |
| Propiedad de código, convenciones de nomenclatura | ✅ | `AGENTS.md` (reglas y convenciones). |
| Política de registro de eventos, taxonomía de errores, rastro de auditoría, matriz de cumplimiento | ⬜ / 🟡 | Sin telemetría (ver `produccion/09_PRIVACIDAD_Y_DATOS.md`, 0 datos); el "rastro" es la `Crónica` del juego. |
| Plan de verificación, plan de validación, estrategia de prueba, entorno/datos de prueba, datos simulados, módulos stub | ✅ | `produccion/04_QA.md` + `tests/` (node:test, por crear) + RNG inyectado (`AGENTS.md` regla 9). |
| Puntos de integración, especificaciones de interfaz, contratos de módulo, API interna | 🧩 | **Cubierto por diseño**: quedan definidos en los tipos (`game_types.js`) y en `ARQUITECTURA.md` (§3). |
| Cadena de herramientas, importador de assets, automatización de build, pipeline CI, repositorio de artefactos | 🟡 | `tools/` (por crear) + `arte/01_ASSETS.md` (pipeline GLB) + `../package.json` (scripts de QA, por crear). |

### Bloque 2 — Build, firma, empaquetado y plataforma móvil

| Ítems | Veredicto | Dónde |
|---|---|---|
| Gestión de secretos, claves de firma, almacén de claves, certificado | 🧩 | **Hueco** (§3): APK offline necesita su doc de build/firma. |
| Paquete de aplicación, APK divididos, optimización de tamaño, reducción de recursos, ofuscación, bibliotecas nativas | 🟡 | `produccion/08_PLATAFORMAS_Y_MINIMOS.md` + `arte/01_ASSETS.md` §3 (~90 MB). |
| Pérdida de contexto WebGL, renderizador alternativo, compatibilidad de shaders, precisión GLSL | 🟡 | `produccion/03_RIESGOS.md` (riesgos WebGL) + `PLAN_MIGRACION_3D.md`. |
| Compresión de texturas/audio, códec de vídeo, formatos de subtítulos/fuentes, licencias de fuentes | 🟡 / ⬜ | Audio: `arte/02_AUDIO.md`. Vídeo/subs: el juego no tiene vídeo. |
| Unicode, RTL, pluralización, género, sustitución, concatenación, expansión, truncamiento, cortes, silabeo, formatos de fecha/número/moneda/unidades | 🟡 | `interfaz/03_I18N_Y_TONO.md` (≤ 90 car., 2 idiomas, plantillas con huecos). RTL/plural: **fuera** (ES/EN). |
| Pruebas de localización, pseudolocalización, QA de traducción, revisión cultural | 🟡 | `npm run validate` (paridad ES/EN; validador por crear). |
| Versión de WebView/Chrome, fragmentación, capas OEM, errores de driver, particularidades de fabricante | ⬜ / 🟡 | Mínimos en `produccion/08_PLATAFORMAS_Y_MINIMOS.md`. |
| Política multiplataforma, plan de portado, abstracción de entrada/render/audio/archivos, adaptador de plataforma, servicios de plataforma | 🟡 | `PLAN_MIGRACION_3D.md` (abstracción de render) + `interfaz/00_CONTROLES.md`. |

### Bloque 3 — Calidad, pruebas y validación

| Ítems | Veredicto | Dónde |
|---|---|---|
| Compatibilidad, humo, cordura, regresión, inventario de tests, guiones manuales | ✅ | `produccion/04_QA.md` + `tools/smoke.mjs` (por crear) + `tests/` (por crear). |
| Triaje de errores, matriz severidad/prioridad | ✅ | `docs/BUGS.md` (ALTA bloquea; formato de registro). |
| Aprobación de calidad, lista de certificación, cumplimiento de tienda | 🟡 | `produccion/05_MERCADO_Y_LANZAMIENTO.md` + `06_LEGAL_Y_AUTORIA.md`. |
| Especificación mínima/recomendada/objetivo, dispositivos probados/no soportados, laboratorio | 🟡 | `produccion/08_PLATAFORMAS_Y_MINIMOS.md`. |
| Migración de guardado, inyección de corrupción | ✅ | `produccion/02_GUARDADO_Y_DATOS.md` (backup corrupto; módulo por crear). |
| Validación de determinismo y repeticiones | ✅ | `batalla/00_REGLAS.md` §10 + `AGENTS.md` regla 9 (RNG inyectado). |
| Simulación de balance, modelo económico | ✅ | `batalla/01_CIFRAS.md` §8 + `sistemas/06_ECONOMIA.md` §7. |
| Pruebas negativas, casos límite, frontera, partición, transición de estado, tablas de decisión, causa-efecto | ✅ | `AGENTS.md` (mínimo 3 casos: normal, borde, error) en `tests/` (por crear). |
| Casos de uso, historias de usuario, aceptación, alfa, beta (cerrada/abierta), acuerdo/NDA, feedback, encuesta, entrevista, grupo focal, métricas de usabilidad | 🧩 | **Hueco** (§3): no hay plan de **playtest/beta**. |

### Bloque 4 — Rendimiento, latencia y presupuestos

| Ítems | Veredicto | Dónde |
|---|---|---|
| Presupuestos de tamaño/carga/latencia/memoria/fotograma/hilo | ✅ | `arte/00_ESTILO.md` §6, `mundo/01_EXPLORACION.md` §7, `batalla/04_PRESENTACION.md` §4, `agua`/`props` (60 fps). |
| Regresión/puerta de rendimiento y calidad, calidad de build | 🟡 | `produccion/04_QA.md` + `smoke`. |
| Candidato de versión, master dorado, build final/firmada/sin firmar/de depuración/liberación/perfil/prueba/demo/prototipo | 🟡 | `produccion/07_RELEASES_Y_VERSIONES.md`. |
| Corte vertical/horizontal, build jugable/de hito/nocturna/CI | 🟡 | `produccion/00_ALCANCE.md` (rodaja vertical) + `01_FASES.md`. |
| Versionado de artefactos/semántico, número de build, hash de commit, builds reproducibles/deterministas | 🟡 | `produccion/07_RELEASES_Y_VERSIONES.md` (semver). |
| Escaneo de vulnerabilidades, análisis estático, lint, formato, cobertura, mutación, property-based, fuzzing, caos, inyección de fallos | 🟡 | `npm run qa` (tsc + lint + cobertura ≥ 90 %). Mutación/fuzzing/caos: **no** aplican. |
| Tirones, tartamudeo, microtartamudeo, picos (GC/asignación/draw calls/triángulos), shaders, pipeline, streaming de texturas, mipmaps, anisotrópico, antialiasing | 🟡 | Rendimiento cubierto por `arte/00_ESTILO.md`; perfiladores: **fuera** (§4). |
| Análisis de trazas, captura de fotogramas, suite de benchmark, profilers (GPU/CPU/almacenamiento/batería/térmico/UI/entrada/audio/animación/IA/física/render/carga/guardado) | ⬜ | Herramientas externas; el proyecto usará `npm run smoke` (por crear). |

### Bloque 6 — Audio, voz, háptica y accesibilidad avanzada

| Ítems | Veredicto | Dónde |
|---|---|---|
| Casting/sesiones de grabación/edición/mezcla/masterización, doblaje de estudio | ⬜ | **Sin doblaje de estudio** (2026-10-02): voz **TTS local pre-generada** del elenco relevante (opción 1-C, `arte/02_AUDIO.md` §1-§2) y gritos sintetizados; sin casting ni sesiones. |
| Normalización, rango dinámico, atenuación, espacial, oclusión, reverberación, pasos, bucles, música, stingers, audio adaptativo, eventos, bancos de sonido | ✅ / 🟡 | `arte/02_AUDIO.md` (3 buses, ≤ 16 voces, −6 dB ducking) + `contenido/10_VOCES_Y_GRITOS.md`. |
| Patrones/intensidad/desactivación háptica, vibración táctil | ⬜ | Web/APK sin háptica en el diseño. |
| Alerta visual, reducción de destellos, seguridad/convulsiones, prueba fotosensible | 🟡 | `interfaz/04_ACCESIBILIDAD.md` (parpadeo ≤ 3 Hz); falta el apartado fotosensible explícito. |
| Reducción de movimiento, comodidad de cámara/FOV, interruptor de movimiento de cabeza, balanceo de vista/arma | ✅ | `interfaz/04_ACCESIBILIDAD.md` + `mundo/01_EXPLORACION.md` §8 (balanceo apagable). |
| Fuente para dislexia, tamaño de texto, audiodescripción, señales visuales/auditivas/hápticas | 🟡 | `interfaz/04_ACCESIBILIDAD.md` (texto grande, daltonismo); falta audiodescripción. |
| Sacudida de cámara, desenfoque, ajustes de comodidad | ✅ | `interfaz/04_ACCESIBILIDAD.md` (≤ 6 px, desactivable). |
| Pausa al recibir daño, cámara lenta, parada de tiempo | ⬜ | Decisión: **no hay pausa total** (`batalla/00_REGLAS.md` §3). |

### Bloque 7 — Animación, física, combate, IA y tropas

| Ítems | Veredicto | Dónde |
|---|---|---|
| Idle, mezcla, estados, transiciones, root motion, IK, colocación de pies, pendientes, locomoción, variantes, impacto, rendición, ejecución, swing, frames activos/recuperación/invulnerabilidad | ✅ | `arte/03_ANIMACIONES.md` (9 estados atados a cifras) + `batalla/01_CIFRAS.md` §3. |
| Cajas de impacto/daño, capas de colisión, muñeco roto, materiales físicos, superficies de pasos, efectos de impacto, calcos de sangre, polvo, chispas, escombros, destrucción, objetos destructibles, rotura de cobertura | 🟡 | `arte/04_EFECTOS_Y_PARTICULAS.md` (topes) + `mundo/07_PROPS_Y_VEGETACION.md` + `contenido/12_TRAMPAS_Y_OBSTACULOS.md`. Muñeco roto: **no** (sin ragdoll). |
| Física de proyectiles, flechas, virotes, armas de asedio, combate a distancia/cuerpo a cuerpo, armas a dos manos, escudos, astiles, armaduras, armas, munición, carcajes, tiro de arco, ataques cargados | ✅ | `batalla/01_CIFRAS.md` §2–§3 + `contenido/04_ITEMS_Y_EQUIPO.md` (8 armas, alcances). Asedio: Fase 4+. |
| Sistema de combos, acabados, contraataques, ripostas, fintas, esquivas, rodaduras, puñalada por la espalda | ⬜ / 🟡 | Diseño: 3 botones (Golpe/Guardia/Desvío) + Habilidad; **sin combos**. |
| Golpes críticos, puntos débiles, penetración de armadura, tipos de daño (físico/fuego/frío/veneno/sangrado/contundente/cortante/perforante), resistencias, tiradas de salvación | 🟡 | `batalla/01_CIFRAS.md` §2 (crítico 10 % ×1,5; mitigación) — **un solo tipo de daño** por diseño. |
| Tablas RNG, distribuciones, valor esperado, varianza, factor de habilidad, escalado de dificultad | ✅ | `batalla/01_CIFRAS.md` §8 + RNG inyectado (`AGENTS.md`). |
| Frenado elástico, mecánicas de alcance, dificultad dinámica/accesible, modificadores de desafío, mutadores, variantes de reglas, reglas de casa, sandbox, modo dios, atravesar, escala de tiempo | ⬜ / 🟡 | El juego no tiene modos de dificultad ni sandbox; `interfaz/04_ACCESIBILIDAD.md` cubre comodidad. |
| Árboles de comportamiento, IA de utilidad, GOAP, navmesh, áreas de navegación, evitación, formación, flanqueo, carga, enrutamiento, persecución, retirada, reagrupamiento, punto de reunión, mantener posición, guardar área, patrulla, emboscada, alarma, sospecha, investigación, búsqueda, testigos, propagación | ✅ | `batalla/03_IA_Y_ORDENES.md` (2 capas, IA 0,5 s, órdenes, reagrupe) + `contenido/01_ENEMIGOS.md` (rasgos). |
| Refuerzos, disparadores de moral, umbral de huida, pánico, valentía, aura de liderazgo, influencia del héroe | ✅ | `batalla/01_CIFRAS.md` §5 + `batalla/03_IA_Y_ORDENES.md` §4. |
| Experiencia de unidad, rangos de veterano, rasgos, clases, reserva/disponibilidad/coste de unidad, mantenimiento, pago, deserción, lealtad, motín | ✅ | `contenido/00_TROPAS.md` + `sistemas/10_LEALTAD_Y_DESERCION.md` + `sistemas/05_PROGRESION.md`. |

### Bloque 8 — Deuda, reputación, facciones y simulación mundial

| Ítems | Veredicto | Dónde |
|---|---|---|
| Cautiverio, probabilidad de fuga, oportunidad de rescate, fuga, valor de rehén, temporizador, consecuencias de ejecución | ✅ | `sistemas/02_PRISIONEROS.md` (4 salidas, rescates, si caes) + `sistemas/03_FAVORES.md`. |
| Libro de deuda de sangre, rencor, miedo, respeto, infamia, honor, misericordia, crueldad, prudencia, letalidad, decaimiento/topes de reputación | ✅ / 🟡 | `sistemas/00_MEMORIA_Y_DEUDA.md` + `sistemas/01_FIRMA.md` (7 bandas; **sin decay** por decisión). |
| Propagación de rumores, boca a boca, memoria de facción, estado global | ✅ | `sistemas/09_TIEMPO_Y_MUNDO_VIVO.md` + `historia/05_CASAS_Y_FACCIONES.md` + `misiones/03_CADENAS_Y_RUMORES.md`. |
| Cola de eventos, enfriamientos, prioridad, deduplicación, resolución de conflictos | 🟡 | `sistemas/09_TIEMPO_Y_MUNDO_VIVO.md` (eventos deterministas). |
| Condiciones de carrera, hilos, async, orden de actualización, paso de tiempo, interpolación/extrapolación, frecuencias, tick, multihilo, atómica, interbloqueo, hambruna, inversión de prioridad, tiempo real | ⬜ / 🟡 | JS de un solo hilo; determinismo cubierto. |
| Manejo de errores/excepciones, reintentos, timeouts, interruptor de circuito, limitación, anti-rebote, estrangulamiento, colas, contrapresión, búfer, trabajos, planificador, temporizadores | ⬜ / 🟡 | Sin red ni servicios; el bucle de juego y el guardado (por crear) cubren lo local. |
| Interruptor de emergencia, degradación elegante, comportamiento de alternativa | ✅ | `AGENTS.md` ("el fallo nunca atasca"), `produccion/03_RIESGOS.md`. |

### Bloque 9 — Supervivencia, economía medieval y sistemas de mundo

| Ítems | Veredicto | Dónde |
|---|---|---|
| Supervivencia, hambre, sed, descanso, sueño, calor/frío, exposición, sangrado, infección, tratamiento, medicina, seguridad alimentaria, fuentes de agua, refugio, acampada, cocina, recolección, caza, pesca, agricultura, resistencia, fatiga, dolor, estrés, estados | ✅ / 🟡 | `mundo/10_SUPERVIVENCIA_Y_DESCANSO.md` + `contenido/14_COMIDAS_Y_BEBIDAS.md` + `contenido/08_ANIMALES_Y_CRIATURAS.md` + `mundo/09_CLIMA_Y_ESTACIONES.md`. |
| Durabilidad, mantenimiento de armas/armadura, peso, sobrecarga, degradación, reparación, fabricación, alquimia, herrería, sastrería, pociones, venenos, trampas, sigilo, detección, ruido, luz/sombra, línea de visión, percepción, investigación, rastreo, interrogatorio, negociación, persuasión, intimidación, regateo, soborno, robo, carterismo, ganzúa | 🟡 | Reparación/herrería: `contenido/04_ITEMS_Y_EQUIPO.md`; peso: §5; regateo/soborno: `misiones/04_PAGOS_Y_RECOMPENSAS.md`; sigilo: `mundo/01_EXPLORACION.md`; venenos/pociones/ganzúa: **no** en el diseño. |
| Duelos, emboscadas, asedios, patrullas, convoyes, mercados, posadas, tabernas | ✅ | `contenido/01_ENEMIGOS.md`, `mundo/08_AGUA_RIOS_Y_PUENTES.md`, `contenido/05_RECURSOS_Y_MERCADO.md`, `contenido/09_EDIFICIOS_Y_ESTRUCTURAS.md`. |
| Tratados, paz, declaraciones de guerra, tableros de recompensas, prisioneros, planes de fuga, rehenes, cartas de rescate, juramentos de sangre, juicio por combate, códigos de honor, vendettas, resolución de feudos, mediación, testigos, pruebas judiciales | ✅ | `historia/05_CASAS_Y_FACCIONES.md`, `misiones/01_TABLONES_Y_PORTAVOCES.md`, `sistemas/02_PRISIONEROS.md`, `sistemas/11_DEUDAS_DEL_JUGADOR.md`. |
| Crimen, castigos, exilio, forajido, guardias, ley, tribunales, nobleza, campesinado, clero, gremios, mercenarios, órdenes, política, sucesión | 🟡 | Repartido en `historia/05_CASAS_Y_FACCIONES.md`, `produccion/06_LEGAL_Y_AUTORIA.md`, `contenido/04`. |
| Economía: producción, bienes, impuestos, moneda, deuda, banca, seguros, contratos, propiedad, tierra, arriendo, minería, silvicultura, ganadería, fabricación, raros, botín, recompensas, caída, rareza, calidad, afijos, conjuntos, únicos, legendarios, malditos, reliquias, herencias, robados, contrabando, receptación, mercado negro | ✅ / 🟡 | `sistemas/06_ECONOMIA.md` + `contenido/04`/`05`/`07`/`11`. Afijos/conjuntos/malditos: **no** (equipo simple por rareza). |
| Bandidos, saqueadores, piratas, monstruos, jefes, élite, esbirros, campeones, héroes PNJ, villanos, antihéroes | ✅ | `contenido/01_ENEMIGOS.md` + `contenido/02_CAPITANES_Y_NEMESIS.md` + `contenido/08_ANIMALES_Y_CRIATURAS.md`. |

### Bloque 10 — Narrativa, lore, codex y finales

| Ítems | Veredicto | Dónde |
|---|---|---|
| Biblia narrativa, biografías, biblia de lugares, cronología, diseño de misiones, catálogo de eventos, cinemáticas, sistema de diálogo, guion | ✅ | `historia/00`–`08` + `misiones/*`. Cinemáticas: no hay (escenas dialogadas). |
| Historia del protagonista, identidad del jugador, avatar, género, apariencia, voz, generación de nombres, pronombres, nomenclatura, títulos, apodos | 🟡 | `historia/02_PERSONAJES.md` (nombre de jugador); personalización de avatar: **no**. |
| Árboles genealógicos, parentesco, matrimonios, herencias, adopción, ilegitimidad, linajes, casas, clanes, líneas de sangre | 🟡 | `historia/05_CASAS_Y_FACCIONES.md` + `sistemas/00_MEMORIA_Y_DEUDA.md` §5 (herencia). |
| Profecías, presagios, supersticiones, folclore, mitos, leyendas, canciones, poemas, oraciones, rituales, festivales, funerales, bodas, iniciación, juramentos, traiciones, sacrificios, tabúes, lugares sagrados/profanos | ✅ / 🟡 | `historia/07_LEYENDAS_Y_RUMORES.md` + `historia/08_TEXTO_DEL_MUNDO.md` + `sistemas/08_LUTO_Y_MORAL.md`. |
| Ruinas, épocas, caída de Valcoria, cronología antes/después, mapas históricos | ✅ | `historia/06_CRONOLOGIA.md` + `mundo/00_MAPA.md`. |
| Geografía, clima, día/noche, estaciones, biomas, ríos, montañas, bosques, pantanos, costa, puentes, pasos, fronteras, enclaves, disputas, población, asentamientos | ✅ | `mundo/00`–`11`. |
| Arquitectura, vestimenta, cultura alimentaria/bélica, armaduras, animales heráldicos, colores | ✅ | `arte/00_ESTILO.md` + `contenido/15_ESTANDARTES_E_INSIGNIAS.md` + `contenido/14`. |
| Idiomas, dialectos, escrituras, lingüística, inscripciones, libros/pergaminos/cartas/notas/diarios/registros in-game, códice, bestiario, herbolaria, códices | ✅ / 🟡 | `interfaz/03_I18N_Y_TONO.md` + `historia/08_TEXTO_DEL_MUNDO.md`. **Códice/bestiario in-game**: hueco menor (§3); hoy lo cubren Crónica + Libro Mayor. |
| Condiciones de desbloqueo de lore, lore descubrible, narración ambiental, utilería, señalización, grafitis, cadáveres, sangre, violencia | ✅ | `historia/08` + `mundo/07` + `arte/04`. |
| Advertencias de contenido/detonantes, sensibilidad, consulta cultural, precisión histórica, anacronismos | 🟡 | `produccion/06_LEGAL_Y_AUTORIA.md` (originalidad); falta el apartado de avisos. |
| Reglas de magia/tecnología, religión, intervención divina, más allá, almas, no-muertos, demonios, ángeles, espíritus, maldiciones, bendiciones, profecía, destino vs libre albedrío | 🟡 | Criaturas de leyenda en `contenido/08` (🟡 a confirmar); **sin magia jugable** por diseño. |
| Agencia del jugador, narrativa ramificada, consecuencias, banderas, momentos, actos, capítulos, episodios, prólogo, epílogo, variantes/finales múltiples/secretos, NG+ | ✅ / 🟡 | `historia/01_ESTRUCTURA.md` + `historia/04_GUION.md` + `sistemas/11_DEUDAS_DEL_JUGADOR.md` (3 finales). NG+: **no** (no está diseñado). |
| Logros, trofeos, coleccionables, completado, puntuación, clasificaciones locales, estadísticas, tiempo jugado, contadores (muertes/misericordias/rescates/deudas), historial de reputación, exportación de Crónica, resumen compartible, modo captura/foto, repeticiones, momentos destacados, resumen de derrota, informe de batalla, revisión posterior, guía estratégica, recorrido, speedrun, modos de desafío/difícil/hierro/principiante, combate asistido, una mano | 🧩 / ⬜ | **Hueco**: logros/estadísticas/resumen de batalla no están diseñados (§3). Clasificaciones/speedrun: fuera. |
| Canon, retcon, biblia de continuidad, relaciones, agendas de facciones, rumores, noticias del mundo | ✅ | `historia/` + `sistemas/09_TIEMPO_Y_MUNDO_VIVO.md` + `misiones/03_CADENAS_Y_RUMORES.md`. |

### Bloque 11 — UI, HUD, menús, configuración y tutorial

| Ítems | Veredicto | Dónde |
|---|---|---|
| Objetivos táctiles grandes, rueda/radial, barra rápida, guardado/carga rápida, mapa, brújula, marcador, amenaza | 🟡 | `interfaz/00_CONTROLES.md` (≥ 48 px), `interfaz/06_MINIMAPA.md` (sin radar en batalla). Rueda radial/barra rápida: no (3 órdenes fijas). |
| Barras de salud/aliento/moral, retratos, iconos (escuadrón/orden/terreno/estado/beneficios), números de daño, impacto/bloqueo/desvío, retícula, marcadores aliados, fuera de pantalla, HUD mínimo/diegético | ✅ | `interfaz/02_HUD.md` + `batalla/04_PRESENTACION.md` + `arte/05_ICONOS.md`. |
| Navegación de menús, mando externo, conflicto de gestos, rechazo de palma, multitoque, zonas muertas, sensibilidad, invertir ejes, remapeo, presets | 🟡 | `interfaz/00_CONTROLES.md` + `interfaz/04_ACCESIBILIDAD.md`. Mando externo: no (táctil). |
| Configuración inicial, calibración, campo de práctica, muñeco, tutorial de combate, a prueba de fallos, pistas contextuales, ayuda buscable, glosario, herramientas, onboarding, bienvenida de regreso | 🟡 / 🧩 | `batalla/04_PRESENTACION.md` §7 (la primera batalla enseña) + `interfaz/03_I18N_Y_TONO.md` (glosario). **Hueco**: doc de tutorial/onboarding (§3). |
| Ranuras de guardado, último jugado, autoguardado, advertencia de corrupción, modo recuperación/seguro, baja especificación, modos de calidad, ahorro de batería/datos, notificaciones, insignias, widgets, accesos directos, enlaces profundos, desbordamiento de texto | ✅ / 🟡 | `produccion/02_GUARDADO_Y_DATOS.md` + `interfaz/08_TRANSICIONES_Y_CARGAS.md` + `produccion/08_PLATAFORMAS_Y_MINIMOS.md`. |

### Bloque 12 — Legal, tienda, negocio, contratos y continuidad

| Ítems | Veredicto | Dónde |
|---|---|---|
| EULA, compra/validación/desbloqueo de contenido, demo vs completa, migración, reintento, soporte, reembolsos, fraude, facturación, impuestos, ingresos, distribución, retención | 🟡 / ⬜ | `produccion/05_MERCADO_Y_LANZAMIENTO.md` (demo gratis + pago único, sin red); impuestos/contabilidad: **fuera** (doc externo). |
| Retención de tienda, pagos a colaboradores, contabilidad, plan fiscal, entidad legal, contratos, NDA, cesión de IP, reparto, publicación, distribución, marcas, nombre, copyright | 🟡 | `produccion/06_LEGAL_Y_AUTORIA.md` + `THIRD_PARTY.md`. |
| SBOM, auditoría de dependencias, licencias OSS, divulgación de vulnerabilidades, respuesta a incidentes, monitoreo post-lanzamiento, política OSS/contribuciones, código de conducta, parches, obsolescencia, fin de vida, archivo, depósito de fuente, continuidad, recuperación de desastres | 🟡 / ⬜ | `produccion/06_LEGAL_Y_AUTORIA.md` + `03_RIESGOS.md` + `07_RELEASES_Y_VERSIONES.md`. |

### Bloque 13 — Marketing, comunidad, métricas y experimentación

| Ítems | Veredicto | Dónde |
|---|---|---|
| Optimización de store, palabras clave, icono, gráfico, texto, eslogan, pitch, ficha, póster de pilares, inspiración, guía de marca, logotipo, kit de prensa/creadores, política streamers/UGC/fans, merchandising, hoja de ruta de IP | 🟡 | `produccion/05_MERCADO_Y_LANZAMIENTO.md` + `VALCORIA_DEUDA_DE_SANGRE.md` (pilares/eslogan). Varios: **fuera** hoy (single-dev). |
| KPIs, OKR, métrica estrella, embudo, conversión, abandono, sesión, ARPU, LTV, CAC, ROAS, CPI, wishlist, demo, precio | 🧩 / ⬜ | **Fuera de alcance por decisión del dueño** (métricas de lanzamiento). Analytics/telemetría: **fuera** (0 datos, `produccion/09_PRIVACIDAD_Y_DATOS.md`). |
| A/B, experimentos, hipótesis, significancia, muestra, potencia, intervalo, efecto, salvaguardia, telemetría, panel | ⬜ | Sin servidores ni test A/B en un juego offline. |

### Bloque 14 — Gobernanza de documentación y archivos de repositorio

| Ítems | Veredicto | Dónde |
|---|---|---|
| Biblia de arte/técnica/diseño, documento maestro, fuente única de verdad, índice, propiedad, ciclo de revisión, flujo de aprobación, historial de versiones, docs obsoletos, archivo, plantillas, nomenclatura, formato, almacenamiento, acceso, copia | 🟡 | `docs/README.md` (índice + jerarquía), `PLAN_DOCUMENTOS.md`, `PROPUESTA_DE_DOCUMENTOS.md`, `AGENTS.md`. |
| Retrospectiva, post-mortem, base de conocimiento, formación, traspaso, manual de operación/juego, SOPs, checklists (build/lanzamiento/post-lanzamiento), hotfix, plantillas (cambio/bug/feature/PR/incidencia), propuestas de cambio | 🟡 / ⬜ | `produccion/04_QA.md`, `07_RELEASES_Y_VERSIONES.md`, `../AGENTS.md` (formato de bug), `docs/BUGS.md`. |
| ADR/RDD/UX/arte/audio/narrativa/balance/legal/marketing | 🟡 | `DECISIONES.md` (log único) + cada doc de diseño. |
| Archivos raíz: README, LICENSE, NOTICE, CONTRIBUTING, CODE_OF_CONDUCT, SECURITY, SUPPORT, CHANGELOG, KNOWN_ISSUES, TROUBLESHOOTING, DEBUGGING, BUILDING, RUNNING, CONFIGURATION, ENVIRONMENTS, MIGRATION, BACKUP, RECOVERY, RELEASE/LAUNCH/POST_LAUNCH_CHECKLIST, HOTFIX/ROLLBACK/INCIDENT_RESPONSE | 🟡 / ⬜ | `../README.md` + `../CHANGELOG.md` + `../THIRD_PARTY.md`; el resto: **fuera** hoy (repo unipersonal). |

---

## 3. Huecos reales (candidatos a documento nuevo)

Solo lo que **aplica a este juego** y hoy no tiene documento. **✅ Los 7 aprobados el 2026-10-01 y
redactados el mismo día** (dados de alta en `../PLAN_DOCUMENTOS.md`):

| # | Documento propuesto | Por qué | Prioridad |
|---|---|---|---|
| 1 | `produccion/10_BUILD_Y_FIRMA_APK.md` | Generar y **firmar** la APK offline (keystore, secretos, ofuscación, tamaño, CI) — es el único camino de distribución móvil y hoy no está escrito. | **Alta** |
| 2 | `produccion/11_PLAYTEST_Y_BETA.md` | Cómo se prueba con gente (guion, feedback, NDA/acuerdo, criterios de salida). | **Media** |
| 3 | `interfaz/10_TUTORIAL_Y_FIRST_RUN.md` | La enseñanza hoy está repartida (`batalla/04` §7); falta el **primer arranque** y el onboarding completo. | **Media** |
| 4 | `historia/09_CODEX_Y_BESTIARIO.md` | Códice/bestiario in-game (hoy lo cubren Crónica + Libro Mayor, pero no hay ficha de consulta). | Media |
| 5 | `produccion/12_LOGROS_Y_ESTADISTICAS.md` | Logros, estadísticas, resumen de batalla, exportación de Crónica. | Baja |
| 6 | `docs/COBERTURA_REQUISITOS.md` | Matriz que liga requisito ↔ documento ↔ test (trazabilidad real). | Media |
| 7 | `interfaz/11_AVISOS_DE_CONTENIDO.md` | Advertencias de contenido/detonantes y accesibilidad fotosensible explícita. | Baja |

> **✅ Aprobados (2026-10-01)**: los 7 se escriben en su orden (regla 3 de `README.md`) y
> **ya están dados de alta** en `../PLAN_DOCUMENTOS.md` **antes** de redactarlos.

---

## 4. Fuera de alcance por diseño (no son huecos)

- **Servidores, backend, base de datos, cuentas, matchmaking, anti-cheat, live-service, telemetría,
  A/B, analítica**: el juego es **100 % offline y estático** y no recoge datos
  (`produccion/09_PRIVACIDAD_Y_DATOS.md`).
- **Monetización más allá del pago único** (anuncios, IAP, pases): decidido pago único
  (`produccion/05_MERCADO_Y_LANZAMIENTO.md`).
- **Doblaje, cinemáticas de vídeo, háptica, mando externo, RTL/pluralización**: fuera por
  decisiones duras de `arte/02_AUDIO.md`, `interfaz/00_CONTROLES.md`, `interfaz/03_I18N_Y_TONO.md`.
- **Procesos de equipo grande** (interesados, EDT, actas, laboratorio de dispositivos, SOPs):
  proyecto de **un solo desarrollador**.
- **Combos, magia jugable, talentos de estadísticas, modos de dificultad, NG+, speedrun**: fuera
  del diseño actual (Pilares 1–6 de `VALCORIA_DEUDA_DE_SANGRE.md`).
- **Nota (2026-10-01):** el **árbol de habilidades** activas/pasivas **sí** entra
  (`contenido/06_HABILIDADES.md` §4); lo que queda fuera es el **árbol de talentos** de
  estadísticas y cualquier magia.

---

## 5. Conclusión

- **Habilidades: cubierto** (`contenido/06_HABILIDADES.md`), **con árbol** activas/pasivas desde
  el 2026-10-01.
- **Talentos: descartados por decisión del dueño** (2026-10-01); el árbol de habilidades ocupa su
  hueco dando **elección**, no potencia de estadísticas.
- De ~700 títulos externos, **la gran mayoría es de proceso corporativo o de live-service y no
  aplica**; el diseño del juego está cubierto por los **98 documentos** ya escritos.
- **7 huecos reales** (sobre todo `produccion/10_BUILD_Y_FIRMA_APK.md`) **ya redactados**
  el 2026-10-01 (ronda 4-A) y en `PLAN_DOCUMENTOS.md`. El total del diseño sube a **98**
  (con `sistemas/15_FABRICACION_Y_RECETAS.md`, 2026-10-02).
