# 03 · Favores — la deuda blanca

**Estado:** ✅ **aprobado por el dueño (aprobación en bloque, 2026-09-30). Documento final.**

> La segunda verdad de la Ordenanza: **el perdón es moneda** (`../historia/00_PREMISA.md`).
> Cuando perdonas una deuda, no la borras: la cambias por **un favor cobrable una sola vez**.
> La regla base vive en `00_MEMORIA_Y_DEUDA.md` §6; aquí está **cómo se gana, qué se cobra y qué
> se debe**. Mecánica candidata de origen: `../MECANICAS.md` (idea 2).

---

## 1. Qué es un favor

- Un **favor** es una **deuda blanca**: el recuerdo de que **pudiste cobrar y no cobraste**.
- No es oro ni es obediencia: es **una vez** en que esa persona te debe algo, y lo sabe.
- Se guarda en el campo `f` de su ficha de memoria (`f = 1`) y se consume en cuanto se usa.

---

## 2. Cómo se gana

| Vía | Qué pasa |
|---|---|
| **Perdonar** (hecho 4) | Convierte su deuda pendiente en deuda blanca: `f = 1`, `d = 0` (`00_MEMORIA_Y_DEUDA.md` §6) |
| **Rescatarlo sin cobrar** | `02_PRISIONEROS.md` §4: si le debías algo, pasa a favor |
| **Salvarle la vida** (hecho 3) | No da favor, pero sube el rango y su casa lo recuerda |

- **Solo el perdón y el rescate gratuito** crean un favor. Ayudar, comprar o hablar bien **no**.
- **No se hereda:** el favor es cosa suya, no de sus hijos. Muere con él.

---

## 3. Cómo se cobra

- **Una sola vez.** Al cobrarlo se marca el hecho **6 · Favor cobrado** (peso 0, no mueve el
  rango) y `f` vuelve a 0.
- **No se parte:** no se cobra «medio favor». O se gasta entero o no se gasta.
- **Caduca a los 90 días de juego** si no lo usas; al caducar desaparece sin castigo (ya
  perdonaste).
- **Se cobra estando delante** (o por correo, si el PNJ está en otro sitio): la gente honra la
  deuda blanca aunque no le gustes; cobrarla **en público** sube tu Firma (testigos), pero
  también la suya de vergüenza si es un favor humillante.

---

## 4. Qué favores existen

Un favor **cubre un servicio de hasta 100 oro** (o su equivalente), nunca la vida de nadie:

| Favor | Ejemplo | Límite |
|---|---|---|
| **Aviso** | «Te esperan en el vado»: revela una emboscada o una patrulla | Una vez |
| **Puerta abierta** | Un portón, una ronda, una puerta de ciudad | Una vez |
| **Silencio** | Callar ante un Escribano, no delatarte | Una vez |
| **Deserción** | Un soldado que deja a su casa y se viene contigo | Una vez (una unidad) |
| **Préstamo / servicio** | Herrar, curar, reparar, dar techo una noche | Hasta 100 oro |
| **Voto en la asamblea** | Un Escribano o una casa que te apoya (Acto III) | Una vez |

- **Lo que un favor NO puede:** pedir una vida, una casa entera ni una guerra. Eso es una
  alianza, no un favor.

---

## 5. Favores en contra (lo que **tú** debes)

- Si **te perdonan a ti** (al caer, `02_PRISIONEROS.md` §7; o alguien te deja marchar), el favor
  pasa a **tu** debe: la ficha de esa persona lleva `f = 1` **hacia ti como deudor**.
- Mientras debas un favor:
  - No puedes **retener** ni **ejecutar** a quien te lo prestó sin **pagar antes** (Firma −10 y
    rencor si lo haces).
  - Cobrarlo de más se nota: si le pides más de 100 oro, la deuda blanca se rompe y vuelve a ser
    **deuda firmada** (con su `d`).
- El favor en contra **también caduca a 90 días**; el que te lo hizo lo olvida.

---

## 6. Cómo se ve en pantalla

- **Aviso de sistema** (3 s, `../interfaz/02_HUD.md` §4): «Le debes un favor a <nombre>» /
  «<nombre> te debe un favor».
- En el **Libro Mayor** (Fase 2, `../interfaz/05_LIBRO_MAYOR.md`), cada favor es una línea con
  su **día de caducidad**.
- En el mundo, el PNJ que te debe un favor lo menciona **sin popup**: bocadillo al saludarte
  (`../interfaz/07_AVISOS_Y_RUMORES.md`).

---

## 7. Topes y guardado

- **No hay tope propio:** el favor vive en el `f` de cada ficha, dentro de los topes de la
  memoria (`00_MEMORIA_Y_DEUDA.md` §8): 400 fichas, 60 relevantes.
- **Nunca se pierde un `f`** por olvido de memoria: como el rango y la deuda, el favor es de los
  campos intocables al superar la cota.

---

## 8. Datos, tipos y validación

- **Guardado:** no añade campos nuevos: usa `f` de `FichaMemoria` (aditivo).
- **Tipos:** `Favor` en `js/data/game_types.js` (una sola vez, regla 4).
- **Validación:** los tipos de favor viven en `data/favores.json`; esquema en
  `js/data/schemas.js` + cruce con los ids de PNJ en `tools/validate_data.js`.
- **Sistema puro:** `js/systems/favores.js` — concede, cobra y caduca; sin DOM, sin reloj (el día
  entra por día de juego), RNG inyectado.
- **Tests (por escribir):** `tests/favores.test.js`, mínimo 3 casos (normal, borde, error): un favor se cobra una
  vez; caduca a los 90 días; cobrar de más lo rompe.

---

## 9. Cifras que fija este documento

| Cifra | Valor |
|---|---|
| Usos por favor | **1** |
| Caducidad | **90 días** de juego |
| Valor | un servicio de hasta **100 oro** |
| Quién lo crea | perdón (hecho 4) y rescate gratuito |
| Se hereda | **no** |
| Coste al cobrar | 0 (hecho 6, peso 0) |
| Topes | los de la memoria (`00_MEMORIA_Y_DEUDA.md` §8) |

---

## 10. Qué entra en la demo (Fase 1) — y qué sigue

> **Hasta aquí la demo.** La **deuda blanca** con su primer perdón, cobrable una vez, con aviso
> en el HUD y caducidad a 90 días (`../produccion/00_ALCANCE.md` §2.1). Visible en los 6 sitios.

> **Y sigue el juego completo.** Los favores de casa y el **voto en la asamblea** del Acto III
> (`11_DEUDAS_DEL_JUGADOR.md`) se añaden **con estas mismas reglas**: un favor sigue
> siendo una vez y 90 días, cambie quien cambie.

---

## 11. Fuera de este documento

- La deuda y su herencia → `00_MEMORIA_Y_DEUDA.md`
- Las 4 salidas del prisionero → `02_PRISIONEROS.md`
- Cómo se redacta el favor cobrado → `04_CRONICA.md`
- El registro en pantalla → `../interfaz/05_LIBRO_MAYOR.md`
- Precios y flujos de oro → `06_ECONOMIA.md`
- Origen de la idea → `../MECANICAS.md` (idea 2)
