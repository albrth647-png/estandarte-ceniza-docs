# 04 · Efectos y partículas — el golpe que se siente

**Estado:** ✅ **aprobado por el dueño (aprobación en bloque, 2026-09-30). Documento final.**

> Todo efecto vive **solo en las escenas**, nunca en `js/systems/*` (regla 11 de
> `../../AGENTS.md`). Los topes de pantalla los fija `../batalla/04_PRESENTACION.md` §4; aquí se
> detalla **qué efecto, cuándo y a qué coste**.

---

## 1. Catálogo de efectos

| Efecto | Cuándo | Tipo |
|---|---|---|
| **Impacto de acero** | Golpe que conecta | Chispa breve |
| **Polvo** | Pisada fuerte, carga, caída | Partículas de suelo |
| **Sangre** | Golpe recibido (sin gore) | Mancha corta |
| **Salpicadura** | Vado / orilla | Gotas |
| **Humo y fuego** | Zona de riesgo, aldea | Foco continuo |
| **Daño flotante** | Solo golpes del héroe | Número flotante |
| **Sacudida de cámara** | Golpe, carga, caída | Desplazamiento ≤ 6 px |
| **Ruido** | Al caminar, al caer | (sonido, `02_AUDIO.md`) |

- **Tono sobrio:** la sangre **mancha**, no salpica a chorros. Nada de gore (edad del juego,
  `../produccion/06_LEGAL_Y_AUTORIA.md`).

---

## 2. Presupuesto (topes de pantalla)

| Efecto | Máximo a la vez |
|---|---|
| Impactos | **60** |
| Sangre | **30** |
| Daños flotantes | **8** |
| Focos de fuego | **3** |
| Sacudida | **6 px** (desactivable) |

- **Si no cabe, se recorta partícula, nunca información** (moral, vida, quién acata).
- **La hierba no lleva sombra propia** (`../mundo/07_PROPS_Y_VEGETACION.md` §2).

---

## 3. Cuándo aparecen (y cuándo no)

- **Solo lo que el jugador debe notar:** un golpe, una carga, un peligro de terreno.
- **Nada de efectos por decoración:** si un efecto no cambia decisiones, no entra.
- **El jarro de agua fría:** los momentos de deuda y muerte **quitan** efectos y música, no añaden
  (`../batalla/04_PRESENTACION.md` §3).

---

## 4. Accesibilidad

- **Sacudida** y **daño flotante** apagables (`../interfaz/04_ACCESIBILIDAD.md`).
- **Sangre** puede reducirse a «marca de golpe» sin color rojo (daltonismo).
- **Parpadeo** de fuego ≤ **3 Hz** (riesgo fotosensible).

---

## 5. Datos, tipos y validación

- **Datos:** `data/efectos.json` — `{ id, tipo, presupuesto, duracion_ms, ajuste_accesibilidad }`.
- **Tipos:** `Efecto` en `js/data/game_types.js`.
- **Validación:** esquema + cruce de presupuestos con `../batalla/04_PRESENTACION.md` en
  `tools/validate_data.js`.
- **Sistema/escena:** el sistema **emite eventos** («golpe», «carga»); la **escena** los pinta. El
  motor puro no conoce partículas.
- **Tests:** `tests/efectos.test.js`: no se superan los topes; apagar efectos no rompe la escena;
  el sistema no importa nada de `js/scenes/*`.

---

## 6. Cifras que fija este documento

| Cifra | Valor |
|---|---|
| Impactos | ≤ 60 |
| Sangre | ≤ 30 |
| Daños flotantes | ≤ 8 |
| Focos de fuego | ≤ 3 |
| Sacudida | ≤ 6 px · desactivable |
| Parpadeo | ≤ 3 Hz |
| Efectos en `js/systems/` | **0** |

---

## 7. Qué entra en la demo (Fase 1) — y qué sigue

> **Hasta aquí la demo.** Impactos, polvo, sangre sobria, daño flotante y sacudida en los 2 campos
> y en los 6 sitios, con los topes de §2 y las opciones de accesibilidad.

> **Y sigue el juego completo.** Fuego, agua y criaturas añaden focos y gotas **dentro de los
> mismos topes**; si el rendimiento aprieta, se recorta partícula, nunca información.

---

## 8. Fuera de este documento

- Pantalla de batalla y topes → `../batalla/04_PRESENTACION.md`
- Estilo y color → `00_ESTILO.md`
- Audio → `02_AUDIO.md`
- Accesibilidad → `../interfaz/04_ACCESIBILIDAD.md`
