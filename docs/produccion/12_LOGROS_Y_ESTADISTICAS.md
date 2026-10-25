# 12 · Logros y estadísticas — tu marcador privado

**Estado:** ✅ **aprobado por el dueño (2026-10-01, ronda 4-A). Documento final.**

> El juego no tiene servidores ni cuentas (`09_PRIVACIDAD_Y_DATOS.md`): los logros y las
> estadísticas viven **en tu guardado** y se pueden **exportar** (el juego no te sigue; tú te
> llevas tu dato). Aquí está qué se mide, qué se premia y qué se exporta. **Cifras de este
> documento son propuesta de diseño** (cambiables → `../DECISIONES.md`).

---

## 1. Principios

1. **Local y tuyo:** todo en `SaveState`; nada sale del dispositivo salvo **tú** exportándolo.
2. **Los logros no dan poder:** son reconocimiento y texto; **ningún logro** mejora stats, precios
   ni moral (el balance vive en `../batalla/01_CIFRAS.md` y `../sistemas/12_NIVELES_DEL_HEROE.md`).
3. **Nada de «grindeo»:** todo logro se consigue **jugando la historia**, sin repetir batallas.
4. **Sin notificaciones fuera del juego:** ningún aviso del sistema operativo; solo avisos
   internos de 3 s (`../interfaz/07_AVISOS_Y_RUMORES.md`).

---

## 2. Logros: 12 en el juego completo

| # | Logro (nombre propuesto) | Se consigue… | Secreto |
|---|---|---|---|
| 1 | **Primer paso** | completando el prólogo | No |
| 2 | **Deuda pagada** | saldando tu primera deuda | No |
| 3 | **La Firma habla** | cambiando de banda por primera vez | No |
| 4 | **Cuatro en la sombra** | con 4 compañeros en la partida | No |
| 5 | **Maestro de oficio** | llegando a Maestro en una profesión (**450** XP de oficio) | No |
| 6 | **Catador** | probando las 4 bebidas | No |
| 7 | **No a la fuerza** | ganando una batalla sin matar: solo rendición | **Sí** |
| 8 | **El que rescató** | rescatando a un derrotado propio | No |
| 9 | **Memoria larga** | con 100 entradas en la Crónica | No |
| 10 | **Marca borrada** | consiguiendo el artefacto `art_marca_borrada` | **Sí** |
| 11 | **Los tres finales** | viendo los 3 finales en distintas partidas | **Sí** |
| 12 | **Deudor del mundo** | debiendo a la vez a 3 casas distintas | No |

- **Son 12; no 50.** (Reparto: 9 normales + 3 secretos.)
- **Los secretos no aparecen en la lista** hasta que se consiguen (ni su texto).
- **Cada logro guarda su fecha** de consiguió (día de juego) para la lista.

---

## 3. Estadísticas: 14 cifras que se guardan

| Grupo | Cifras |
|---|---|
| **Partida** | días jugados · nivel actual · honor · Firma · deuda pendiente |
| **Batalla** | batallas ganadas · perdidas · huidas ajenas forzadas · bajas propias |
| **Mundo** | sitios visitados · gente que te conoce (fichas de gente en el Códice) |
| **Oficio** | profesión activa · rango · **XP de oficio** · encargos de oficio cobrados · **piezas fabricadas** |
| **Crónica** | entradas escritas |

- Se muestran en **una sola pantalla** (pestaña «Estadísticas» del Registro, junto al Códice:
  `../interfaz/01_PANTALLAS.md`), sin gráficas ni rangos: **la lista cruda y ya está**.
- **Se recalculan al guardar**, no en cada frame (regla 2: nada de relojes en sistemas).

---

## 4. Exportar (el único «online» del juego)

- **Qué sale:** un **texto plano** (`.txt`) con: logros con sus fechas + las 14 estadísticas +
  **las últimas 50 entradas de la Crónica** (`../sistemas/04_CRONICA.md` §3).
- **Cómo:** un toque en «Exportar» → se **copia al portapapeles** y se **guarda un fichero**
  `valcoria_partida.txt` en las Descargas (en web, descarga del navegador; en APK, directorio
  propio del juego).
- **Techo:** el export **≤ 64 KB** (mismo techo de la Crónica, `../sistemas/04_CRONICA.md`).
- **Nunca** se envía a ningún sitio: no hay red (`../../AGENTS.md` regla 8). Compartirlo es
  decisión del jugador.
- **Importar no existe** (sin partidas ajenas = sin trampas posibles).

---

## 5. Datos, tipos y validación

- **Datos (por crear):** `data/logros.json` — `{ id, nombre_txt, desc_txt, secreto }` (12 filas); las
  estadísticas **no** tienen JSON: son campos de `SaveState`.
- **Tipos:** `Logro` y `Estadisticas` en `js/data/game_types.js` (regla 4).
- **Sistema puro:** `js/systems/logros.js` — evalúa condiciones dadas (hechos, contadores) y
  devuelve los logros nuevos; sin DOM, sin reloj, RNG inyectado si hiciera falta.
- **Guardado:** `SaveState.logros = { ids: [], fechas: {} }` y `SaveState.estadisticas = {…}` —
  **aditivos** (`../produccion/02_GUARDADO_Y_DATOS.md`); la migración rellena vacío y
  nunca se pierde nada.
- **Validación:** esquema en `js/data/schemas.js` + paridad ES/EN de los 24 textos en
  `tools/validate_data.js` (regla 10).
- **Tests (por escribir):** `tests/logros.test.js`, mínimo 3 casos (normal, borde, error): un logro no se suma
  dos veces; un secreto no aparece hasta lograrse; un `id` duplicado se rechaza.

---

## 6. Cifras que fija este documento

| Cifra | Valor |
|---|---|
| Logros (juego completo) | **12** (9 normales + 3 secretos) |
| Logros de la demo | **0** (los logros se activan en Fase 2) |
| Poder dado por logro | **0** |
| Estadísticas | **14** |
| Export | texto plano ≤ **64 KB** (50 entradas de Crónica) |
| Import | **no existe** |
| Pantalla nueva | **0** (pestaña del Registro) |
| Guardado | versionado aditivo |

---

## 7. Qué entra en la demo (Fase 1) — y qué sigue

> **Fuera de la demo (Fase 2).** El Acto I no muestra **logros** ni **estadísticas**: el Registro
> de la demo es el **simple** de `../interfaz/05_LIBRO_MAYOR.md`. Las **14 estadísticas** y el
> **export ≤ 64 KB** llegan con el Acto II (recorte de `../produccion/00_ALCANCE.md` §5,
> 2026-10-02).

> **Y sigue el juego completo.** Los logros de los actos nuevos se encienden **solo** añadiendo su
> fila en `logros.json` y su condición; la lista de 14 estadísticas y el export **no cambian**.

---

## 8. Fuera de este documento

- La Crónica (su contenido y su techo) → `../sistemas/04_CRONICA.md`
- Códice y bestiario → `../historia/09_CODEX_Y_BESTIARIO.md`
- Logros como logros de tienda/concursos → no existen (0 datos, `../produccion/09_PRIVACIDAD_Y_DATOS.md`)
- Dónde se ve (Registro) → `../interfaz/01_PANTALLAS.md`, `../interfaz/05_LIBRO_MAYOR.md`
- Avisos de sistema → `../interfaz/07_AVISOS_Y_RUMORES.md`
- Guardado y migración → `../produccion/02_GUARDADO_Y_DATOS.md`
