# 03 · Recorrido — cómo se cuenta la historia en pantalla

**Estado:** ✅ **aprobado por el dueño (aprobación en bloque, 2026-09-30). Documento final.**

> La estructura está en `01_ESTRUCTURA.md`; aquí se decide **cómo se cuenta**: qué ve, qué toca y
> qué decide el jugador, escena a escena. **Sin cinemáticas**: todo es 1.ª persona jugable
> (`../mundo/01_EXPLORACION.md`). Los textos concretos, nodo a nodo, en `04_GUION.md`.

---

## 1. Regla de presentación

1. **Se cuenta caminando:** el jugador camina, mira, habla y lee. No hay pantallas de vídeo.
2. **El mundo da la información:** un cartel, una cara, una deuda en el Libro. El HUD no narra.
3. **Nada de texto encima de texto:** dos líneas de diálogo a la vez como máximo; el resto,
   bocadillos del mundo (`../interfaz/07_AVISOS_Y_RUMORES.md`).
4. **La memoria es la narración:** lo que el mundo recuerda es lo que el jugador ve cambiar
   (`../sistemas/00_MEMORIA_Y_DEUDA.md`).
5. **El jugador puede saltar** cualquier escena manteniendo pulsado 1 s
   (`SKIP_MS` de `js/systems/dialogue.js`), **aplicando sus efectos**
   (`../DECISIONES.md`, 2026-09-27).

---

## 2. Los primeros 30 minutos (la promesa se prueba aquí)

| Min | Qué ve / toca | Cómo se cuenta |
|---|---|---|
| **0-5** | El **patio del cadalso**: de rodillas, la sentencia leída, Doña Sira dice «reclamo la espada» | Diálogo del Escribano joven; la plaza contempla (reacciones de PNJ) |
| **5-10** | Sales con la **marca** en la mejilla; la gente te reconoce | Bocadillos por la calle; una **banda de Firma** en el HUD |
| **10-20** | **Primera cobranza**: una aldea que ni sabe quién eres | Tablón + portavoz; diálogo de negociación |
| **20-25** | **Primera batalla** (5-6 por bando): la moral se rompe y **huyen tres** | Campo de batalla (`../batalla/00_REGLAS.md`); el aviso «Tres huyen» |
| **25-30** | **El primer Marcado** se alista; la noticia de tu Firma corre | Diálogo + recluta (`../contenido/00_TROPAS.md` §5) |

- Si a los 30 minutos el jugador entiende que **las deudas y lo que el mundo recuerda** son el
  juego, la demo cumple (`../produccion/00_ALCANCE.md` §4).

---

## 3. Cómo se abre y se cierra cada escena

Toda la columna vertebral (`01_ESTRUCTURA.md`) usa el **mismo molde**:

1. **Apertura:** una **imagen que se camina** (la plaza, la puerta, el fuego) + una línea de
   situación. Nada de rótulos de acto.
2. **Nudo:** **2-6 líneas** de diálogo o **una decisión**; el jugador mueve o responde.
3. **Cierre:** una **consecuencia visible** (una cara cambia, una deuda entra en el Libro, la
   moral del bando cambia) y se sale **andando**, sin fundido a negro.

- **Escena larga = dos cortas.** Si una escena pide más de ~8 líneas, se parte en dos con un
  movimiento por medio.

| Escena | Apertura | Nudo | Cierre |
|---|---|---|---|
| **Prólogo** | Patio del cadalso | Decisión: callar o hablar antes de que Sira compre la espada | La marca caliente; primera página de misión |
| **Hito de acto** | Un sitio nuevo | Diálogo con portavoz/posadero | La deuda entra en el Libro |
| **Flashback** | El fuego del camino | Revives la noche (2 líneas + 1 decisión) | Vuelves al presente; nada roto |
| **Asamblea (Acto III)** | El Paso del Juramento | **Árbol de decisión** (los 3 caminos) | El final elegido, sin marcha atrás |

---

## 4. Dónde vive cada texto

