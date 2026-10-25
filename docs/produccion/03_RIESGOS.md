# 03 · Riesgos — lo que puede salir mal (y el plan B)

**Estado:** ✅ **aprobado por el dueño (aprobación en bloque, 2026-09-30). Documento final.**

> Amplía los riesgos de `01_FASES.md` §8. Cada riesgo trae **detección temprana** y **plan B**.
> Regla: se recorta **alcance**, nunca la mecánica del alma (memoria y Firma).

---

## 1. Riesgos de producto

| Riesgo | Cuándo se nota | Plan B |
|---|---|---|
| **Los controles táctiles no convencen** | 1.1 | Probar variantes de palanca/enfocar con pulgares reales antes de 1.2 |
| **La memoria universal infla el guardado** | 1.2 | Recortar **topes** (400 fichas, 400 KB), nunca la mecánica |
| **El campo con 5-6 no se siente** | 1.4 | Subir a 8 antes del cierre; si aún no, simplificar el campo |
| **El guion se desborda** | 1.6 | Recortar secundario, no la columna vertebral |
| **La demo pasa de 2-3 h** | 1.6-1.7 | Cortar en el **giro** (ya fijado como final de la demo) |
| **Los 3 finales comen calendario** | Fase 3 | Cierres primero, epílogos variables después |
| **10+ por bando rompe el rendimiento** | Fase 4 | Simplificar campos y LOD **antes** que bajar unidades |

---

## 2. Riesgos técnicos

| Riesgo | Detección | Plan B |
|---|---|---|
| **Audio offline no suena en algún móvil** | Humo en dispositivo real | Fallback: silencio total sin error (`../arte/02_AUDIO.md` §1) |
| **`localStorage` lleno / corrupto** | Test de migración | Respaldo `valcoria_save.corrupt` + migración aditiva |
| **GLB pesados** | Presupuesto de assets | Recorte con `tools/recortar_glb.mjs`; **~90 MB demo** ✅ 2026-10-02 (antes 8 MB) |
| **Terceros sin licencia** | `validate_data.js` | Ficha obligatoria antes de commit; no entra |
| **Rutas absolutas rompen la APK** | ESLint + validadores | Solo rutas relativas (`data/…`) |

---

## 3. Riesgos de proceso

| Riesgo | Plan B |
|---|---|
| **Documentar de más y no construir** | El orden manda: doc → datos → código → tests (`01_FASES.md` §1) |
| **Un bug ALTA bloquea avanzar** | Es por diseño: nada avanza con un ALTA abierto (`../BUGS.md`) |
| **Diseño que envejece** | Los docs se escriben **uno o dos pasos antes** de su fase |
| **Perder el norte (demo vs juego final)** | Los docs son del **juego final**; solo `00_ALCANCE.md` acota la demo |

---

## 4. Riesgos de alcance (lo que NO se hace)

- **No se resucita** el motor táctico ni el mapa por casillas (`../../docs/DECISIONES.md`).
- **No se añaden dependencias** nuevas (mismo repo, cero instalaciones).
- **No se publica** la demo antes de que enseñe la promesa (`00_ALCANCE.md` §4).

---

## 5. Cómo se vigila

- **Hito jugable por paso** (`01_FASES.md` §2): si el paso no se juega, no cierra.
- **`npm run qa` verde** antes de dar nada por terminado (`04_QA.md`).
- **Registro de bugs** en `../BUGS.md`: un ALTA bloquea.

---

## 6. Cifras que fija este documento

| Cifra | Valor |
|---|---|
| Riesgos listados | 15 (7 de producto + 5 técnicos + 3 de proceso) |
| Recorte permitido | topos/alcance, **nunca** la mecánica |
| Umbral de bloqueo | bug **ALTA** |
| Presupuesto de assets demo | **~90 MB** (APK ~100 MB) ✅ 2026-10-02 |
| QA | verde antes de cerrar |

---

## 7. Qué entra en la demo (Fase 1) — y sigue

> **Hasta aquí la demo.** Los riesgos del Acto I (controles, guardado, campo pequeño, guion) con
> su detección y plan B.

> **Y sigue el juego completo.** Los riesgos de las Fases 2-5 (mundo vivo, 10+, finales) se añaden
> a esta tabla **con el mismo formato**: riesgo, detección, plan B.

---

## 8. Fuera de este documento

- Fases y sus riesgos → `01_FASES.md`
- QA → `04_QA.md`
- Guardado → `02_GUARDADO_Y_DATOS.md`
- Bugs → `../BUGS.md`
