# 01 · Mapa y mundo — sectores, caminos, sitios y viajes

> Contrato de construcción del continente (Valcoria). Modelo mental heredado de BoC:
> cuadrícula de sectores + grafo de caminos + tabla de sitios — reconstruido con
> datos versionados y presentación moderna.

## 1. Contrato de datos

```jsonc
// datos/mapa.json  —  schema_version: 1
{
  "schema_version": 1,
  "sectores": { "columnas": 5, "filas": 5, "tile": 1600 },
  "caminos": {
    "nodos": [ { "id": 0, "x": 841, "y": 940, "enlaces": [1, 2] } ]   // grafo plano
  },
  "sitios": [
    {
      "id": 1, "tipo": "ciudad",           // ciudad|castillo|aldea|abadia|granja|forja|rancho|mina|guarida
      "nombre": { "es": "Puente Ceniza", "en": "Ashbridge" },
      "pos": [2256, 3536], "sector": [2, 3],
      "depende_de": null,                  // aldeas → id de castillo (hereda caída)
      "prosperidad": { "inicial": 1400, "techo": 5000 },
      "defensa": { "inicial": 1000, "techo": 2000 },
      "huecos_torre": 3,
      "mercado": { "provisiones": [...], "mercaderia": [...] },   // gramática de tiradas
      "recetas_herreria": [...]            // solo forjas
    }
  ],
  "reinos": [
    { "id": 2, "rey": 105,
      "corte": [ { "id": 118, "lealtad": 100 }, { "id": 120, "lealtad": 95 } ],
      "sitios": [ { "id": 5, "guarnicion": [105, 118, 119] } ] }
  ]
}
```

Reglas del validador (`herramientas/valida_datos.js`): ids únicos, referencias
resueltas (`depende_de`, `rey`, guarniciones), posiciones dentro del mundo,
tipos de sitio conocidos, mercado con probabilidades que sumen ≤100.

## 2. Algoritmo de viajes (grafo, no campo a través)

```
ruta(origen, destino):
  A* sobre el grafo de caminos con peso por arista = distancia × factor_secto(sector)
  factor_secto: peligro (bandas activas cerca) × estación × evento (guerra)
movimiento de la hueste: interpolar por aristas; cada sector cruzado dispara
  encuentros (banda en radio de patrulla) y actualiza niebla de guerra.
```

Mejoras sobre BoC (donde era grafo estático): pesos vivos, rutas alternativas
explicadas al jugador ("por la sierra: 2 días más, sin bandidos"), y las bandas
también viajan por el grafo (en BoC solo patrullaban en radio).

## 3. Render (lo bonito)

- **Canvas/WebGL por sectores**: solo el sector activo y vecinos; tiles a 2× de
  resolución con atlas; paralaje de 3 capas (cielo/terreno/primer plano).
- **Ciclo día-noche** con tinte de luz y ventanas encendidas en sitios; estaciones
  que cambian paleta del terreno (mismo atlas, ajuste de tinte HSL).
- **Nombres en el mapa** tipografiados con contorno, escala por zoom; minimapa
  derivado del mismo grafo (clic = viaje).
- Fog of war binaria por sector + "recuerdos": los sectores visitados conservan
  la última imagen vista (composición pre-renderizada), como fotografías.

## 4. Pruebas de aceptación

1. Cargar `datos/mapa.json` sin errores y pintar los 25 sectores en <1 s.
2. Viaje A→B calcula ruta y muestra coste estimado antes de partir.
3. Aldea cae cuando cae su castillo (`depende_de`) con aviso en la Crónica.
4. Guardar/cargar conserva: posesión de sitios, prosperidad, niebla, posición.
