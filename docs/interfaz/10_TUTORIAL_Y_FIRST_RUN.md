# 10 · Tutorial y primer arranque — aprender sin manual

**Estado:** ✅ **aprobado por el dueño (2026-10-01, ronda 4-A). Documento final.**

> La batalla ya se enseña sola (`../batalla/04_PRESENTACION.md` §7); aquí se cierra **todo lo
> demás**: qué ve el jugador al abrir el juego por primera vez y cómo aprende el resto sin un muro
> de texto. Regla de la casa: **se aprende jugando, con una línea y 3 segundos**
> (`07_AVISOS_Y_RUMORES.md`). **Cifras de este documento son propuesta de diseño** (cambiables →
> `../DECISIONES.md`).

---

## 1. El principio: 4 reglas

1. **Nunca una pantalla de manual.** Si hay que leer un párrafo para jugar, el diseño ha fallado.
2. **Una idea por vez**, en **una línea**, **3 s**, por el canal de aviso están previstoste
   (`07_AVISOS_Y_RUMORES.md` §1). Nada de popups con «OK».
3. **Se enseña en el momento en que importa**: la lección sale **justo antes** de necesitarse, no
   en una lista al principio.
4. **Se puede volver a ver** (§5) y **se puede apagar** entera en Opciones (igual que la ayuda de
   batalla).

---

## 2. El primer arranque (pantalla por pantalla)

| # | Pantalla | Qué ve | Qué aprende |
|---|---|---|---|
| 1 | Portada | Título + una tecla | Por construir (diseño cerrado) |
| 2 | Menú | Continuar / nueva partida / opciones | Por construir (diseño cerrado) |
| 3 | **Crear partida** | Nombre, origen, dificultad | Un toque por casilla; los 3 orígenes explicados en **una línea** (`../sistemas/13_ESTADISTICAS_DEL_HEROE.md`) |
| 4 | **Prólogo** | La plaza del cadalso (`../historia/03_RECORRIDO.md` §2) | Que el mundo **recuerda** y que **debes** |
| 5 | **Primer paso** | La palanca se ilumina sola | **Mover** = palanca izquierda (`00_CONTROLES.md`) |
| 6 | **Primer mirar** | Un NPC con brillo suave | **Mirar** = centro de pantalla; acercarse desbloquea el saludo |
| 7 | **Primer toque** | «Toca para hablar» (una línea) | **Hablar** = un toque en el bocadillo |

- **Del minuto 0 al 5 no se explica nada más**: mover, mirar, hablar. Los otros gestos (correr,
  desvío, inventario) salen **cuando hagan falta**, igual que en la batalla.
- El prólogo es **narrativa, no tutorial**: solo se enseña lo que la escena ya pide
  (`../historia/03_RECORRIDO.md`).

---

## 3. Las 8 lecciones del juego (y cuándo salen)

| # | Lección | Se dispara cuando… | Texto (1 línea, ejemplo) |
|---|---|---|---|
| 1 | Moverte | primer arranque | «La palanca te lleva: márvala y camina.» |
| 2 | Mirar | primer NPC en la mirada | «Acerca la mirada para oír a la gente.» |
| 3 | Hablar | primer NPC a alcance | «Un toque en su cara y hablas.» |
| 4 | El tablón | primer tablón a la vista | «Aquí se cobra la deuda: coge un encargo.» |
| 5 | El registro | primer cobro | «Todo lo que pasa queda en tu Registro.» |
| 6 | Dar una orden | primera batalla (fase 2) | «Toca tu bandera: tu gente obedece de golpe.» |
| 7 | El aliento | primer Desvío fallido | «Gastas aliento al defenderte: mídelo.» |
| 8 | La deuda | primera derrota | «Caíste. Te rescatan o trabajas la deuda.» |

- **Son 8, no 30.** Cualquier otra enseñanza se mete **dentro** de una de las 8 lecciones.
- **Orden fijo** en el registro de lecciones, pero **el disparo es por evento**: si el jugador ve
  la lección 6 antes que la 5 (batea antes de cobrar), no se rompe nada.

---

## 4. Cómo se muestra

