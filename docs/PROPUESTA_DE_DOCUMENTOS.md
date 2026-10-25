# 02 · Propuesta de documentos — qué contendrá cada uno y en qué orden

**Estado:** ✅ **aprobado por el dueño (2026-09-30). Documento final.**
El estado con casillas vive en `PLAN_DOCUMENTOS.md`. Este documento es el **contenido** de cada
archivo y el **orden** de escritura. El índice general es `README.md`.

> **Regla aplicada a los 98 documentos:** cada uno describe el **juego completo** (mundo entero,
> 10+ por bando, todos los sistemas) y cierra con la sección **«Qué entra en la demo (Fase 1)»**,
> que es lo único que se acota. Un documento recortado a la demo es un error (regla 6 de
> `README.md`). El único archivo que acota a la demo es `produccion/00_ALCANCE.md`, porque para
> eso existe.

---

## 1. Orden de escritura (acordado)

Se escribe **de un documento a la vez**, respetando el orden en que los pide cada paso de
`produccion/01_FASES.md`:

| # | Documento | Para el paso |
|---|---|---|
| 1 | `sistemas/00_MEMORIA_Y_DEUDA.md` | 1.1–1.2 |
| 2 | `sistemas/01_FIRMA.md` | 1.1–1.2 |
| 3 | `mundo/00_MAPA.md` | 1.1 |
| 4 | `mundo/01_EXPLORACION.md` | 1.1 |
| 5 | `interfaz/00_CONTROLES.md` | 1.1 |
| 6 | `interfaz/02_HUD.md` | 1.1 |
| 7 | `batalla/01_CIFRAS.md` | 1.1 |
| 8 | `mundo/02_VIAJE_Y_ENCUENTROS.md` · `mundo/03_LUGARES.md` | 1.3 |
| 9 | `mundo/06_TERRENO_DEL_MUNDO.md` · `mundo/07_PROPS_Y_VEGETACION.md` · `mundo/08_AGUA_RIOS_Y_PUENTES.md` | 1.3 |
| 10 | `batalla/00_REGLAS.md` · `02_TERRENO.md` · `03_IA_Y_ORDENES.md` | 1.4 |
| 11 | `batalla/04_PRESENTACION.md` | 1.4 |
| 12 | `contenido/00_TROPAS.md` · `01_ENEMIGOS.md` | 1.4 |
| 13 | `sistemas/02_PRISIONEROS.md` · `03_FAVORES.md` | 1.5 |
| 14 | `sistemas/04_CRONICA.md` · `06_ECONOMIA.md` | 1.5 |
| 15 | `historia/03_RECORRIDO.md` · `04_GUION.md` | 1.6 |
| 16 | `misiones/00..05` (6 docs) | 1.6 |
| 17 | `interfaz/03_I18N_Y_TONO.md` | 1.6 |
| 18 | `arte/00_ESTILO` · `01_ASSETS` · `02_AUDIO` | 1.7 |
| 19 | `arte/03_ANIMACIONES` · `04_EFECTOS_Y_PARTICULAS` · `05_ICONOS` | 1.7 |
| 20 | `interfaz/01_PANTALLAS` · `04_ACCESIBILIDAD` · `08_TRANSICIONES_Y_CARGAS` | 1.7 |
| 21 | `mundo/04_PNJ.md` | 1.7 |
| 22 | `produccion/02_GUARDADO_Y_DATOS` · `03_RIESGOS` | 1.7–1.8 |
| 23 | `produccion/04_QA` · `05_MERCADO_Y_LANZAMIENTO` · `06_LEGAL_Y_AUTORIA` · `07_RELEASES_Y_VERSIONES` · `08_PLATAFORMAS_Y_MINIMOS` · `09_PRIVACIDAD_Y_DATOS` | 1.8 |
| 24 | **Fase 2:** `historia/05..08`, `sistemas/07_CICATRICES`, `09_TIEMPO_Y_MUNDO_VIVO`, `interfaz/05_LIBRO_MAYOR`, `06_MINIMAPA`, `07_AVISOS_Y_RUMORES`, `contenido/02_CAPITANES_Y_NEMESIS`, `mundo/05_TIEMPO_DEL_MUNDO`, `mundo/11_CIUDADES` | Fase 2 |
| 25 | **Fase 3:** `sistemas/11_DEUDAS_DEL_JUGADOR`, `batalla/06_BATALLAS_DE_LA_HISTORIA` | Fase 3 |
| 26 | **Fase 4:** `mundo/09_CLIMA_Y_ESTACIONES`, `10_SUPERVIVENCIA_Y_DESCANSO`, `contenido/03..15`, `sistemas/08_LUTO_Y_MORAL`, `10_LEALTAD_Y_DESERCION`, `batalla/05_CATALOGO_DE_CAMPOS` | Fase 4 |
| 27 | **Fase 5:** `sistemas/05_PROGRESION`, `contenido/07_ARTEFACTOS` | Fase 5 |

