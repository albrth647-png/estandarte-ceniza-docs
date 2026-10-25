# 00 · Alcance — la demo del Acto I

**Estado:** ✅ **Aprobado por el dueño (2026-09-30). Documento final.**
Este documento **manda sobre el ALCANCE DE LA DEMO**: lo que se **construye** en la Fase 1 se
recorta a lo que aquí se decide. Los documentos de diseño describen el **juego completo**
(regla 6 de `../README.md`) y solo marcan con una sección final qué entra aquí. Si algo no cabe
en la demo, no se construye todavía: se apunta en §5 y espera su tanda.

---

## 1. Definición

**Nombre interno:** «Demo del Acto I».

**Promesa al jugador (una frase):** *Un reino entero apunta tu nombre en un libro; en Valcoria
todo se paga, y tú acabas de salir del cadalso con una deuda que no era tuya.*

**Qué es, en corto:**

| | |
|---|---|
| **Duración objetivo** | **2-3 horas** de juego (6 encargos + prólogo + 3 batallas) |
| **Historia** | **El Acto I completo**, desde el Patio del Cadalso hasta el giro de las páginas arrancadas |
| **Mundo** | **1 ciudad + 3 aldeas + 1 tramo de camino** (6 sitios jugables) |
| **Batalla** | Campo semi-tiempo real **pequeño: 5-6 por bando** (8 en la batalla de cierre) |
| **Sistemas** | Memoria y deuda · La Firma · Prisioneros (4 salidas) · Favores · Crónica |
| **Cierre de la demo** | El giro: alguien ha arrancado las páginas del Libro Mayor (gancho al Acto II) |

**Por qué este tamaño (y no otro):** es una **rodaja vertical completa** del bucle real
(explorar → encontrarse → pelear → decidir con el prisionero → que el mundo lo recuerde →
cobrar). Una demo corta no enseña la memoria ni la Firma; una demo de 10 horas se come el
presupuesto de texto (todo se escribe ×2, ES/EN) antes de saber si el bucle engancha.

---

## 2. Qué entra (lo aprobado)

### 2.1 Sistemas
| Sistema | Qué entra en la demo |
|---|---|
| **Memoria y deuda** | Memoria **ligera** para todo el mundo + **completa** para los relevantes; deudas a favor y en contra |
| **La Firma** | Se escribe con lo que haces; se propaga **por testigos** entre las aldeas del camino |
| **Prisioneros** | Las **4 salidas** (rescatar, retener, voltear, ejecutar) con precios y consecuencias |
| **Favores** | La **deuda blanca**: un favor cobrable **una vez** por persona |
| **Crónica** | Diario autoescrito con lo que pasa (batallas, bajas, deudas, favores) |
| **Registro simple** | La pestaña que cumple la promesa literal: lista de **Crónica** y de deudas/favores de los 6 sitios (`../interfaz/05_LIBRO_MAYOR.md`). El Libro Mayor **completo** sigue fuera (§5) |
| **Casa alquilada** | Los **cuartos** donde se guarda un rehén: **1 en la demo**, renta 5 oro/día, rédito rescate ÷ 10 y 1 ración/día (`../sistemas/02_PRISIONEROS.md` §3.1) |
| **Profesión (fina)** | **1** profesión (la del origen) en rango **Aprendiz**, sus **3 recetas base** y 1 recurso de nivel 1 (`../sistemas/14_PROFESIONES.md`, `../sistemas/15_FABRICACION_Y_RECETAS.md`) |

### 2.2 Soporte imprescindible (lo que estos sistemas necesitan para funcionar)
- **Guardado**: guardar, cargar, migrar, slots y respaldo de corruptos (previsto y no se rompe).
- **Derrota sin bloqueo** (Pilar 3, lado B): si caes, el mundo decide qué te pasa
  (cautiverio, rescate, te arrastra un aldeano). **El fallo nunca atasca.**
