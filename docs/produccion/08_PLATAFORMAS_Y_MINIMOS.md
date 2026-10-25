# 08 · Plataformas y mínimos — dónde corre

**Estado:** ✅ **aprobado por el dueño (aprobación en bloque, 2026-09-30). Documento final.**

> El juego es **web estático y offline** (`../../AGENTS.md`): corre en navegador y se empaqueta en
> **APK**. **No** exige teclado, mando ni conexión. Aquí están **los mínimos**.

---

## 1. Plataformas

| Plataforma | Cómo corre | Requisito |
|---|---|---|
| **Web** | navegador moderno con **WebGL2** | `index.html` servido (o abierto) |
| **APK** | empaquetado local (Capacitor) | Android compatible |
| **Escritorio** | el mismo build web | navegador con WebGL2 |

- **Móvil primero:** el diseño es **táctil horizontal** (`../interfaz/00_CONTROLES.md`).
- **Sin instalación obligatoria:** la web juega directo; la APK es opcional.

---

## 2. Mínimos técnicos

| Requisito | Mínimo |
|---|---|
| **Render** | WebGL2 |
| **Pantalla** | base **960×540** horizontal; se adapta a más |
| **Almacenamiento** | `localStorage` ~5 MB (el guardado queda muy por debajo, `02_GUARDADO_Y_DATOS.md`) |
| **Entrada** | pantalla táctil **o** ratón; teclado **no** necesario |
| **Red** | **ninguna** (100 % offline) |

- **Verificado** con el humo en **960×683** y **915×555** (`npm run smoke`).

---

## 3. Rendimiento objetivo

- **60 fps** en gama media con **10+10** unidades y props (`../arte/00_ESTILO.md` §6).
- **Android modesto:** si aprieta, se recorta **densidad y partículas**, nunca la información
  (`../interfaz/02_HUD.md`).

---

## 4. Dispositivos sin funciones

- **Sin vibración:** no rompe (`../interfaz/04_ACCESIBILIDAD.md` §3).
- **Sin audio:** arranca igual (`../arte/02_AUDIO.md` §1).
- **Sin WebGL2:** mensaje claro de requisito (el juego **no** finge que corre).

---

## 5. Datos y despliegue

- **Rutas relativas** (`data/…`, `art/…`, `vendor/…`), nunca absolutas (regla 3, APK).
- **Todo vendorizado:** Three.js y assets locales; cero CDNs (regla offline).
- **Sin servidores:** el hosting solo sirve ficheros estáticos.

---

## 6. Cifras que fija este documento

| Cifra | Valor |
|---|---|
| Render mínimo | **WebGL2** |
| Pantalla base | 960×540 horizontal |
| Almacenamiento | `localStorage` ~5 MB |
| Red | **0** |
| Objetivo | 60 fps con 10+10 |
| Humo | 960×683 y 915×555 |
| Teclado/mando | **no** necesarios |

---

## 7. Qué entra en la demo (Fase 1) — y sigue

> **Hasta aquí la demo.** Web estática + APK, con los mínimos de §2 y el rendimiento de los 6
> sitios y 2 campos.

> **Y sigue el juego completo.** Las regiones y unidades de las Fases 2-5 caben en **los mismos
> mínimos**; si no, se optimiza el contenido, no se sube el listón del dispositivo.

---

## 8. Fuera de este documento

- Controles táctiles → `../interfaz/00_CONTROLES.md`
- Guardado → `02_GUARDADO_Y_DATOS.md`
- Estilo y presupuesto → `../arte/00_ESTILO.md`
- Privacidad → `09_PRIVACIDAD_Y_DATOS.md`
