# 00 · Tropas — los que luchan contigo

**Estado:** ✅ **aprobado por el dueño (aprobación en bloque, 2026-09-30). Documento final.**

> Tus tropas son **los Marcados**: deudores de sangre que pagan su cuenta sirviéndote
> (`../historia/00_PREMISA.md`). Describe el **juego completo** (10+ por bando, Pilar 6). Las
> **stats** viven en `../batalla/01_CIFRAS.md`; los **precios y salarios** en
> `../sistemas/06_ECONOMIA.md`; cómo suben, en `../sistemas/05_PROGRESION.md`; lo que
> pasa cuando caen, en `../sistemas/08_LUTO_Y_MORAL.md`.
>
> **Nombres e ids son propuesta de diseño**; si el dueño los cambia, se anota en
> `../DECISIONES.md`.

---

## 1. La regla de oro de la compañía

1. **Nadie sirve de gratis:** cada tropa es un deudor que paga con la espada, o un hombre que se
   alista por oro. **Toda tropa tiene cuenta, casa, nombre y miedo** — ninguna es decorado.
2. **La deuda manda:** el que se alista por deuda es **leal** mientras se pague con servicio; el
   que se alista por oro se va si no cobra (`../sistemas/10_LEALTAD_Y_DESERCION.md`).
3. **Tu Firma filtra quién viene:** los honorables solo sirven a Firma ≥ Honrado; los crudos, a
   Firma ≤ Fiera (`../sistemas/01_FIRMA.md` §6).
4. **Se pelea con lo que hay:** la misma tropa que reclutas es la que pelea, la que come y la que
   puedes perder.

---

## 2. Los roles (y por qué el campo no es una masa)

| Rol | Qué hace en el campo | Stats (`../batalla/01_CIFRAS.md`) |
|---|---|---|
| **Línea** | Aguanta, forma y carga; el muro de la compañía | Vida **60** · ataque **16** · defensa **22** |
| **Distancia** | Dispara desde atrás; el daño que decide sin contacto | Vida **40** · ataque **14** · defensa **8** |
| **Apoyo** | Sostiene moral, cura fuera de combate, abre paso | Vida **45** · ataque **12** · defensa **12** |
| **Montado** | Rompe líneas y persigue (no entra en la demo) | Vida **80 / 100** (ligero/pesado) · ataque/defensa en Fase 4 |
| **Especialista** | Perro, zapador, mercenario de paso (alguno llega en Fase 4) | Vida **35 / 55** (perro/mercenario) · ataque/defensa en Fase 4 |

- **Las 3 líneas base (línea / distancia / apoyo) están cerradas** en `01_CIFRAS.md` §1–§2.
- **Vidas de montados y especialistas cerradas** (2026-10-01) en `01_CIFRAS.md` §1; su ataque y
  defensa se cierran **cuando entren**: aquí se reservan, no se inventan.

---

## 3. El catálogo

Cada tropa tiene: rol, arma, alcance, estadísticas (de `01_CIFRAS.md`), **coste de recluta**,
**salario diario** y un **rasgo** propio. Precios = **propuesta** a cerrar en
`../sistemas/06_ECONOMIA.md`.

### 3.1 Línea (el muro)

| id | Nombre | Arma | Alcance | Coste (prop.) | Salario/día (prop.) | Rasgo |
|---|---|---|---|---|---|---|
| `marcado_lancero` | Marcado de lanza | Lanza | 3,5 m | 40 oro | 3 | Aguanta la carga con la lanza plantada |
| `marcado_espada` | Marcado de espada y escudo | Espada | 2,5 m | 45 oro | 3 | Mejor Guardia (más ventana de bloqueo) |
| `marcado_hacha` | Marcado de hacha | Hacha | 2,5 m | 50 oro | 4 | Rompe escudos y empalizadas |

### 3.2 Distancia (el daño de atrás)

