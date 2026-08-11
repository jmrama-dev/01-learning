# Repaso de fundamentos de IA y gestión del contexto

Este día tuvo dos líneas de aprendizaje distintas, que se reflejan en dos recursos añadidos a
`04-Recursos-Creados/`.

## Qué hice

- Añadí el recurso *"Gestión profesional del contexto en ChatGPT para proyectos largos"*, como parte
  de profundizar en cómo gestionar el contexto en ChatGPT y en proyectos largos.
- Añadí el recurso *"De las primeras neuronas artificiales a ChatGPT: evolución de la inteligencia
  artificial moderna"*, como repaso de conceptos que ya había trabajado años atrás en mi TFM
  relacionado con visión artificial (redes neuronales, redes neuronales convolucionales y visión
  artificial), esta vez conectándolos con la evolución posterior de la IA moderna. No era la primera vez
  que trabajaba estos conceptos — fue un repaso y una puesta al día, no un aprendizaje desde cero.

## Gestión del contexto: ideas clave

- El contexto, el historial, la memoria y la documentación no son lo mismo. El modelo mental
  profesional separa cuatro capas: historial almacenado, contexto activo (lo que el modelo realmente
  usa para responder), memoria del producto (personalización, no exhaustiva) y fuente de verdad
  externa (repositorio, documentación — la capa canónica).
- Que un mensaje siga "visible" en un chat no garantiza que el modelo lo esté usando realmente para
  responder: "estar dentro de la ventana" no equivale a "ser recuperado, interpretado y aplicado
  correctamente" (fenómeno *lost in the middle*).
- Existen distintas formas de "olvidar": exclusión, compresión con pérdida, fallo de recuperación, fallo
  de atención, conflicto entre instrucciones, obsolescencia o inferencia errónea — cada una requiere un
  diagnóstico distinto.
- Señales para abrir un chat nuevo: cambia la unidad de trabajo (pasar de requisitos a implementación,
  cambiar de funcionalidad, empezar una investigación con mucho contenido descartable) o ya no se
  puede completar la frase "este chat existe exclusivamente para...".
- Un buen resumen de continuidad no narra la conversación, representa el estado operativo vigente:
  objetivo, decisiones tomadas, alternativas descartadas, restricciones, archivos relevantes, próximo
  paso exacto.
- Comparación con Claude Code: cada sesión de Claude Code empieza con una ventana de contexto
  nueva, y la continuidad se sostiene mediante `CLAUDE.md`, memoria automática, Skills cargadas bajo
  demanda, subagentes con contexto aislado y compactación — un patrón de gestión explícita del
  contexto, no de ventanas cada vez más grandes.

## Evolución de la IA: ideas clave

- Mapa conceptual: inteligencia artificial → machine learning → deep learning → modelos de lenguaje
  → Transformers → GPT → ChatGPT → agentes. Arquitectura, modelo entrenado y producto son cosas
  distintas (por ejemplo, Transformer es una arquitectura; GPT-4 un modelo; ChatGPT un producto).
  Repasar esta cadena me sirvió para recolocar en un mismo mapa cosas que ya conocía por separado
  desde el TFM (redes neuronales, CNNs) y lo que estoy aprendiendo ahora (LLMs, agentes).
- Línea evolutiva que conecta con lo que estudié en su día: neurona de McCulloch-Pitts (1943) →
  perceptrón de Rosenblatt (1958) → redes multicapa y retropropagación (1986) → redes recurrentes
  (1990) → LSTM (1997) → renacimiento del deep learning con más datos y GPU (2006-2012, AlexNet) →
  mecanismos de atención (2014) → Transformer (2017) → GPT-1 a GPT-3 → ChatGPT (2022) → GPT-4 y
  modelos multimodales → modelos de razonamiento y agentes.
- Por qué resultó útil recuperar esta base ahora: entender bien de dónde vienen las redes neuronales y
  las CNNs ayuda a situar mejor por qué los Transformers y los LLMs actuales funcionan de otra manera
  (atención en vez de recurrencia), y a no tratar los agentes de hoy como algo desconectado de lo que
  ya había estudiado en el TFM.

## Próximos pasos

Seguir conectando esta base conceptual con el trabajo práctico en Claude Code y con los cursos de
Anthropic en curso.

---

*Entrada reconstruida posteriormente a partir del historial Git (commit de adición de los dos recursos),
el contenido íntegro de ambos PDFs, y contexto sobre el TFM confirmado directamente por el autor con
posterioridad — este último dato no proviene del repositorio ni de los PDFs.*
