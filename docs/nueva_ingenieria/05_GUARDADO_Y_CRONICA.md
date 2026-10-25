# 05 · Guardado y Crónica — la partida que recuerda su historia

> Contrato de construcción del guardado. Del original se conserva la granularidad
> (un save = todo el estado del mundo) y los puntos de guardado en mapa y ciudad;
> se sustituye su saco de escalares sin versión por un esquema versionado v1 completo
> (contrato en `../produccion/02_GUARDADO_Y_DATOS.md`).

## 1. Esquema v1 (resumen operativo)

```jsonc
// save_<slot>.json — SAVE_VERSION: 1  (el esquema demo COMPLETO nace en v1)
{
  "SAVE_VERSION": 1,
  "meta": { "fecha_iso": "...", "jugador": "nombre", "dias_jugados": 0, "capitulo": 1 },
  "jugador": { "atributos": {...}, "aliento_max": 100, "oro": 100, "deuda": 0,
               "skills": {...}, "talentos": {...}, "inventario": [...] },
  "hueste": [ { "unidad": "milicia", "efectivos": 12, "exp_acumulada": 40 } ],
  "mundo": {
    "sitios": [ { "id": 5, "dueno": 2, "prosperidad": 1400, "defensa": 1000, "torres": 1 } ],
    "reinos": [ { "id": 2, "vasallos": [ { "id": 118, "lealtad": 100, "memoria": [...] } ] } ],
    "bandas": [ { "id": "bandidos_corvo", "viva": true, "veterania": 0,
                  "memoria": [ { "hecho": "huyo_de_jugador", "dia": 12 } ] } ],
    "dia_juego": 34, "estacion": "verano"
  },
  "cronica": [ { "dia": 1, "capitulo": 1, "texto": "clave_cronica_001" } ],  // claves i18n
  "niebla": [ "0_0", "0_1" ]
}
```

Reglas: claves de texto para todo lo narrado (paridad ES/EN ya exigida por el repo);
validador estricto al cargar; migración documentada solo para versiones futuras
(`MIGRACIONES.md` nace con v2, no antes).

## 2. Flujo de guardado

- **Autosave** al cerrar capítulo y al liquidar semana (ranura rotativa aparte).
- **Manual** desde mapa y desde ciudad (mismos dos contextos que BoC) con confirmación.
- Exportar/importar fichero de save (copia de seguridad del jugador, offline total).
- 3 ranuras + autosave; cada ranura muestra: nombre, día, capítulo, oro, deuda y la
  **última línea de la Crónica** como subtítulo (el save tiene rostro).

## 3. La Crónica dentro del save

- Cada hecho relevante escribe una entrada (clave de texto + datos interpolados).
- La pantalla de Crónica reconstruye la historia de la partida desde el save —
  jugable como "registro de campaña" exportable a texto.
- Los capitanes con memoria leen de `memoria[]`: sus diálogos citan hechos con día y lugar.

## 4. Pruebas de aceptación

1. Guardar→cargar restaura bit a bit oro, deuda, mundo, bandas y Crónica.
2. Un save con `SAVE_VERSION` desconocido se rechaza con mensaje claro (no se corrompe).
3. La Crónica exportada es legible de principio a fin sin contextos faltantes.
4. Cargar un save editado a mano que viola el esquema muestra error de validación exacto.
