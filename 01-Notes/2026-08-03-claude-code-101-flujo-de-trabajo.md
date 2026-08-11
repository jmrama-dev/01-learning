# Claude Code 101: flujo de trabajo y primer CLAUDE.md

## Qué hice

- Creé el primer `CLAUDE.md` del repositorio, documentando el patrón de estructura (curso único vs.
  proveedor con varios cursos).
- Completé el `reflections.md` de Claude Code 101 con las tres preguntas del curso.
- Añadí un `resumen.md` como referencia rápida de los conceptos clave del curso.
- Aplané `Claude-Code-101/` eliminando el subnivel `Module-01/` (el curso no lo necesitaba) y actualicé
  `CLAUDE.md` en consecuencia.

## Qué aprendí

Aprendí que Claude Code no es simplemente un asistente para escribir código, sino una herramienta
diseñada para acompañar todo el flujo de desarrollo.

La idea más importante del curso fue cambiar mi forma de trabajar: antes de programar, primero
explorar el proyecto, planificar la solución, implementarla y finalmente revisar y hacer commit.

También entendí la importancia de proporcionar contexto mediante CLAUDE.md, gestionar
correctamente la ventana de contexto y utilizar herramientas como subagentes, MCP o Hooks cuando
el proyecto crezca.

Durante el curso pude aplicar estos conceptos creando la estructura para los cursos de Anthropic
dentro de mi repositorio, utilizando el modo Plan, realizando varios commits y entendiendo mejor
cómo trabajar desde la terminal con Claude Code.

## Ideas clave

- Flujo recomendado: Explora → Planifica → Codifica → Revisa → Commit. Saltarse "Explora" o "Revisa"
  es la causa más común de cambios mal dirigidos o incompletos.
- CLAUDE.md evita repetir las mismas instrucciones en cada conversación y documenta comandos y
  arquitectura — pero no debe llevar cosas obvias, buenas prácticas genéricas ni listados exhaustivos.
- El contexto es un recurso limitado (`/context`, `/compact`, `/clear`).
- Los subagentes son especialistas con contexto propio, útiles para paralelizar exploración o revisión
  sin saturar la conversación principal.
- MCP conecta Claude Code con herramientas y datos externos; los Hooks automatizan comportamientos
  ante eventos sin depender de que el modelo se acuerde de aplicarlos.

## Qué me costó entender

Al principio me costó diferenciar qué herramientas merece la pena utilizar desde el principio y cuáles
están pensadas para proyectos más grandes.

Conceptos como MCP, Hooks o los subagentes personalizados me parecían complejos porque todavía no
tengo un proyecto real donde utilizarlos.

También fui entendiendo poco a poco cuándo conviene dejar que Claude actúe automáticamente y
cuándo es mejor darle un objetivo bien definido mediante un prompt más estructurado.

## Próximos pasos

En mis futuros proyectos quiero adoptar este flujo desde el primer día: usar el modo Plan antes de
implementar, mantener un CLAUDE.md actualizado con las convenciones del proyecto, e ir incorporando
subagentes, MCP y Hooks cuando los proyectos lo justifiquen.

---

*Entrada reconstruida posteriormente a partir del historial Git y del contenido ya escrito ese día en
`reflections.md` y `resumen.md`.*