| id | Nombre | Arma | Alcance | Coste (prop.) | Salario/día (prop.) | Rasgo |
|---|---|---|---|---|---|---|
| `marcado_ballestero` | Marcado ballestero | Ballesta | 18 m | 55 oro | 4 | Recarga lenta, golpe fuerte |
| `marcado_arquero` | Marcado arquero | Arco | 18 m | 50 oro | 3 | Cadencia alta, poco daño por flecha |
| `marcado_hondero` | Marcado hondero | Honda | 14 m | 30 oro | 2 | Barato; aturde (ver `../batalla/01_CIFRAS.md` al cerrarlo) |

### 3.3 Apoyo (lo que sostiene)

| id | Nombre | Arma | Alcance | Coste (prop.) | Salario/día (prop.) | Rasgo |
|---|---|---|---|---|---|---|
| `portaestandarte` | Portaestandarte | Asta y bandera | 2,5 m | 60 oro | 5 | +5 de moral al bando mientras está en pie |
| `barbero` | Barbero de la marca | Cuchillo | 2,5 m | 45 oro | 4 | Venda: evita 1 baja de campaña por batalla |
| `zapador` | Zapador | Pica y hacha | 2,5 m | 50 oro | 4 | Abre puertas y empalizadas |

- **Portaestandarte:** su bandera sube la moral del bando **+5** mientras esté en pie (se suma a
  la contextura del capitán, `../batalla/03_IA_Y_ORDENES.md` §4).
- **Barbero:** **fuera de combate** cura heridas de campaña (`../sistemas/08_LUTO_Y_MORAL.md`);
  dentro del campo, solo venda rápida (evita 1 baja de campaña por batalla).
- **Zapador:** abre puertas y empalizadas (`../contenido/09_EDIFICIOS_Y_ESTRUCTURAS.md`).

### 3.4 Montados y especialistas (juego completo)

| id | Nombre | Rol | Entra en |
|---|---|---|---|
| `jinete_marcado` | Jinete de la marca | Montado ligero | Fase 4 (`../contenido/13_MONTURAS_Y_TRANSPORTE.md`) |
| `caballero_de_casa` | Caballero de casa | Montado pesado | Fase 4 |
| `perro_de_guerra` | Perro de guerra | Especialista | Fase 4 (`../contenido/08_ANIMALES_Y_CRIATURAS.md`) |
| `mercenario_de_paso` | Mercenario del Paso | Especialista | Fase 4 |

---

## 4. El aforo: cuántos puedes llevar

- **Aforo de la compañía = 6 + 2 × (nivel del héroe − 1)**, con techo **40** (se alcanza en el
  nivel **18**; `../sistemas/12_NIVELES_DEL_HEROE.md` §2).
- En cada **campo** solo pelea una **vanguardia**: hasta **20 por bando** en el juego completo
  (10+ del Pilar 6); el resto espera. En la **demo**, 5-6 por bando (8 en el cierre).
- **Qué lo limita:**
  - **Oro:** no puedes pagar más de lo que cobras (`../sistemas/06_ECONOMIA.md`).
  - **Comida:** cada tropa come; sin reserva, la lealtad cae (**Fase 4**,
    `../sistemas/10_LEALTAD_Y_DESERCION.md`; en la demo solo afecta a la moral de campaña).
  - **Firma:** los honorables no sirven a un Hiena; los crudos no sirven a un Palabra dada.

---

## 5. Cómo se reclutan (en el mundo)

| Dónde | Quién llega | Puerta |
|---|---|---|
| **Aldea** | El deudor que quiere pagar sirviendo | Memoria/banda del PNJ y tu Firma |
| **Posada / cruce** | El que se alista por oro | Tu oro y tu Firma |
| **Tras la batalla** | El **volteado** y el **rescatado** | Las **4 salidas** (`../sistemas/02_PRISIONEROS.md`) |
| **Encuentro de viaje** | El reclutador de Marcados | `../mundo/02_VIAJE_Y_ENCUENTROS.md` §3 |

- El recluta **recuerda**: viene con su ficha de memoria (`../sistemas/00_MEMORIA_Y_DEUDA.md`)
  y su casa puede cobrarle después.
- **Quien no quiere servir contigo:** el honrado a Firma baja, el que te odia, el que tiene
  rencor activo.

