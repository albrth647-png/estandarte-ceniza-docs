# 03 · Cadenas y rumores — lo que se enlaza solo

**Estado:** ✅ **aprobado por el dueño (aprobación en bloque, 2026-09-30). Documento final.**

> La historia no se despilfarra: **se ramifica** (`../historia/01_ESTRUCTURA.md`). Las cadenas y
> los rumores son el mecanismo por el que **un encargo llama a otro** sin que nadie escriba cada
> combinación a mano. Se apoyan en la memoria (`../sistemas/00_MEMORIA_Y_DEUDA.md`) y en el
> mundo vivo (`../sistemas/09_TIEMPO_Y_MUNDO_VIVO.md`).

---

## 1. Qué es una cadena

- Una **cadena** es un encargo que **nace de cómo acabó el anterior**:
  - *Cobras al deudor* → su casa te busca (`vengar`).
  - *Limpias el camino* → la banda vuelve con su señor (`limpiar` → `vencer` mayor).
  - *Median entre casas* → el bando que perdiste te lo cobra.
- Se declara con el campo **`cadenas`** (`02_ESTRUCTURA_DE_ENCARGO.md` §1): los ids que **abre** o
  **cierra**.
- **Largo de una cadena:** **3-5 eslabones** como máximo; luego se **cierra** con una resolución
  (una deuda saldada, un rencor apagado o un feudo abierto).

---

## 2. Qué es un rumor

- Un **rumor** es **una frase suelta** que **abre un encargo oculto**: no es un tablón, es algo
  que alguien dice.
  - Un peregrino en el cruce: «Dicen que el herrero de Herreruela debe más de lo que tiene.»
  - Un posadero: «Los de la casa no han pagado a sus hombres en dos meses.»
- **La memoria los siembra:** quien te debe un favor o te tiene rencor **suelta el rumor** por
  donde pasas (`03_FAVORES.md`, `../sistemas/00_MEMORIA_Y_DEUDA.md` §7).
- Un rumor **no es información fiable**: puede ser verdad, a medias o una trampa. Confirmarlo es
  parte del encargo (`investigar`).

---

## 3. Cómo se encadenan sin guion fijo

Reglas deterministas (mismo guardado = mismas cadenas, RNG inyectado):

1. **De la deuda:** si un deudor no paga, su acreedor busca a alguien que cobre por él.
2. **Del rencor:** si un hecho enciende rencor (hecho 13, 11, 12), esa casa abre un `vengar`.
3. **Del favor:** quien te debe un favor puede **pagarlo** con un rumor o una puerta
   (`../sistemas/03_FAVORES.md`).
4. **Del mundo vivo:** las casas abren y cierran encargos solas cada temporada.

- **A mano solo se escriben:** las cadenas de la **columna** (`05_ENCARGOS_DE_LA_HISTORIA.md`) y
  unas pocas de escaparate. El resto, **generado**.

---

## 4. Ruido: cuántos caben sin marear

- **Rumores activos:** **1 por lugar** (y solo se oye al acercarte; no se apilan).
- **Cadenas abiertas:** máximo **3** a la vez; la cuarta **espera** hasta que cierres una.
- **Un rumor caduca a los 7 días** de juego: si no lo sigues, se enfría (y quizá el otro lo coge).
- **El jugador manda:** puede **ignorar** todo rumor sin penalización; el mundo sigue.

---

## 5. La Crónica como recordatorio

- Toda cadena abierta deja una línea en la **Crónica** (`../sistemas/04_CRONICA.md`): fecha, a
  quién afecta y qué queda por hacer.
- Así el jugador **no necesita memorizar** tres rumores: su propio diario se los recuerda.
- **Nunca** un aviso de sistema persigue al jugador con un rumor; la Crónica espera a que la lea.

---

## 6. Datos, tipos y validación

- **Datos (por crear):** `data/rumores.json` — `{ id, texto_txt, lugar, abre_encargo, caduca_dias, fuente }`.
  Las cadenas van en el campo `cadenas` de `data/encargos.json`.
- **Tipos:** `Rumor` y `Cadena` en `js/data/game_types.js` (una sola vez, regla 4).
- **Validación:** esquema en `js/data/schemas.js` + cruce de `abre_encargo` e ids de cadena en
  `tools/validate_data.js` (una cadena no puede apuntar a un encargo inexistente).
- **Sistema puro:** `js/systems/rumores.js` — siembra, caduca y encadena; sin DOM, sin reloj (día
  por día de juego), RNG inyectado.
- **Tests (por escribir):** `tests/rumores.test.js`, mínimo 3 casos (normal, borde, error): un rumor caduca a los
  7 días; no se superan 3 cadenas; una cadena sin salida no deja al jugador atrapado.

---

## 7. Cifras que fija este documento

| Cifra | Valor |
|---|---|
| Eslabones por cadena | **3-5** |
| Rumores activos | **1 por lugar** |
| Cadenas abiertas | máximo **3** |
| Caducidad de un rumor | **7 días** |
| Coste de ignorar | **0** |
| Determinismo | misma semilla + guardado = mismas cadenas |

---

## 8. Qué entra en la demo (Fase 1) — y qué sigue

> **Hasta aquí la demo.** **1 cadena** por sitio del Acto I (p. ej. el peaje → el viejo vuelve →
> su casa) y los rumores de la posada y el cruce, sembrados por la memoria de los 6 sitios.

> **Y sigue el juego completo.** Las cadenas de las casas rivales y el mundo vivo que las abre y
> cierra solo llegan con la Fase 2; las reglas (3-5, 1 por lugar, 3 abiertas, 7 días) **no
> cambian**.

---

## 9. Fuera de este documento

- Clases y choques de encargos → `00_TIPOS_DE_ENCARGO.md`
- Formato de datos → `02_ESTRUCTURA_DE_ENCARGO.md`
- Los encargos de la trama → `05_ENCARGOS_DE_LA_HISTORIA.md`
- La memoria que siembra → `../sistemas/00_MEMORIA_Y_DEUDA.md`
- El diario que las recuerda → `../sistemas/04_CRONICA.md`
