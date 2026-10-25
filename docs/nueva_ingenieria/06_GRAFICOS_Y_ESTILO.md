# 06 · Gráficos y estilo — el "mucho más bonito a simple vista"

> Contrato de construcción de la capa visual. El esqueleto es BoC; la piel es 2026:
> WebGL, luz, clima, tipografía y personajes que respiran. Objetivo del dueño: que la
> primera pantalla ya impresione, sin cargar 500 MB.

## 1. Presupuesto técnico (canon del repo)

- Assets ~90 MB · APK/paquete ~100 MB (ya fijado en `docs/sistemas/`).
- Objetivo de arranque: <5 s en portátil medio; mundo y batalla a 60 fps.
- Todo WebGL (PixiJS/Three según capa); sin motor pesado — control total y offline.

## 2. Paleta y luz

- **Paleta de ceniza y oros** (identidad de la Deuda): base gris-cálido, acentos oro y
  rojo sangre; noche azul-profundo con ventanas ámbar. Referencias: iluminación de
  Battle Brothers (claridad táctica) con color de Elden Ring (solemnidad).
- Ciclo día/noche con sombras largas y niebla por la mañana; estaciones retocan tinte
  y partículas (hojas, nieve) sin cambiar assets.
- Batalla: hit-stop 60 ms en críticos, sacudida sutil, destellos de bloqueo —
  legibilidad primero (la masas se entienden de un vistazo, como en Total War).

## 3. Personajes y sitios

- Unidades: modelos CC0 (KayKit/Quaternius de reserva según `art/`) con esqueleto,
  equipo por pieza y variación de color por banda/reino. Nada de sprites planos de 2017.
- Héroe: 1.ª persona con brazos/armas en cámara, manos que agarran, heridas visibles
  en el espejo de personaje.
- Sitios: vista de fachada con paralaje + NPCs con rutina (mercado de día, hoguera de
  noche); faroles, banderas animadas con viento, humo de chimeneas.
- Mapa mundial: nombres tipografiados, símbolos por tipo de sitio, camino que se
  "dibuja" al planear ruta, sellos de reino sobre los sitios conquistados.

## 4. UI y tipografía

- Una tipografía de título con carácter (serif rústica) + una de UI legible;
  paridad ES/EN tipográfica garantizada (mismos pesos).
- Paneles de madera/tinta con esquinas irregulares sutiles (nada de plástico); iconos
  vectoriales propios con trazo grueso coherente.
- Cada número importante tiene forma legible: oro con moneda dibujada, aliento con
  anillo, deuda con sello rojo creciente.

## 5. Pipeline de producción

1. **Bloqueo visual** (pantallas clave: título, mapa, batalla, ciudad) en mockups HTML.
2. Atlas y fuentes generadas por script (`herramientas/`), medición de peso por build.
3. Efectos evaluados siempre en la peor máquina objetivo antes de aprobarse.

## 6. Pruebas de aceptación

1. Captura del título y del mapa pasa la "prueba de captura": un desconocido dice
   "esto se ve caro" en <5 s.
2. Batalla con 2 legiones de 20 + efectos: 60 fps en portátil integrado.
3. Peso total del paquete ≤ canon (assets ~90 MB).
4. Día/noche y estaciones visibles sin recargar texturas.
