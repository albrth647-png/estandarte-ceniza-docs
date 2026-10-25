# 01 · Cifras — todo el balance del campo en una página

**Estado:** ✅ **aprobado por el dueño (aprobación en bloque, 2026-09-30). Documento final.**

> Es el sitio donde viven las **cifras generales de combate** (vida, daño, moral, ritmo). Las
> cifras propias del **terreno** viven en `02_TERRENO.md` y las de la **IA y las órdenes** en
> `03_IA_Y_ORDENES.md`. Si una cifra cambia, cambia en su documento y se anota en
> `../DECISIONES.md`. El alcance de la demo no las toca (`../produccion/00_ALCANCE.md` §7).

---

## 1. Vida

| Pieza | Vida | Notas |
|---|---|---|
| Héroe | **120 + 10 × (nivel − 1)** | Nivel 60 → **710** (`../sistemas/12_NIVELES_DEL_HEROE.md`) |
| Tropa de línea | **60** | ×escalado por nivel |
| Tropa de distancia | **40** | ×escalado por nivel |
| Tropa de apoyo | **45** | ×escalado por nivel |
| Capitán enemigo | **160** | +20 por rango de casa · ×escalado |
| Aldeano / civil | **30** | No combate: huye o se rinde |
| Zapador / barbero | **45-50** | Rol de apoyo (`../contenido/00_TROPAS.md` §3.3) |
| Montado ligero / pesado | **80 / 100** | ✅ Fase 4 (`../contenido/00_TROPAS.md` §3.4) |
| Perro de guerra | **35** | ✅ especialista, Fase 4 |
| Mercenario del Paso | **55** | ✅ especialista, Fase 4 |
| Bestias (lobo · jabalí · oso · cuervo) | **25 · 30 · 90 · 10** | ✅ `../contenido/08_ANIMALES_Y_CRIATURAS.md` |

- **Toda unidad tiene vida** (héroe, tropas, compañeros, capitanes, enemigos de zona, bestias y
  civiles); las vidas de Fase 4 están **cerradas** (2026-10-01). El escalado por nivel, en
  `../sistemas/12_NIVELES_DEL_HEROE.md` §5.

---

## 2. Ataque, defensa y daño

- **Mitigación (herencia de nuestro balance):** `daño = ataque × 80 / (defensa + 80)`.

| Quién | Ataque | Defensa |
|---|---|---|
| Héroe (nivel 1) | 28 | 18 |
| Héroe (nivel 15) | 60 | 55 |
| Héroe (nivel 60) | **164** | **177** |
| Tropa de línea | 16 | 22 |
| Tropa de distancia | 14 | 8 |
| Tropa de apoyo | 12 | 12 |
| Capitán | 30 | 30 |

*Ejemplos:* 28 de ataque contra 22 de defensa → **19** daño. Contra 55 → **13**. La defensa
nunca anula el daño (tope práctico: ~85 % con defensa 400).

- **Crítico:** 10 % de probabilidad × **1,5**. Nunca más del 10 %, nunca acumulable.
- **Daño máximo por golpe:** 90 (héroe) / 45 (tropa) — para que nadie «onewipe». **Se aplica
  después de escalar por nivel** (`../sistemas/12_NIVELES_DEL_HEROE.md` §5).
- **Las joyas no rompen el tope:** anillo de plata (+2 ataque) + arma `rara` +1 en nivel 30 sigue
  por debajo de 90. Test de borde en `tests/recetas.test.js`
  (`../sistemas/15_FABRICACION_Y_RECETAS.md` §8).

---

## 3. Tiempos y alcances

| Magnitud | Valor |
|---|---|
| Cadencia del golpe del héroe | **1,2 s** |
| Ventana de Guardia | **0,5 s** (reduce 75 %) |
| Recuperación de Guardia | 0,4 s en los que no bloqueas |
| Desvío (esquiva) | 0,35 s de invulnerabilidad, coste 15 de aliento |
| Aliento | 100, regenera **5/s** fuera de acción |
| Alcance cuerpo a cuerpo | **2,5 m** (lanza: 3,5 m) |
| Alcance de arco | **18 m** |
| Vista de campo | **60 m** (la niebla corta antes) |
| Cadencia de IA | **0,5 s** por unidad |

---

## 4. Movimiento

| Quién | Andar | Correr |
|---|---|---|
| Héroe | 3,0 m/s | 5,0 m/s (exploración: `../mundo/01_EXPLORACION.md`) |
| Tropa de línea / apoyo | 3,0 | 4,5 |
| Tropa de distancia | 3,2 | 4,8 |
| Unidad huyendo | — | 5,5 |

- Órdenes: **Cargar** = +30 % de velocidad 5 s; **Defender** = −40 % de velocidad mientras
  dure; **Seguirme** = velocidad de tu tropa más lenta.
- Monturas: ver `../contenido/13_MONTURAS_Y_TRANSPORTE.md` (no entran en la demo).

---

## 5. Moral

| Magnitud | Valor |
|---|---|
| Moral inicial (unidad y bando) | **100** |
| Muerte de un aliado a < 6 m | **−15** |
| Muerte propia vista (baja en tu formación) | **−8** |
| Un aliado huye a < 10 m | **−25** |
| Quedar en inferioridad numérica | **−10** (una vez por batalla) |
| Orden **Cargar** recibida | **+10** |
| Héroe o capitán a < 8 m | **+2/s** |
| Recuperación sin daño | **+2/s** |
| **Ruptura** | a **0** · con miedo (Fiera/Hiena) a **10** |
| Pánico en cadena | se rompe **un tercio** del bando |
| Capitán: sus pérdidas pesan | ×**2** en su gente |

---

## 6. Duración y ritmo

| Magnitud | Valor |
|---|---|
| Batalla de 5-6 por bando | **90–180 s** |
| Batalla de 10+ por bando | **150–240 s** |
| Despliegue | 5 s (emboscada: 0) |
| Reloj | 100 % · **25 %** al abrir órdenes · 100 % 1 s al confirmar |
| Aviso de encuentro | 2 s o botón (si no, arranca a los 10 s) |

---

## 7. Cifras de la demo (recorte de cantidad, no de reglas)

| Pieza | Demo | Juego completo |
|---|---|---|
| Unidades por bando | **5-6** (8 en el cierre) | **10+** |
| Campos | **2** (llanura, bosque/aldea) | Todos los del catálogo |
| Capitanes con memoria | **4+** | Todos los de casa |

---

## 8. Cómo se verifica

- Todas estas cifras viven en `data/` (números en JSON, no escondidos en el código) y pasan
  por `tools/validate_data.js`.
- Tests de balance en `tests/campo.test.js`: daño esperado, ruptura de moral por tres huidos
  y duración objetivo (simulación de 100 batallas con RNG inyectado).
- Si un cambio rompe la duración objetivo (§6), se revierte **aquí** y en
  `../DECISIONES.md`.

---

## 9. Qué entra en la demo (Fase 1)

**Las mismas cifras de este documento**, con la recarga de §7. Nada especial que recortar:
la demo es el juego pequeño.

---

## 10. Fuera de este documento

- Reglas y fases → `00_REGLAS.md`
- Precios, oro y salarios → `../sistemas/06_ECONOMIA.md`
- Vida y daño de objetos → `../contenido/04_ITEMS_Y_EQUIPO.md`
- Habilidades y sus costes → `../contenido/06_HABILIDADES.md`
