# 08 · Transiciones y cargas — sin esperas ni pantallas muertas

**Estado:** ✅ **aprobado por el dueño (aprobación en bloque, 2026-09-30). Documento final.**

> El juego es **offline y estático** (`../../AGENTS.md`): todo está en disco, así que **no hay
> motivos para esperar**. Regla: **nunca** una pantalla negra que no avise y no avance.

---

## 1. Los tres cambios de escena (y cómo se hacen)

| Cambio | Cómo se hace | Duración |
|---|---|---|
| **Entre sitios** (nodo → nodo) | Fundido corto sobre el **mapa**; el nodo nuevo se prepara detrás | ≤ 250 ms |
| **Sitio → batalla** | Del campo al campo: **zoom corto** al enemigo y despliegue (`../batalla/00_REGLAS.md` §2) | 2 s de aviso |
| **Pantallas de sistema** | Panel que **sube** sobre el mundo (que sigue detrás) | ≤ 200 ms |

- **No hay pantalla de carga** entre sitios: al cruzar el umbral, se cambia de nodo **sin negro**
  (`../mundo/01_EXPLORACION.md` §4).
- **El viaje por días** se representa en la **pantalla de mapa** (1,5 s/día, máx. 9 s) o **instantáneo**
  con «viaje rápido» (`../mundo/02_VIAJE_Y_ENCUENTROS.md` §1). Nunca una carreta en movimiento.

---

## 2. Por qué no hay esperas

1. **Todo es local:** modelos, datos y audio están en el disco; no se descarga nada.
2. **Preparación en segundo plano:** el nodo siguiente se carga **mientras caminas** hacia su puerta.
3. **Assets compartidos:** los GLB y texturas se reutilizan entre sitios (`../arte/01_ASSETS.md`).
4. **Nada de servidores:** cero red, cero «vuelve en 24 h» (`../sistemas/09_TIEMPO_Y_MUNDO_VIVO.md`).

---

## 3. En dispositivos modestos

- Si la preparación **no llega a tiempo**, se dibuja el nodo nuevo **por capas** (suelo → props →
  PNJ) en menos de **1 s**, con el fundido tapando el relleno. **Nunca** un cartel de «cargando».
- El presupuesto de render (`../arte/00_ESTILO.md`) deja margen para que el cambio no dé tirón.
- **Medido** con la batería de humo (`npm run smoke`) en 960×683 y 915×555.

---

## 4. Transiciones de la trama

- **Escena de diálogo:** entra deslizando; al acabar, el mundo ya está ahí.
- **Flashback:** cambio de **luz y sonido**, no de motor (`../historia/03_RECORRIDO.md`).
- **Asamblea / final:** la única transición con peso (cierre de acto): se permite un **fundido
  largo** (≤ 2 s) porque no hay prisa.

---

## 5. Datos, tipos y validación

- La preparación de escena vive en el `scene_manager` y el render (`js/render/*`); **no simula**
  (regla 2 de `../../AGENTS.md`).
- **Tipos:** `Transicion` en `js/data/game_types.js`.
- **Tests:** `tests/transiciones.test.js`: ninguna transición dura más del tope; un nodo sin
  preparar no deja la pantalla en negro; el humo sigue verde.

---

## 6. Cifras que fija este documento

| Cifra | Valor |
|---|---|
| Fundido entre sitios | ≤ 250 ms |
| Panel de sistema | ≤ 200 ms |
| Aviso de batalla | 2 s |
| Viaje representado | 1,5 s/día · máx. 9 s · instantáneo opcional |
| Fundido de cierre de acto | ≤ 2 s |
| Pantalla de carga | **no existe** |
| Ruta de datos | relativa (`data/…`), nunca `/…` |

---

## 7. Qué entra en la demo (Fase 1) — y qué sigue

> **Hasta aquí la demo.** Transiciones entre los 6 sitios, el viaje por el tramo de camino y las
> pantallas de sistema, con estos topes y **sin pantallas de carga**.

> **Y sigue el juego completo.** Ciudades, agua y regiones nuevas **heredan** estas transiciones;
> el mundo grande no añade esperas, solo más nodos con la misma preparación en segundo plano.

---

## 8. Fuera de este documento

- El mapa y el viaje → `../mundo/00_MAPA.md`, `../mundo/02_VIAJE_Y_ENCUENTROS.md`
- El render y los assets → `../arte/01_ASSETS.md`, `../arte/00_ESTILO.md`
- El HUD → `02_HUD.md`
- El armazón y el boot → `../produccion/02_GUARDADO_Y_DATOS.md`
