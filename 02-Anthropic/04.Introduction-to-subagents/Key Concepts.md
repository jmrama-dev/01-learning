# Introducción a los subagentes · Conceptos fundamentales

## 1. Qué es un subagente

Un subagente es un **asistente especializado** al que Claude Code delega una tarea concreta en una **ventana de contexto separada**.

Hace su trabajo de forma aislada y devuelve solo un resumen al hilo principal.

La gran ventaja es:

> mantener limpio el contexto principal.

El subagente puede leer muchos archivos, buscar, ejecutar herramientas y explorar sin llenar tu conversación principal con todo ese ruido.

---

## 2. La pregunta clave para decidir si usar uno

> ¿Me importa el trabajo intermedio o solo el resultado final?

* Si solo importa el resultado → **subagente**.
* Si necesitas ver y reaccionar al proceso → **hilo principal**.

---

## 3. Cuándo usarlos

Especialmente para:

* investigación y exploración;
* revisión de código con una perspectiva independiente;
* tareas que necesitan un prompt de sistema muy específico;
* trabajo aislado que generaría mucho ruido de contexto.

---

## 4. Cuándo NO usarlos

Evita usarlos para:

* crear "expertos" genéricos tipo "experto en Python";
* procesos secuenciales donde cada paso depende mucho del anterior;
* ejecutar tests cuando necesitas ver toda la salida para depurar.

---

## 5. Cómo crear uno

Normalmente con:

```text
/agents
```

Puede ser:

* **personal** → disponible en todos tus proyectos;
* **de proyecto** → guardado en `.claude/agents/`.

Su archivo suele tener:

```yaml
---
name:
description:
tools:
model:
color:
---
```

Y debajo va el system prompt que define cómo debe trabajar.

---

## 6. Las 4 claves para diseñarlo bien

### Descripción específica

Controla cuándo Claude lo usa y también cómo formula la tarea que le delega.

### Formato de salida claro

Muy importante. Le dice qué debe devolver y cuándo ha terminado.

### Informar obstáculos

Si descubre problemas, workarounds, flags especiales o peculiaridades del entorno, debe devolverlos al hilo principal.

### Mínimos permisos necesarios

Un revisor no necesita editar. Un investigador normalmente solo necesita leer.

---

## 7. Ejemplo mental

Sin subagente:

```text
Pregunta
→ Claude lee 15 archivos
→ búsquedas
→ llamadas a herramientas
→ todo queda en tu contexto
→ respuesta
```

Con subagente:

```text
Pregunta
→ subagente explora 15 archivos en su contexto
→ devuelve resumen
→ hilo principal conserva solo lo útil
```

---

## 8. Skill frente a subagente

Esta distinción sí quiero tenerla grabada:

* **Skill** = añade conocimiento a la conversación actual.
* **Subagente** = delega trabajo a una conversación separada.

---

# Frase para recordar

> **Usa subagentes cuando quieras delegar trabajo cuyo proceso no necesitas conservar, pero cuyo resultado sí necesitas.**
