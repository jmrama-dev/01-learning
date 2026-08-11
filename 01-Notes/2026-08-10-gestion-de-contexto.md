# 2026-08-10 — Gestión del contexto en Claude Code

## Qué hice hoy

- Dediqué el día a profundizar en cómo se gestiona el contexto en Claude Code: vi vídeos sobre el tema e hice algunas prácticas para entenderlo mejor en la práctica, no solo en teoría.
- Repasé la documentación oficial de Claude Code, tanto la [visión general (overview)](https://code.claude.com/docs/en/overview) como otras secciones enlazadas desde ahí, para tener una visión más completa de las herramientas disponibles más allá de lo visto en los cursos.
- Configuré mi **status line** en Claude Code.

## Ideas clave sobre gestión de contexto

- El contexto es un recurso finito y hay que tratarlo como tal: no se trata de "hablar más" con Claude, sino de mantener en la conversación únicamente lo que aporta valor a la tarea actual.
- Herramientas como `/compact`, `/clear` y el resumen automático del historial existen precisamente para esto: liberar espacio sin perder el hilo de lo importante.
- Un CLAUDE.md bien pensado (pequeño, claro, específico) también es una forma de gestión de contexto: evita que el modelo tenga que "redescubrir" las mismas reglas o convenciones en cada sesión.

## Lo que descubrí en el overview de la documentación

Claude Code no es solo la CLI del terminal: es un mismo "motor" accesible desde varias superficies (terminal, extensión de VS Code, extensión de JetBrains, app de escritorio y navegador), y todas comparten los mismos CLAUDE.md, settings y servidores MCP. Algunas cosas que no tenía tan claras antes de leer esto:

- **Auto memory**: además del CLAUDE.md que yo escribo, Claude Code puede ir guardando por su cuenta aprendizajes (comandos de build, notas de debugging) entre sesiones, sin que yo tenga que documentarlo todo a mano.
- **Skills**: se pueden empaquetar flujos de trabajo repetibles como comandos propios (p. ej. `/review-pr`, `/deploy-staging`) para compartirlos con un equipo.
- **Agentes en paralelo**: es posible lanzar varios agentes de Claude Code trabajando a la vez en distintas partes de una tarea, coordinados por un agente principal ("lead") que reparte el trabajo y junta los resultados.
- **Automatización y CLI "a la Unix"**: se puede usar `claude -p` en scripts o pipes (por ejemplo, analizar logs o revisar archivos modificados en un `git diff`), lo que encaja con la idea de tratar a Claude como una pieza más de un flujo automatizado, no solo como un chat interactivo.
- **Tareas programadas**: existen varias formas de ejecutar Claude de forma recurrente — *Routines* (en la nube, siguen corriendo aunque el ordenador esté apagado), tareas programadas del escritorio (con acceso directo a archivos locales) y `/loop` (para repetir un prompt dentro de una misma sesión de CLI).
- **Trabajar desde cualquier sitio**: se puede empezar una tarea en el navegador o el móvil y continuarla en el terminal con `claude --teleport`, o al revés, pasar una sesión de terminal a la app de escritorio con `/desktop`.

## Status line

Configuré la status line de Claude Code para tener información visible de forma constante durante las sesiones (en vez de tener que consultarla con comandos como `/context`). Es un pequeño ajuste, pero va en la línea de las ideas de hoy: reducir la fricción de gestionar el contexto y el estado de la sesión.

## Próximos pasos

- Seguir con la documentación oficial de Claude Code para cubrir las partes que aún no he explorado en profundidad (subagentes, hooks, MCP, Agent SDK).
- Aplicar lo aprendido sobre gestión de contexto en las próximas sesiones de trabajo con Claude Code en este mismo repositorio.
- Revisar más a fondo las opciones de personalización de la status line, más allá de la configuración inicial de hoy.
