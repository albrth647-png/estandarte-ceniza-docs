# Valcoria — Deuda de Sangre

> **Documento del juego — v0.1 (idea aprobada).**
> 🟡 **Idea, no implementado.** Nada de esto existe en código. Las cifras concretas **no están
> decididas**: lo que aparece entre «» es una **pregunta**, no una decisión.
> Este documento **no enlaza todavía** a los demás docs del proyecto: se decide primero, se
> indexa después.

---

## 1. El gancho

> **Cada enemigo se acuerda de ti. Y no todos mueren.**

---

## 2. Qué es esto

| | |
|---|---|
| **Género** | RPG de supervivencia y memoria, **medieval**, en **1.ª persona, tiempo real** |
| **Plataforma** | Móvil primero (APK), **sin mando**, 100 % offline y estático |
| **Cámara** | **1.ª persona** (la 3.ª queda como red de seguridad si la 1.ª no convence al probar) |
| **Control** | Táctil propio, diseñado **para** táctil; no una imitación de consola |
| **Modelo** | Juego **de pago** único, sin micropagos. Demuestra primero, cobra después |
| **Tono** | No eres el héroe elegido: eres un superviviente de la caída de Valcoria |
| **Repo** | **El mismo de siempre** y con **las mismas dependencias**: cero instalaciones nuevas |

**Se tira de cima:** el motor de batalla táctica (escuadrones, mitigación, moral, Ola de choque)
y el mapa por casillas. **Base nueva.** El código viejo se queda en el repo como historia.

---

## 3. Los 5 pilares

### Pilar 1 — Controles táctiles propios ✅

**Regla maestra:** *deslizar para sentir, tocar para responder.*

**Explorar**

- **Pulgar izquierdo:** **palanca fija** (tradicional y lo que todos los juegos modernos usan).
- **Resto de la pantalla:** deslizar con el dedo = **mirar**.

**Luchar**

- **Pulgar derecho:** **botones fijos**, grandes y siempre en el mismo sitio:
  **Golpe** (toque) · **Guardia** (mantener) · **Desvío** (toque en el instante exacto).
  **Sin deslizamientos** en combate.
- **Enfocar** (*soft lock*): la cámara **gira sola** hacia el enemigo más cercano. Nunca luchas
  a ciegas.
- **Amenaza lateral** con **botón lateral**, ajustable zurdo/diestro.

**Por qué funciona aquí:** el conflicto clásico del táctil era *no poder moverte y girar a la
vez*. El enfocar automático se queda con la cámara, así que la izquierda **solo** mueve. La
palanca fija deja de ser un problema.

> ⏳ **Pendiente menor:** confirmar si en exploración se combina con *"punto y ve"* o
> *"sendero automático"* para trayectos largos. No bloquea nada.

---

### Pilar 2 — La Firma (tu estilo = tu reputación) ✅

**Cómo peleas no es solo cómo ganas: es lo que Valcoria cree de ti.** No eliges tu honor en un
menú — **lo escribes con las manos**, pelea a pelea.

| Si peleas... | Te recuerdan como... | Lo que te da |
|---|---|---|
| Guardia y parada | Prudente, honorable | Rescates más baratos, nobles aliados |
| Tajos sin piedad | Temido, cruel | Huyen de ti, pero te odian y se alían |
| Sin rematar (dejas vivir) | Misericordioso | Puedes capturar; te toman por blando |
| Rematando siempre | Limpio, letal | Rápido y barato, pero crías venganzas de sangre |

- Queda registrada en la **Crónica** (diario que la partida escribe sola).
- **Alimenta directamente la Deuda de Sangre:** cambia precios de rescate, quién te respeta,
  quién te odia y quién acude cuando pides ayuda.

⏳ *La fórmula concreta (qué suma, cuánto, tope) está por decidir.*

---

### Pilar 3 — Deuda de Sangre (memoria y rescate) ✅

**Ganar la batalla es lo fácil. El juego empieza después.**

El sistema tiene **dos lados, espejo el uno del otro**.

#### Lado A — lo que TÚ haces con los que no matas

| Decisión | Ahora | Después |
|---|---|---|
| **Rescatarlo** | Oro inmediato | Vuelve **más rico** y te recuerda |
| **Retenerlo como rehén** | Su casa paga por él **cada día** que lo retienes (`sistemas/02_PRISIONEROS.md` §3.1) | Su casa te odia |
| **Voltearlo** | Un veterano con su rasgo | Sus hermanos lo llaman traidor |
| **Ejecutarlo** | Gratis y "limpio" | Su **sangre** entra en la partida como enemigo permanente |
| **Canjearlo** | Recuperas algo perdido | Creas una deuda con ese bando |

