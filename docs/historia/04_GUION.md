# 04 · Guion — escenas y diálogos jugables

**Estado:** ✅ **aprobado por el dueño (aprobación en bloque, 2026-09-30). Documento final.**

> Aquí van **las escenas de la columna vertebral escritas nodo a nodo**, listas para
> `js/systems/dialogue.js` (nodos `habla / decision / une / batalla`). El resto de la partida
> (encuentros, encargos, rumores) se **compone con plantillas** (`txt_*`) sobre los sistemas.
> El recorrido en pantalla está en `03_RECORRIDO.md`; la estructura, en `01_ESTRUCTURA.md`.

---

## 1. Cómo se lee este documento

- **Notación:** `[habla] QUIÉN: "línea"` · `[decision] ¿pregunta?` con opciones y efectos ·
  `[une] compañero` · `[batalla] id_campo` · `[efecto] firma +3 · memoria hecho 4 · flag x`.
- **Todo nodo lleva condición** (sobre el guardado) y **efecto** (oro, Firma, memoria, bandera,
  compañeros). Ampliar condiciones/efectos es **aditivo** (regla 6 de `../../AGENTS.md`).
- **Una escena no pasa de ~8 líneas** sin un movimiento o una decisión por medio
  (`03_RECORRIDO.md` §6).
- **Idioma:** cada línea nace **en ES y EN** en el mismo commit (regla 10); el esquema de claves
  es `txt_esc_<escena>_<n>` (§9).

---

## 2. Tono y voces

| Personaje | Voz | Cómo suena |
|---|---|---|
| **Escribano joven** | Formal, paciente | Lee una fórmula vieja como quien ya no la oye |
| **Doña Sira** | Seca, dura | Habla con la ley en la boca; no pide, **reclama** |
| **Maestro Ambrosio** | Serena, culta | Se cree bueno; no amenaza, **explica** |
| **El Teniente** | Cansada, culpable | Dice la verdad a medias y se calla |
| **Portavoz / aldeano** | Rústica, directa | Sin pleitesía; teme o desafía |
| **Marcado** | Sencilla, con miedo | Habla de deudas como quien habla del tiempo |
| **Crónica (narrador)** | Sobria | Nombra y fecha; no juzga (`../sistemas/04_CRONICA.md`) |

- **Regla de voz:** nadie da un discurso. Si una línea explica más de una idea, se parte.

---

## 3. Prólogo — *El patio del cadalso*

**Escena `esc_prologo`.** Apertura: de rodillas ante una losa grabada con cuentas.

```
[habla] ESCRIBANO_JOVEN: "Por los cuarenta del Paso del Juramento, por la traición de
        contrato, por la sangre de casas no saldada: vida por vida."
[habla] ESCRIBANO_JOVEN: "Al alba, la cuenta se cierra."
[decision] El reo puede hablar una vez. ¿Qué dices?
  · "No traicioné a nadie."            → flag reo_habla; Aldeano A recuerda
  · Callar.                            → flag reo_calla; Sira lo mira distinto
  · "Un nombre: el que giró el cerrojo." → flag reclama_teniente (memoria: se recordará)
[habla] MUJER_DE_LA_PLAZA: (escupiendo) — sin texto, solo animación + sonido
[habla] DOÑA_SIRA: "Bajo la Ordenanza, reclamo la espada."
[efecto] firma 0 (la sentencia no la cambia) · flag espada_reclamada
[habla] DOÑA_SIRA: "Si mueres, tu deuda muere contigo y mi oro contigo. No me sirve un muerto."
[efecto] memoria(SIRA) hecho 0 · deuda inicial 20 marcos · oro 50
[habla] ESCRIBANO_JOVEN: "Primera página. Cobra lo que los cuarenta esperaban."
[cierre] → exploración libre del Patio del Cadalso
```

- **Sin tutorial:** el escribano te da la primera misión **escrita en el libro**, y caminas.

---

## 4. Acto I — *La marca* (escenas fijas del Acto)

### 4.1 Primera cobranza — `esc_vega_quemada`
```
[habla] PORTAVOZ: "¿Tú eres el que cobra por la viuda?"
[decision] Cómo entras en la aldea.
  · Mostrar la marca.        → firma −2 (los aldeanos temen); cobra sin pelea
  · Guardarla.               → memoria(PORTAVOZ) hecho 1 (trato); negocias
[habla] PORTAVOZ: "El viejo se fugó con el peaje. Si lo encuentras, no lo mates: paga."
[efecto] encargo cobranza_peaje (200 oro) · memoria(VEGA) hecho 1
```