- **Canal:** aviso de sistema de `07_AVISOS_Y_RUMORES.md` (borde superior, **3 s**, una idea).
- **Icono + texto** (nunca solo color, `../arte/05_ICONOS.md`).
- **Máximo 1 lección a la vez**: si coinciden, se espera a que se vaya la anterior.
- **Nunca en mitad de una acción**: si el jugador está corriendo o peleando, la lección **espera**
  (la de la batalla entra en la fase de despliegue, no en el choque).
- **Destello mínimo** en el elemento del que habla (≤ 3 Hz, `04_ACCESIBILIDAD.md`).

---

## 5. Repetir y desactivar

- **Repetir:** en la pausa hay una lista **«Volver a ver»** con las lecciones ya vistas
  (máximo **8** de la tabla §3); cada una se reproduce igual, de 3 s.
- **Olvidar:** una lección se marca «vista» tras mostrarse **1 vez completa**; no vuelve a salir
  sola.
- **Apagar:** Opciones → «Ayuda: al principio / siempre / nunca» (por defecto **al principio**).
  Con «nunca» desaparecen también las de batalla (misma llave).
- **Olvidar no bloquea nada:** si el jugador la apaga sin haber aprendido, el juego sigue siendo
  jugable; la ayuda está en «Volver a ver».

---

## 6. Datos, tipos y validación

- **Datos (por crear):** `data/tutoriales.json` — `{ id, orden, disparador, txt_es, txt_en }` con sus **8**
  filas; sin lógica en el JSON.
- **Tipos:** `Tutorial` en `js/data/game_types.js` (regla 4).
- **Sistema puro:** `js/systems/tutorial.js` — dada la lista de eventos y las vistas, devuelve la
  lección a mostrar (o `null`); **sin DOM, sin reloj**, el evento entra por parámetro.
- **Guardado:** `SaveState.tutoriales = { vistas: [], ayuda: "inicio" }` — **aditivo**
  (bandera aditiva, `../produccion/02_GUARDADO_Y_DATOS.md`); la migración lo rellena vacío.
- **Validación:** esquema en `js/data/schemas.js` + cruce de `id` y paridad ES/EN en
  `tools/validate_data.js` (regla 10).
- **Tests (por escribir):** `tests/tutorial.test.js`, mínimo 3 casos (normal, borde, error): una lección vista no
  se repite; dos disparos a la vez encolan una; un evento desconocido no rompe.

---

## 7. Cifras que fija este documento

| Cifra | Valor |
|---|---|
| Lecciones del juego | **8** |
| Duración | **3 s** · 1 línea · 1 idea |
| A la vez | **1** (nunca apiladas) |
| Pantalla de manual | **0** |
| Repeticiones | **8** en «Volver a ver» (1 entrada por lección) |
| Desactivación | 1 llave en Opciones (3 estados) |
| Guardado | versionado aditivo |

---

## 8. Qué entra en la demo (Fase 1) — y qué sigue

> **Hasta aquí la demo.** Las **8 lecciones** de la tabla §3 con su disparador, «Volver a ver» y
> la llave de Opciones; primer arranque completo del §2 (crear partida → prólogo → mover/mirar/
> hablar) sobre las pantallas del armazón actual.

> **Y sigue el juego completo.** Si una fase nueva necesita una enseñanza, **entra en la lista de
> 8 como otra más** (o se amplía una de las 8); el canal, la duración de 3 s y la llave de
> Opciones **no cambian**. Crecer = más filas en `tutoriales.json`, no un sistema nuevo.

---

## 9. Fuera de este documento

- Cómo se enseña la batalla → `../batalla/04_PRESENTACION.md` §7
- Gestos y palanca → `00_CONTROLES.md`
- Mapa de pantallas → `01_PANTALLAS.md`
- Canal de avisos → `07_AVISOS_Y_RUMORES.md`
- Accesibilidad (parpadeo, texto) → `04_ACCESIBILIDAD.md`
- Los primeros 30 minutos (narrativa) → `../historia/03_RECORRIDO.md` §2
- Avisos de contenido → `11_AVISOS_DE_CONTENIDO.md`
