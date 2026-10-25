# 02 · Tropas y héroe — crecimiento, habilidades y aliento

> Contrato de construcción de las tropas y del héroe. Esqueleto heredado de BoC
> (árbol de mejora, stats con crecimiento, habilidades en escuelas) con las
> decisiones de Valcoria ya fijadas: aliento en vez de mana, fórmulas publicadas.

## 1. Contrato de datos

```jsonc
// datos/unidades.json — schema_version: 1
{
  "schema_version": 1,
  "unidades": [
    {
      "id": "milicia", "nombre": { "es": "Miliciano", "en": "Militia" },
      "linea": "milicia", "mejora_de": null,        // árbol por referencia
      "nivel_recluta": 0, "nivel_max": 10, "nivel_requerido": 0,
      "coste_recluta": 10, "coste_mejora": 1,
      "intervalo_ataque_s": 2.8, "rango": 0,        // 0 = cuerpo a cuerpo
      "stats_base":    { "vida": 260, "ataque": 40, "defensa": 4, "critico": 30, "velocidad": 50 },
      "crecimiento":   { "vida": 400, "ataque": 100, "defensa": 40, "critico": 100, "velocidad": 50 },
      "botin": [...], "experiencia_otorgada": 60
    }
  ]
}
```

Líneas de tropa (paridad con BoC, nombres Valcoria): milicia → espada/pica → élite;
arqueros (con `rango`, `dispersion`, `velocidad_proyectil`); caballería ligera y de
lanza (desde espada/pica); fe (monjes → cruzados, apoyo).

**Fórmula por nivel (publicada):** `stat(nv) = base + crecimiento × nv` — idéntica en
espíritu a BoC pero escrita en `docs/batalla/01_CIFRAS.md` y visible en la ficha de tropa
con gráfico de progresión.

## 2. Héroe: atributos, skills y talentos

- **Atributos** FILO/AGI/MENTE (paridad STR/AGI/INT) con crecimiento decimal por nivel.
- **4 escuelas de habilidades** (Filo, Aza, Lumbre, Cura) × 8 habilidades, ramas 5+5+3
  con prerrequisitos (admite OR), valores por nivel `val1..5[5]` — misma métrica de
  árbol que BoC para conservar el ritmo de progresión.
- **Recurso de combate = aliento** (canon: 100; regenera 4/s en combate · 5/s fuera,
  +AGI): cada activa cuesta aliento; la recarga propia (`cd`) y global (3 s) se mantienen.
- **Talentos** (17): pasivas de campaña ligadas a atributos, con ecos en la Crónica
  (saqueo, captura, elocuencia, ingeniería…).

## 3. Ficha de tropa y de héroe (lo bonito)

- Ficha con retrato grande, barras de progresión por stat, árbol dibujado (no lista),
  y **los números en texto natural**: "A nivel 5 pega como 3 milicianos y aguanta 2".
- Animaciones esqueletales (KayKit/Quaternius CC0) con equipo visible; heridas y
  cicatrices persistentes en el héroe (memoria visual de la Deuda).
- El anillo de acción en batalla muestra aliento, recargas y órdenes — sin menús enterrados.

## 4. Pruebas de aceptación

1. Validador pasa con las 23 unidades equivalentes y sus árboles completos.
2. Una tropa de nivel N tiene exactamente `base + crecimiento×N` en todos los stats.
3. Las 32 habilidades cargan con prerrequisitos válidos (incluye OR).
4. Gastar aliento por debajo de 0 es imposible; regeneración respeta 4/5 por segundo.