- **Economía mínima**: oro que entra (botín, cobranza) y sale (recluta, salarios, soborno,
  rescate). Precios simples.
- **Reclutamiento**: los **Marcados** se alistan en el mundo (tropas para el campo de batalla).

### 2.3 Mundo
- **El Patio del Cadalso** (la ciudad donde empieza todo) + **3 aldeas** + **1 tramo de camino**
  con **2 hitos**: una posada y un cruce (vado o puente).
- **El Paso del Juramento** solo **en flashback** (la noche de la guardia).
- Cada sitio tiene su razón de ser: cobrar, reclutar, descansar, escuchar rumores, comprar.

### 2.4 Historia
- **Prólogo** (el cadalso y la compra de tu espada) + **Acto I completo** hasta el giro de
  las páginas arrancadas.
- **1 flashback jugable**: la noche de la guardia (Paso del Juramento).
- Los personajes fijos de esta tanda: **Doña Sira**, **el escribano joven**, **los Marcados**
  y **PNJ de aldea** con memoria completa.

### 2.5 Batalla
- Campo **semi-tiempo real** con **5-6 por bando** (8 en la batalla de cierre), **órdenes
  globales** (Cargar / Seguirme / Defender) + tus botones (Golpe / Guardia / Desvío).
- **Moral, huida y rendición**, funcionando (de ellas nacen los prisioneros y los testigos).
- **3 campos**: llanura de camino, aldea y bosque (el campo depende del terreno,
  Pilar 6).

### 2.6 Presentación y textos
- HUD mínimo que **no tapa** el campo, avisos sin gritar, transiciones **sin esperas reales**.
- **Todo el texto ES/EN** con paridad (validador en verde).
- **Estilo película medieval** (enmienda 2026-10-02): dirección de fotografía en paisajes (luz de
tarde, niebla, paleta de tierra) y **retratos pintados** de los 16 personajes clave en los
bocadillos (`../arte/00_ESTILO.md` §1, `../arte/01_ASSETS.md` §2b).
- **Voz hablada del elenco relevante** (TTS local en producción, ES y EN, `../arte/02_AUDIO.md`
  §1) y **texto con sonido de mundo** en lo generativo; presupuesto de audio **≤ 20 MB** dentro
  de los ~90 MB de la demo.

---

## 3. Números del alcance (mínimos de la demo)

| Pieza | Mínimo | Por qué |
|---|---|---|
| Sitios jugables | **6** | 1 ciudad + 3 aldeas + 2 hitos de camino: el mapa se recuerda sin GPS |
| Encargos | **6** | uno por sitio: enseña el sistema sin repetirse |
| Batallas | **3** | la que enseña, la que aprieta y la del cierre del acto |
| Tipos de tropa reclutables | **3** | una de línea, una de distancia y una de apoyo |
| Familias enemigas | **3** | bandidos de camino, cuadrilla de una casa y patrulla de Altamir |
| Campos de batalla | **2** | llanura y bosque/aldea (los dos extremos del terreno) |
| Capitanes enemigos con memoria | **4+** | los que huyen y vuelven; el resto, tropa rasa |
| PNJ con memoria completa | **12** | los 8 del elenco + 4 de mundo; el resto, memoria ligera |
| Nivel máximo del héroe (demo) | **15** | tope de la demo; el juego completo llega a **60** (`../sistemas/12_NIVELES_DEL_HEROE.md`) |
| Cuartos de rehén | **1** | Retener es una decisión, no una acumulación |
| Profesión en la demo | **1** (Aprendiz, 3 recetas) | Muestra el oficio sin arrastrar el sistema completo |
| Claves `txt_*` nuevas (estimación) | **300-450 ×2** | presupuesto de guion; se ajusta al escribir `historia/04_GUION` |
| Presupuesto de audio (demo) | **≤ 20 MB** | voz del elenco relevante ×2 idiomas, sin motor de voz embebido ✅ 2026-10-02 |
| Retratos de los personajes clave | **16** (2D) | la cara de película sin pagar 3D; 1 imagen vale ES+EN ✅ 2026-10-02 |
| Cuerpos de personaje | **proporción humana, todos** | nada de muñecos en pantalla; cartoon KayKit → reserva ✅ 2026-10-02 |
| Topes de peso (90 MB / APK 100) | 🟡 a revisar | el dueño los confirma al ver la **primera escena de paisaje** (2026-10-02) |

