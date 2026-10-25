# Plan de documentos — la checklist del proyecto completo

> **Regla de oro:** nada de código hasta que el diseño esté escrito y aprobado.
> **Alcance de estos documentos:** el **juego completo**; la demo solo se marca dentro de cada
> uno (Fase 1 vs. continuación).
> **Qué contendrá cada uno y el orden de escritura:** `PROPUESTA_DE_DOCUMENTOS.md` (aprobado).
> Aquí está **todo** lo que el juego lleva dentro, con casillas: 🟡 pendiente · ✅ aprobado.
> Índice general: `README.md`. Fuente de decisiones: `DECISIONES.md`.

## Estado (2026-10-02)

- **✅ Documentos base** (raíz de `docs/` + `AGENTS.md`/`README.md`): indice, propuesta de
  documentos, decisiones, arquitectura, datos, registro de bugs y las reglas del repo.
- **✅ 98 documentos de diseño aprobados (98 de 98):** 10 de `historia/`, **16 de `sistemas/`**,
  12 de `mundo/`, 7 de `batalla/`, **16 de `contenido/`**, 6 de `misiones/`, **11 de `interfaz/`**,
  6 de `arte/` y **13 de `produccion/`**, más `COBERTURA_REQUISITOS.md` en la raíz.
- **✅ Sin pendientes de redacción (2026-10-01):** se redactaron los **7** aprobados el
  2026-10-01 (`ANALISIS_COBERTURA_DOCUMENTOS.md` §3). Los que quedan por **decidir** (cifras o
  nombres concretos marcados 🟡 dentro de su documento) se cierran con el dueño sin reabrir el
  documento entero; las decisiones vivas están en `DECISIONES.md` (§Pendientes).
- **Nuevos (2026-10-01):** `sistemas/12_NIVELES_DEL_HEROE.md` (escala 1-60, tropas, zonas y
  enemigos), `sistemas/13_ESTADISTICAS_DEL_HEROE.md` (origen, atributos y stats derivadas) y
  `sistemas/14_PROFESIONES.md` (profesiones del héroe, dentro y fuera del combate).
- **Nuevo (2026-10-02):** `sistemas/15_FABRICACION_Y_RECETAS.md` (XP de oficio, 63 recetas, 4 armas
  nuevas × 3 apariencias, joyería y los 4 recursos de nivel 2).

---

## 📖 `historia/` — narrativa (10 ✅)

- [x] `00_PREMISA.md` — logline, tema, el mundo de la Ordenanza, el eslogan
- [x] `01_ESTRUCTURA.md` — prólogo, actos, giros y finales
- [x] `02_PERSONAJES.md` — el elenco
- [x] `03_RECORRIDO.md` — **aprobado**: cómo se cuenta en pantalla, primeros 30 min, memoria
- [x] `04_GUION.md` — **aprobado**: columna vertebral nodo a nodo, tono y claves ES/EN
- [x] `05_CASAS_Y_FACCIONES.md` — **aprobado**: 6 facciones, memoria de casa, herencia
- [x] `06_CRONOLOGIA.md` — **aprobado**: línea de tiempo del mundo y de la partida
- [x] `07_LEYENDAS_Y_RUMORES.md` — **aprobado**: 7 leyendas, cada una esconde una deuda
- [x] `08_TEXTO_DEL_MUNDO.md` — **aprobado**: 6 familias de texto, `txt_mundo_*` ES/EN
- [x] `09_CODEX_Y_BESTIARIO.md` — **aprobado (2026-10-01)**: 5 secciones, ≤ 120 fichas, llenado por hecho

## 🗺️ `mundo/` — cómo es y cómo se camina (12 ✅)

- [x] `00_MAPA.md` — **aprobado**: 5 zonas, 29 sitios, grafo nodos/caminos
- [x] `01_EXPLORACION.md` — **aprobado**: 1.ª persona, enfocar, radio 2,5 m
- [x] `02_VIAJE_Y_ENCUENTROS.md` — **aprobado**: 1 tirada/día, tabla por zona, RNG inyectado
- [x] `03_LUGARES.md` — **aprobado**: ficha única + los 6 de la demo con sus deudas
- [x] `04_PNJ.md` — **aprobado**: 8 oficios, rutinas de 4 franjas, cupo 25
- [x] `05_TIEMPO_DEL_MUNDO.md` — **aprobado**: días, franjas, estaciones, caducidades
- [x] `06_TERRENO_DEL_MUNDO.md` — **aprobado**: 9 tipos, velocidad/visibilidad/encuentro
- [x] `07_PROPS_Y_VEGETACION.md` — **aprobado**: catálogo propio, semilla por zona, presupuesto
- [x] `08_AGUA_RIOS_Y_PUENTES.md` — **aprobado**: 4 formas de cruce, peajes, vado en batalla
- [x] `09_CLIMA_Y_ESTACIONES.md` — **aprobado**: 4 estaciones, lluvia/nieve/niebla, comercio
- [x] `10_SUPERVIVENCIA_Y_DESCANSO.md` — **aprobado**: raciones, posada, fuego, hambre no letal
- [x] `11_CIUDADES.md` — **aprobado**: 1 ciudad, 7 servicios, toque de queda, recargos

