# Mecánicas candidatas — análisis (2026-09-30)

> **Qué es:** 10 propuestas de mecánicas analizadas contra los pilares cerrados
> (`VALCORIA_DEUDA_DE_SANGRE.md`) y las reglas duras del repo.
> **Son candidatas, no decisiones:** nada entra en el roadmap hasta que el dueño aprueba
> pieza por pieza. El ranking del final está **propuesto, pendiente de confirmación**.

> **Actualizado el 2026-10-02:** varias de estas candidatas **ya son documentos aprobados** —
> Favores → [`sistemas/03_FAVORES.md`](sistemas/03_FAVORES.md) · Semana de luto →
> [`sistemas/08_LUTO_Y_MORAL.md`](sistemas/08_LUTO_Y_MORAL.md) · Cicatrices →
> [`sistemas/07_CICATRICES.md`](sistemas/07_CICATRICES.md) · Oficio fuera de batalla →
> [`sistemas/14_PROFESIONES.md`](sistemas/14_PROFESIONES.md) y
> [`sistemas/15_FABRICACION_Y_RECETAS.md`](sistemas/15_FABRICACION_Y_RECETAS.md) · Red de rencores →
> [`interfaz/05_LIBRO_MAYOR.md`](interfaz/05_LIBRO_MAYOR.md) · Soborno → el soborno de
> [`sistemas/06_ECONOMIA.md`](sistemas/06_ECONOMIA.md). Y sus **dependencias ya están cerradas**
> (memoria y Firma, mundo a pie con zonas, control de exploración). Lo único que **sigue abierto**
> es la **fase previa al campo** (ideas 7 y 10).

## Criterios del análisis

- **Encaje** con los pilares: Deuda de Sangre (Pilar 3), memoria (5), La Firma (7),
  campo de batalla (Pilar 6, diseño cerrado 2026-09-30).
- **Coste real:** pantallas nuevas, cadenas `txt_*` ×2 (ES/EN), peso en `SaveState`
  (localStorage ≤ 5 MB), balance nuevo.
- **Reglas del repo:** lógica en `systems/` puro y testeable (QA ≥ 90 %), determinismo
  (RNG sembrado), cero dependencias nuevas, sin esperas reales.

## Las 10, con veredicto

| # | Mecánica | Encaje | Coste real | Condición / riesgo | Veredicto |
|---|---|---|---|---|---|
| 1 | **Testigos**: si huye al menos un enemigo, tu Firma se propaga en la zona; si no huye nadie, no hay reputación (y los cuerpos después ata cabos alguien) | Une moral→huída (ya decidido) con Firma y memoria | **Bajo**: flag por batalla + propagación regional | Necesita **zonas/regiones** (mundo a pie sin diseñar) | ✅ Fuerte |
| 2 | **Favores**: cada capitán al que perdonas entra en tu bolsa; una sola vez por capitán puedes cobrarlo (deserta, avisa, abre) | El perdón pasa a ser moneda (Pilar 3) | Datos bajísimos; **cada efecto es un sistema** | Falta identidad de capitanes; etapa: **un solo efecto** al empezar | ✅ Fuerte, por rodajas |
| 3 | **Red de rencores**: visor del grafo de deudas y sangres entre casas | La Crónica hecha visible; único en el género | **No es "un visor"**: UI de grafo en móvil + i18n | Exige memoria rica **ya construida**; si no, grafo vacío | ⏳ Meta, no inicio |
| 4 | **Sangre llama a sangre**: si cae un tuyo, semanas después aparece su hermano (se alista o te culpa) | El mundo reacciona a tus bajas | **Medio-alto**: personajes, textos ×2, eventos | Sin LLM: texto **precocinado** (pool limitado) | ⏳ Fase 2 con pool |
| 5 | **Oficio fuera de batalla**: oficio civil por mercenario (herrero, cazador, curandero) que produce/cura con los días | Profundidad sin pantallas nuevas (números sobre el roster) | Código bajo, **balance medio** | Atado al bloque **economía** (sin plantear) | ⏳ Con economía |
| 6 | **Semana de luto**: tras perder hombres rinden menos; un funeral (oro+comida) lo compensa | La muerte pesa en economía y ánimo | **El más barato**: moral está previsto (0..100), 2 variables + 1 opción | No chocar con la moral de batalla están previstoste | ✅ **Muy fuerte** |
| 7 | **Soborno pre-batalla**: compras una unidad enemiga (oro vs lealtad); si falla, viene más enfadado | "Todo el mundo tiene precio" | Medio: **exige pantalla previa** + soporte de traidor | Rompe el "te topas → se abre el campo" directo; comparte eje con el 2 | ⚠️ Decidir antes la fase previa |
| 8 | **El campo después**: paseas el campo en 1.ª persona con mochila limitada y reloj (cuervos, lobos, refuerzos) | **El más tuyo**: reutiliza la exploración 1.ª persona; une batalla→mundo | Medio: mochila, reloj, amenazas | Bloqueado por el **control de exploración** (§10.8). Rodaja: paseo + 2-3 saqueos + reloj | ✅ 🥇 con rodaja |
| 9 | **Cicatrices**: cada derrota deja una cicatriz con historia; NPCs reaccionan y la Crónica la anota | Tu cara cuenta tu partida sin menús | Bajo: 1 campo en el guardado + reacciones con pool | Requiere **rangos de memoria** (§10.3) | ✅ Fuerte |
| 10 | **Duelo de campeones**: retas a su campeón; ganas → su moral cae antes de empezar; pierdes → entras herido | Drama puro con los controles del héroe ya decididos | Bajo: 1 botón + estado inicial modificado | "Antes de la batalla" → pide la **fase previa**; no resucitar el duelo 1v1 sustituido | ✅ Si hay fase previa |