*Cifras de balance (vida, daño, moral, precios) NO se deciden aquí: viven en
`../batalla/01_CIFRAS.md` y `../sistemas/06_ECONOMIA.md`.*

---

## 4. Los primeros 30 minutos (prueba de la promesa)

| Minuto | Qué pasa | Qué enseña |
|---|---|---|
| 0-5 | El cadalso: te leen la sentencia y **Doña Sira compra tu espada** | La Ordenanza: la sangre se paga |
| 5-10 | Primer camino con la marca en la cara; la gente te reconoce | La marca y la memoria ligera |
| 10-20 | **Primera deuda**: cobrar en una aldea que ni sabe quién eres | Cobranza, negociación, precios |
| 20-25 | **Primera batalla** (5-6 por bando): la moral enemiga se rompe y **huyen tres** | Campo, órdenes, moral, huida |
| 25-30 | **El primer Marcado se alista** contigo y la noticia de tu Firma empieza a correr | Recluta, Firma y testigos |

Si a los 30 minutos el jugador entiende que **las deudas y lo que el mundo recuerda** son el
juego, la demo está bien construida.

---

## 5. Qué queda fuera (y en qué tanda vuelve)

| Queda fuera de la demo | Vuelve en |
|---|---|
| Acto II, Acto III y los **tres finales** | Segunda y tercera tanda |
| **Luto y moral**, **Libro Mayor completo**, **cicatrices** | Segunda tanda (sistemas que ya tienen su documento). **Nota (2026-10-02):** el **Registro simple** y la **marca del cadalso** del prólogo sí están en la demo (§2.1) |
| **Red de rencores** (grafo visible) y **mundo vivo** | Tras la memoria rica del Acto II |
| Lealtad y deserción · supervivencia · clima y estaciones · monturas · animales | Segunda tanda |
| Más ciudades y regiones, más campos, **10+ por bando** | Al escalar la demo a juego |
| Créditos, mercado y publicación | `../produccion/05_MERCADO_Y_LANZAMIENTO.md` |

Nada de esta tabla se diseña ahora **en detalle**: primero se termina la demo. Sus documentos
existen en el plan (`../PLAN_DOCUMENTOS.md`) y se abordan en su orden.

---

## 6. Criterio de terminado (qué significa «está»)

1. **Se juega de principio a fin** (prólogo → giro final) sin atascos ni callejones sin salida.
2. **El fallo nunca bloquea**: caer, perder una batalla o no pagar siempre dan salida.
3. **Guardado intacto**: guardar, cargar, migrar, slots y respaldo del corrupto funcionando.
4. **`npm run qa` verde**: check + lint + validate + docs + tests con cobertura ≥ 90 % + humo.
5. **Paridad ES/EN**: cero claves sin traducir y cero enlaces rotos en la documentación.
6. **10 minutos sin errores en consola** y humo en dos tamaños de pantalla.
7. **La promesa se cumple** (§4): alguien ajeno al proyecto lo entiende jugando 30 minutos.

---

## 7. Qué NO se decide aquí

- **Cifras de balance** (vida, daño, moral, precios, topes): `../batalla/01_CIFRAS.md` y
  `../sistemas/06_ECONOMIA.md`.
- **Guion línea a línea y escenas**: `../historia/03_RECORRIDO.md` y `../historia/04_GUION.md`.
- **Catálogos** (tropas, enemigos, ítems, encargos): `../contenido/*` y `../misiones/*`.
- **Orden de construcción**: `01_FASES.md` (siguiente documento).