> **Regla de oro:** los documentos se escriben **uno o dos pasos antes** de la fase que los
> necesita. Ni antes (se quedan viejos), ni después (se improvisa).

---

## 2. 📜 `historia/` — narrativa (10 documentos)

| Documento | Qué contendrá |
|---|---|
| `03_RECORRIDO.md` | Cómo se cuenta la historia **en pantalla**: Prólogo y los 3 actos escena a escena, cámaras, flashbacks jugables, puntos de no retorno y los 3 finales. |
| `04_GUION.md` | Diálogos completos de toda la historia, voz de cada personaje, decisiones con sus consecuencias y claves `txt_*` ES/EN. |
| `05_CASAS_Y_FACCIONES.md` | Las casas nobles de Valcoria, sus ciudades, reclamos mutuos, heráldica y su memoria de ti. |
| `06_CRONOLOGIA.md` | Línea de tiempo del reino: Ordenanza, Paso del Juramento, reinados y hechos datables para que nada se contradiga. |
| `07_LEYENDAS_Y_RUMORES.md` | Lo que la gente cree vs. lo que pasó; leyendas y rumores jugables que esconden deudas reales. |
| `08_TEXTO_DEL_MUNDO.md` | Carteles, inscripciones, cartas, epitafios y libros: el texto ambiental con su estilo fijado. |
| `09_CODEX_Y_BESTIARIO.md` | Códice de 5 secciones y bestiario llenados por hecho (aprobado 2026-10-01). |

## 3. 🗺️ `mundo/` — cómo es y cómo se camina (12 documentos)

| Documento | Qué contendrá |
|---|---|
| `00_MAPA.md` | Valcoria entera: zonas, plazas y aldeas, caminos, ríos, fronteras, distancias en días y formato de datos. |
| `01_EXPLORACION.md` | 1.ª persona a pie: cámara, colisión, enfocar, entrar/salir, qué se puede tocar y qué no. |
| `02_VIAJE_Y_ENCUENTROS.md` | Viaje por días entre zonas, tabla de encuentros con RNG inyectado, sin esperas reales. |
| `03_LUGARES.md` | Ficha de cada lugar del reino: para qué sirve, quién vive ahí y qué deuda tiene pendiente. |
| `04_PNJ.md` | Aldeanos y gentes del mundo: rutinas ligeras, oficios, qué dicen y **qué recuerdan de ti**. |
| `05_TIEMPO_DEL_MUNDO.md` | Días, calendario y qué eventos giran sobre el tiempo de juego. |
| `06_TERRENO_DEL_MUNDO.md` | Tipos de terreno (rocío, barro, roca…) y su efecto en viaje, combate y props. |
| `07_PROPS_Y_VEGETACION.md` | Catálogo propio de árboles y arbustos, densidad por zona y presupuesto de render. |
| `08_AGUA_RIOS_Y_PUENTES.md` | Ríos, vados y puentes: obstáculos, atajos y escenas de emboscada. |
| `09_CLIMA_Y_ESTACIONES.md` | Lluvia, nieve, calor y estaciones con efecto real en viaje, moral y economía. |
| `10_SUPERVIVENCIA_Y_DESCANSO.md` | Raciones, descanso, fuego y campamentos: cuánto aguanta tu gente. |
| `11_CIUDADES.md` | Las ciudades grandes (una es el **Patio del Cadalso**): barrios, puertas, mercado, cortes. |

