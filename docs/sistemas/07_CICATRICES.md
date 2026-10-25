# 07 · Cicatrices — las marcas que el mundo comenta

**Estado:** ✅ **aprobado por el dueño (aprobación en bloque, 2026-09-30). Documento final.**

> En Valcoria, la cicatriz **no es vergüenza: es tu crédito** (`../historia/00_PREMISA.md`). La
> **marca del cadalso** ya la llevas desde el prólogo; aquí se rige el resto: las heridas que
> ganan historia y cómo el mundo las comenta.

---

## 1. Tipos de marca

| Marca | De dónde | Qué dice el mundo |
|---|---|---|
| **Marca del cadalso** | La sentencia (prólogo) | «Ese es el del Paso»: sube el miedo y la Firma pública |
| **Cicatriz de batalla** | Heridas graves en el campo | Los veteranos te reconocen |
| **Marca de deuda** | Un feudo o un cobro por la fuerza | Algunas casas te cierran la puerta |
| **Cicatriz de honor** | Un rescate o un perdón | Los que te deben lo recuerdan |

- **Toda marca es visible** (`../arte/00_ESTILO.md` §4) y **el mundo la comenta** según su memoria.

---

## 2. Cuándo se gana una cicatriz

- **Batalla:** al caer por debajo del **25 % de vida** y sobrevivir, o al caer y ser rescatado
  (`../sistemas/02_PRISIONEROS.md` §7). Se marca a **1 por batalla** como máximo.
- **Feudo o cobro:** cuando ejerces la fuerza o ejecutas a un rendido (memoria en contra).
- **Honor:** cuando perdonas a un capitán o rescatas sin cobrar (`01_FIRMA.md` §4).
- **Sin aleatoriedad injusta:** la cicatriz nace de lo que hiciste, no de una tirada.

---

## 3. Efecto en el juego

- **La marca del cadalso:** activa desde el Día 1; algunos te temen (sube el precio de huida
  enemiga) y otros te cierran puertas (`01_FIRMA.md` §6).
- **Comentarios:** un PNJ puede **mencionar una cicatriz** al saludarte (bocadillo,
  `../interfaz/07_AVISOS_Y_RUMORES.md`); nunca un aviso de sistema.
- **No hay bonus ocultos:** las cicatrices **informan** memoria y Firma; no dan stats.

---

## 4. Datos, tipos y validación

- **Datos:** `data/cicatrices.json` — `{ id, tipo, origen, efecto, comentario_txt }`.
- **Tipos:** `Cicatriz` en `js/data/game_types.js`.
- **Validación:** `comentario_txt` con pareja ES/EN; cruce del `origen` con los hechos de memoria y
  Firma (`tools/validate_data.js`).
- **Sistema puro:** `js/systems/cicatrices.js` — concede y consulta; sin DOM ni reloj.
- **Tests:** `tests/cicatrices.test.js`: no se gana más de 1 por batalla; una cicatriz no da stats;
  la marca del cadalso existe desde el Día 1.

---

## 5. Cifras que fija este documento

| Cifra | Valor |
|---|---|
| Tipos de marca | **4** |
| Cicatrices por batalla | ≤ 1 |
| Umbral de herida de batalla | **< 25 % de vida** |
| Efecto directo | solo memoria/Firma (nunca stats) |
| Comentarios | bocadillo, nunca aviso |

---

## 6. Qué entra en la demo (Fase 1) — y sigue

> **Fuera de la demo (Fase 2).** En el Acto I solo se ve la **marca del cadalso** como elemento
> de prólogo y de diálogo (`../historia/03_RECORRIDO.md`); este sistema **no se construye** hasta
> el Acto II (recorte de `../produccion/00_ALCANCE.md` §5, 2026-10-02).

> **Y sigue el juego completo.** Las **marcas de deuda** de feudos y casas se añaden en la **Fase
> 2** con estas mismas reglas; crecer = más filas en `cicatrices.json`, sin efectos ocultos.

---

## 7. Fuera de este documento

- La marca narrativa → `../historia/00_PREMISA.md`
- Firma y memoria → `01_FIRMA.md`, `00_MEMORIA_Y_DEUDA.md`
- Caer y rescate → `02_PRISIONEROS.md`
- Estilo de la marca → `../arte/00_ESTILO.md`
