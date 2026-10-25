# 11 · Deudas del jugador — lo que TÚ debes

**Estado:** ✅ **aprobado por el dueño (aprobación en bloque, 2026-09-30). Documento final.**

> No solo cobras: **debes**. La Ordenanza pone una cuenta sobre ti desde el prólogo
> (`../historia/00_PREMISA.md`) y **el final lo elige quien paga, cobra o quema**. Aquí está **tu
> deuda grande** y la **asamblea** que la cierra. La estructura, en `../historia/01_ESTRUCTURA.md`.

---

## 1. Tu deuda (las cuentas a tu nombre)

| Deuda | De dónde | Se paga |
|---|---|---|
| **La espada alquilada** | Doña Sira (prólogo) | Sirviendo (deuda de servicio) |
| **La de los cuarenta** | Lo que los muertos esperaban | Cobrando a quien debía |
| **La verdad de la puerta** | El Paso del Juramento | Averiguándola (Acto II) |
| **Lo que hiciste (negligencia)** | El cambio de guardia | Con años de espada (no con sangre) |

- **El jugador es un deudor**, no un héroe impoluto: su culpa es **pequeña y real**
  (`../historia/02_PERSONAJES.md`).

---

## 2. Cómo se cobra (o se perdona) tu deuda

- **Servicio:** cumples encargos de la viuda hasta cubrir la cuenta.
- **Perdón:** la **deuda blanca** vale para los dos lados (`03_FAVORES.md`): alguien puede
  perdonarte y quedar tú debiendo un favor.
- **Herencia:** como toda deuda, se hereda — salvo en el final de **quemar**.
- **Nunca desaparece sola:** solo se paga, se perdona o se quema.

---

## 3. La asamblea (Acto III)

- Se celebra en el **Paso del Juramento**, el sitio donde empezó todo (`../historia/01_ESTRUCTURA.md`).
- **Quién lee tu cuenta:** la **asamblea de Escribanos y casas** consulta tu **Firma**
  (`01_FIRMA.md` §6), tu **deuda total** y tu **rango medio** en el reino (`00_MEMORIA_Y_DEUDA.md` §9).
- **Los Marcados esperan fuera:** cuántos saldaron su cuenta a tu lado depende de la memoria.

---

## 4. Los tres finales

| Final | Qué haces | Qué queda |
|---|---|---|
| **PAGAR** | Lees la línea falsa y la reescribes | El libro se salva; tu nombre, limpio |
| **COBRAR** | Declaras el clamor bajo tu cuenta | Te vuelves el mayor acreedor de Valcoria |
| **QUEMAR** | Das fuego al Libro Mayor | Valcoria empieza de cero; desaparece tu Firma y tu Crónica |

- **Ninguno es «el bueno»:** el **epílogo** se tiñe de tu Firma (piadoso o temido) y de tus
  Marcados (cuántos pagaron, cuántos heredaron).
- **No hay marcha atrás:** la asamblea es el punto de no retorno (`../interfaz/01_PANTALLAS.md` §3).

---

## 5. Datos, tipos y validación

- **Guardado:** la deuda total se **calcula** desde `memoria` (no se guarda aparte);
  `SaveState.firma` y las banderas `final_*` marcan el desenlace.
- **Tipos:** `DeudaJugador` y `Final` en `js/data/game_types.js`.
- **Validación:** los 3 finales existen; las banderas `final_*` cruzan con `../historia/04_GUION.md`
  (`tools/validate_data.js`).
- **Sistema puro:** el cálculo de la deuda grande vive en `js/systems/memoria.js` + `finales.js`;
  sin DOM ni reloj.
- **Tests:** `tests/deudas_jugador.test.js`: la deuda total suma la memoria; ningún final deja la
  partida sin cierre; quemar limpia Firma y Crónica.

---

## 6. Cifras que fija este documento

| Cifra | Valor |
|---|---|
| Finales | **3** (pagar · cobrar · quemar) |
| Punto de no retorno | la asamblea |
| Quién lee tu cuenta | la asamblea (Firma + deuda + rango) |
| Deuda inicial | 20 marcos (`06_ECONOMIA.md`) |
| Epílogo | variable por Firma y Marcados |
| Marcha atrás | **no** |

---

## 7. Qué entra en la demo (Fase 1) — y sigue

> **Hasta aquí la demo.** Tu **deuda con Sira** y la de los cuarenta, gestionables durante el Acto
> I; la **asamblea** se anuncia y se deja para la Fase 3.

> **Y sigue el juego completo.** El **Acto III**, la **asamblea** y los **3 finales** cierran la
> historia **con estas mismas reglas**; no hay un cuarto camino ni un final secreto.

---

## 8. Fuera de este documento

- La estructura y los finales → `../historia/01_ESTRUCTURA.md`
- Firma → `01_FIRMA.md`
- Memoria y herencia → `00_MEMORIA_Y_DEUDA.md`
- Favores → `03_FAVORES.md`
- Economía → `06_ECONOMIA.md`
