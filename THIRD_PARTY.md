# Terceros — licencias y autoría

> **Estado greenfield:** este fichero es el **contenedor de las fichas de terceros** del juego.
> Se rellenará al producir cada asset/código de tercero (Fase 1, paso 1.1). Hasta entonces,
> lo que hay aquí son **compromisos de diseño**, no inventarios de ficheros.
> La ficha viva de los modelos 3D propios con licencia vive en `art/AUTORES.md` (por crear).

## 1. Terceros previstos (diseño, no inventario)

| Tercero | Uso previsto | Licencia | Ficha |
|---|---|---|---|
| **Three.js** (r186 planeado) + GLTFLoader | render 3D (`vendor/three/`, vendorizado, sin CDN) | MIT | por crear al vendorizar |
| **Modelos KayKit** (reserva de prototipo: 5 humanos) | cuerpos de reserva; los cuerpos en pantalla serán de proporción humana (decisión 2026-10-02) | CC0 | por crear al descargar |
| **Modelo de zorro** (reserva de fauna) | fauna de reserva | CC0 + CC-BY | por crear al descargar; **crédito CC-BY obligatorio en los créditos del juego** |

## 2. Reglas duras de originalidad (regla 7 de `AGENTS.md`)

- **Cero activos, nombres o textos de juegos de terceros.** Ni referencias, ni homenajes con
  nombre, ni música reconocible de nadie.
- Arte y audio: solo **material propio** (generado con herramientas propias, fuera de la
  ejecución) o **libre con ficha** en este documento o en `art/AUTORES.md`.
- **Los buscadores de stock quedan fuera** por originalidad (decisión 2026-10-02, ronda 9).
- Toda ficha nueva se añade aquí **en la misma tarea** que introduce el tercero; el validador
  de enlaces (`npm run docs`, por crear) comprobará que las fichas no están rotas.

## 3. Formato de la ficha (cuando se rellene)

```
| Fichero/carpeta | Autor | Licencia | Origen (URL) | Dónde se usa | Crédito exigido |
```
