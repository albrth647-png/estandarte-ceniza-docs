# 03 · Batalla — formaciones, órdenes, daño y 1.ª persona

> Contrato de construcción de la batalla. Del esqueleto de BoC se hereda el choque en
> tiempo real con legiones, formaciones de 20 huecos, órdenes de compañía y héroe
> controlable + auto-batalla. Valcoria añade la vista en 1.ª persona y fórmulas abiertas.

## 1. Núcleo headless (simulación ≠ render)

```
SimBatalla (determinista, seed explícita)
  ├─ legiones[]: id, bando, formación, compañías[]
  ├─ roles[]: posición, objetivo, temporizador_ataque, stats efectivos
  ├─ paso(dt): mover → buscar objetivo → atacar → resolver daño → limpiar muertos
  └─ eventos[]: golpe, crit, bloqueo, muerte, habilidad, orden
Render (WebGL) solo reproduce eventos; el núcleo corre sin pantalla (tests + auto-batalla).
```

La determinismo con seed hace posible: repetir la batalla como informe, autosave exacto
y que la IA de auto-batalla sea reproducible.

## 2. Formaciones y órdenes

- Plantillas JSON (paridad con `formation.dat`): 20 huecos en 2 columnas, `pos_mando`
  adelante/centro/reverso; el editor de formación es un drag visual.
- Órdenes de compañía (panel radial, 63 métodos del panel original ⇒ 5 órdenes claras):
  **avanzar · sostener · retroceder · seguirme · cargar**. Pausa táctica de 3 s para dar
  órdenes (recarga de pausa por batalla: 3 usos).
- Los capitanes con memoria pueden **desobedecer** si su lealtad está rota — y lo dicen.

## 3. Fórmula de daño (publicada, heredada y ajustada)

De la descompilación de BoC (`13_CODIGO_NATIVO.md` §1), con los ajustes Valcoria:

```
atk_ef = ataque + crecimiento_ataque × 1.2        (igual que BoC)
def_neta = max(defensa − penetracion, 0)           (penetración explícita, nueva)
daño = atk_ef − 2 × def_neta
bloqueo: mitiga 60 % (BoC anulaba el golpe — se suaviza)
critico: prob = critico% → daño × 1,0–1,5           (igual)
suelo: daño ≥ 25 % de atk_ef                       (igual: no hay golpes de papel)
varianza: × aleatorio(0,90–1,10)                   (igual)
```

Constantes vivas en `docs/batalla/01_CIFRAS.md`; la ficha de cualquier unidad muestra
un ejemplo de daño contra 3 perfiles (milicia/escudo/caballo).

## 4. El héroe en 1.ª persona (lo bonito y lo nuevo)

- Cámara en 1.ª persona sobre el héroe (decisión de diseño del dueño) + botón de
  "vista de mando" (aérea estilo BoC) — alternar es gratis en cualquier momento.
- Anillo de acción: aliento, 4 skills equipadas, recargas visibles; hit-stop y
  sacudida de cámara en críticos; sangre estilizada con persistencia breve en el suelo.
- Formaciones se ven de verdad: banderas por compañía, tambores al avanzar,
  voces de capitanes que repiten la orden con su personalidad.
- Auto-batalla → informe de la Crónica ("qué salió bien/mal") en vez de un timer opaco.

## 5. Pruebas de aceptación

1. Misma seed ⇒ misma batalla (hash de eventos idéntico).
2. Daño contra perfiles de prueba cae siempre dentro del rango publicado.
3. Bloqueo mitiga 60 % exacto; el suelo del 25 % nunca se cruza hacia abajo.
4. Órdenes radiculares alcanzables en <2 toques; pausa táctica limitada a 3 usos.
