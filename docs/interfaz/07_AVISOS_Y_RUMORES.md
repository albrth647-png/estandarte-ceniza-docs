# 07 · Avisos y rumores — informar sin interrumpir

**Estado:** ✅ **aprobado por el dueño (aprobación en bloque, 2026-09-30). Documento final.**

> Todo lo que el juego te **dice** pasa por aquí: avisos de sistema, rumores de camino y recuerdos
> de la gente. Regla de oro (`02_HUD.md` §1): **un aviso nunca tapa la acción**.

---

## 1. Los tres canales

| Canal | Quién lo dice | Cómo entra | Duración |
|---|---|---|---|
| **Aviso de sistema** | El juego | Borde superior, entrada suave | **3 s** |
| **Rumor** | Un PNJ o un cartel | **Bocadillo** sobre quien lo dice | mientras esté cerca |
| **Recuerdo** | Un PNJ que te conoce | **Bocadillo** al saludarte | 1 frase |

- **Nada de popups con botón «OK»:** lo que se lee, se va solo.
- **Nada de voz en off** que narre lo que ya ves.

---

## 2. Qué avisa el sistema

| Aviso | Cuándo |
|---|---|
| **Deuda** | Al despertar con deuda pendiente (`../sistemas/00_MEMORIA_Y_DEUDA.md`) |
| **Firma** | Al **cambiar de banda** (`../sistemas/01_FIRMA.md` §3) |
| **Favor** | Al ganar un favor o al estar por caducar (`../sistemas/03_FAVORES.md`) |
| **Moral** | Cuando se quiebra en batalla (`../batalla/04_PRESENTACION.md` §3) |
| **Encargo** | Al aceptar, caducar o cerrar (`../misiones/01_TABLONES_Y_PORTAVOCES.md`) |
| **Riesgo de terreno** | Al pisar una zona de riesgo (`../batalla/02_TERRENO.md` §7) |

- **Prioridad:** combate > vida > encargo > Firma > deuda. Si dos coinciden, se **encola** uno; no
  se apilan.

---

## 3. Qué es un rumor (y de dónde sale)

- Un **rumor** es una frase que **abre un encargo oculto** (`../misiones/03_CADENAS_Y_RUMORES.md`):
  la dice un peregrino, un posadero, un cartel.
- **La memoria los siembra:** quien te debe un favor o te tiene rencor suelta el rumor por donde
  pasas.
- **Un rumor no es fiable:** puede ser verdad o trampa; confirmarlo es el encargo `investigar`.
- **No persigue:** si no te acercas, no lo oyes; si lo ignoras, se enfría (7 días).

---

## 4. Qué es un recuerdo

- Un **recuerdo** es un PNJ diciéndote **lo que hiciste por él** (o contra él), sacado de su
  memoria (`../sistemas/00_MEMORIA_Y_DEUDA.md` §4).
- **No se narra en tercera persona:** sale de su boca («Tú eres el que perdonó a mi hermano»).
- **Es la forma de que el jugador vea la memoria funcionando** sin abrir una pantalla.

---

## 5. Reglas de contención (no marear)

1. **Máximo 1 aviso de sistema a la vez** (los demás esperan su turno).
2. **En batalla, avisos mínimos:** solo moral, vida y orden (`../batalla/04_PRESENTACION.md`).
3. **Nada a menos de 24 px del borde** si hay botones (`00_CONTROLES.md` §2).
4. **El silencio también informa:** algunos cambios (música que calla) valen más que un cartel.
5. **Todo aviso es apagable** en opciones (accesibilidad, `04_ACCESIBILIDAD.md`).

---

## 6. Datos, tipos y validación

- Claves `txt_aviso_*` y `txt_rumor_*` con **paridad ES/EN** (`03_I18N_Y_TONO.md`).
- **Tipos:** `Aviso` y `Rumor` en `js/data/game_types.js`.
- **Pintura** en escena (DOM); la **cola de avisos** es pura y testable.
- **Tests:** `tests/avisos.test.js`: nunca hay 2 avisos a la vez; un aviso caduca a los 3 s; en
  batalla solo entran los permitidos.

---

## 7. Cifras que fija este documento

| Cifra | Valor |
|---|---|
| Duración de un aviso | **3 s** |
| Avisos simultáneos | **1** |
| Canales | **3** (sistema · rumor · recuerdo) |
| Caducidad de rumor | **7 días** (`../misiones/03_CADENAS_Y_RUMORES.md`) |
| Prioridad | combate > vida > encargo > Firma > deuda |
| Margen al borde | ≥ 24 px |

---

## 8. Qué entra en la demo (Fase 1) — y qué sigue

> **Hasta aquí la demo.** Avisos de **deuda, Firma, favor y moral**, más los rumores de la posada
> y el cruce y los recuerdos de los PNJ con memoria de los 6 sitios.

> **Y sigue el juego completo.** Los rumores del reino grande y el **grafo de rencores** avisado
> desde el Libro Mayor (`05_LIBRO_MAYOR.md`) usan **estos mismos 3 canales**; no se añade uno
> nuevo.

---

## 9. Fuera de este documento

- El HUD → `02_HUD.md`
- Rumores y cadenas → `../misiones/03_CADENAS_Y_RUMORES.md`
- Memoria → `../sistemas/00_MEMORIA_Y_DEUDA.md`
- Accesibilidad → `04_ACCESIBILIDAD.md`
