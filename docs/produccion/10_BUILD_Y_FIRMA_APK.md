# 10 · Build y firma de la APK — cómo se empaqueta para Android

**Estado:** ✅ **aprobado por el dueño (2026-10-01, ronda 4-A). Documento final.**

> El juego es **web estática** (`08_PLATAFORMAS_Y_MINIMOS.md`); la **APK es un empaquete local**
> con Capacitor. Aquí está el proceso completo de **build, firma y entrega**: keystore, secretos,
> ofuscación, tamaño y verificación. **Cifras y nombres de paso de este documento son propuesta de
> diseño** (cambiables → `../DECISIONES.md`).

---

## 1. El principio

- **Un solo build para todo**: el mismo `www/` alimenta la web y la APK (rutas relativas, regla 3
  de `../../AGENTS.md`).
- **Todo local:** sin CI en la nube, sin tienda; el proceso cabe en una máquina (proyecto de una
  sola persona). Si algún día hay CI, **los pasos no cambian**: solo se automatizan.
- **Nada se empaqueta sin `npm run qa` verde** (`04_QA.md`).

---

## 2. Las etapas (6)

| # | Etapa | Comando / paso | Qué sale |
|---|---|---|---|
| 1 | QA completo | `npm run qa` | verde o no se sigue |
| 2 | Build web | `npm run build` (propuesta: `tools/build_web.mjs`) | `dist/` con `index.html`, `js/`, `css/`, `data/`, `art/`, `vendor/` |
| 3 | Copia a la app | `npx cap sync` | assets públicos dentro del proyecto Android |
| 4 | Compilar | `./gradlew assembleRelease` | APK sin firmar |
| 5 | Firmar | `apksigner sign --ks valcoria.keystore …` | APK final |
| 6 | Verificar | `apksigner verify --print-certs` + instalación real | entregable |

- **`versionName`** = el semver de `package.json` (`07_RELEASES_Y_VERSIONES.md`); **`versionCode`**
  = entero que sube **+1** en cada entrega (Android lo exige para poder actualizar).
- **Sin bundler obligatorio:** los módulos ES ya son estáticos; si se minifica, se hace aquí y el
  código fuente no cambia.

---

## 3. El keystore (la llave de la APK)

- **Una sola llave para toda la vida del juego:** si se pierde, **no se pueden enviar
  actualizaciones** a quienes ya instalaron (Android exige la misma firma).
- **Generación única** (una sola vez):

  ```bash
  keytool -genkeypair -v -keystore valcoria.keystore -alias valcoria \
    -keyalg RSA -keysize 2048 -validity 10000
  ```

- **Firma con esquema v2+** (`apksigner`), nunca solo v1.
- **Dos copias de seguridad del keystore** en soportes distintos (disco + otro), con la contraseña
  en un gestor **fuera** del repositorio.

---

## 4. Secretos (qué nunca se commitea)

| Secreto | Dónde vive | Si se cuela en el repo |
|---|---|---|
| `valcoria.keystore` | fuera del repo (`.gitignore`) | se rota **antes** de publicar |
| Contraseña del keystore | gestor de contraseñas | se rota |
| Cualquier token o firma futura | variables de entorno locales | se rota |

- **Regla:** el repositorio **no lleva binarios firmados**; solo el proceso para crearlos.
- **Hoy no hay CI**: el proceso es manual y reproducible — esta tabla es el guion. Si se añade CI,
  los secretos van al cofre de la CI, **nunca** a los ficheros.

---

## 5. Ofuscación y tamaño

- **Android:** `minifyEnabled true` + `shrinkResources` (R8) en la variante `release`.
- **Tamaño objetivo: APK ≈ 100 MB** (decisión del dueño 2026-10-02: la **demo debe pesar unos
  100 MB**). Los assets de la demo pueden llegar a **~90 MB** — modelos y **audio hablado
  (≤ 20 MB)** —; el presupuesto por personaje sube de 1 MB a **≤ 6 MB** recortado
  (`../arte/01_ASSETS.md` §3).
