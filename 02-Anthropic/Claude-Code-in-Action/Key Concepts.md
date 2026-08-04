# Claude Code in Action · Conceptos Clave

# Filosofía del curso

Claude Code no pretende sustituir al desarrollador.

Su objetivo es convertirse en un asistente de ingeniería capaz de trabajar durante largas sesiones con la mínima supervisión posible.

La clave no es escribir mejores prompts, sino diseñar flujos de trabajo fiables.

---

# 1. Planificar antes de ejecutar

Las tareas grandes deben comenzar en Modo Plan.

Revisar y mejorar un plan siempre será más rápido que corregir una mala implementación.

**Idea principal:**

> Planificar primero. Ejecutar después.

---

# 2. Gestionar el contexto

El contexto es un recurso limitado.

Claude ofrece diferentes herramientas para conservar la información importante sin saturar la ventana de contexto:

- Compact
- Rewind
- Goal
- Loop

Gestionar correctamente el contexto es fundamental en sesiones largas.

---

# 3. CLAUDE.md

CLAUDE.md es una guía.

No es un mecanismo que garantice el cumplimiento de reglas.

Principios fundamentales:

- Mantenerlo corto.
- Cada regla compite por la atención del modelo.
- Las reglas deben ser específicas.
- Las reglas deben ser verificables.
- Debe revisarse continuamente.

Cuanto más grande sea el archivo, menos fiable será.

---

# 4. Tres niveles de instrucciones

## CLAUDE.md

Define las convenciones del proyecto.

Ejemplos:

- Nombres de archivos.
- Organización de carpetas.
- Estilo de código.

---

## Skills

Automatizan procedimientos repetitivos.

Ejemplos:

- Verificación del código.
- Generación de documentación.
- Checklist de despliegue.

---

## Hooks

Garantizan comportamientos obligatorios.

Ejemplos:

- Nunca hacer push a main.
- Ejecutar siempre los tests.
- Bloquear comandos peligrosos.

Los Hooks ejecutan código.

No dependen de que Claude recuerde las instrucciones.

---

# 5. Modos de permisos

Cada tarea requiere un nivel diferente de confianza.

Modos disponibles:

- Manual
- Accept Edits
- Plan
- Auto
- Don't Ask
- Bypass Permissions

El modo Auto protege la intención.

La verificación protege la calidad del resultado.

---

# 6. Verificación

Cuanto más autónoma sea una ejecución, mayor debe ser la verificación.

Proceso recomendado:

1. Revisar el diff.
2. Ejecutar los tests.
3. Ejecutar análisis estáticos.
4. Obtener una segunda revisión independiente.

La confianza no proviene de creer en Claude.

Proviene de verificar el resultado.

---

# 7. Automatización del trabajo repetitivo

Siempre comenzar por la solución más sencilla.

Solo aumentar el nivel de control cuando sea necesario.

Niveles de automatización:

1. Rutinas
2. Modo Headless (-p)
3. Modo Bare
4. Agent SDK

---

## Rutinas

Automatización gestionada por Anthropic.

Ideales para:

- Trabajos programados.
- Informes diarios.
- Auditorías periódicas.
- Automatizaciones sencillas.

---

## Modo Headless

Permite ejecutar Claude Code desde scripts.

Ideal para:

- Bash
- PowerShell
- Python
- Automatizaciones locales
- Pipelines

---

## Modo Bare

Pensado para obtener ejecuciones deterministas.

Especialmente útil en Integración Continua (CI).

---

## Agent SDK

Permite integrar Claude Code directamente dentro de una aplicación.

Es el mayor nivel de personalización.

---

# 8. Integración con GitHub

Existen dos formas principales.

## Code Review

Claude revisa una Pull Request.

Publica comentarios.

No modifica el código.

---

## GitHub Actions

Claude pasa a formar parte del flujo de trabajo del repositorio.

Ejemplos:

- Responder a @claude.
- Automatizar tareas.
- Ejecutar revisiones.
- Implementar cambios.

---

# 9. Verificación de ejecuciones

Cuanta menos supervisión haya tenido una ejecución, mayor debe ser su verificación.

Orden recomendado:

- Revisar el diff.
- Ejecutar pruebas.
- Análisis estático.
- Segunda revisión independiente.

Nunca confiar únicamente en el resumen generado por Claude.

---

# 10. Plugins

Un Plugin empaqueta configuraciones reutilizables de Claude Code.

Puede incluir:

- Skills
- Hooks
- Subagentes
- Servidores MCP
- Configuración

Antes de instalar un Plugin siempre debe revisarse su contenido.

Un Plugin ejecuta código con tus permisos.

---

# Modelo mental del curso

Planificar

↓

Guiar

↓

Automatizar

↓

Verificar

↓

Compartir

---

# Reglas de oro

- Planificar antes de programar.
- Mantener CLAUDE.md pequeño.
- CLAUDE.md guía.
- Las Skills automatizan.
- Los Hooks garantizan.
- Verificar siempre el trabajo autónomo.
- Automatizar de forma progresiva.
- Confiar en sistemas, no en suposiciones.
