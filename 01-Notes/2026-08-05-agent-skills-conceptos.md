# Introducción a las Agent Skills

## Qué hice

- Renombré/renumeré las carpetas de cursos de Anthropic (`01.Claude-Code-101`,
  `02.Claude-Code-in-Action`) y añadí el scaffold del curso `03.Introduction-to-agent-skills`.
- Completé `Key Concepts.md` de este curso.

*(El `Reflections.md` de este curso quedó sin rellenar ese día, así que esta entrada se centra en los
conceptos trabajados, no en una reflexión personal.)*

## Qué aprendí

- Una **Skill** es una carpeta de instrucciones y recursos reutilizables (`SKILL.md`) que enseña a Claude
  Code a realizar una tarea concreta de una forma determinada. No es un prompt guardado: codifica un
  procedimiento o conocimiento especializado.
- Cómo se activa: al iniciar sesión Claude Code solo carga el nombre y la descripción de cada Skill; al
  recibir una solicitud, compara su significado con las descripciones mediante coincidencia semántica.
  Por eso la descripción es la parte más importante de una Skill.
- Estructura básica: carpeta propia, `name` y `description` obligatorios en el YAML de cabecera, y el
  cuerpo con las instrucciones.
- **Skills personales** (`~/.claude/skills/`) acompañan al usuario en todos sus proyectos; **Skills de
  proyecto** (`.claude/skills/`) se versionan con el repositorio y las recibe cualquiera que lo clone.
- Jerarquía de prioridad cuando coinciden nombres: Empresa → Personal → Proyecto → Plugins.
- Diferencia entre CLAUDE.md (siempre activo), Skills (activación bajo demanda según intención) y
  comandos de barra (activación manual explícita).
- Metadatos avanzados: `allowed-tools` (restringe herramientas disponibles) y `model` (elige qué
  modelo ejecuta la Skill).
- **Divulgación progresiva**: mantener `SKILL.md` con solo lo esencial y cargar contenido adicional
  (`references/`, `scripts/`, `assets/`) únicamente cuando sea necesario.
- Diferencias con otras piezas: una Skill aporta conocimiento a la conversación actual; un subagente
  aísla trabajo en un contexto separado; un Hook garantiza una acción ante un evento; MCP conecta con
  herramientas o sistemas externos.
- Troubleshooting: causas típicas de que una Skill no aparezca, no se active, se active la equivocada, o
  quede anulada por otra de mayor prioridad — casi siempre relacionadas con el archivo, la ruta o la
  descripción.

## Ideas clave

- Una Skill captura una forma repetible de trabajar; no se crea porque la función existe, sino porque
  se ha detectado un procedimiento recurrente.
- La descripción decide si Claude encuentra la Skill — las mejores instrucciones no sirven si la
  descripción no la activa.
- Las mejores Skills nacen de problemas reales, no de una biblioteca hipotética de Skills.

---

*Entrada reconstruida posteriormente a partir del historial Git y del contenido ya escrito ese día en
`Key Concepts.md`. No incluye reflexión personal porque `Reflections.md` de este curso se dejó vacío.*
