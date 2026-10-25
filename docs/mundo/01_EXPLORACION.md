# 01 · Exploración — caminar Valcoria en 1.ª persona

**Estado:** ✅ **aprobado por el dueño (aprobación en bloque, 2026-09-30). Documento final.**

> Pilar 4 («explorar Valcoria a pie») y Pilar 1 (controles). Describe el **juego completo**;
> la demo solo recorre 6 sitios con estas mismas reglas.

---

## 1. Qué es

Caminas en **1.ª persona pura** por cada sitio del mapa (`00_MAPA.md`). No hay cámara
estratégica ni mapa por casillas: lo que ves es lo que hay. Entre sitios hay viaje por días
(`02_VIAJE_Y_ENCUENTROS.md`).

---

## 2. Cámara y cuerpo

| Dato | Valor |
|---|---|
| Altura de ojos | 1,65 m |
| Campo de visión | 70° (horizontal), 60° en pantallas estrechas |
| Giro vertical (pitch) | −60° … +60° |
| Giro horizontal | libre, 360° |
| Balanceo (head bob) | 2 cm · **desactivable** (accesibilidad) |
| Sombras propias | solo del héroe y props cercanos (presupuesto en `../arte/00_ESTILO.md`) |

---

## 3. Movimiento

- **Palanca virtual fija** en la esquina inferior izquierda (Pilar 1): mueve respecto a la
  dirección de la mirada (relativa, no absoluta).
- **Mirar:** arrastrar en cualquier zona libre de la pantalla.
- **Velocidades:** andar **3,0 m/s** · correr **5,0 m/s** (manteniendo el botón de correr) ·
  sigilo **1,2 m/s**.
- **No se puede caer a muerte:** el terreno está acotado y cualquier desnivel tiene barandilla
  natural o caída con solo daño menor (regla: *el fallo nunca atasca*).
- **Sin salto** en exploración: el salto es de combate (batalla, `../batalla/00_REGLAS.md`).

---

## 4. Colisión y terreno

- Cuerpo = **cápsula** de 0,4 m de radio; suelo con altura por vértices (mismo terreno que el
  combate → `../batalla/02_TERRENO.md`).
- **Escalón:** sube solo hasta **0,4 m**; más alto = muro.
- **Puertas y portones:** se abren al tocar (no hay animación de mano).
- **Carga entre sitios:** al cruzar el umbral de salida, se cambia de nodo **sin pantalla de
  carga** (transiciones en `../interfaz/08_TRANSICIONES_Y_CARGAS.md`).

---

## 5. Enfocar: «la mirada lleva» (Pilar 1)

Al acercarte a algo con el que se puede tratar (menos de **3 m** y a menos de 45° del eje de
la mirada):

1. La cámara **gira sola** hacia el objeto en **250 ms** (suave, nunca brusca).
2. El objeto muestra un **aro** de interacción.
3. Un **toque** ejecuta la acción; un **toque largo** (400 ms) abre la acción secundaria.

- Arrastrar **cancela** el enfocar en el mismo instante: el jugador manda siempre.
- Nunca se enfoca más de **1 objeto a la vez**.
- Con opción «enfocar» desactivada, la mirada no se mueve sola (accesibilidad).

---

## 6. Qué se puede tocar

| Tipo | Ejemplo | Efecto |
|---|---|---|
| **Hablable** | Aldeano, posadero, escribano | Abre diálogo (`js/systems/dialogue.js`) |
| **Recogible** | Leña, hierro, botín | Suma al inventario |
| **Comprable** | Mesa de mercado, estante | Abre pantalla de trato |
| **Contenedor** | Arcón, saco, cadáver | Abre botín (`../contenido/11_TABLAS_DE_BOTIN.md`) |
| **Lectura** | Cartel, lápida, libro | Muestra texto de `../historia/08_TEXTO_DEL_MUNDO.md` |
| **Portal** | Puerta de sitio, camino real | Cambia de nodo (viaje) |

- **Radio de interacción: 2,5 m**; objetos fuera de radio se ignoran sin error.
- Todo lo interactuable es **objetivo de 48 px** mínimo en pantalla (regla de `css/ui.css`).

---

## 7. Rendimiento (presupuesto fijo)

| Medida | Valor |
|---|---|
| Distancia de dibujo | **60 m** con niebla al final |
| Props | instanciados; LOD a 20 m (×0,5) y 45 m (×0,25) |
| Vegetación | densidad por zona en `07_PROPS_Y_VEGETACION.md` |
| Objetivo | **60 fps** en gama media, sin caídas al entrar en un sitio |

Medido con la batería de humo (`npm run smoke`) y el presupuesto de `../arte/00_ESTILO.md`.

---

## 8. Accesibilidad

- Sensibilidad de giro ajustable (5 niveles).
- Balanceo y sacudida de cámara **apagables**.
- «Modo un pulgar»: palanca desplazable a cualquiera de los dos lados.
- Velocidad de caminar reducible a 2,0 m/s.

---

## 9. Datos, tipos y validación

- Sistema puro: `js/systems/exploracion.js` (reglas de radio, enfocar y transición de nodo)
  — sin DOM, sin reloj; la escena pinta y envía gestos.
- Gestos: `js/core/input.js` (tap / drag / long-press), ya existente.
- Tests: `tests/exploracion.test.js`, mínimo 3 casos (normal, borde, error).

---

## 10. Qué entra en la demo (Fase 1)

- 6 sitios con estas mismas reglas; **caminar, mirar, entrar y salir** es el hito 1.1.
- Enfocar activo desde el primer aldeano.
- Presupuesto de rendimiento **idéntico** al del juego completo.

---

## 11. Cifras que fija este documento

| Cifra | Valor |
|---|---|
| Altura de ojos / FOV | 1,65 m / 70° |
| Velocidades | 3,0 · 5,0 · 1,2 m/s |
| Radio de interacción | 2,5 m |
| Enfocar | 250 ms · 45° · 1 objeto |
| Toque largo | 400 ms |
| Escalón | 0,4 m |
| Distancia de dibujo | 60 m |

---

## 12. Fuera de este documento

- Palanca, botones y gestos → `../interfaz/00_CONTROLES.md`
- Lo que se ve en pantalla → `../interfaz/02_HUD.md`
- Viaje entre sitios → `02_VIAJE_Y_ENCUENTROS.md`
- Terreno compartido con combate → `../batalla/02_TERRENO.md`
