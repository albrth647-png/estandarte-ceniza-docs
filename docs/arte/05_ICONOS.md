# 05 · Iconos — leerse desde 48 px

**Estado:** ✅ **aprobado por el dueño (aprobación en bloque, 2026-09-30). Documento final.**

> Los iconos son **la interfaz que no habla**: órdenes, estados y objetos. Regla dura: deben
> entenderse **desde 48 px** (objetivo táctil mínimo, `../interfaz/00_CONTROLES.md`) y **sin
> depender del color** (`../interfaz/04_ACCESIBILIDAD.md` §2).

---

## 1. Familias de iconos

| Familia | Iconos | Dónde |
|---|---|---|
| **Órdenes** | Cargar · Seguirme · Defender | Barra de órdenes (`../batalla/04_PRESENTACION.md`) |
| **Combate** | Golpe · Guardia · Desvío · Habilidad | Botones del héroe (en arco) |
| **Estados** | Moral Firme/Quebrada/Rota · Deuda · Favor | HUD (`../interfaz/02_HUD.md`) |
| **Firma** | 7 bandas (una marca cada una) | HUD y Libro Mayor |
| **Objetos** | Arma · armadura · recurso · botín | Tienda, inventario, botín |
| **Mundo** | Interactuable · Peligro · Fuego | Sobre el objeto enfocado |

- **Una familia, un trazo:** todos los iconos comparten grosor y esquinas (`00_ESTILO.md`).

---

## 2. Reglas de diseño

1. **Silueta primero:** el icono se reconoce **en negro**; el color es refuerzo, no información.
2. **Un concepto por icono:** nada de iconos combinados.
3. **Sin texto dentro del icono** (el texto va al lado, como clave `txt_*`).
4. **Escala limpia:** se dibujan a **96 px** y se reducen a 48/56 sin perder forma.
5. **Estado por forma:** por ejemplo, la moral Rota **se parte**; no solo cambia de color.

---

## 3. Dónde se usan (y dónde no)

- **En el HUD y los paneles (DOM):** sí.
- **En el mundo:** solo el **aro** de interacción y el **chip** de capitanes
  (`../batalla/04_PRESENTACION.md` §2). **No** se llena el mundo de iconos flotantes.
- **No hay minimapa de iconos** en batalla (`../interfaz/06_MINIMAPA.md`).

---

## 4. Cifras y tamaños

| Uso | Tamaño |
|---|---|
| Objetivo táctil mínimo | **≥ 48 px** |
| Primario (órdenes, combate) | **≥ 56 px** |
| Icono dibujado (fuente) | 96 px, reducido |
| Separación con el vecino | **≥ 8 px** |
| Colores por icono | ≤ **2** + contorno |

---

## 5. Datos, tipos y validación

- **Datos:** `data/iconos.json` — `{ id, familia, forma, tinte, uso }`.
- **Tipos:** `Icono` en `js/data/game_types.js`.
- **Validación:** esquema + cruce con las familias de §1 y comprobación de que **ningún icono
  depende solo del color** (tiene `forma`).
- **Pintura:** DOM/CSS (sin imágenes, `../../THIRD_PARTY.md`); el sistema **no** conoce iconos.
- **Tests:** `tests/iconos.test.js`: todo icono tiene forma propia; tamaños ≥ 48; contraste mínimo
  (4,5:1) en el HUD.

---

## 6. Cifras que fija este documento

| Cifra | Valor |
|---|---|
| Familias | **6** |
| Tamaño mínimo | ≥ 48 px (primario ≥ 56) |
| Tamaño fuente | 96 px |
| Separación | ≥ 8 px |
| Colores por icono | ≤ 2 + contorno |
| Imágenes externas | **0** (DOM/CSS) |

---

## 7. Qué entra en la demo (Fase 1) — y qué sigue

> **Hasta aquí la demo.** Órdenes, combate, estados, las 7 bandas de Firma y los objetos básicos,
> legibles desde 48 px y con contraste.

> **Y sigue el juego completo.** Objetos, recursos y estados nuevos (clima, monturas) añaden
> iconos **con estas mismas reglas**; crecer = más filas en `iconos.json`, no un estilo nuevo.

---

## 8. Fuera de este documento

- Controles y tamaños → `../interfaz/00_CONTROLES.md`
- HUD → `../interfaz/02_HUD.md`
- Estilo y color → `00_ESTILO.md`
- Accesibilidad → `../interfaz/04_ACCESIBILIDAD.md`