| Texto | Vive en | Se lee |
|---|---|---|
| **Columna vertebral** | `04_GUION.md` + `data/` del motor | Escena de diálogo (`js/systems/dialogue.js`) |
| **Reacciones de los PNJ** | Memorias + plantillas `txt_mem_*` | Bocadillo al saludarte |
| **Carteles y lápidas** | `../historia/08_TEXTO_DEL_MUNDO.md` (`txt_mundo_*`) | Enfocar y tocar (Lectura) |
| **Tablones** | `../misiones/01_TABLONES_Y_PORTAVOCES.md` (`txt_enc_*`) | Cartel del tablón |
| **Tu diario** | `../sistemas/04_CRONICA.md` (`txt_cron_*`) | Lista del registro |
| **El Libro Mayor** | Fase 2 (`../interfaz/05_LIBRO_MAYOR.md`) | Pantalla del registro |
| **Avisos y rumores** | `../interfaz/07_AVISOS_Y_RUMORES.md` (`txt_aviso_*`) | Borde de la pantalla, 3 s |

- **Cada texto tiene una casa.** Ninguna frase se reutiliza en dos sitios con dos sentidos.

---

## 5. Cómo entra y sale la memoria en pantalla

- **Entra por el mundo, no por un menú:** un PNJ te saluda con un recuerdo tuyo
  («Tú eres el que perdonó a mi hermano»), un precio cambia, una puerta se abre o se cierra.
- **Sube en jerarquía:** primero un bocadillo, luego la Crónica, y solo en la Fase 2 el Libro
  Mayor lo pone por escrito.
- **Nunca se muestra el número:** rangos y deudas se leen como **bandas** y palabras
  (`00_MEMORIA_Y_DEUDA.md` §3, `01_FIRMA.md` §2).
- **El jugador se entera de que le recuerdan** por cómo lo tratan, no por un aviso de sistema.

---

## 6. Ritmo y cuánta lectura se tolera

| Momento | Lectura máxima sin acción |
|---|---|
| Exploración libre | 2 líneas (bocadillo) |
| Diálogo con un PNJ | 6 líneas antes de una opción |
| Escena de la columna | 8 líneas, con un movimiento por medio |
| Batalla | 0 (solo avisos de 3 s) |
| Asamblea final | Bloques de 4 líneas, con decisión cada bloque |

- **Una decisión cada 2-3 minutos** como máximo en la columna vertebral.
- **Lo que se puede contar sin texto, se cuenta sin texto:** una puerta cerrada, un precio que
  sube, un silencio.

---

## 7. Datos, tipos y validación

- Las escenas son **nodos** del motor existente (`habla / decision / une / batalla`,
  `js/systems/dialogue.js`) con **condiciones** sobre el guardado; ampliar el juego de
  condiciones (Firma, memoria, día) es **aditivo** (regla 6 de `../../AGENTS.md`).
- El recorrido vive en `data/escenas.json` (ids `snake_case`); las claves `txt_*` con paridad ES/EN.
- **Tests:** `tests/recorrido.test.js`: toda escena de la columna es alcanzable; ninguna puerta
  deja sin salida; el salto de escena aplica sus efectos.

---

## 8. Cifras que fija este documento

| Cifra | Valor |
|---|---|
| Primeros 30 min | 5 bloques (§2) |
| Líneas por diálogo | ≤ 6 antes de opción · ≤ 8 en columna |
| Decisión | cada 2-3 min como máximo |
| Salto de escena | mantener 1 s (`SKIP_MS`) con efectos |
| Cinemáticas | **0** (todo jugable en 1.ª persona) |
| Actos | prólogo + 3 actos + asamblea (`01_ESTRUCTURA.md`) |

---

## 9. Qué entra en la demo (Fase 1) — y qué sigue

> **Hasta aquí la demo.** El **Acto I completo** en pantalla: prólogo, 6 sitios, 6 encargos,
> 3 batallas, **1 flashback jugable** (la noche de la guardia) y el giro de las páginas
> arrancadas (`../produccion/00_ALCANCE.md`).

> **Y sigue el juego completo.** El **Acto II** (los 3 giros + **flashback 2**), el **Acto III**
> (la asamblea) y los **3 finales** usan **este mismo molde de escena**: crecer = más escenas en
> el mismo formato, no una forma nueva de contar.

---

## 10. Fuera de este documento

- La estructura y los giros → `01_ESTRUCTURA.md`
- Las líneas nodo a nodo → `04_GUION.md`
- Los encargos que sostienen la trama → `../misiones/05_ENCARGOS_DE_LA_HISTORIA.md`
- El diario y el registro → `../sistemas/04_CRONICA.md`, `../interfaz/05_LIBRO_MAYOR.md`
- Avisos y rumores → `../interfaz/07_AVISOS_Y_RUMORES.md`