#### Lado B — lo que TE hacen cuando pierdes (escenarios de derrota)

**No mueres y no recargas.** El mundo decide qué te pasa según **dónde** caíste y **quién** te
venció: cautiverio, desvalío, rescate pagado, te arrastra un aldeano… o incluso algo bueno.

> **Regla de oro:** el fallo **nunca bloquea**. Doler sí, narrar sí, atascar nunca. Siempre hay
> salida: pagar, escapar, que te rescaten.

#### Memoria (mezcla aprobada ✅)

| Nivel | Quién | Qué guarda |
|---|---|---|
| **Ligera** | **Cualquier persona** de Valcoria | Una clase de relación: te odia / te teme / te lo debes / te ignora |
| **Completa** | Quien te venza, venzas o te cruces varias veces | **Nombre, hechos y deuda** con detalle |

Así el mundo está **lleno de gente que te conoce de oídas**, y muy pocos a los que conoces
**de verdad**. Explorar a pie se recompensa: vas caminando y reconoces a alguien.

> ⚠️ **Lo que hay que vigilar:** con miles de personas, el guardado del móvil (pequeño) se llena.
> Por eso la mezcla: **clase ligera para todos, memoria completa solo para los que importan.**

---

### Pilar 4 — Explorar Valcoria a pie ✅

Vas **a pie** por el mundo: caminos, campamentos, plazas, ruinas. Reconoces a la gente, te la
encuentras y **tú decides con quién te metes**.

⏳ *Qué hay exactamente en el mundo (alcance) está por decidir: define el riesgo nº 1.*

---

### Pilar 5 — Encuentro libre: ¿quién inicia? ✅

| Situación | Quién inicia |
|---|---|
| Suelto en el mundo | **Tú eliges** (libertad total) |
| Zona hostil | **Ellos** |
| Venganza concreta (rencor activo) | **Él va a buscarte** |
| Zona aliada | Casi nadie te ataca |
| Refuerzo en plena pelea | Pueden llegar más (con límite) |

**Tú eres libre de buscar pelea — pero el mundo también puede buscarla a ti.**

---

### Pilar 6 — El campo de batalla ✅ (diseño cerrado 2026-09-30; solo faltan cifras)

**El juego se mantiene igual** (1.ª persona, explorar a pie, memoria), pero **las batallas son
así**: vas caminando y **te topas con un enemigo** → **se abre un campo de batalla** donde **tú
tienes tus unidades** y **el enemigo trae las suyas**.

> Es decir: **la exploración es en 1.ª persona y el combate de tropas es táctico**, con tu
> escuadrón frente al suyo. Así **se mantiene algo del proyecto anterior** (el sistema de
> batalla con unidades) sin volver al mapa por casillas.

| Pieza | Cómo queda |
|---|---|
| **Explorar** | 1.ª persona, a pie, en el mundo de Valcoria. Libertad de movimiento. |
| **Encuentro** | Te cruzas con un enemigo (o él va a buscarte). |
| **Campo de batalla** | Pantalla aparte: **tus unidades vs. las suyas**. |
| **Después de la batalla** | La **Deuda de Sangre**: rescate / rehén / volteo / ejecutar (Pilar 3). |

**Lo que esto cambia respecto a lo que habíamos hablado:** el combate deja de ser un duelo 1
contra 1, y pasa a **mandar tropas en un campo con unidades** sin dejar de ser tú quien esgrime.
En batalla conviven **dos capas de control**: la barra de órdenes (tropas) y los botones de
combate (tu héroe).

**Diseño cerrado el 2026-09-30 (las cifras se deciden en la fase de datos):**

| Pieza | Decisión |
|---|---|
| Ritmo | **Semi-tiempo real**: el campo corre, pero **se frena al dar una orden** (tiempo para pensar con el pulgar). |
| Tu papel | **Eres una unidad más**: tu héroe está en el campo y lo esgrimes tú (Golpe/Guardia/Desvío). |
| Mando de las tropas | **Órdenes globales** (Cargar / Seguirme / Defender) + IA propia de la tropa. **Sin micromando** unidad a unidad. |
| Cámara | **1.ª persona pura**, también dentro de la batalla. |
| Control (móvil) | **Barra de órdenes** de la batalla (tropas) + **botones de combate** (tu héroe), ambos fijos en pantalla. |
| Escala | **10+ unidades por bando**. |
| Terreno | El campo **depende de dónde te encontraste**: el terreno del encuentro da cobertura, frena o favorece la carga. |
| Tus tropas | **Reclutas en el mundo**. |
| Fin de batalla | Rota la **moral**: huyen o se rinden → entra el Pilar 3 (rescate / rehén / volteo). **Si pierdes tú, la misma mecánica de la deuda.** |
| Motor | **Prototipo nuevo**; `battle.js` (commit `6fcddb7`) no se resucita sin decisión documentada. |

