# 05 · Casas y facciones — quién manda en Valcoria

**Estado:** ✅ **aprobado por el dueño (aprobación en bloque, 2026-09-30). Documento final.**

> Bajo la Ordenanza (`00_PREMISA.md`), las **casas** son acreedoras y deudoras entre sí; los
> **Escribanos** escriben; y la **otra ribera** vive fuera del libro. Toda facción **tiene memoria
> de ti** (`../sistemas/00_MEMORIA_Y_DEUDA.md` §9). Nombres provisionales (cambiables →
> `../DECISIONES.md`).

---

## 1. Las facciones

| Facción | Qué es | Qué quiere | Memoria de ti |
|---|---|---|---|
| **Casa Altamir** | La casa de los peajes; dueña del camino | Conservar el paso y que nadie mire el libro | **Media ponderada** de sus miembros |
| **La Escribanía** | El cuerpo de los Escribanos de la Sangre | Que la cuenta cuadre | Conocida + Correcto y deudas |
| **La otra ribera** | Libres del paso; sin escribano | Que el libro no vuelva a cruzarlo | Fanáticos: no se rinden |
| **Doña Sira** | Escribana viuda, tu acreedora | Verdad de la puerta y cobrar lo de los cuarenta | Su memoria manda en tu partida |
| **Los Marcados** | Tu compañía de deudores | Saldar su cuenta sirviendo | Lealtad y moral propias |
| **Casas menores** | Feudos, gremios, molinos | Su parte del peaje | Por casa |

---

## 2. Casa Altamir (la antagonista de sistema)

- Necesitaba **muertos** a los cuarenta (sabían que el paso no era suyo y venía el día de pagarles)
  y **contratos anulados** (la traición anula contratos bajo la Ordenanza → no debían nada).
- **No es mala por gusto:** es la casa que `00_MEMORIA_Y_DEUDA.md` pone de ejemplo en la herencia
  (padre → hijo) y la que el juego trata como **familia** con su propia memoria.
- Su **heráldica** vive en `../contenido/15_ESTANDARTES_E_INSIGNIAS.md`.

---

## 3. Cómo se hereda la memoria de una casa

- La casa hereda la memoria de sus miembros con **media ponderada** (`00_MEMORIA_Y_DEUDA.md` §9):
  matar a uno pesa, pero no borra a los demás.
- **Rencores de sangre** marcan a toda la casa (`00_MEMORIA_Y_DEUDA.md` §7): una casa con rencor
  queda, para ti, **Enemigo mínimo**.
- **Casas que se apagan:** si no queda nadie con su apellido, la deuda **se extingue** (por eso los
  Escribanos marcan la piel).

---

## 4. Faccciones y el fin del juego

- En la **asamblea** (Acto III, `01_ESTRUCTURA.md`), cada facción lee su memoria de ti y decide:
  apoyarte, callar o cobrarte.
- **Doña Sira** y los **Escribanos** son el eje; la otra ribera y los Marcados, la fuerza.
- Los **3 finales** cambian qué facción manda después (pagar: la Escribanía; cobrar: tú; quemar:
  nadie).

---

## 5. Datos, tipos y validación

- **Datos:** `data/facciones.json` — `{ id, tipo (casa/escribania/ribera/compañia), miembros,
  heraldica, memoria_peso, quiere }`.
- **Tipos:** `Faccion` en `js/data/game_types.js`.
- **Validación:** cada `miembro` existe en `data/pnj.json`; la `heraldica` existe en
  `data/estandartes.json` (`tools/validate_data.js`).
- **Sistema puro:** la memoria de casa se calcula en `js/systems/memoria.js`; sin DOM ni reloj.
- **Tests:** `tests/facciones.test.js`: una casa con rencor queda Enemigo; una casa sin miembros se
  extingue; la media ponderada no supera el rango de su miembro más extremo.

---

## 6. Cifras que fija este documento

| Cifra | Valor |
|---|---|
| Facciones | **6** (Altamir · Escribanía · ribera · Sira · Marcados · casas menores) |
| Memoria de casa | media ponderada de sus miembros |
| Rencores de casa | Enemigo mínimo |
| Herencia | hijo 100 % · casa 50 % |
| Extinción | sin apellido, se extingue |

---

## 7. Qué entra en la demo (Fase 1) — y qué sigue

> **Hasta aquí la demo.** **Casa Altamir**, la **Escribanía**, **Doña Sira** y los **Marcados**,
> con su memoria y su presencia en los 6 sitios; la ribera se **menciona** (no se visita).

> **Y sigue el juego completo.** Las **casas menores** y la **otra ribera** se añaden en la
> **Fase 2** con la misma herencia de memoria; crecer = más filas en `facciones.json`.

---

## 8. Fuera de este documento

- La Ordenanza → `00_PREMISA.md`
- El elenco → `02_PERSONAJES.md`
- Memoria y herencia → `../sistemas/00_MEMORIA_Y_DEUDA.md`
- Heráldica → `../contenido/15_ESTANDARTES_E_INSIGNIAS.md`
- Los finales de facción → `01_ESTRUCTURA.md`
