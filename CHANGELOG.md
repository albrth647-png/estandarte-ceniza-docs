# Changelog

Resumen por entregas de la **documentación de diseño** de *Valcoria — Deuda de Sangre*.
El código del juego aún no existe: este historial cubre el diseño. Formato: cambios
agrupados; la línea `Unreleased` es lo que hay en `master`.

## [Unreleased]

### Saneamiento greenfield de la documentación (2026-10-25)

- **Reescritura completa en clave «sin código»**: toda la documentación describe ahora el
  juego que se va a construir, sin referencias a builds, commits, hitos cerrados, tests
  corridos ni cobertura medida (no hay código: nunca lo hubo en este repo).
- **Se retira la historia del primer juego** («Estandarte de Ceniza», mapa por casillas +
  batalla táctica 2D) del changelog vivo: queda comprimida como memoria en
  `docs/DECISIONES.md` §1 y como lecciones en `docs/VISION_JUEGO_COMPLETO.md` §1. Su código
  ya no existe ni se conserva en este repositorio.
- **Guardado unificado**: el juego nuevo arranca con `SAVE_VERSION` **1** (aditivo). Las
  referencias dispersas a v2/v3/v4/v5 eran herencia del build retirado y se han eliminado.
- **Contradicciones numéricas corregidas** (oro inicial 100 base, aliento 4/s en combate,
  aforo 6+2×(n−1), 11 clases de encargo, 7 formas de cobro, 3 campos en la demo del Acto I,
  presupuesto de assets ~90 MB demo / ~100 MB APK, 16 riesgos, 8 pasos de QA, 12 logros
  9+3, ejemplos de daño recalculados, radio de interacción 2,5 m, 5 rasgos de IA de
  enemigos, 6 puertas de vuelta de los capitanes, 5 salidas del prisionero con el canje,
  915×555 → 960×540 en el humo).
- **Enlaces y referencias reparados** (rutas `../` que no resolvían, documentos citados que
  no existían) y creados los contenedores de fichas `THIRD_PARTY.md` y `art/AUTORES.md`
  (por rellenar al producir los assets).
- **Verificaciones futuras marcadas como tales**: «Verificado con el humo» pasa a
  «Verificable (por implementar)»; los tests y validadores citados quedan como contratos
  del build, no como herramientas en marcha.

### Historial previo (comprimido)

- **2026-09-30 → 2026-10-02:** redacción y aprobación de los **98 documentos de diseño**
  (10 historia + 12 mundo + 16 contenido + 16 sistemas + 7 batalla + 6 misiones +
  11 interfaz + 6 arte + 13 producción, más `COBERTURA_REQUISITOS.md`), en 14 rondas de
  decisiones del dueño (ver `docs/DECISIONES.md`).
- **2026-09-26 → 2026-09-30:** primer proyecto («Estandarte de Ceniza», demo Acto I
  jugable con mapa por casillas). **Retirado por decisión del dueño el 2026-09-30**: el
  género cambió a 1.ª persona y tiempo real; solo sobreviven sus *lecciones de diseño*
  (la batalla por escuadrones como concepto, el reloj de campaña, la teoría de longevidad
  de `VISION_JUEGO_COMPLETO.md`).

## Cómo se usa este archivo

1. Antes de una entrega grande: línea nueva en `Unreleased`.
2. Al cerrar la entrega: mover a `[0.x.y] — Descripción (fecha)`.
3. El código del juego tendrá su propia numeración de releases
   (`docs/produccion/07_RELEASES_Y_VERSIONES.md`).
