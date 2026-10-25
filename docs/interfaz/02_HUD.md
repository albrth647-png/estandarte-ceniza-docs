# 02 · HUD — lo que se ve mientras juegas

**Estado:** ✅ **aprobado por el dueño (aprobación en bloque, 2026-09-30). Documento final.**

> Describe la capa de interfaz del **juego completo** en sus dos momentos: exploración y
> batalla. Los gestos están en `00_CONTROLES.md`; las pantallas completas en `01_PANTALLAS.md`.

---

## 1. Reglas de casa

1. **El centro es sagrado:** nada fijo se pinta en la mitad central de la pantalla (ahí está
   la mirada y el objetivo).
2. **Menos es más:** lo que no hace falta **no se pinta**; la información importante entra y
   sale, no se apila.
3. Todo texto se lee a **320 px** de ancho de fuente y todo botón mide **≥ 48 px**.
4. Los avisos **nunca** tapan la acción: entran por el borde y se van solos (§5).
5. El HUD es **DOM** (capa `#ui` sobre el lienzo), no se dibuja en el canvas.

---

## 2. HUD de exploración

| Pieza | Situación | Qué dice |
|---|---|---|
| **Oro y deuda** | Arriba-izq. | Oro en bolsa; si debes, el importe en rojo con su marca |
| **Día** | Arriba-izq., bajo el oro | Día de juego (p. ej. «Día 12») |
| **Firma** | Arriba-der. | **Nombre de la banda** (nunca el número): «Sin nombre», «Duro»… |
| **Punto de interacción** | Centro-bajo del punto de mira | Aparece solo con algo toquible a < 2,5 m |
| **Botones fijos** | Inferior der. | Acción y secundario (el de correr va junto a la palanca, `00_CONTROLES.md`) |
| **Palanca** | Inferior izq. | Invisible hasta que se toca |

- **No hay barra de vida en exploración**: la vida solo se muestra cuando baja (aviso §5) o
  en batalla. El mundo no está lleno de barras.

---

## 3. HUD de batalla

| Pieza | Situación | Qué dice |
|---|---|---|
| **Barra de órdenes (tropas)** | Franja central inferior | Cargar / Seguirme / Defender + cuántas órdenen acatan |
| **Botones de combate (héroe)** | Inferior der., en arco | Golpe, Guardia, Desvío y Habilidad (puntería por botón, no por gesto) |
| **Moral propia** | Arriba-izq. | Tu moral y la de tus tropas |
| **Moral enemiga** | Arriba-der. | Rota = victoria (romper moral es ganar) |
| **Vida del héroe** | Arriba-izq., bajo la moral | Solo mientras combates |
| **Capitanes con nombre** | Sobre su unidad | Chip con su nombre y su banda, si la tiene memoria |

- Todo lo de presentación, partículas y cámara → `../batalla/04_PRESENTACION.md`.
- Simulación de la batalla → `../batalla/00_REGLAS.md` y `../batalla/01_CIFRAS.md` (el HUD **nunca**
  decide nada, solo pinta).

---

## 4. Avisos y chips (memoria, deuda, Firma)

- **Chip de deuda**: aparece al despertar con deuda pendiente; se cierra con un toque.
- **Recordatorio de Firma**: al cambiar de banda, una línea breve («Ahora te dicen *Fiera*»)
  durante 3 s.
- **Recuerdo suelto**: cuando un PNJ te saluda con un recuerdo tuyo, va como bocadillo, no
  como popup.
- **Bocadillo con retrato** (2026-10-02): si el que habla es uno de los **16 con retrato**
  (`../arte/01_ASSETS.md` §2b), su cara acompaña el bocadillo; el resto, solo texto. El tamaño
  del bocadillo no cambia (≤ 2 líneas, `03_I18N_Y_TONO.md` §4).
- Aviso completo y ritmo → `07_AVISOS_Y_RUMORES.md`.

---

## 5. Estados y vida

| Situación | Se muestra |
|---|---|
| Vida > 50 % | Nada |
| Vida 25–50 % | Pulsos tenues en el borde |
| Vida < 25 % | Pulsos rojos + latido tenue (apagable) |
| Caído | Pantalla de rescate (`../sistemas/02_PRISIONEROS.md`) |
| Sin oro y con deuda | Chip rojo de deuda |

- **Nunca hay pantalla de muerte sin salida**: si caes, siempre aparece la salida (regla 7 de
  `../produccion/01_FASES.md`).

---

## 6. Escalado y orientación

- Base **960×540** (horizontal). En pantallas más estrechas se reducen **los márgenes**, no
  los botones (se prefiere apretar que encoger objetivos).
- Humo (a verificar, por implementar) en **960×683** y **960×540**.
- El HUD respeta la escala de la opción «Tamaño de texto» (`../interfaz/04_ACCESIBILIDAD.md`).

---

## 7. Datos, tipos y validación

- Pintura en escenas (`js/scenes/*`), con el kit de DOM (por construir) (`dom_kit.js`).
- Las claves de texto son `txt_hud_*` en `strings_es.json` / `strings_en.json` con **paridad
  obligatoria** (regla 10).
- Tests: `tests/scene_hud.test.js` (pintura, estados, paridad de claves).

---

## 8. Qué entra en la demo (Fase 1)

- Las dos caras del HUD completas: exploración y batalla.
- Avisos de deuda, de Firma y de recuerdo.
- Escalado a verificar en los dos tamaños del humo.

---

## 9. Cifras que fija este documento

| Cifra | Valor |
|---|---|
| Texto mínimo | legible a 320 px de fuente |
| Botones | ≥ 48 px |
| Vida en exploración | solo aviso por debajo del 50 % |
| Aviso de banda | 3 s |
| Base de pantalla | 960×540 horizontal |

---

## 10. Fuera de este documento

- Pantallas completas y navegación → `01_PANTALLAS.md`
- Barra de órdenes y botones de combate → `../batalla/04_PRESENTACION.md`
- Avisos y rumores → `07_AVISOS_Y_RUMORES.md`
- Accesibilidad → `04_ACCESIBILIDAD.md`
