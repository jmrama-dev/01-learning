# 2026-08-13 — Aprender a mejorar un sistema mediante experimentos controlados

## Qué hice hoy

Hoy avancé en `synthesis-rlab`, pasando de investigar qué caracteriza a un buen resumen a diseñar y replicar experimentos para comprobar una mejora concreta. Comparé un resumen directo con otro en el que el modelo analiza antes la estructura argumental y los matices de la fuente. También ordené el proyecto por fases y dejé separada para más adelante la comparación entre modelos y niveles de razonamiento.

## Ideas clave de hoy

* Construir un buen sistema de resúmenes exige separar las intuiciones de la evidencia. Experimentar bien no es probar muchos prompts, sino formular una pregunta concreta, mantener controladas las variables y diseñar cada prueba a partir de lo aprendido en la anterior.

* La conclusión más sólida de esta fase: pedir al modelo que identifique primero la estructura argumental y los matices epistémicos mejora la jerarquización y evita convertir hipótesis en afirmaciones firmes. La mejora apareció en fuentes de dominios distintos, con un pequeño coste en concisión.

* Una mejora general no elimina los errores puntuales de fidelidad. Ante un fallo aislado, mejor repetir la misma condición que cambiar de método o fuente, para comprobar si el problema es estable o solo ruido de una ejecución.

* Cerrar una fase no significa haber resuelto el problema completo. Los experimentos aportan evidencia interna útil, pero aún queda distinguir qué depende del modelo o del dominio, qué ya está establecido en la literatura y dónde hay realmente un espacio propio de investigación.

* Desarrollar con IA no consiste solo en escribir código o construir agentes: también implica diseñar procesos, evaluar resultados y documentar qué sabemos antes de añadir complejidad. Trabajar por fases mantiene el proyecto enfocado.

* No conviene saltar directamente a construir `knowledge-representation-v0` ni seguir acumulando experimentos sin revisar antes el estado del arte, para no investigar desde cero ni confundir una observación local con un descubrimiento general.

## Próximos pasos

* Comenzar la Fase 5 de `synthesis-rlab` siguiendo el roadmap definido para el proyecto.
* Evaluar más adelante si un modelo más potente o un mayor nivel de razonamiento mejora lo suficiente el resumen como para justificar su coste.
