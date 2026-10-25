# 10 · Lealtad y deserción — los tuyos también se van

**Estado:** ✅ **aprobado por el dueño (aprobación en bloque, 2026-09-30). Documento final.**

> Los Marcados te siguen por **deuda** o por **oro**, y las dos se pueden romper. Aquí está
> **cuándo se van, a dónde y qué dejan**. La moral de campaña, en `08_LUTO_Y_MORAL.md`; los
> salarios, en `06_ECONOMIA.md` §3.

---

## 1. Por qué se queda (o no) un Marcado

| Motivo | Peso |
|---|---|
| **Debe sangre** y paga sirviendo | Alta lealtad (mientras cumples) |
| **Cobró bien y a tiempo** | Lealtad media-alta |
| **Te tiene cariño** (memoria) | Lealtad alta (`00_MEMORIA_Y_DEUDA.md`) |
| **Tiene rencor** (contra ti) | Lealtad baja; te sirve con el rencor dentro |
| **Su casa se opone** | Lealtad frágil; presión externa |

- **Todo Marcado es una persona con cuenta, casa y miedo** (`../historia/02_PERSONAJES.md`).

---

## 2. Cuándo se desata una deserción

| Detonante | Efecto |
|---|---|
| **Sin salario** ≥ 3 días | Moral −5/día; deserciones posibles (`06_ECONOMIA.md` §3) |
| **Sin comida** ≥ 2 días | Igual (`../mundo/10_SUPERVIVENCIA_Y_DESCANSO.md` §1) |
| **Semana de luto** sin funeral | Sube el riesgo (`08_LUTO_Y_MORAL.md` §2) |
| **Feudo contra su casa** | Se va por deber familiar |
| **Promesa incumplida** (memoria, hecho 9) | Se va con testigos |

- **La deserción es por tandas, no por sorpresa:** un aviso de 1-2 días antes
  (`../interfaz/07_AVISOS_Y_RUMORES.md`).

---

## 3. A dónde se van

- **A su casa** (deuda heredada, `00_MEMORIA_Y_DEUDA.md` §5) o **a un rival** (se vuelve
  `../contenido/01_ENEMIGOS.md` familia `rencorosos`).
- **No es una baja de campaña:** se puede **recuperar** si pagas su deuda o cumples lo prometido
  (una vez por persona).

---

## 4. Traiciones (grado alto)

- Un capitán o un relevante puede **voltearse en plena batalla** si su lealtad es mínima y hay
  testigos: pasa al bando enemigo (`../batalla/03_IA_Y_ORDENES.md` §3).
- **Se prepara, no se improvisa:** la traición exige rencor activo o deuda blanca cobrada en tu
  contra (`03_FAVORES.md`).
- Deja **crónica** y **memoria**: los traidores vuelven como némesis (`../contenido/02_CAPITANES_Y_NEMESIS.md`).

---

## 5. Datos, tipos y validación

- **Datos:** `data/lealtad.json` — `{ detonante, umbral, efecto, recuperable }`.
- **Tipos:** `Lealtad` en `js/data/game_types.js`.
- **Validación:** cruce con `data/tropas.json` (salario) y `data/economia.json`; sin ellos, falla
  (`tools/validate_data.js`).
- **Sistema puro:** `js/systems/lealtad.js` — aplica detonantes y deserciones; sin DOM ni reloj.
- **Tests:** `tests/lealtad.test.js`: sin salario 3 días hay riesgo; una deserción se puede
  recuperar una vez; una traición deja némesis.

---

## 6. Cifras que fija este documento

| Cifra | Valor |
|---|---|
| Sin salario | −5/día desde el día 3 |
| Sin comida | −5/día desde el día 2 |
| Aviso previo | 1-2 días |
| Recuperación | 1 vez por persona |
| Traición | exige rencor o favor cobrado en contra |
| Deserción | no es baja de campaña |

---

## 7. Qué entra en la demo (Fase 1) — y sigue

> **En la demo:** el **Marcado que se alista** (`../contenido/00_TROPAS.md` §5), porque es
> reclutamiento (`../produccion/00_ALCANCE.md` §2.2).
> **Fuera (Fase 4):** la barra de lealtad y la **deserción** — en el Acto I, si no pagas ni das de
> comer todavía no se va nadie (recorte de `../produccion/00_ALCANCE.md` §5, 2026-10-02).

> **Y sigue el juego completo.** Traiciones, némesis y lealtad de casas entran con el reino grande
> **con estas mismas reglas**; crecer = más filas en `lealtad.json`.

---

## 8. Fuera de este documento

- Moral y luto → `08_LUTO_Y_MORAL.md`
- Salarios → `06_ECONOMIA.md`
- Memoria → `00_MEMORIA_Y_DEUDA.md`
- Capitanes que vuelven → `../contenido/02_CAPITANES_Y_NEMESIS.md`
