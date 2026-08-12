# 2026-08-12 — Certificación: Introducción a los subagentes

## Qué hice hoy

- Completé el curso [Introduction to Subagents](https://anthropic.skilljar.com/introduction-to-subagents) de Anthropic y obtuve la certificación.
- Guardé el resumen detallado en `02-Anthropic/04.Introduction-to-subagents/Key Concepts.md`, siguiendo el mismo formato que los cursos anteriores.

## Ideas clave de hoy

Un subagente es un asistente especializado al que Claude delega una tarea en un contexto independiente, devolviendo solo un resumen al hilo principal. Su principal ventaja es conservar limpia la ventana de contexto, evitando que búsquedas, lecturas de archivos o llamadas a herramientas saturen la conversación principal.

Úsalos cuando solo importe el resultado, no el proceso intermedio (investigación, exploración, revisiones de código, análisis especializados). No los uses para tareas donde necesites seguir todo el proceso (debugging complejo, pipelines secuenciales o ejecución de tests con salida detallada).

Un buen subagente se diseña con cuatro principios:

- **Descripción específica**, que determine cuándo Claude debe utilizarlo.
- **Formato de salida estructurado**, para que sepa cuándo ha terminado y entregue resultados consistentes.
- **Informe de obstáculos**, incluyendo problemas, workarounds o peculiaridades encontradas.
- **Permisos mínimos necesarios**, limitando las herramientas según su función.

Los subagentes pueden ser personales o de proyecto, y se configuran mediante archivos Markdown en `.claude/agents`.

Diferencia fundamental: una Skill aporta conocimiento reutilizable al contexto actual; un subagente delega trabajo a un contexto aislado para mantener la conversación principal limpia y enfocada.

## Próximos pasos

- Rellenar `Reflections.md` del módulo de subagentes cuando haya podido aplicarlo en algún caso real.
- Seguir con el siguiente curso de la ruta de Anthropic.
