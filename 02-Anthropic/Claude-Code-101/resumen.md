# Resumen — Claude Code 101

Referencia rápida de los conceptos clave del curso, para consultar sin tener que repasar todos los apuntes.

## 1. Flujo de trabajo: Explora → Planifica → Codifica → Revisa → Commit

El ciclo de trabajo recomendado con Claude Code:

1. **Explora** — entender el código/contexto antes de tocar nada (leer archivos, buscar patrones existentes).
2. **Planifica** — definir los pasos a seguir antes de escribir código (modo plan, para tareas no triviales).
3. **Codifica** — implementar los cambios siguiendo el plan.
4. **Revisa** — comprobar el resultado (diff, tests, ejecución real) antes de dar la tarea por terminada.
5. **Commit** — guardar el trabajo con un mensaje claro, solo cuando el usuario lo pide.

> Saltarse "Explora" o "Revisa" es la causa más común de cambios mal dirigidos o incompletos.

## 2. CLAUDE.md

Archivo de contexto que Claude Code lee automáticamente al empezar a trabajar en un repositorio.

**Para qué sirve:**
- Evita repetir las mismas instrucciones en cada conversación.
- Documenta comandos habituales (build, lint, test) y la arquitectura del proyecto.
- Alinea a todo el equipo (humano + IA) sobre las convenciones a seguir.

**Qué NO debe llevar:**
- Cosas obvias o derivables leyendo el código.
- Buenas prácticas genéricas ("escribe tests", "no expongas secretos").
- Listados exhaustivos de archivos/carpetas fáciles de descubrir con `ls`.

**Ejemplo mínimo de estructura:**

```markdown
# CLAUDE.md

## Comandos
- Test: npm test
- Lint: npm run lint

## Arquitectura
Breve descripción de las piezas grandes del sistema, no de cada archivo.
```

## 3. El contexto es un recurso limitado

Claude Code trabaja con una ventana de contexto finita; gestionarla bien evita respuestas peores o pérdida de información relevante.

| Comando | Qué hace | Cuándo usarlo |
|---|---|---|
| `/context` | Muestra cuánto contexto se está usando y en qué (sistema, herramientas, mensajes). | Para diagnosticar si la conversación se está quedando sin espacio. |
| `/compact` | Resume la conversación para liberar espacio sin perder el hilo de la tarea. | Cuando `/context` muestra poco espacio libre pero la tarea sigue en curso. |
| `/clear` | Empieza una conversación nueva desde cero. | Al terminar una tarea y pasar a algo no relacionado. |

## 4. Los subagentes son especialistas

En vez de pedirle a un único agente que haga todo, se puede dividir el trabajo en subagentes con un propósito concreto (ej. explorar código, revisar seguridad, planificar).

**Por qué:**
- Cada subagente arranca con un contexto limpio, enfocado solo en su tarea.
- Permite paralelizar trabajo independiente (varios subagentes a la vez).
- Protege el contexto de la conversación principal de resultados intermedios voluminosos.

**Ejemplo de cuándo delegar:**
- "Busca en todo el repo dónde se usa esta función" → un subagente de exploración.
- "Revisa este PR buscando bugs de seguridad" → un subagente especializado en revisión.

## 5. MCP y Hooks: de modelo a agente

- **MCP (Model Context Protocol)** — conecta Claude Code con herramientas y datos externos (APIs, bases de datos, servicios) de forma estandarizada, para que pueda actuar sobre sistemas reales, no solo generar texto.
- **Hooks** — comandos que se ejecutan automáticamente en respuesta a eventos (antes/después de una herramienta, al terminar una tarea), útiles para automatizar validaciones o acciones repetitivas sin depender de que el modelo se acuerde de hacerlas.

Juntos convierten a Claude Code en algo que **actúa** sobre el entorno real, en lugar de limitarse a responder texto.