---

## 6. Cómo mejora (veteranía)

- **Nivel de tropa (1-60, misma escala que el héroe):** los supervivientes suben por **veteranía**
  (`../sistemas/12_NIVELES_DEL_HEROE.md` §4). Al reclutar entran al **nivel de la zona**, no al
  tuyo; a los hitos, **+2 de ataque** o **+4 de vida** (a elegir por rol). **Techo: nivel de zona
  + 2.**
- **Equipo:** armas y armaduras por tropa (`../contenido/04_ITEMS_Y_EQUIPO.md`).
- **Sin números infinitos:** el techo de mejora no rompe el balance de `../batalla/01_CIFRAS.md`.

---

## 7. Qué pasa cuando caen

- **Muerte de tropa = baja de campaña** (no se recupera en el campo, `../batalla/00_REGLAS.md` §9).
- Se paga con **luto** (`../sistemas/08_LUTO_Y_MORAL.md`): moral de la compañía y su nombre
  en la **Crónica** (`../sistemas/04_CRONICA.md`).
- **Herederos:** si el muerto debía, su deuda pasa a su hijo (100 %) o su casa (50 %)
  (`../sistemas/00_MEMORIA_Y_DEUDA.md` §5). La memoria de la gente que sirvió contigo **no se
  borra**.

---

## 8. Datos, tipos y validación

- **Datos (por crear):** `data/tropas.json` — `{ id, rol, arma, alcance, stats, coste, salario, moral,
  rasgo, entrada }`.
- **Tipos:** `Tropa` en `js/data/game_types.js` (una sola vez, regla 4).
- **Validación:** esquema en `js/data/schemas.js` + cruce con `data/terreno.json` (rol válido) y
  con `../batalla/01_CIFRAS.md` (stats conocidas) en `tools/validate_data.js`.
- **Sistema puro:** el reclutamiento y el aforo vivirán en `js/systems/tropas.js`; sin DOM, sin reloj.

---

## 9. Cifras que fija este documento

| Cifra | Valor |
|---|---|
| Roles | 5 (línea · distancia · apoyo · montado · especialista) |
| Tropas de las 3 líneas base | **9** (3 por rol) |
| Aforo de compañía | 6 + 2 × (**nivel − 1**) · techo **40** |
| Vanguardia en el campo | hasta **20** por bando (10+ del Pilar 6) |
| Portaestandarte | +5 de moral al bando |
| Barbero | evita 1 baja de campaña por batalla |
| Moral inicial | **100** para toda tropa (`../batalla/01_CIFRAS.md` §5); los rasgos matizan, no bajan el 100 |

---

## 10. Qué entra en la demo (Fase 1) — y qué sigue

> **Hasta aquí la demo.** **3 tipos reclutables**, uno por rol:
> `marcado_lancero` (línea) · `marcado_ballestero` (distancia) · `portaestandarte` (apoyo)
> (`../produccion/00_ALCANCE.md` §3). Reclutamiento en los 6 sitios y aforo por nivel,
> funcionando con estas mismas reglas. El resto del catálogo entrará en datos pero **no se
> ofrece** hasta su fase.

> **Y sigue el juego completo.** Los **9** de las 3 líneas base, los **montados** y los
> **especialistas** se añaden **con estas mismas reglas**: crecer = añadir filas a
> `tropas.json`, no rehacer el sistema. Las cifras de montado/especialista se cierran en
> `../batalla/01_CIFRAS.md` al abrir la Fase 4.

---

## 11. Fuera de este documento

- Stats y daño → `../batalla/01_CIFRAS.md`
- Órdenes y comportamiento → `../batalla/03_IA_Y_ORDENES.md`
- Precios y salarios → `../sistemas/06_ECONOMIA.md`
- Subida de nivel → `../sistemas/05_PROGRESION.md`
- Muerte y luto → `../sistemas/08_LUTO_Y_MORAL.md`
- Prisioneros y las 4 salidas → `../sistemas/02_PRISIONEROS.md`
- Enemigos contra los que pelean → `01_ENEMIGOS.md`