## 🎒 `contenido/` — los catálogos jugables (16 ✅)

- [x] `00_TROPAS.md` — **aprobado**: 3 roles base, 9 tropas, aforo 6 + 2 × nivel
- [x] `01_ENEMIGOS.md` — **aprobado**: 5 familias (4 fijas + rencorosos), rasgos de IA
- [x] `02_CAPITANES_Y_NEMESIS.md` — **aprobado**: capitanes con memoria, rangos, némesis y herencia
- [x] `03_COMPANEROS.md` — **aprobado**: 4 compañeros (1 en la demo), motor `une`
- [x] `04_ITEMS_Y_EQUIPO.md` — **aprobado**: 4 rarezas, 8 armas del catálogo + 4 nuevas, mejoras +3, mochila 12
- [x] `05_RECURSOS_Y_MERCADO.md` — **aprobado**: **11** recursos (7 de nivel 1 + 4 de nivel 2), precios, trueque, stock finito
- [x] `06_HABILIDADES.md` — **aprobado**: 4 habilidades del héroe (tronco), acciones de tropa, aliento y **árbol de habilidades** (3 ramas × 4 nodos, activas/pasivas)
- [x] `07_ARTEFACTOS.md` — **aprobado**: 6 piezas únicas, estante, botín señalado
- [x] `08_ANIMALES_Y_CRIATURAS.md` — **aprobado**: 8 animales, 4 bestias, 1 leyenda (🟡)
- [x] `09_EDIFICIOS_Y_ESTRUCTURAS.md` — **aprobado**: 14 edificios, 5 interiores, assets
- [x] `10_VOCES_Y_GRITOS.md` — **aprobado**: 9 familias de frases, paridad ES/EN, voz del elenco relevante y texto en lo generativo
- [x] `11_TABLAS_DE_BOTIN.md` — **aprobado**: 5 contenedores, garantizado + extra, determinista
- [x] `12_TRAMPAS_Y_OBSTACULOS.md` — **aprobado**: 8 obstáculos, 6 trampas, siempre hay rodeo
- [x] `13_MONTURAS_Y_TRANSPORTE.md` — **aprobado**: el héroe va a pie; carreta de compañía
- [x] `14_COMIDAS_Y_BEBIDAS.md` — **aprobado**: 8 alimentos, 4 bebidas, moral de campaña
- [x] `15_ESTANDARTES_E_INSIGNIAS.md` — **aprobado**: 6 facciones, 5 estados del estandarte

## 📜 `misiones/` — encargos, tablones y rumores (6 ✅)

- [x] `00_TIPOS_DE_ENCARGO.md` — **aprobado**: 11 clases, generados vs manuales, choques
- [x] `01_TABLONES_Y_PORTAVOCES.md` — **aprobado**: tablón, posada, escribano, casa; cupo 5
- [x] `02_ESTRUCTURA_DE_ENCARGO.md` — **aprobado**: 9 campos, 6 objetivos, validación
- [x] `03_CADENAS_Y_RUMORES.md` — **aprobado**: cadenas 3-5, 1 rumor/lugar, 3 abiertas
- [x] `04_PAGOS_Y_RECOMPENSAS.md` — **aprobado**: tarifas, ±20 % regateo, 6 formas de cobro
- [x] `05_ENCARGOS_DE_LA_HISTORIA.md` — **aprobado**: 11 encargos fijos (6 en el Acto I)

## ⚙️ `sistemas/` — el alma del juego (16 ✅)

