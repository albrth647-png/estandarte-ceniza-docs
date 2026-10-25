# 01 · Pantallas — el mapa de todo lo que se puede abrir

**Estado:** ✅ **aprobado por el dueño (aprobación en bloque, 2026-09-30). Documento final.**

> Todo lo que se abre está en **un solo mapa**: menús, mundo jugable y pantallas de sistema.
> La regla es de `00_CONTROLES.md`: **dos toques como máximo** para cualquier acción; ningún
> menú dentro de otro menú.

---

## 1. Las pantallas (una sola lista)

| Grupo | Pantalla | Qué es | Estado |
|---|---|---|---|
| **Armazón** | Portada | Título y primera tecla | Por construir (diseño cerrado) |
| | Menú | Continuar, nueva partida, cargar, opciones, créditos | Por construir (diseño cerrado) |
| | Crear partida | Nombre, origen, dificultad | Por construir (diseño cerrado) |
| | Cargar | 3 slots + respaldo de corrupto | Por construir (diseño cerrado) |
| | Opciones | Idioma, calidad, texto, control, accesibilidad | Por construir (diseño cerrado) |
| | Créditos | Autoría y terceros | Por construir (diseño cerrado) |
| **Mundo** | Exploración | 1.ª persona, libre | Demo |
| | Diálogo | Conversación por nodos | Demo |
| | Viaje / mapa | Elegir destino y resolver días | Demo |
| | Batalla | Campo semi-tiempo real | Demo |
| | Post-batalla | Las 4 salidas del prisionero | Demo |
| **Sistema** | Registro (Crónica) | Tu diario | Demo |
| | Tienda / trato | Comprar y vender | Demo |
| | Tablón | Encargos del sitio | Demo |
| | Libro Mayor | Deudas, favores, rencores | Fase 2 |
| | Minimapa | Capa sobre el mundo | Fase 2 |
| | Asamblea | Decisión final de la trama | Fase 3 |

---

## 2. Cómo se navega

- **Mundo ↔ sistema:** desde exploración, un toque abre el registro, el mapa o la tienda; para
  volver, el botón de atrás del propio panel.
- **Nunca** se sale del mundo a un menú negro: el mundo **sigue detrás** (el tiempo no se
  detiene; `../batalla/00_REGLAS.md` §3).
- **Diálogo y batalla son pantallas del mundo**, no menús: no tienen «volver al menú» salvo por
  el menú de pausa.
- **Pausa:** el juego **no tiene pausa total** (`../batalla/00_REGLAS.md` §3); el menú de pausa solo abre
  opciones y guardado, y el mundo espera **dentro de lo posible** (días de juego, no reloj real).

---

## 3. Flujos principales

```
Portada → Menú → (Cargar | Crear) → Exploración ⇄ Diálogo | Viaje | Registro | Tienda | Tablón
Exploración → encuentro → Batalla → Post-batalla → Exploración
Exploración → destino → Viaje (días) → Exploración
Acto III → Asamblea → Final
```

- **Cada flujo** empieza y acaba en **Exploración** salvo el final: la asamblea es el único
  punto de no retorno (`../historia/01_ESTRUCTURA.md`).

---

## 4. Reglas de casa (comunes a todas)

1. **Base 960×540**, horizontal; los márgenes se reducen, no los botones (`02_HUD.md` §6).
2. **Objetivos ≥ 48 px** (primarios ≥ 56) y separados **≥ 8 px** (`00_CONTROLES.md`).
3. **El HUD es DOM** (capa `#ui`), sobre el lienzo; no se dibuja en el canvas.
4. **Nada de listas de 30 items:** cada pantalla muestra **pocas y del sitio**.
5. **Todo texto por clave `txt_*`** con paridad ES/EN (`03_I18N_Y_TONO.md`).

---

## 5. Datos, tipos y validación

- Las escenas (`js/scenes/*`, por construir) y el gestor de escenas gestionarán la navegación; las
  nuevas se añaden como escenas **que dibujan, no simulan** (regla 2 de `../../AGENTS.md`).
- **Tipos:** `Pantalla` en `js/data/game_types.js`.
- **Tests (por escribir):** `tests/scene_manager.test.js` (por escribir) + `tests/pantallas.test.js` (toda pantalla
  es alcanzable y **regresable**, salvo la asamblea).

---

## 6. Cifras que fija este documento

| Cifra | Valor |
|---|---|
| Pantallas | **17** (6 de armazón + 5 de mundo + 6 de sistema) |
| Toques por acción | ≤ 2 |
| Base de pantalla | 960×540 horizontal |
| Pausa total | **no existe** |
| Punto de no retorno | Asamblea |

---

## 7. Qué entra en la demo (Fase 1) — y qué sigue

> **Hasta aquí la demo.** El armazón completo + exploración, diálogo, viaje, batalla,
> post-batalla, registro, tienda y tablón — todo navegable y regresable.

> **Y sigue el juego completo.** **Libro Mayor**, **minimapa** (Fase 2) y **asamblea** (Fase 3)
> se añaden **con estas mismas reglas** de navegación.

---

## 8. Fuera de este documento

- Gestos y botones → `00_CONTROLES.md`
- Qué se ve en el mundo → `02_HUD.md`
- El registro ampliado → `05_LIBRO_MAYOR.md`
- Transiciones → `08_TRANSICIONES_Y_CARGAS.md`