## 4. 🎒 `contenido/` — los catálogos jugables (16 documentos)

| Documento | Qué contendrá |
|---|---|
| `00_TROPAS.md` | Catálogo de tropas reclutables: tipos, stats, coste, subida de nivel y a quién se recluta. |
| `01_ENEMIGOS.md` | Los bandos enemigos y sus familias: tropas, señas, maneras de pelear y sus campos. |
| `02_CAPITANES_Y_NEMESIS.md` | Capitanes con memoria completa, rasgos, y las némesis que vuelven contra ti. |
| `03_COMPANEROS.md` | Compañeros con nombre, historia y lealtad propia. |
| `04_ITEMS_Y_EQUIPO.md` | Armas, armaduras y arreos por rareza, con stats, precios y mejoras. |
| `05_RECURSOS_Y_MERCADO.md` | Oro, hierro, grano…: qué se compra, dónde y a qué precio; flujos del reino. |
| `06_HABILIDADES.md` | Habilidades del héroe y de las tropas, costes, tiempos, contra-medidas y **árbol de habilidades** (activas y pasivas). |
| `07_ARTEFACTOS.md` | Objetos con historia que cambian cómo juegas, repartidos por el mundo. |
| `08_ANIMALES_Y_CRIATURAS.md` | Animales de Valcoria y sus criaturas: encuentros, peligro y utilidad. |
| `09_EDIFICIOS_Y_ESTRUCTURAS.md` | Edificios del mundo y del campo: qué se construye, qué abre. |
| `10_VOCES_Y_GRITOS.md` | Gritos de batalla, eslogan de las casas, llamadas y silencios. |
| `11_TABLAS_DE_BOTIN.md` | Tablas de botín con pesos y garantías; nada aleatorio injusto. |
| `12_TRAMPAS_Y_OBSTACULOS.md` | Trampas del camino y del campo, y cómo se ven y se evitan. |
| `13_MONTURAS_Y_TRANSPORTE.md` | Monturas, carros y alforjas: moverte y transportar con ellos. |
| `14_COMIDAS_Y_BEBIDAS.md` | Posadas, guisos y bebidas con efecto en descanso, moral y encuentros. |
| `15_ESTANDARTES_E_INSIGNIAS.md` | Heráldica propia de cada casa y tropa (todo original, sin copiar a nadie). |

## 5. 📜 `misiones/` — encargos, tablones y rumores (6 documentos)

| Documento | Qué contendrá |
|---|---|
| `00_TIPOS_DE_ENCARGO.md` | Categorías de encargo (carga, cobro, caza, escolta…) y cuántos tiene el juego. |
| `01_TABLONES_Y_PORTAVOCES.md` | Dónde se cuelgan, quién los publica y cómo cambia según tu Firma. |
| `02_ESTRUCTURA_DE_ENCARGO.md` | 9 campos y 6 objetivos de todo encargo: oferta → objetivo → cobro; el fallo **nunca bloquea**. |
| `03_CADENAS_Y_RUMORES.md` | Cadenas encadenadas, rumores que abren otros y encargos que nacen de tu memoria. |
| `04_PAGOS_Y_RECOMPENSAS.md` | Pagos en oro, componenda o servicio; qué cobras por hacerlo de una forma u otra. |
| `05_ENCARGOS_DE_LA_HISTORIA.md` | Los encargos principales de la historia, ligados a los giros y a los 3 finales. |

## 6. ⚙️ `sistemas/` — el alma del juego (16 documentos)