### 4.2 El primer campo — `esc_primer_campo`
```
[batalla] campo_llanura_camino   (5-6 por bando; la moral se rompe; 3 huyen)
[efecto] al ganar → prisioneros (4 salidas, ../sistemas/02_PRISIONEROS.md)
[habla] (testigos) "El que llegó con nombre y salió sin nombre… o el que perdonó."
[efecto] firma ± (según lo que hagas con los rendidos)
```

### 4.3 El primer Marcado — `esc_primer_marcado`
```
[habla] JOVEN_MARCADO: "Yo debo veinte. Con usted se pagan sirviendo."
[decision] ¿Lo aceptas?
  · "Vente."      → une marcado_lancero · memoria(JOVEN) hecho 1
  · "Aún no."     → flag marcado_espera (vuelve más tarde)
[efecto] aforo abierto · nace la compañía
```

### 4.4 Flashback 1 — *La noche de la guardia* — `esc_flashback_guardia`
```
[habla] COMPAÑERO_DE_TURNO: "Todo bien por aquí. Vete a dormir, que yo aguanto."
[decision] ¿Te quedas un rato o te vas?
  · Quedarte.   → recuerdas más (flag culpa_mas)
  · Irte.       → recuerdas menos (flag culpa_menos)
[cierre] al presente: no se ve la puerta (la memoria falla a propósito)
```

### 4.5 Giro de cierre — `esc_giro_paginas`
```
[habla] VIEJO_DEL_GREMIO: "Los del Paso no debían nada: les venía el peaje el mes que
        vinieron a abrir la puerta…"
[habla] VIEJO_DEL_GREMIO: "…"
[efecto] flag paginas_arrancadas · abre el Acto II
```

---

## 5. Acto II — *El libro de todos* (los 3 giros y el flashback 2)

| Escena | Nudo | Efecto |
|---|---|---|
| `esc_giro_ambrosio` | «¿Cuántos morirían si escribiera la verdad?» | flag verdad_ambrosio |
| `esc_giro_viuda` | Sira guardaba copia de los contratos | memoria(SIRA) up · alianza tensa y reforzada |
| `esc_giro_teniente` | El «muerto» vive, mayordomo de Altamir | flag teniente_vivo |
| `esc_flashback_puerta` | La misma noche, completa: el cerrojo | flag culpa_vista |

```
[habla] MAESTRO_AMBROSIO: "No lo niego. Elegí la paz."
[habla] MAESTRO_AMBROSIO: "¿Cuántos morirían si escribiera la verdad?"
[decision] Qué le respondes (queda en memoria como hecho 11 o 15 si luego reconcilias).
[habla] DOÑA_SIRA: "Sabía que faltaban páginas desde el primer día. No te lo dije."
[decision] "¿Me ocultaste esto?"  · Perdonar → rencor no · Reprochar → flag grieta_viuda
[habla] EL_TENIENTE: "No fui yo quien te vendió. Fui yo quien giró el cerrojo."
```

- **Flashback 2** repite la escena del fuego, ahora con la puerta visible: **no se juzga al
  jugador; se le muestra**.

---

## 6. Acto III — *La deuda mayor* (la asamblea y los 3 finales)

**Escena `esc_asamblea`.** El Paso del Juramento; fuera, tu ejército; dentro, el libro y tres caminos.

```
[habla] MAESTRO_AMBROSIO: "Dinos, entonces. ¿Qué hacemos con lo que está escrito?"
[decision] El camino (no hay vuelta atrás):
  · PAGAR  → lees la línea falsa y la reescribes delante de todos.
  · COBRAR → declaras el clamor contra Altamir bajo tu cuenta.
  · QUEMAR → das fuego al Libro Mayor.
[bifurcación por Firma]
  · Firma piadosa  → epílogo "piadoso" (los Marcados saldan su cuenta a tu lado)
  · Firma temible  → epílogo "temido" (los Marcados heredan su deuda)
[efecto] final elegido · flag final_pagar | final_cobrar | final_quemar
```

| Final | Nudo | Cierre |
|---|---|---|
| **PAGAR** | La verdad a su precio | Libro salvado; tu nombre, limpio |
| **COBRAR** | El feudo como ley | Te vuelves el mayor acreedor de Valcoria |
| **QUEMAR** | Sin libro | Valcoria empieza de cero; desaparece tu Firma |

