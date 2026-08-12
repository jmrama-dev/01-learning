---
name: nota-diaria
description: Convierte un resumen libre del día (pegado por el usuario, en español) en una
  entrada fechada de 01-Notes/, siguiendo la plantilla y el tono del learning log. Actívala
  cuando el usuario pegue un resumen de lo que hizo hoy, pida crear o actualizar la nota del
  día, o mencione "nota diaria".
allowed-tools: Read, Write, Edit, Glob
---

Cuando el usuario pega un resumen libre (en español) de lo que hizo hoy, conviértelo en una
entrada fechada en `01-Notes/YYYY-MM-DD-slug-descriptivo.md` (fecha = hoy, slug = tema corto en
kebab-case). No preguntes formato/carpeta cada vez — créala y muestra el resultado directamente.
Solo pausa para preguntar sobre archivos opcionales al margen de la nota (p. ej. un
`reflections.md` vacío para un curso nuevo).

## Plantilla

No es obligatoria — omite cualquier sección sin contenido real, nunca la rellenes solo por
mantener la forma. No toda entrada es un resumen diario: explicaciones conceptuales, reflexiones
o análisis de problemas pueden usar la estructura que mejor encaje con el contenido en vez de
esta plantilla.

```
# YYYY-MM-DD — Título

## Qué hice hoy
- lista de bullets, reordenando/limpiando el resumen bruto del usuario en bullets concretos

## Qué aprendí / Ideas clave
- ver la regla de tono más abajo

## Qué me costó entender
(solo si hay evidencia real de una dificultad en el resumen del usuario)

## Próximos pasos
(solo si es razonablemente inferible del resumen)
```

## Tono para "Ideas clave"

- Si redactas tú esta sección (el usuario no te ha dado el contenido exacto): por defecto, un
  párrafo reflexivo corto — elige 1-3 cosas que destacaron, en la voz del usuario. Nunca una lista
  que repita casi literalmente un archivo fuente (p. ej. el `key-concepts.md` de un curso).
- Si el usuario pega su propio texto y pide ponerlo en esta sección: úsalo casi verbatim (solo
  formato ligero), sin condensarlo. Es su decisión, no una violación de la regla anterior.

## Preservar la voz del usuario

Nunca inventes reflexiones, dificultades o aprendizajes que no estén respaldados por contenido
real. Cuando el resumen ya trae palabras propias del usuario (de un `reflections.md`, un
`resumen.md`, o el propio texto pegado), consérvalas — solo corrige claridad/gramática si te lo
piden.

## Actualizar los índices

Toda nota nueva requiere actualizar a mano estos dos sitios (sin scripts/automatización):

1. `01-Notes/README.md` — índice cronológico completo. Añade fecha, título y enlace en orden
   inverso-cronológico (la más reciente primero).
2. La sección "Últimas notas" del `README.md` raíz — recórtala a las 3-5 entradas más recientes
   (añade la nueva arriba y elimina la más antigua si hace falta para mantener ese límite).