- **Por qué sube:** las **4 armas nuevas × 3 apariencias** (`../sistemas/15_FABRICACION_Y_RECETAS.md`
  §7), los nuevos modelos de oficios y el **audio del elenco relevante** (Kokoro pre-generado,
  ES + EN, `../arte/02_AUDIO.md` §1) entran **dentro de la demo**.
  Si crece, se recorta contenido (`../arte/01_ASSETS.md`), no se sube el listón del dispositivo.
- **Cero dependencias externas:** sin CDNs; fuentes, audio y modelos incluidos (regla 8 de
  `../../AGENTS.md`).
- 🟡 **2026-10-02:** estos topes (APK ~100 MB, assets ~90 MB) los **revisa el dueño al ver la
  primera escena de paisaje**; la dirección de estilo (película medieval, `../arte/00_ESTILO.md`)
  **no sube** el presupuesto de render: 60 fps, LOD y niebla a 60 m siguen intactos.

---

## 6. Verificación antes de entregar

1. **Instalación en un dispositivo real** (no solo emulador).
2. **Modo avión encendido:** el juego arranca y se juega entero (**offline**, regla 8).
3. **Guardar/cargar en el móvil**: 3 slots + respaldo de corrupto (`02_GUARDADO_Y_DATOS.md`).
4. **Rutas relativas**: nada de `/data/...` (regla 3) — ya cubierta por validador y humo.
5. **0 errores de consola** en 10 minutos (`04_QA.md`).
6. **`npm run qa` verde** justo antes de firmar (si algo se rompió al empaquetar, no se entrega).

---

## 7. Datos, tipos y validación

- **Sin JSON nuevo:** este documento no añade filas de datos; usa los mismos umbrales que
  `04_QA.md` y los mismos guardados que `02_GUARDADO_Y_DATOS.md`.
- **Tooling:** `tools/build_web.mjs` y `tools/apk.mjs` (propuesta) encapsulan las etapas 2-6 para
  que el proceso sea de un comando y no de memoria.
- **Tests (por escribir):** `tests/apk.test.js` (normal, borde, error) al implementar: el build se niega si
  `npm run qa` está rojo; el `versionCode` sube siempre; un keystore ausente avisa y no compila
  `release`.

---

## 8. Cifras que fija este documento

| Cifra | Valor |
|---|---|
| Etapas de build | **6** |
| Keystore | RSA **2048** · validez 10 000 días · **1** llave para siempre |
| Esquema de firma | **v2+** |
| APK objetivo | **~100 MB** ✅ (2026-10-02) |
| `versionCode` | entero, **+1** por entrega |
| CI | **ninguna** (todo local) |
| Verificación | dispositivo real + modo avión + qa verde |

---

## 9. Qué entra en la demo (Fase 1) — y qué sigue

> **Hasta aquí la demo.** El proceso completo de las 6 etapas con su keystore real, la APK de
> prueba instalada en el móvil del desarrollador y la web publicada
> (`05_MERCADO_Y_LANZAMIENTO.md`).

> **Y sigue el juego completo.** Las entregas de las Fases 2-5 usan **las mismas etapas y la misma
> llave**: solo suben `versionCode` y semver (`07_RELEASES_Y_VERSIONES.md`) y repiten el proceso;
> nada cambia salvo el tamaño del contenido.

---

## 10. Fuera de este documento

- Qué se publica y a qué precio → `05_MERCADO_Y_LANZAMIENTO.md`
- Numeración de entregas → `07_RELEASES_Y_VERSIONES.md`
- Dispositivos y mínimos → `08_PLATAFORMAS_Y_MINIMOS.md`
- Qué significa «terminado» → `04_QA.md`
- Privacidad (0 datos, 0 rastreadores) → `09_PRIVACIDAD_Y_DATOS.md`
- Licencias y autoría → `06_LEGAL_Y_AUTORIA.md`
