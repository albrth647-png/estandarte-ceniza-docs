# 04 · Presentación — cómo se ve y se toca el campo

**Estado:** ✅ **aprobado por el dueño (aprobación en bloque, 2026-09-30). Documento final.**

> Decidido: **1.ª persona pura**, **barra de órdenes (tropas) + botones de combate (héroe)**
> (`00_REGLAS.md`). Este documento dice **cómo se ve, se oye y se toca** la batalla; la
> **simulación** vive en `00_REGLAS.md`, `01_CIFRAS.md`, `02_TERRENO.md` y `03_IA_Y_ORDENES.md`
> y **no cambia por esto**. Todo efecto visual o sonoro vive **solo** en las escenas
> (`js/scenes/*`), nunca en `js/systems/*` (regla 11 de `../../AGENTS.md`).

---

## 1. La pantalla de batalla (sin tapar el centro)

Se respeta el HUD de `../interfaz/02_HUD.md` §3: el **centro es sagrado** (ahí está tu mirada y
el enemigo).

| Zona | Qué se pone | Tamaño |
|---|---|---|
| **Arriba-izq.** | Moral propia (banda + gente que la sostiene) y **vida del héroe** | franjas de 8 px |
| **Arriba-der.** | **Moral enemiga** (rota = victoria) y capitanes enemigos visibles | franjas de 8 px |
| **Franja central inferior** | **Barra de órdenes** (Cargar / Seguirme / Defender + quién acata) | botones ≥ 56 px |
| **Inferior der., en arco** | **Botones del héroe**: Golpe · Guardia · Desvío · Habilidad | ≥ 56 px |
| **Inferior izq.** | **Palanca** (sigues siendo una unidad, `../interfaz/00_CONTROLES.md`) | 120×120 px |
| **Centro** | **Nada fijo**: solo el retículo y lo que aparece y se va | — |

- **Sin minimapa en batalla**: el campo se lee con los ojos, no con un plano.
- **Sin barras de vida por unidad**: la moral del bando resume cómo va la pelea; las unidades
  heridas **cojean y sangran** (efecto, §4).

---

## 2. La información mínima

Lo que el jugador **necesita** para decidir, y nada más:

1. **¿Voy ganando?** → la **moral** de los dos bandos (no las bajas).
2. **¿Me quedan tropas?** → el **número de quién acata** la orden vigente en la barra.
3. **¿Estoy en peligro?** → la **vida del héroe** solo aparece cuando baja del 50 %
   (`../interfaz/02_HUD.md` §5).
4. **¿Quién es quién?** → **chip con su nombre y banda** solo sobre **capitanes con memoria**;
   el resto son tropa rasa sin etiqueta.

- La moral se muestra como **banda** (Firme / Quebrada / Rota), no como número, salvo en la
  Crónica y el Libro Mayor.

---

## 3. Los avisos

Los avisos **nunca tapan la acción**: entran por el borde, duran **3 s** y se van solos
(regla del HUD).

| Aviso | Cuándo | Texto |
|---|---|---|
| **Moral quebrándose** | baja de 40 | «La moral se quiebra» |
| **Un tercio roto** | pánico en cadena | «Tres huyen: se deshacen» |
| **Orden cumplida** | la tropa reagrupa sin coste | «Aguardan» |
| **Capitán en el campo** | aparece el primero | «Ojo: <nombre>» |
| **Ventaja de carga** | entras a cargar | (sin texto: solo el sonido y la sacudida) |

- **El silencio también avisa:** cuando la moral enemiga se rompe, **calla la música** un
  instante antes del grito de victoria (`../arte/02_AUDIO.md`).

---

## 4. Los efectos (solo en escena)

Viven **únicamente** en la escena de batalla; el motor puro no los conoce (regla 11):

| Efecto | Qué es | Presupuesto |
|---|---|---|
| **Impactos** | chispa de acero, polvo al pisar, salpicadura en el vado | ≤ 60 partículas a la vez |
| **Sangre** | manchas cortas; **sin gore** (edad del juego, `../produccion/06_LEGAL_Y_AUTORIA.md`) | ≤ 30 |
| **Sacudida de cámara** | golpe recibido, carga, caída | ≤ 6 px · **desactivable** |
| **Daño flotante** | solo golpes del héroe | ≤ 8 en pantalla |
| **Humo y fuego** | zonas de riesgo (`02_TERRENO.md` §7) | ≤ 3 focos |

- **Prueba de rendimiento:** 10+10 unidades + 4 puntos de interés + efectos a **60 fps** en gama
  media (`../mundo/01_EXPLORACION.md` §7). Si no cabe, se recorta **partícula**, nunca
  información de juego.
- Cómo se ve todo esto → `../arte/00_ESTILO.md` y `../arte/04_EFECTOS_Y_PARTICULAS.md`.

