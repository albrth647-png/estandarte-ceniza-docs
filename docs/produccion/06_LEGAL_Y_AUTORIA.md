# 06 · Legal y autoría — de quién es cada cosa

**Estado:** ✅ **aprobado por el dueño (aprobación en bloque, 2026-09-30). Documento final.**

> El proyecto es **propiedad del autor** (todos los derechos reservados): **no** usa licencia libre
> (decisión del dueño, `../../THIRD_PARTY.md`). Aquí está **qué es propio, qué es de terceros y qué
> se exige** para añadir algo.

---

## 1. Derechos

- **Código, textos, diseño y audio propios:** © del autor, todos los derechos reservados.
- **Nada se libera** bajo licencia abierta.
- La **política de datos** es parte del legal → `09_PRIVACIDAD_Y_DATOS.md`.

---

## 2. Terceros (en tiempo de ejecución)

| Componente | Uso | Licencia |
|---|---|---|
| **Three.js r186** + GLTFLoader/BufferGeometryUtils/SkeletonUtils | render y carga `.glb` | **MIT** |
| **10 modelos `.glb`** | personajes y animal | **CC0 1.0** (KayKit) · **CC0 + CC-BY 4.0** (Fox) |
| **Assets generados con herramientas propias** (retratos, texturas, voz) | caras, materiales y voz hablada | Propios del proyecto; herramienta y licencia fichadas en `../../art/AUTORES.md` |

- **Todo vendorizado** en `vendor/` y `art/`: cero CDNs, cero red (regla offline).
- **Crédito CC-BY obligatorio** del **zorro** (PixelMannen · tomkranis · AsoboStudio): se conserva
  en los créditos del juego (`js/scenes/sc_creditos.js`).
- Fichas y licencias completas: `../../art/AUTORES.md` y `../../THIRD_PARTY.md`.

---

## 3. Originalidad (regla 7)

- **Cero** activos, nombres o textos de juegos de terceros.
- **Toda pieza nueva** entra **con su ficha** (autor, licencia, enlace, fecha) **antes** de
  commitearse; sin ficha, no entra (lo comprueba `tools/validate_data.js`).
- **Prueba de originalidad:** el nombre «Valcoria», sus casas, su Ordenanza y sus textos son
  **propios**; los modelos libres están atribuidos.
- **Assets generados (2026-10-02):** todo lo generado con las herramientas del dueño (imagen y
  voz) se declara en su ficha **como cualquier otro asset**; los **buscadores de stock NO se
  usan** en este juego (originalidad, regla 7).

---

## 4. Edad y contenido

- **Violencia de guerra sobria:** golpes, cicatrices y muertes sin gore (`../arte/04_EFECTOS_Y_PARTICULAS.md` §1).
- **Temas duros:** deuda, rescates, ejecuciones — tratados con tono adulto, sin morbo.
- **Recomendación de edad: 16+ ✅** (cerrado 2026-10-01).

---

## 5. Marcas y nombre

- **Nombre del juego:** «Valcoria — Deuda de Sangre»; logotipo propio.
- **Uso del término «Valcoria»:** reservado al juego.
- **Sin marcas de terceros** en el producto ni en su ficha.

---

## 6. Cómo se prueba el cumplimiento

- `tools/validate_data.js` falla si un asset referenciado **no tiene ficha** o **no existe**.
- `npm run docs` comprueba que los enlaces a las fichas (`art/AUTORES.md`, `THIRD_PARTY.md`) no
  están rotos.

---

## 7. Cifras que fija este documento

| Cifra | Valor |
|---|---|
| Licencia del proyecto | **Todos los derechos reservados** |
| Terceros de código | Three.js + loaders (**MIT**) |
| Terceros de arte | 10 `.glb` (**CC0** · **CC0+CC-BY** Fox) |
| Créditos obligatorios | el **zorro** (CC-BY) |
| Ficha antes de commit | **sí** |
| Red en ejecución | **0** |

---

## 8. Qué entra en la demo (Fase 1) — y sigue

> **Hasta aquí la demo.** Los modelos actuales con sus fichas, los créditos con el zorro y la
> comprobación de assets.

> **Y sigue el juego completo.** Cada asset de las Fases 2-5 sigue **la misma regla**: ficha antes
> de commit, licencia abierta, crédito cuando toca.

---

## 9. Fuera de este documento

- Fichas y licencias → `../../art/AUTORES.md`, `../../THIRD_PARTY.md`
- Privacidad → `09_PRIVACIDAD_Y_DATOS.md`
- Plataformas → `08_PLATAFORMAS_Y_MINIMOS.md`
- Estilo y contenido → `../arte/00_ESTILO.md`, `../arte/04_EFECTOS_Y_PARTICULAS.md`
