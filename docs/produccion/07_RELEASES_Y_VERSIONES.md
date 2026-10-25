# 07 · Releases y versiones — numerar sin romper partidas

**Estado:** ✅ **aprobado por el dueño (aprobación en bloque, 2026-09-30). Documento final.**

> Cada entrega se **numera**, se **anota** y **respeta las partidas** de la anterior. El guardado
> versionado es la columna (`02_GUARDADO_Y_DATOS.md`); aquí está la **política de entregas**.

---

## 1. Numeración (semver simplificado)

| Cambio | Número | Ejemplo |
|---|---|---|
| **Grande** (acto nuevo, mecánica) | **MAYOR** | `0.1 → 0.2`, `1.0` |
| **Medio** (contenido, mejora) | **MENOR** | `0.2.0 → 0.2.1` |
| **Pequeño** (arreglo) | **PARCHE** | `0.2.1 → 0.2.2` |

- **Demo del Acto I** = primera entrega jugable (`0.x`).
- **1.0** = juego completo con los 3 finales (`01_FASES.md` §6).

---

## 2. Changelog para el jugador

- **En lenguaje humano:** qué cambia para quien juega, sin jerga.
- **Qué avisa siempre:** cambios de balance, actos nuevos y añadidos de contenido.
- **Dónde vive:** junto al juego; en la demo, al arrancar si hubo novedades.

---

## 3. Compatibilidad de guardados

- **Regla dura:** una partida de la versión **penúltima** se puede cargar en la última (`00_ALCANCE.md` §6).
- **Migración aditiva** (`migrateSave()`): los campos nuevos se rellenan, **nunca** se borra nada.
- **Un guardado más nuevo** que el juego avisa y no rompe.

---

## 4. Cómo se publica una versión

1. **`npm run qa` verde** (`04_QA.md`).
2. **Prueba manual** de 10 minutos y humo en dos tamaños.
3. **Migración probada** desde la penúltima versión.
4. **Changelog** escrito y **este documento** actualizado.
5. **Número** subido en el build.

---

## 5. Datos, tipos y validación

- La versión del **build** y la del **guardado** (`SAVE_VERSION`) son **cosas distintas**: una
  numera el producto; la otra, el formato de partida (`02_GUARDADO_Y_DATOS.md` §2).
- **Tests:** `tests/migracion.test.js` cubre la carga desde la penúltima versión.

---

## 6. Cifras que fija este documento

| Cifra | Valor |
|---|---|
| Esquema | MAYOR.MENOR.PARCHE |
| Compatibilidad | penúltima → última |
| Migración | aditiva (nunca borra) |
| Pruebas por release | qa + manual + migración |
| Guardado más nuevo | avisa, no rompe |

---

## 7. Qué entra en la demo (Fase 1) — y sigue

> **Hasta aquí la demo.** La **primera entrega** del Acto I (`0.x`) con su changelog y su migración
> probada desde los guardados de desarrollo.

> **Y sigue el juego completo.** Cada acto sube **MAYOR/MENOR** y **siempre** respeta la partida
> anterior; la política no cambia hasta la 1.0.

---

## 8. Fuera de este documento

- Guardado y migración → `02_GUARDADO_Y_DATOS.md`
- QA → `04_QA.md`
- Fases → `01_FASES.md`
- Mercado → `05_MERCADO_Y_LANZAMIENTO.md`