- [x] `00_MEMORIA_Y_DEUDA.md` — **aprobado**: memoria ligera/completa, 7 bandas, rencores, herencia, topes
- [x] `01_FIRMA.md` — **aprobado**: −100…+100, 7 bandas, 14 hechos, enmienda ×3
- [x] `02_PRISIONEROS.md` — **aprobado**: 4 salidas, rescates, rehén, volteo, si caes
- [x] `03_FAVORES.md` — **aprobado**: deuda blanca, 1 uso, 90 días, valor 100 oro
- [x] `04_CRONICA.md` — **aprobado**: diario, 200 entradas, 3 voces, ≤64 KB
- [x] `05_PROGRESION.md` — **aprobado**: nivel 1-60 (demo 15), veteranía, mejoras duras (Fase 5)
- [x] `06_ECONOMIA.md` — **aprobado**: 1 marco = 10 oro, salarios, recargos por Firma
- [x] `07_CICATRICES.md` — **aprobado**: 4 tipos de marca, solo memoria/Firma
- [x] `08_LUTO_Y_MORAL.md` — **aprobado**: luto 7 días, moral de campaña
- [x] `09_TIEMPO_Y_MUNDO_VIVO.md` — **aprobado**: mundo por eventos, determinista (Fase 2)
- [x] `10_LEALTAD_Y_DESERCION.md` — **aprobado**: deserción por tandas, traiciones
- [x] `11_DEUDAS_DEL_JUGADOR.md` — **aprobado**: tu deuda, asamblea, 3 finales
- [x] `12_NIVELES_DEL_HEROE.md` — **aprobado (2026-10-01)**: escala 1-60, tropas, zonas y enemigos
- [x] `13_ESTADISTICAS_DEL_HEROE.md` — **aprobado (2026-10-01)**: origen, atributos FUE/AGI/INT, stats
- [x] `14_PROFESIONES.md` — **aprobado (2026-10-01)**: profesiones del héroe (1 activa), dentro y fuera
- [x] `15_FABRICACION_Y_RECETAS.md` — **aprobado (2026-10-02)**: XP de oficio, 63 recetas, armas nuevas y joyería

## ⚔️ `batalla/` — el campo de batalla (7 ✅)

- [x] `00_REGLAS.md` — **aprobado**: 5 fases, semi-tiempo real, moral
- [x] `01_CIFRAS.md` — **aprobado**: vida, daño `def/(def+80)`, moral, ritmo
- [x] `02_TERRENO.md` — **aprobado**: 9 terrenos, cobertura 0-3, carga +25 %, 6 plantillas
- [x] `03_IA_Y_ORDENES.md` — **aprobado**: IA a 0,5 s, 3 órdenes, capitán, reagrupe
- [x] `04_PRESENTACION.md` — **aprobado**: HUD de batalla, avisos, efectos, 1.ª persona
- [x] `05_CATALOGO_DE_CAMPOS.md` — **aprobado**: 6 plantillas, ≤ 4 puntos, escala 120 m
- [x] `06_BATALLAS_DE_LA_HISTORIA.md` — **aprobado**: 4 batallas fijas, derrota nunca bloquea

## 📱 `interfaz/` — lo que el pulgar toca (11 ✅)

- [x] `00_CONTROLES.md` — **aprobado**: palanca, gestos, 48 px
- [x] `01_PANTALLAS.md` — **aprobado**: 17 pantallas, 2 toques, sin pausa total
- [x] `02_HUD.md` — **aprobado**: exploración y batalla, centro sagrado
- [x] `03_I18N_Y_TONO.md` — **aprobado**: 2 idiomas, glosario, ≤ 90 caracteres
- [x] `04_ACCESIBILIDAD.md` — **aprobado**: texto, daltonismo, sin mareos
- [x] `05_LIBRO_MAYOR.md` — **aprobado**: 5 pestañas, grafo de rencores (Fase 2)
- [x] `06_MINIMAPA.md` — **aprobado**: no es radar, nunca en batalla
- [x] `07_AVISOS_Y_RUMORES.md` — **aprobado**: 3 canales, 3 s, 1 a la vez
- [x] `08_TRANSICIONES_Y_CARGAS.md` — **aprobado**: sin pantallas de carga
- [x] `10_TUTORIAL_Y_FIRST_RUN.md` — **aprobado (2026-10-01)**: 8 lecciones, 1 línea/3 s, sin manual
- [x] `11_AVISOS_DE_CONTENIDO.md` — **aprobado (2026-10-01)**: 4 etiquetas, techo fotosensible 3 Hz, guion de 5

## 🎨 `arte/` — la cara y el sonido (6 ✅)

- [x] `00_ESTILO.md` — **aprobado**: paleta, luz, niebla 60 m, LOD, 60 fps
- [x] `01_ASSETS.md` — **aprobado**: 10 GLB con ficha, pipeline, **~90 MB demo** (APK ~100 MB)
- [x] `02_AUDIO.md` — **aprobado**: 100 % offline, 3 buses, ≤ 16 voces
- [x] `03_ANIMACIONES.md` — **aprobado**: 9 estados, atadas a cifras de combate
- [x] `04_EFECTOS_Y_PARTICULAS.md` — **aprobado**: solo escena, topes de pantalla
- [x] `05_ICONOS.md` — **aprobado**: ≥ 48 px, nunca solo color