---

## 5. La cámara (1.ª persona pura)

- La cámara **es tu cabeza**: altura de ojos 1,65 m, FOV 70° (`../mundo/01_EXPLORACION.md` §2).
  En batalla **no hay** vista táctica ni cenital.
- **Mirar:** arrastrar en la zona libre; **enfocar** a capitanes o al enemigo más cercano a
  < 45° (250 ms, `../mundo/01_EXPLORACION.md` §5).
- **No ves lo que no miras:** por eso la **moral** y el **número de quién acata** están en el
  HUD — son tu «mirada de reojo».
- **Verificación de combate:** si dos o más unidades enemigas salen de tu campo de visión y la
  moral de tu bando no baja, un aviso suave («Te flanquean») entra por el borde **como pista**,
  nunca como flecha en pantalla.
- La sacudida y el balanceo son **apagables** (`../interfaz/04_ACCESIBILIDAD.md`).

---

## 6. Cambiar de orden y el reloj

- Abrir la **barra de órdenes** atenúa el reloj al 25 % y **desenfoca** el centro con una viñeta
  suave (no borra el campo). Confirmar devuelve el 100 % durante 1 s («el golpe»).
- La orden vigente se queda **marcada** en la barra; el resto se apaga. No hay menús anidados
  (`../interfaz/00_CONTROLES.md` §1): dar una orden es **un toque**.

---

## 7. Enseñar a jugar sin tutorial

La **primera batalla** enseña sola, con la presentación:

1. **Aviso (fase 1):** quien contra quién y dónde — y **qué terreno pisas** (`02_TERRENO.md`).
2. **Despliegue (fase 2):** tus tropas se colocan a la vista; tú ya llevas la palanca.
3. **Primer golpe:** el enemigo viene a alcance; el botón **Golpe** se ilumina.
4. **Primera orden:** la moral enemiga se quiebra con **Cargar**; el aviso «Tres huyen» explica
   la victoria sin texto de manual.
5. **Nadie explica las reglas con un muro de texto:** se aprenden peleando (Pilar 6).

- La ayuda contextual es **de una línea y 3 s**; se puede desactivar entera en Opciones.

---

## 8. Datos, tipos y validación

- Pintura en la escena de batalla (por construir) con el kit de DOM (`dom_kit.js`, por crear) y el render
  3D (por construir); **nada** de esto entrará en la simulación.
- Claves `txt_bat_*` en `strings_es.json` / `strings_en.json` con **paridad obligatoria**
  (regla 10).
- Los efectos se prueban en `tests/scene_battle.test.js` (pintura, avisos, estados) y su coste con
  `npm run smoke`.

---

## 9. Cifras que fija este documento

| Cifra | Valor |
|---|---|
| Zona central | libre de HUD fijo |
| Objetivos táctiles | ≥ 48 px · botones de combate y órdenes ≥ 56 px |
| Avisos | entran por el borde · duran **3 s** · no tapan la acción |
| Ayuda contextual | 1 línea · 3 s · desactivable |
| Partículas | ≤ 60 impactos · ≤ 30 sangre · ≤ 8 daños flotantes · ≤ 3 fuegos |
| Sacudida | ≤ 6 px · desactivable · balanceo desactivable |
| Reloj al abrir órdenes | 25 % · confirmar 100 % 1 s |
| Objetivo de render | 60 fps con 10+10 y 4 puntos de interés |
| Puntos de interés | ≤ 4 por campo (`02_TERRENO.md`) |

---

## 10. Qué entra en la demo (Fase 1) — y qué sigue

> **Hasta aquí la demo.** Las **dos mitades del HUD** de batalla (moral y quién acata) y las de
> exploración, los **3 botones de combate** más la Habilidad, la barra de órdenes y los avisos
> por construir en los **3 campos** con **5-6 por bando** (8 en el cierre). Escalado a verificar en
> 960×683 y 960×540.

> **Y sigue el juego completo.** Con **10+ por bando** la presentación **no cambia**: mismas
> franjas, mismos avisos, mismo presupuesto. Si el rendimiento aprieta, se recortan partículas
> y densidad — **nunca** información de juego (moral, quién acata, vida).

---

## 11. Fuera de este documento

- Reglas y fases → `00_REGLAS.md`
- Cifras → `01_CIFRAS.md`
- Terreno y cobertura → `02_TERRENO.md`
- IA, órdenes y avisos de orden → `03_IA_Y_ORDENES.md`
- HUD completo de ambas caras → `../interfaz/02_HUD.md`
- Gestos y botones → `../interfaz/00_CONTROLES.md`
- Estilo, efectos y audio → `../arte/00_ESTILO.md`, `../arte/04_EFECTOS_Y_PARTICULAS.md`,
  `../arte/02_AUDIO.md`