🟡 **Solo faltan cifras:** moral cuánto aguanta y cuándo se rompe, coste y aforo de la
recluta, qué hace cada terreno en el campo y el reparto exacto de las 10+ unidades.

---

## 4. El bucle ✅

```
Caminas por Valcoria (1.ª persona, a pie)
   → Te encuentras a alguien (que ya te conoce, o va a conocerte)
   → Peleas o evitas (TÚ decides, salvo en zonas hostiles)
   → **Se abre el campo de batalla**: tus unidades vs. las suyas
   → Decisión: rescatar / retener / voltear / ejecutar
   → Tu Firma sube o baja tu reputación
   → Todo se escribe en la Crónica
   → La memoria vuelve a la gente de Valcoria
   → El mundo reacciona (y a veces, va a buscarte)
   → Vuelves a caminar, con más deudas que antes
```

---

## 5. Gráficos

**Objetivo (enmienda del dueño, 2026-10-02):** el juego **se ve como una película medieval de
aventuras** — paisajes y personajes con dirección de fotografía (luz oblicua, niebla, paleta de
tierra, siluetas, rostros de cine; referencia: *El Señor de los Anillos* **como dirección, no como
presupuesto**).

**Lo que de verdad mejora la percepción** no son más polígonos: **iluminación, sombras, niebla,
paleta, texturas, animación y efectos.** Ahí está el salto de calidad. Por dentro la producción
sigue siendo **ligera** (low-poly, LOD, texturas optimizadas): es la fotografía, no la cantidad
de geometría, la que hace la película.

**Los personajes:** **todos los cuerpos, de proporción humana** — nada de muñecos ni cartoon
en pantalla (los modelos KayKit pasan a reserva de prototipo). Los **16 clave** llevan además
**retrato pintado estilo película** en los bocadillos y el diálogo de cerca (generado con
herramientas propias, fuera de la ejecución); el cuerpo 3D manda en el campo
(`../arte/01_ASSETS.md` §2b).

**Compromiso honesto:** offline + móvil + Three.js + una sola persona = **el fotorrealismo de
motor no es posible**; lo que sí es posible — y es lo que se pide — es la **impresión de
película** con arte dirigido. Un arte estético bien dirigido envejece mejor que el realista a
medias.

⏳ *Los paquetes CC0 de castillo/interiores (Quaternius MegaKit, Modular Castle Kit, KayKit
City Builder Bits) están identificados pero **no descargados**.*

---

## 6. Reglas duras (no se negocian)

1. Sistemas **puros**: sin DOM, sin `fetch`, sin reloj; el tiempo entra por parámetro.
2. Todo dato entra con su **validador**; si los datos están mal, no arranca.
3. **Guardado versionado y aditivo**; corrupción → copia de seguridad.
4. **Determinismo:** misma partida → mismo mundo y mismas deudas.
5. **Nada de esperas reales:** todo plazo en días de juego.
6. **Todo lo que crezca, acotado** (el almacenamiento del móvil es pequeño).
7. **ES/EN** desde el primer momento.
8. **Originalidad total:** el sistema de memoria es **diseño propio**, no copia de nadie.

---

## 7. Posición de mercado (honestidad)

- **No es un juego de masas.** Es un **nicho premium**: pago único, offline, profundo.
  ~97 % de los móviles fracasan, pero **los juegos de pago son el 60 % del mercado indie** —
  el modelo es válido.
- **El mejor activo no es el género: es el gancho.** *"Maté al hermano del Tuerto y 60 horas
  después me encontré al mismo."* Eso se cuenta en un GIF. **El hook es marketing gratuito.**
- **Riesgos, en orden:** ① **alcance** (mucho para una persona) ② **el combate táctil** (hay
  que probarlo en la semana 1) ③ **descubribilidad** ④ vender (es el último; con el gancho se
  resuelve).

---

## 8. Por dónde se construye