## Tres ejes de implementación compartida

1. **El traidor (2 + 7)** — comparten el mismo núcleo: *unidad enemiga que cambia de bando*.
   Se implementa **una vez**; Favores lo gana por misericordia, Soborno por dinero.
2. **El parte de batalla (1 + 9 + 3 + 4)** — los cuatro se alimentan del mismo registro:
   *quién huyó, quién murió, qué pasó*. Un registro en `systems/` puro y de ahí cuelgan
   Firma, Crónica, cicatrices y (luego) el grafo de rencores.
3. **El paseo del campo (8 + 6)** — la **semana de luto** puede cobrarse dentro del paseo:
   enterrar a los tuyos (oro+comida → lealtad) frente a saquear al enemigo. Barato y vivo.

## Ranking propuesto (impacto / coste)

El podio original planteado (8, 1, 2) se mantiene salvo el bronce: **6 (luto) cuesta la mitad
que 2 (favores)** y su efecto es inmediato.

| Pos | Mecánica | Motivo |
|---|---|---|
| 🥇 | **8. El campo después** (rodaja: paseo + saqueo limitado + reloj) | Reutiliza la exploración 1.ª persona y une los dos modos |
| 🥈 | **1. Testigos** | Una regla diminuta que cambia cómo se juega cada batalla |
| 🥉 | **6. Semana de luto** | Dos variables, mucho tono, el coste más bajo del podio |
| 4 | **2. Favores** (un solo efecto al empezar) | Convierte el perdón en sistema económico |
| 5 | **9. Cicatrices** | Barato; prepara el terreno de la Crónica |
| 6 | **10. Duelo de campeones** | Espera a la decisión de la fase previa |
| 7 | **7. Soborno pre-batalla** | Comparte eje con el 2; también espera la fase previa |
| 8 | **5. Oficio fuera de batalla** | Junto al bloque economía |
| 9 | **4. Sangre llama a sangre** | Con pool de contenido cocinado (ES/EN) |
| 10 | **3. Red de rencores** | Es la meta del sistema de memoria, no su primera pieza |

## Dependencias de diseño que faltan

1. **¿Fase previa al campo?** — El Pilar 6 dice "te topas → se abre el campo". Las ideas 7 y 10
   necesitan un alto previo (sobornar / retar / intimidar). **Única decisión abierta.**
2. **Memoria y Firma** — ✅ **cerradas** (`sistemas/00_MEMORIA_Y_DEUDA.md`, `sistemas/01_FIRMA.md`).
3. **Mundo a pie con zonas** — ✅ **cerrado** (`mundo/00_MAPA.md`, **5** zonas).
4. **Control de exploración** — ✅ **cerrado** («la mirada lleva», 2026-10-01).

## Próximo paso

Elegir las primeras piezas (se propone: rodaja de **8** + **1** + **6**), diseñarlas con cifras
y escribir lo aprobado en `VALCORIA_DEUDA_DE_SANGRE.md` (§9 y §10) y `DECISIONES.md`.
