# Nueva ingeniería — Cómo se construye cada cosa de Valcoria (mejor y más bonito)

> Serie Fase D. Puente entre lo aprendido del esqueleto de Blade of Conquest
> (`../ingenieria_inversa/blade_of_conquest/`) y la implementación real de Valcoria
> como juego web offline. Cada guía: contrato de datos + algoritmo + mejora visual.
> Nada de aquí copia código o assets del original: reconstrucción desde cero.

| Guía | Sistema | Basada en |
|---|---|---|
| `01_MAPA_Y_MUNDO.md` | sectores, grafo de caminos, sitios, viajes | dossiers 04, 05 |
| `02_TROPAS_Y_HEROE.md` | unidades, crecimiento, habilidades, aliento | dossiers 06, 07 |
| `03_BATALLA.md` | formaciones, órdenes, daño, 1.ª persona | dossier 09 + fórmula de 13 |
| `04_MUNDO_VIVO.md` | bandas con respawn, reinos, presupuesto, mercado | dossiers 08, 10, 11 |
| `05_GUARDADO_Y_CRONICA.md` | save v1 versionado + Crónica dentro | dossier 12 |
| `06_GRAFICOS_Y_ESTILO.md` | el "mucho más bonito a simple vista" | transversal |

## Metodología (la misma para todos los sistemas)

1. **Contrato de datos primero**: JSON versionado en `datos/` con validador — el
   contenido nunca vive en código (lección de los `.dat` de BoC, buena en concepto,
   frágil en formato: sin esquema, sin versiones).
2. **Fórmulas publicadas**: cada número que afecta al jugador está en
   `docs/batalla/01_CIFRAS.md` o `docs/sistemas/` — sin constantes ocultas compiladas
   (la gran deuda del original: fórmulas solo visibles descompilando).
3. **Simulación desacoplada de la presentación**: la batalla y el mundo corren en un
   núcleo headless testeable; el render (WebGL) es un espectador — esto permite
   auto-batalla, informes de Crónica y guardado exacto.
4. **Offline total**: sin red, sin IAP, sin telemetría externa; todo local.
