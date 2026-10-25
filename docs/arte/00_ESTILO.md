# 00 · Estilo — cómo se ve Valcoria

**Estado:** ✅ **aprobado por el dueño (aprobación en bloque, 2026-09-30). Documento final.**

> Decisión ya tomada (enmienda 2026-10-02): **dirección de arte cinematográfica medieval** — el
> resultado se ve como **una película de aventuras** (fotografía de referencia: *El Señor de los
> Anillos*), y por dentro la producción sigue siendo **low-poly ligero** para el móvil
> (`../VALCORIA_DEUDA_DE_SANGRE.md` §5). Aquí están la **paleta, la luz, la lectura de juego y el
> presupuesto**. Los modelos, en `01_ASSETS.md`; los efectos, en `04_EFECTOS_Y_PARTICULAS.md`.

---

## 1. La dirección (película, no videojuego)

- **La regla:** cada pantalla tendría que poder **colgarse en la pared como un fotograma**.
- **Paisaje:** luz **oblicua de tarde**, niebla en el fondo, siluetas arboladas y horizonte bajo;
  el color va de la tierra al cielo (tierra / verde / ocre apagados).
- **Personajes:** **todos los cuerpos, de proporción humana** (nada de muñecos ni cartoon en
  pantalla); **de cerca manda el retrato pintado** (`01_ASSETS.md` §2b), de lejos el cuerpo y su
  porte.
- **Low-poly con intención (técnica, no estética):** formas limpias y siluetas legibles para el
  móvil; la impresión de película se consigue con **luz, niebla, paleta y rostro**, no con
  polígonos.
- **Sucio y vivido:** hierro mojado, ceniza, barro. El reino está cansado, no roto.
- **Coherente de arriba abajo:** el mismo trazo en un aldeano, una casa y una bandera.

---

## 2. La paleta (una sola, dos capas)

| Capa | Dónde | Colores |
|---|---|---|
| **UI** (DOM) | HUD, menús | La guía de UI (por escribir): fondo `#12141c` / `#1b1e2b`, texto `#e8e4d8`, acento **oro `#c8a24a`**, peligro `#d1615a`, borde `#2c3044` |
| **Mundo** (3D) | Sitios, campo | **Ceniza** (gris piedra), **óxido** (rojo hierro), **sebo** (crema), **piedra** (azul-gris), **hierro** (casi negro) |
| **Acento vivo** | Solo lo importante | **Oro** (dinero/objetivo), **sangre** (daño), **ámbar** (fuego) |

- **Regla de acento:** el oro y la sangre son **escasos**. Si todo brilla, nada destaca.
- El **HUD no compite** con el mundo: mismo tono apagado; el acento se reserva a lo jugable.

---

## 3. Luz, sombras y niebla

- **Luz de día:** sol oblicuo, sombras suaves; **hora del día** cambia color y ángulo
  (`../mundo/05_TIEMPO_DEL_MUNDO.md`).
- **Sombras propias:** solo del héroe y props cercanos (presupuesto); el mundo lejano va con
  **niebla** que corta a 60 m (`../mundo/01_EXPLORACION.md` §7).
- **Niebla = información:** además de rendimiento, marca el **límite de lo que ves** (coherente
  con la visibilidad del terreno, `../batalla/02_TERRENO.md` §6).

---

## 4. Lectura de juego (aliado / enemigo / deudor / PNJ)

- **Silueta primero, color después:** casco, capa, arma y porte distinguen a cada tipo.
- **Aliado:** tonos del jugador (marrón/crema). **Enemigo:** óxido/hierro. **Civil:** sebo apagado.
- **El que te debe** no lleva cartel: se nota en cómo te trata, no en un icono flotante
  (`../sistemas/00_MEMORIA_Y_DEUDA.md`). Como mucho, un **chip** sobre capitanes con nombre
  (`../batalla/04_PRESENTACION.md` §2).
- **Nunca se depende solo del color** (daltonismo, `../interfaz/04_ACCESIBILIDAD.md` §2).

---

## 5. Reutilización sin que se note

- **Piezas modulares:** cuerpos, armas, escudos y banderas se combinan para crear variedad sin
  modelos nuevos (`01_ASSETS.md`).
- **El reciclaje se esconde con:** paleta, heráldica (`../contenido/15_ESTANDARTES_E_INSIGNIAS.md`)
  y desgaste distinto por sitio.
- **Menos variedad, mejor usada:** tres tipos de árbol bien colocados sientan mejor que diez
  amontonados (`../mundo/07_PROPS_Y_VEGETACION.md`).

---

## 6. Presupuesto de render (gama media, 60 fps)

| Medida | Valor |
|---|---|
| Distancia de dibujo | 60 m con niebla final |
| Personajes a la vez (batalla) | 10+10 + props |
| LOD | ×1 → ×0,5 (15-20 m) → ×0,25 (45 m) |
| Hierba / arbustos / árboles | los de `../mundo/07_PROPS_Y_VEGETACION.md` |
| Sombra propia | solo héroe y props cercanos |
| Objetivo | **60 fps** sin caídas al entrar en un sitio |

- **Verificable** con la batería de humo (por implementar) en 960×683 y 960×540.

---

## 7. Datos, tipos y validación

- La paleta del mundo vivirá en `data/estilo.json` (por crear) (colores `#rrggbb`, convención de datos).
- **Tipos:** `Paleta` y `TemaVisual` en `js/data/game_types.js`.
- **Validación:** esquema + comprobación de formato `#rrggbb` en `tools/validate_data.js`.
- **Tests (por escribir):** `tests/estilo.test.js`: todo color es `#rrggbb`; el acento es escaso (conteo por
  escena); no hay color fuera de paleta en la UI.

---

## 8. Cifras que fija este documento

| Cifra | Valor |
|---|---|
| Estilo | fotografía de película medieval (producción low-poly) ✅ 2026-10-02 |
| Paleta | UI (`css/ui.css`) + mundo (ceniza/óxido/sebo/piedra/hierro) |
| Acentos vivos | oro · sangre · ámbar (escasos) |
| Niebla / dibujo | 60 m |
| LOD | 3 niveles |
| Objetivo de render | 60 fps con 10+10 |

---

## 9. Qué entra en la demo (Fase 1) — y qué sigue

> **Hasta aquí la demo.** La paleta, la luz de tarde, la niebla a 60 m, la lectura de aliado/
> enemigo/civil y los **retratos de los 16 personajes clave** (`01_ASSETS.md` §2b), con los
> assets actuales y los 6 sitios.

> **Y sigue el juego completo.** Ciudades, clima y estaciones (`../mundo/09_CLIMA_Y_ESTACIONES.md`)
> añaden variación de luz y color **dentro de esta paleta**; no se cambia el estilo al escalar.

---

## 10. Fuera de este documento

- Modelos y licencias → `01_ASSETS.md`
- Audio → `02_AUDIO.md`
- Animaciones → `03_ANIMACIONES.md`
- Efectos → `04_EFECTOS_Y_PARTICULAS.md`
- Iconos → `05_ICONOS.md`
- Vegetación → `../mundo/07_PROPS_Y_VEGETACION.md`