| Documento | Qué contendrá |
|---|---|
| `00_MEMORIA_Y_DEUDA.md` | **El corazón**: qué recuerda quién (ligera/completa), rangos de relación, rencores, herencia y **topes de guardado**. |
| `01_FIRMA.md` | Reputación por **cómo** peleas: qué la sube, qué la baja, rangos, quién la mira y qué puertas abre. |
| `02_PRISIONEROS.md` | El fin de batalla: liberar, rescate, voltear o ejecutar — las 4 salidas y sus consecuencias. |
| `03_FAVORES.md` | La deuda blanca: favores que te deben y se cobran una sola vez. |
| `04_CRONICA.md` | Tu crónica legible: lo que has hecho, a quién y qué te queda por pagar. |
| `05_PROGRESION.md` | Niveles, atributos y mejoras del héroe, con techo para no romper el balance. |
| `06_ECONOMIA.md` | Cuánto cuesta la sangre: oro, componenda, rescates, salarios y flujos del reino. |
| `07_CICATRICES.md` | Cicatrices visibles y comentadas por el mundo. |
| `08_LUTO_Y_MORAL.md` | Moral de las tropas, semana de luto y qué pasa cuando cae alguien tuyo. |
| `09_TIEMPO_Y_MUNDO_VIVO.md` | El mundo se mueve sin ti: cobranzas, sastrerías y casas que avanzan solas. |
| `10_LEALTAD_Y_DESERCION.md` | Lealtad de tu gente, deserciones y traiciones. |
| `11_DEUDAS_DEL_JUGADOR.md` | Tu deuda mayor, la asamblea y los **3 finales** (pagar / cobrar / quemar). |
| `12_NIVELES_DEL_HEROE.md` | Escala de niveles **1-60**: héroe, tropas, personajes y las zonas del mapa con sus enemigos. |
| `13_ESTADISTICAS_DEL_HEROE.md` | Origen, atributos FUE/AGI/INT y las **stats derivadas** del héroe. |
| `14_PROFESIONES.md` | Profesiones del héroe (1 activa): ventajas fuera y dentro del combate. |
| `15_FABRICACION_Y_RECETAS.md` | XP de oficio, recetas de cada oficio, armas nuevas y joyería. |

## 7. ⚔️ `batalla/` — el campo de batalla (7 documentos)

| Documento | Qué contendrá |
|---|---|
| `00_REGLAS.md` | El combate semi-tiempo real: eres una unidad más, órdenes globales, victoria por ruptura de moral. |
| `01_CIFRAS.md` | Daño, mitigación `def/(def+80)`, moral, ritmo y todas las fórmulas cerradas. |
| `02_TERRENO.md` | Cómo el terreno del encuentro forma el campo y qué ventajas da. |
| `03_IA_Y_ORDENES.md` | Órdenes globales (Cargar / Seguirme / Defender) + IA propia de cada unidad. |
| `04_PRESENTACION.md` | Cámara 1.ª persona, barra de órdenes, botones de combate y sensación de golpe. |
| `05_CATALOGO_DE_CAMPOS.md` | Catálogo de campos jugables, de 10+ por bando, por zona del reino. |
| `06_BATALLAS_DE_LA_HISTORIA.md` | Las batallas grandes de la historia, con su montaje y sus consecuencias. |

## 8. 📱 `interfaz/` — lo que el pulgar toca (11 documentos)

| Documento | Qué contendrá |
|---|---|
| `00_CONTROLES.md` | Palanca fija izq., botones fijos der., enfocar: *deslizar para sentir, tocar para responder*. |
| `01_PANTALLAS.md` | Mapa de todas las pantallas y cómo se navega entre ellas. |
| `02_HUD.md` | Qué se ve en exploración y en batalla, y en qué zona de la pantalla. |
| `03_I18N_Y_TONO.md` | Reglas de voz, tamaño y estilo de las claves `txt_*`, con paridad ES/EN. |
| `04_ACCESIBILIDAD.md` | Texto grande, contraste, una sola mano, sin mareos. |
| `05_LIBRO_MAYOR.md` | La pantalla de tu libro de deudas: leer quién te debe y a quién le debes. |
| `06_MINIMAPA.md` | Minimapa y cómo se evita tapar el juego. |
| `07_AVISOS_Y_RUMORES.md` | Cómo entran avisos, rumores y recuerdos sin interrumpir. |
| `08_TRANSICIONES_Y_CARGAS.md` | Transiciones y cargas **offline**, sin esperas ni pantallas muertas. |
| `10_TUTORIAL_Y_FIRST_RUN.md` | Primer arranque y las 8 lecciones del juego, sin manual (aprobado 2026-10-01). |
| `11_AVISOS_DE_CONTENIDO.md` | Avisos de contenido (4 etiquetas) y techo fotosensible con su guion de 5 (aprobado 2026-10-01). |