---

## 7. Textos secundarios (compuestos, no escritos a mano)

| Texto | Fuente | Plantilla |
|---|---|---|
| **Reacciones de PNJ** | memoria + banda | `txt_mem_*` |
| **Rumores** | `../misiones/03_CADENAS_Y_RUMORES.md` | `txt_rumor_*` |
| **Carteles / lápidas** | `../historia/08_TEXTO_DEL_MUNDO.md` | `txt_mundo_*` |
| **Tablones** | `../misiones/01_TABLONES_Y_PORTAVOCES.md` | `txt_enc_*` |
| **Crónica** | `../sistemas/04_CRONICA.md` | `txt_cron_*` |
| **Avisos** | `../interfaz/07_AVISOS_Y_RUMORES.md` | `txt_aviso_*` |

- **Solo la columna (§3-§6) se escribe a mano.** Lo demás se compone y se prueba en paridad.

---

## 8. Decisiones con consecuencia (resumen)

| Decisión | Consecuencia |
|---|---|
| Hablar o callar en el cadalso | Banderas de memoria; cambia el prólogo del Acto II |
| Entrar con la marca o esconderla | Firma y memoria de la aldea |
| Qué hacer con los rendidos | Firma (±) y **rencores** heredados |
| Perdonar o reprochar a Sira | Grieta o refuerzo de la alianza |
| Los 3 caminos de la asamblea | **Final** y epílogo según Firma |

- **Ninguna decisión bloquea:** siempre hay salida (`01_FASES.md` §1 regla 7).

---

## 9. Claves `txt_*` (esquema y muestra)

- **Esquema:** `txt_esc_<escena>_<n>` para la columna; `txt_mem_*`, `txt_rumor_*`, `txt_mundo_*`,
  `txt_enc_*`, `txt_cron_*`, `txt_aviso_*` para el resto. Paridad **obligatoria** ES/EN.

| Clave | ES | EN |
|---|---|---|
| `txt_esc_prologo_1` | «Por los cuarenta del Paso del Juramento…» | "For the forty of the Oath Pass…" |
| `txt_esc_prologo_sira` | «Bajo la Ordenanza, reclamo la espada.» | "Under the Ordinance, I claim the sword." |
| `txt_esc_giro_ambrosio_2` | «¿Cuántos morirían si escribiera la verdad?» | "How many would die if I wrote the truth?" |
| `txt_esc_asamblea_q` | «¿Qué hacemos con lo que está escrito?» | "What do we do with what is written?" |

- **Presupuesto de claves:** el del alcance (`../produccion/00_ALCANCE.md` §3: 300-450 ×2), se
  ajusta al escribir cada escena. Ninguna clave entra sin su pareja EN.

---

## 10. Cifras que fija este documento

| Cifra | Valor |
|---|---|
| Escenas de la columna | **8** (prólogo · 3 hitos del Acto I · 3 giros + 2 flashbacks · asamblea) |
| Líneas por escena | ≤ 8, con movimiento o decisión por medio |
| Salto de escena | mantener **1 s** con efectos |
| Banderas de trama | `espada_reclamada`, `paginas_arrancadas`, `teniente_vivo`, `final_*`… |
| Caminos finales | **3** (pagar · cobrar · quemar) |
| Claves `txt_esc_*` | esquema + paridad ES/EN |

---

## 11. Qué entra en la demo (Fase 1) — y qué sigue

> **Hasta aquí la demo.** Las escenas del **prólogo, Acto I y el giro** (§3-§5, hasta
> `esc_giro_paginas`) con sus líneas ES/EN, más los textos secundarios compuestos en los 6
> sitios (`../produccion/00_ALCANCE.md`).

> **Y sigue el juego completo.** Las escenas del **Acto II** (§5) y del **Acto III** (§6) se
> escriben **con el mismo formato de nodo** y su pareja EN; el motor de diálogo no cambia.

---

## 12. Fuera de este documento

- La estructura y los giros → `01_ESTRUCTURA.md`
- Cómo se cuenta en pantalla → `03_RECORRIDO.md`
- El mundo y sus textos ambientales → `08_TEXTO_DEL_MUNDO.md`
- Los encargos de la trama → `../misiones/05_ENCARGOS_DE_LA_HISTORIA.md`
- El motor que ejecuta los nodos → `js/systems/dialogue.js`