## 🏗️ `produccion/` — para que salga vivo y a tiempo (13 ✅)

- [x] `00_ALCANCE.md` — **aprobado**: demo del Acto I, 2-3 h, 6 encargos, batalla 5-6
- [x] `01_FASES.md` — **aprobado**: Fase 1 = Acto I de la demo (8 pasos), Fases 2-5 continuación
- [x] `02_GUARDADO_Y_DATOS.md` — **aprobado**: SAVE_VERSION 5 aditivo, 3 slots, ≤ 5 MB
- [x] `03_RIESGOS.md` — **aprobado**: 15 riesgos con plan B
- [x] `04_QA.md` — **aprobado**: 6 pasos, cobertura ≥ 90 %, 0 errores
- [x] `05_MERCADO_Y_LANZAMIENTO.md` — **aprobado**: demo gratis + pago único, sin red
- [x] `06_LEGAL_Y_AUTORIA.md` — **aprobado**: derechos reservados, MIT + CC0/CC-BY
- [x] `07_RELEASES_Y_VERSIONES.md` — **aprobado**: semver, migración penúltima → última
- [x] `08_PLATAFORMAS_Y_MINIMOS.md` — **aprobado**: web + APK, WebGL2, 960×540
- [x] `09_PRIVACIDAD_Y_DATOS.md` — **aprobado**: 0 datos, 0 rastreadores, localStorage
- [x] `10_BUILD_Y_FIRMA_APK.md` — **aprobado (2026-10-01)**: 6 etapas, keystore RSA 2048, APK **~100 MB** (2026-10-02), sin CI
- [x] `11_PLAYTEST_Y_BETA.md` — **aprobado (2026-10-01)**: 5 jugadores, guion 60 min, 3 tareas, criterios de salida
- [x] `12_LOGROS_Y_ESTADISTICAS.md` — **aprobado (2026-10-01)**: 12 logros, 14 stats, export ≤ 64 KB

## 📐 `docs/` raíz — trazabilidad (1 ✅)

- [x] `COBERTURA_REQUISITOS.md` — **aprobado (2026-10-01)**: 11 reglas + 6 pilares + 10 no funcionales ↔ doc ↔ test

---

## Cómo se trabaja esta lista

1. Se elige el documento siguiente (orden propuesto: alcance → memoria/Firma → mundo →
   batalla → contenido/misiones → resto).
2. Se redacta **con el dueño**; lo pendiente se marca 🟡, nunca se inventa.
3. Al aprobarse: se marca ✅ aquí y en el índice de su carpeta.
4. `npm run qa` en verde antes de dar el documento por cerrado.
5. **El documento se escribe completo y final** (decision del dueno): no se deja a medias ni se
   reescribe; la cifra que falte se marca 🟡 **dentro** y se cierra al aprobarse.
6. **Todos los documentos son del juego FINAL**: se documenta el juego completo, no la demo.
   Dentro de cada uno se **marca** qué entra en la demo (Fase 1) y qué es continuación
   (`produccion/01_FASES.md`). El único doc que acota a la demo es `produccion/00_ALCANCE.md`.

> Si falta una idea o una pieza del juego, **su documento se añade aquí antes de inventarla
> en código**. Esta lista es la que manda sobre el orden de trabajo.

---

## 🔓 Aprobados y redactados 2026-10-01 (7)

> Del `ANALISIS_COBERTURA_DOCUMENTOS.md` §3. **Ya escritos** (ronda 4-A): hoy **98** documentos de diseño (con `sistemas/15_FABRICACION_Y_RECETAS.md`, 2026-10-02).

- [x] `produccion/10_BUILD_Y_FIRMA_APK.md` — **Alta**: generar y firmar la APK (keystore, secretos, ofuscación, tamaño)
- [x] `produccion/11_PLAYTEST_Y_BETA.md` — guion de prueba con gente, feedback y criterios de salida
- [x] `interfaz/10_TUTORIAL_Y_FIRST_RUN.md` — primer arranque y onboarding completo
- [x] `historia/09_CODEX_Y_BESTIARIO.md` — códice y bestiario in-game
- [x] `produccion/12_LOGROS_Y_ESTADISTICAS.md` — logros, estadísticas y exportación de la Crónica
- [x] `docs/COBERTURA_REQUISITOS.md` — requisito ↔ documento ↔ test
- [x] `interfaz/11_AVISOS_DE_CONTENIDO.md` — avisos de contenido y accesibilidad fotosensible
