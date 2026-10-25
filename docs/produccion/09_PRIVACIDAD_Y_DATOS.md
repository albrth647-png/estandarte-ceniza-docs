# 09 · Privacidad y datos — el juego no te espía

**Estado:** ✅ **aprobado por el dueño (aprobación en bloque, 2026-09-30). Documento final.**

> El juego es **offline y sin servidores** (`../../AGENTS.md`): no hay cuentas, no hay red y **no
> hay rastreadores**. Los datos de la partida **son del jugador** y se quedan en su dispositivo.

---

## 1. Qué se recoge

**Nada.** Concretamente:

| Categoría | ¿Se recoge? |
|---|---|
| Cuentas / login | **No** |
| Datos personales | **No** |
| Analítica / rastreadores | **No** |
| Anuncios / identificadores | **No** |
| Telemetría o «crash reports» | **No** |
| Conexión a red en ejecución | **No** |

---

## 2. Dónde vive todo

- **Partida:** `localStorage` del navegador (`eb_save`, 3 slots) (`02_GUARDADO_Y_DATOS.md`).
- **Opciones:** `eb_opts` (fuera de la partida) (`../DECISIONES.md`, 2026-09-26).
- **Backup de corrupto:** `eb_save.corrupt` (solo local).
- **No** se sube nada a ninguna parte: el juego no abre conexiones.

---

## 3. Los datos son del jugador

- **Borrar una partida** borra sus datos del dispositivo (no hay copia en la nube).
- **Sin exportación obligatoria:** si el jugador quiere respaldar, es cosa suya (los datos son
  legibles en su navegador).
- **Sin cuenta:** reinstalar = empezar de cero en ese dispositivo.

---

## 4. Qué se declara (si se publica en tienda)

- **Política de privacidad simple:** «no recogemos datos».
- **Permisos:** ninguno de red; almacenamiento local únicamente.
- **Público y edad:** **16+** (según `06_LEGAL_Y_AUTORIA.md` §4, ✅).

---

## 5. Cómo se cumple por diseño

- **Cero `fetch`/`XMLHttpRequest`** en `js/**` (lo veta el lint/reglas del repo).
- **Cero SDK de terceros** (solo Three.js local, `../../THIRD_PARTY.md`).
- **Cero cookies de seguimiento.**

---

## 6. Cifras que fija este documento

| Cifra | Valor |
|---|---|
| Datos recogidos | **0** |
| Cuentas | **0** |
| Rastreadores | **0** |
| Conexiones en ejecución | **0** |
| Dónde vive la partida | `localStorage` (3 slots) |
| Borrar partida | borra del dispositivo |

---

## 7. Qué entra en la demo (Fase 1) — y sigue

> **Hasta aquí la demo.** Privacidad total desde el primer build: sin red, sin cuentas, sin
> rastreo; partida y opciones solo en local.

> **Y sigue el juego completo.** Las Fases 2-5 **no añaden** red ni cuentas: la política no cambia
> al crecer.

---

## 8. Fuera de este documento

- Guardado → `02_GUARDADO_Y_DATOS.md`
- Legal y autoría → `06_LEGAL_Y_AUTORIA.md`
- Plataformas → `08_PLATAFORMAS_Y_MINIMOS.md`
- Reglas duras del código → `../../AGENTS.md`