**No se construye un mundo entero.** Se construye **una sola pelea jugable** en 1.ª persona con
el control nuevo. Si ese duelo no se siente bien en la mano, **nada de lo demás importa**.

Con eso aprobado, se añade en este orden: **memoria → decisión de rescate → explorar**.

---

## 9. Decisiones cerradas (log)

| # | Decisión | Fecha |
|---|---|---|
| 1 | Juego **nuevo**, medieval, **1.ª persona, tiempo real**, sin mando | 2026-09-30 |
| 2 | **Fuera** el motor de batalla viejo y el mapa por casillas | 2026-09-30 |
| 3 | Pilares: **Deuda de Sangre** + **explorar Valcoria a pie** | 2026-09-30 |
| 4 | Control: **palanca fija** izquierda, **botones fijos** derecha, **enfocar** automático | 2026-09-30 |
| 5 | Memoria **para todos** (clase ligera) + **completa** para los relevantes | 2026-09-30 |
| 6 | Encuentro **libre**; el enemigo inicia en zonas hostiles y por venganza | 2026-09-30 |
| 7 | **La Firma**: cómo peleas escribe tu reputación | 2026-09-30 |
| 8 | Nombre: **Valcoria — Deuda de Sangre** | 2026-09-30 |
| 9 | **Mismo repo y mismas dependencias** (cero instalaciones nuevas) | 2026-09-30 |
| 10 | **Batallas por campo de batalla con unidades** (tuyas vs. enemigas) al encontrarte; exploración en 1.ª persona | 2026-09-30 |
| 11 | Campo de batalla **semi-tiempo real** (se frena al dar orden), **eres una unidad más**, cámara **1.ª persona pura** | 2026-09-30 |
| 12 | Tropas con **órdenes globales** + IA propia (sin micromando), escala **10+ por bando**; pantalla: **barra de órdenes + botones de combate** | 2026-09-30 |
| 13 | El campo **depende del terreno** del encuentro; tropas **reclutas en el mundo** | 2026-09-30 |
| 14 | Fin de batalla: moral rota = huir/rendición → **Pilar 3**; derrota propia = **misma mecánica de la deuda** | 2026-09-30 |
| 15 | Motor: **prototipo nuevo**; `battle.js` (commit `6fcddb7`) no se resucita sin decisión documentada | 2026-09-30 |

---

## 10. Lo que queda POR DECIDIR (las cifras las decide el dueño)

> **Reescrito el 2026-10-01:** los 8 puntos de esta lista **ya están decididos** en los documentos
> de `docs/`. Aquí solo queda el apuntador para no duplicar números:

| Antes pendiente | Hoy vive en |
|---|---|
| 1. Campo de batalla (cifras) | `../batalla/01_CIFRAS.md` — **único bloque que se cierra en Fase 2** |
| 2. La Firma | `../sistemas/01_FIRMA.md` ✅ |
| 3. Memoria y deuda | `../sistemas/00_MEMORIA_Y_DEUDA.md` ✅ |
| 4. Rescate y escenarios | `../sistemas/02_PRISIONEROS.md` ✅ (+ **casa alquilada** y cuartos, 2026-10-02) |
| 5. El mundo | `../mundo/*` ✅ |
| 6. La Crónica | `../sistemas/04_CRONICA.md` ✅ |
| 7. Progresión | `../sistemas/12_NIVELES_DEL_HEROE.md` ✅ (máx. **60**, demo **15**) |
| 8. Control de exploración | **«la mirada lleva»** ✅ (`../DECISIONES.md`) |
| 9. Profesiones y oficios | `../sistemas/14_PROFESIONES.md` + `../sistemas/15_FABRICACION_Y_RECETAS.md` ✅ (7 profesiones, XP de oficio, 63 recetas) |

**Lo que sigue abierto** (2026-10-02): **cifras del campo de batalla** en Fase 2 (moral, coste y
aforo de recluta, qué hace cada terreno, reparto con 10+ unidades) y la **URL y fecha de
lanzamiento** — todo en `../DECISIONES.md` (§Pendientes) y `../PLAN_DOCUMENTOS.md`.

---

## 11. Próximo paso

~~Prototipar el **duelo jugable 1v1**~~ — **superado el 2026-09-30**: el campo es una **batalla
con unidades y órdenes globales** (§Pilar 6 y `../batalla/00_REGLAS.md`).

**El próximo paso real:** redactar los **7 documentos aprobados**
(`../ANALISIS_COBERTURA_DOCUMENTOS.md` §3) y cerrar las **cifras del campo** en la Fase 2.

---

— Generado con Codebuff
