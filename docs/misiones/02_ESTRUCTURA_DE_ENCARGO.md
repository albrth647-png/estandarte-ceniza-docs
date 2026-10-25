# 02 · Estructura de un encargo — cómo se define en datos

**Estado:** ✅ **aprobado por el dueño (aprobación en bloque, 2026-09-30). Documento final.**

> Un encargo es **datos, no código**: el mismo motor lo ejecuta para los 6 de la demo y para los
> miles del juego completo. Todo dato nuevo entra **con su validador** (regla 5 de
> `../../AGENTS.md`). Los tipos, en `00_TIPOS_DE_ENCARGO.md`.

---

## 1. Los campos de un encargo

| Campo | Qué es | Obligatorio |
|---|---|---|
| `id` | `snake_case` único (`cobranza_peaje_vega`) | Sí |
| `titulo_txt` | Clave `txt_enc_*` para el cartel | Sí |
| `clase` | Una de las **11** (`00_TIPOS_DE_ENCARGO.md`) | Sí |
| `da` | Quién lo publica: id de PNJ o de casa | Sí |
| `lugar` | Id de sitio (`data/lugares.json`) donde se coge | Sí |
| `objetivo` | Qué hay que lograr (§2) | Sí |
| `plazo_dias` | Días de juego (0 = no caduca) | Sí |
| `testigos` | `sí`/`no`: ¿queda escrito en tu Firma? | Sí |
| `recompensa` | Qué se cobra (§4 de `04_PAGOS_Y_RECOMPENSAS.md`) | Sí |
| `fallo` | Qué pasa si no la cumples (§3) | Sí |
| `cadenas` | Ids de encargos que abre/cierra | No |
| `gating` | Condiciones para ofrecerlo (Firma, memoria, día) | No |

---

## 2. Objetivos (los seis tipos)

| `objetivo.tipo` | `meta` | Ejemplo |
|---|---|---|
| `cobrar` | Oro y deudor | Cobrar 200 oro al viejo del peaje |
| `acompañar` | Destino | Llevar al merciero a la villa |
| `vencer` | Id de campo/familia | Romper la cuadrilla del cruce |
| `salvar` | Id de PNJ | Sacar al joven de la cuadrilla |
| `negociar` | Las dos partes | Poner paz entre dos casas |
| `callar` | Id y días | No hablar ante el Escribano |

- Un encargo tiene **un** objetivo (a lo sumo, uno principal y uno opcional). Si pide dos cosas
  igual de importantes, son **dos encargos** (y una cadena, `03_CADENAS_Y_RUMORES.md`).

---

## 3. Fallo: qué pasa si no la cumples

- **Fallo blando** (plazo vencido, lo coge otro): pierdes el pago; si diste palabra, memoria
  hecho **9 · Incumplimiento** (−5).
- **Fallo duro** (haces lo contrario: saqueas al cliente, matas al rehén):
  - Firma según el hecho (`../sistemas/01_FIRMA.md` §4),
  - memoria del agraviado (que puede **encender rencor**, `../sistemas/00_MEMORIA_Y_DEUDA.md` §7),
  - y, si había testigos, **crónica**.
- **Nunca bloquea:** el fallo cierra esa puerta, no la partida (`../produccion/01_FASES.md` §1 regla 7).

---

## 4. Testigos y Firma

- **`testigos: sí`** → tu desempeño **queda escrito**: Firma y Crónica. Ej.: cobrar delante de la
  aldea, ganar un campo delante de testigos.
- **`testigos: no`** → solo mueve la **memoria personal** (`00_MEMORIA_Y_DEUDA.md`), no la Firma:
  lo que nadie vio, no te lo apunta el reino (`01_FIRMA.md` §1).
- Los testigos se cuentan **en el sitio** (aliados, aldeanos, enemigos vivos, Escribanos).

---

## 5. Ejemplos completos

```json
{
  "id": "cobranza_peaje_vega",
  "titulo_txt": "txt_enc_cobranza_peaje",
  "clase": "cobrar",
  "da": "dona_sira",
  "lugar": "vega_quemada",
  "objetivo": { "tipo": "cobrar", "meta": 200, "deudor": "viejo_peaje" },
  "plazo_dias": 5,
  "testigos": true,
  "recompensa": { "oro": 200, "favor": false, "info": false },
  "fallo": { "memoria_hecho": 9, "firma": 0, "rencor": false },
  "cadenas": ["enc_peaje_vuelve"],
  "gating": { "firma_min": -100, "dia_min": 1 }
}
```

```json
{
  "id": "limpiar_cruce_dos_sendas",
  "titulo_txt": "txt_enc_limpiar_cruce",
  "clase": "limpiar",
  "da": "portavoz_cruce",
  "lugar": "cruce_dos_sendas",
  "objetivo": { "tipo": "vencer", "meta": "cuervos_del_camino" },
  "plazo_dias": 3,
  "testigos": true,
  "recompensa": { "oro": 120, "info": true },
  "fallo": { "memoria_hecho": 9, "firma": 0, "rencor": true },
  "cadenas": ["enc_cuervos_casa"],
  "gating": { "firma_min": -100, "dia_min": 3 }
}
```

---

## 6. Datos, tipos y validación

- **Datos (por crear):** `data/encargos.json` (array de objetos con el formato de §1).
- **Tipos:** `Encargo`, `Objetivo`, `Recompensa`, `Fallo` en `js/data/game_types.js` (una vez).
- **Validación** (`js/data/schemas.js` + `tools/validate_data.js`):
  - `clase` ∈ las 11; `lugar` existe en `lugares.json`; `da` entrará en datos de PNJ/casas;
  - `objetivo.tipo` ∈ los 6; `meta` coherente con el tipo;
  - `plazo_dias` ≥ 0; `recompensa` no vacía; ids de `cadenas` existen;
  - **sin validador en verde, la carga no arranca (regla 5, cuando exista el build)** (regla 5).
- **Sistema puro:** `js/systems/encargos.js` — ofrece, acepta, resuelve y caduca; sin DOM ni reloj.
- **Tests (por escribir):** `tests/encargos.test.js`, mínimo 3 casos (normal, borde, error): un encargo mal
  formado se rechaza al cargar; el fallo blando no rompe nada; `cadenas` inexistentes fallan.

---

## 7. Cifras que fija este documento

| Cifra | Valor |
|---|---|
| Campos obligatorios | 9 (§1) |
| Tipos de objetivo | **6** (cobrar · acompañar · vencer · salvar · negociar · callar) |
| Objetivos por encargo | **1** (+1 opcional) |
| Plazo | 0 = no caduca (columna) |
| Testigos | sí → Firma · no → solo memoria |
| Validación | obligatoria (regla 5) |

---

## 8. Qué entra en la demo (Fase 1) — y qué sigue

> **Hasta aquí la demo.** Los **6 encargos** del Acto I escritos con este formato, pasando por su
> validador, con `testigos` y `cadenas`, funcionando.

> **Y sigue el juego completo.** Todos los encargos del reino usan **este mismo formato**: crecer
> = añadir filas a `encargos.json` (a mano o generadas con `js/systems/encargos.js`), sin tocar el
> motor.

---

## 9. Fuera de este documento

- Clases → `00_TIPOS_DE_ENCARGO.md`
- Dónde se cogen → `01_TABLONES_Y_PORTAVOCES.md`
- Cadenas y rumores → `03_CADENAS_Y_RUMORES.md`
- Pagos → `04_PAGOS_Y_RECOMPENSAS.md`
- Checklist de datos → `../DATOS.md`