## 9. 🎨 `arte/` — la cara y el sonido (6 documentos)

| Documento | Qué contendrá |
|---|---|
| `00_ESTILO.md` | Paleta, formas, luz y referencias: cómo se ve Valcoria de principio a fin. |
| `01_ASSETS.md` | Qué hay (10 GLB con ficha) y qué falta conseguir, con licencia de cada pieza. |
| `02_AUDIO.md` | Sonido **100 % offline**: síntesis Web Audio o ficheros propios/libres con ficha. |
| `03_ANIMACIONES.md` | Animaciones de héroe, tropas y props, con sus tiempos. |
| `04_EFECTOS_Y_PARTICULAS.md` | Sangre, polvo, chispas — solo en escenas, nunca en la simulación (los futuros `js/systems/*`). |
| `05_ICONOS.md` | Iconos de órdenes, ítems y estados, legibles desde 48 px. |

## 10. 🏗️ `produccion/` — para que salga vivo y a tiempo (13 documentos)

| Documento | Qué contendrá |
|---|---|
| `02_GUARDADO_Y_DATOS.md` | `SaveState`, migraciones por versión, 3 slots, techo ~5 MB y qué campo va en cada versión. |
| `03_RIESGOS.md` | Todos los riesgos con su detección temprana y plan B (amplía los de `01_FASES.md`). |
| `04_QA.md` | Qué significa «terminado»: qa en verde, humo, 10 min sin errores, cobertura ≥ 90 %. |
| `05_MERCADO_Y_LANZAMIENTO.md` | Dónde se publica, precio de pago único, página y demo del Acto I. |
| `06_LEGAL_Y_AUTORIA.md` | Licencias, autoría y prueba de originalidad total. |
| `07_RELEASES_Y_VERSIONES.md` | Versionado, changelog para el jugador y migración entre versiones. |
| `08_PLATAFORMAS_Y_MINIMOS.md` | Web + APK y requisitos mínimos de dispositivo. |
| `09_PRIVACIDAD_Y_DATOS.md` | Sin cuentas ni servidores: `localStorage`, sin rastreadores, datos solo del jugador. |
| `10_BUILD_Y_FIRMA_APK.md` | Generar y firmar la APK: keystore, secretos, ofuscación, tamaño, verificación (aprobado 2026-10-01). |
| `11_PLAYTEST_Y_BETA.md` | Cómo se prueba con gente: guion de 60 min, 3 tareas, 5 preguntas y criterios de salida (aprobado 2026-10-01). |
| `12_LOGROS_Y_ESTADISTICAS.md` | 12 logros, 14 estadísticas y export de la Crónica en texto plano (aprobado 2026-10-01). |

---

## 11. 📐 `docs/` raíz — trazabilidad (1 documento)

| Documento | Qué contendrá |
|---|---|
| `COBERTURA_REQUISITOS.md` | Requisito ↔ documento ↔ test/comando: 11 reglas duras, 6 pilares y 10 no funcionales trazados (aprobado 2026-10-01). |

---

## 12. Cómo se cierra cada documento

1. Se escribe **completo y final**, del **juego completo**, con la sección final
   **«Qué entra en la demo (Fase 1)»**.
2. Las cifras que fija van en su **tabla de cifras**, para que el dueño las apruebe de un vistazo.
3. Lo que no esté decidido se marca 🟡 **dentro**; no se inventa.
4. Cuando exista el build: `npm run qa` en verde y se marca ✅ en `PLAN_DOCUMENTOS.md` y en
   el índice de su carpeta.
