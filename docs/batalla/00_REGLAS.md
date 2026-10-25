# 00 · Reglas — el campo de batalla

**Estado:** ✅ **aprobado por el dueño (aprobación en bloque, 2026-09-30). Documento final.**

> Pilar 6 cerrado: **semi-tiempo real**, **eres una unidad más**, **1.ª persona pura**,
> órdenes globales y sin micromando. Describe el **juego completo** (10+ por bando); la demo
> recorta a 5-6 con estas mismas reglas. Las cifras están en `01_CIFRAS.md`.

---

## 1. Cómo se llega aquí

Un encuentro en el camino o en el mundo (`../mundo/02_VIAJE_Y_ENCUENTROS.md`) abre un **campo
de batalla formado por el terreno** del sitio donde estás (`02_TERRENO.md`). No hay dos campos
iguales: llanura de camino, bosque, aldea, vado o puerta de ciudad.

---

## 2. Las cinco fases

| Fase | Duración | Qué pasa |
|---|---|---|
| **1 · Aviso** | 2 s | Quién contra quién y dónde; botón «Preparado» (o espera de 10 s) |
| **2 · Despliegue** | 5 s | Tu gente ocupa su posición; en **emboscada** no hay despliegue: empiezas rodeado |
| **3 · Combate** | 90–240 s | Fases reales del apartado §3 |
| **4 · Ruptura** | — | La moral enemiga se rompe: **huyen, se rinden o se desbandan** |
| **5 · Post-batalla** | libre | Las **4 salidas** del prisionero (`../sistemas/02_PRISIONEROS.md`) |

**La victoria es romper la moral, no aniquilar.** Un bando sin gente viva pero con moral
íntegra sigue en pie; un bando con tres huidos se cae.

---

## 3. Semi-tiempo real

| Situación | Reloj |
|---|---|
| Combate normal | **100 %** |
| Abres la barra de órdenes | **25 %** (el tiempo se atenúa para que pienses) |
| Confirmas una orden | **100 %** durante 1 s («el golpe»: tu orden entra en marcha) |
| Pausa total | **no existe** — el mundo nunca se detiene del todo |

---

## 4. Eres una unidad más

- Mismos puntos de vida, mismo daño, mismo alcance que tus tropas de la misma línea.
  No eres intocable ni invencible: **si caes, se activa el Pilar 3** (rescate, cautiverio o
  que un aldeano te arrastre) y la partida **nunca** se atasca.
- Te mueves con la palanca, miras arrastrando y golpeas con tus botones
  (`../interfaz/00_CONTROLES.md`): sigues siendo un peón del campo, no una torre.
- Los enemigos **pueden dirigirse a ti** con preferencia si te conocen (Firma o memoria
  personal: los que te odian te buscan).

---

## 5. Tus botones (héroe)

| Botón | Qué hace |
|---|---|
| **Golpe** | Ataque cuerpo a cuerpo con tu arma (cadencia y daño en `01_CIFRAS.md`) |
| **Guardia** | Bloquea durante su ventana; reduce el daño recibido 75 % |
| **Desvío** | Paso lateral con invulnerabilidad breve; gasta aliento |
| **Habilidad** | Abre la tira de habilidades (`../contenido/06_HABILIDADES.md`): el tronco por nivel y los nodos elegidos del árbol |

---

## 6. Órdenes globales (tropas)

Tres órdenes, **para todo tu bando a la vez** — no se seleccionan unidades individuales:

| Orden | Efecto |
|---|---|
| **Cargar** | Avance rápido contra el enemigo; moral +10 al recibirla; más bajas esperables |
| **Seguirme** | Te forman en torno a ti y se mueven con tu mirada |
| **Defender** | Mantienen posición; ganan defensa y no persiguen |

La barra de órdenes está siempre a la vista (`../interfaz/02_HUD.md`); abrirla ralentiza el
reloj (§3).

---

## 7. IA propia (sin micromando)

Cada unidad decide por su cuenta cada **0,5 s**: enemigo más cercano a su alcance, distancia,
moral propia y la orden global vigente. Con «Defender» no persigue; con «Cargar» sí. Nadie
espera tu permiso para defenderse — y nadie obedece si su moral está rota.

---

## 8. Moral: el verdadero marcador

- Todo empieza en **100** (unidades y bandos por separado).
- **Baja** por: muerte cercana, huida de un aliado, quedar en inferioridad, y —contra una
  Firma temible— **se rompe antes** (`../sistemas/01_FIRMA.md` §3).
- **Se rompe a 0** → la unidad huye; con miedo (Fiera/Hiena) se rompe al llegar a **10**.
- Si se rompe **un tercio** del bando → **pánico en cadena**: es el «**tres huyen**» que abre
  la rendición.
- Los **capitanes** tienen moral propia y su ruptura pesa el doble en su gente.
- Recuperación en combate: **+2/s** si el capitán o el héroe está a menos de 8 m, y **+2/s**
  más mientras no recibas daño (hasta **+4/s** combinados).

---

## 9. Fin de batalla

1. Moral enemiga rota → la mitad huye, el resto se rinde.
2. **Nadie muere «definitivamente» en el campo**: muerte de tropa = baja de campaña (se paga
   con `../sistemas/08_LUTO_Y_MORAL.md`), muerte de capitán = crónica y memoria.
3. Pasas a las salidas con los prisioneros (`../sistemas/02_PRISIONEROS.md`).
4. Si **caes tú**, el mundo decide y siempre hay salida (§4).

---

## 10. Motor y reglas duras

- **Prototipo nuevo**: `js/systems/campo.js` (por construir), **puro** — sin DOM, sin fetch, sin reloj; `dt`
  y RNG **inyectados** (reglas 2 y 11 de `../../AGENTS.md`). El motor táctico antiguo no se
  resucita (`../DECISIONES.md` 2026-09-30).
- La simulación **no** pinta: las escenas (HUD, partículas, cámara) están en
  `../batalla/04_PRESENTACION.md`.
- **Determinismo:** misma semilla + mismas decisiones = misma batalla.
- **Presupuesto:** 10+10 unidades + campo + props a 60 fps en gama media.
- Tests: `tests/campo.test.js`, mínimo 3 casos (normal, borde, error) y cobertura ≥ 90 %.

---

## 11. Qué entra en la demo (Fase 1)

- Las 5 fases, semi-tiempo real, los botones del héroe (Golpe / Guardia / Desvío) y las 3 órdenes: **todo**.
- **5-6 por bando** (8 en la batalla de cierre), **3 campos** (llanura de camino, aldea y
  bosque), **4+ capitanes** con memoria, **3 familias enemigas**.
- Igual que el juego completo en reglas; solo cambia la **cantidad** de unidades.

---

## 12. Fuera de este documento

- Todas las cifras → `01_CIFRAS.md`
- Terreno y campos → `02_TERRENO.md`, `05_CATALOGO_DE_CAMPOS.md`
- IA en detalle y órdenes → `03_IA_Y_ORDENES.md`
- Cómo se ve y se oye → `04_PRESENTACION.md`
- Prisioneros y las 4 salidas → `../sistemas/02_PRISIONEROS.md`
- Cómo se dispara un encuentro → `../mundo/02_VIAJE_Y_ENCUENTROS.md`
