# Introducción a las habilidades de agente · Conceptos fundamentales

## 1. Qué es una Skill

Una Skill es una **carpeta de instrucciones y recursos reutilizables** que enseña a Claude Code a realizar una tarea concreta de una forma determinada.

Su archivo principal es:

```text
SKILL.md
```

La idea central es:

> Si tengo que explicarle a Claude el mismo procedimiento varias veces, probablemente debería convertirlo en una Skill.

Ejemplos:

* preparar mensajes de commit;
* revisar Pull Requests;
* crear documentación;
* seguir una guía de marca;
* ejecutar una lista de verificación;
* analizar un proyecto con un método concreto.

Una Skill no es simplemente un prompt guardado. Es una forma de **codificar un procedimiento o conocimiento especializado** para que Claude lo aplique automáticamente cuando corresponda.

---

# 2. Cómo se activa una Skill

Cuando Claude Code inicia una sesión, no carga todas las instrucciones completas de todas las Skills.

Inicialmente solo carga:

* el nombre;
* la descripción.

Cuando escribes una solicitud, Claude compara su significado con las descripciones disponibles mediante **coincidencia semántica**.

El flujo es:

```text
Solicitud del usuario
        ↓
Claude compara la intención con las descripciones
        ↓
Encuentra una Skill relevante
        ↓
Carga su SKILL.md completo
        ↓
Aplica sus instrucciones
```

Por eso, la descripción es probablemente la parte más importante de una Skill.

Una buena descripción debe responder:

1. **¿Qué hace esta Skill?**
2. **¿Cuándo debe utilizarla Claude?**

Ejemplo:

```yaml
---
name: commit-message
description: Analiza los cambios de Git y propone mensajes de commit. Úsala cuando el usuario solicite preparar, revisar o crear un commit.
---
```

Una descripción vaga como:

```yaml
description: Ayuda con Git.
```

sería mucho menos fiable.

---

# 3. Estructura básica de una Skill

Cada Skill debe estar dentro de su propia carpeta:

```text
commit-message/
└── SKILL.md
```

La carpeta y el campo `name` deben coincidir.

El archivo se divide en dos partes:

```markdown
---
name: nombre-de-la-skill
description: Qué hace y cuándo debe utilizarse.
---

Instrucciones que Claude debe seguir cuando la Skill se active.
```

Los metadatos básicos son:

```yaml
name:
description:
```

Ambos son obligatorios.

Reglas para el nombre:

* usar minúsculas;
* usar números y guiones;
* máximo 64 caracteres;
* evitar nombres demasiado genéricos;
* hacerlo coincidir con la carpeta.

Por ejemplo, es mejor:

```text
frontend-code-review
```

que:

```text
review
```

---

# 4. Skills personales y Skills de proyecto

## Skills personales

Se guardan en:

```text
~/.claude/skills/
```

En Windows:

```text
C:/Users/<usuario>/.claude/skills/
```

Te acompañan en todos tus proyectos.

Son adecuadas para preferencias personales como:

* formato de commits;
* estilo de documentación;
* forma de explicar código;
* procedimientos que utilizas en cualquier repositorio.

---

## Skills de proyecto

Se guardan en:

```text
.claude/skills/
```

dentro del repositorio.

Se versionan con Git y cualquier persona que clone el proyecto las recibe.

Son adecuadas para:

* estándares del equipo;
* arquitectura específica del repositorio;
* flujos de trabajo propios del proyecto;
* normas de diseño o documentación compartidas.

La pregunta para elegir ubicación es:

> ¿Esta forma de trabajar es mía o pertenece al proyecto?

---

# 5. Prioridad cuando existen Skills con el mismo nombre

El curso establece esta jerarquía:

```text
Empresa
   ↓
Personal
   ↓
Proyecto
   ↓
Plugins
```

La Skill de mayor prioridad prevalece cuando varias comparten el mismo nombre.

Para evitar conflictos:

* usa nombres descriptivos;
* comprueba si ya existe otra Skill similar;
* renombra la tuya si está siendo anulada.

---

# 6. Diferencia entre Skills, CLAUDE.md y comandos

## CLAUDE.md

Se carga en todas las conversaciones.

Se utiliza para reglas y convenciones que deben estar presentes permanentemente:

* lenguaje o framework del proyecto;
* estructura de carpetas;
* estilo de código;
* convenciones generales;
* restricciones permanentes.

Ejemplo:

> Las nuevas rutas de API se guardan en `src/api/handlers`.

---

## Skills

Se cargan bajo demanda.

Se utilizan para conocimientos o procedimientos que solo son relevantes en determinadas tareas:

* revisión de una PR;
* generación de documentación;
* checklist de publicación;
* formato de commits;
* auditoría de accesibilidad.

Ejemplo:

> Cuando revises una PR, ejecuta estas comprobaciones y presenta los resultados con este formato.

---

## Comandos de barra

Requieren que el usuario los invoque explícitamente.

La diferencia fundamental es:

* `CLAUDE.md`: siempre activo;
* Skill: activación automática según la intención;
* comando de barra: activación manual.

---

# 7. Metadatos avanzados

Además de `name` y `description`, una Skill puede incluir campos opcionales.

## `allowed-tools`

Restringe las herramientas que Claude puede utilizar cuando la Skill está activa.

Ejemplo:

```yaml
---
name: codebase-onboarding
description: Ayuda a comprender la estructura y arquitectura del proyecto.
allowed-tools: Read, Grep, Glob, Bash
---
```

Esto resulta útil para:

* análisis de solo lectura;
* auditorías;
* tareas sensibles;
* evitar modificaciones accidentales.

Si no se incluye `allowed-tools`, Claude utiliza su sistema normal de permisos.

---

## `model`

Permite seleccionar el modelo que ejecutará la Skill.

Ejemplo:

```yaml
model: sonnet
```

Puede utilizarse para adaptar coste, velocidad o capacidad al tipo de tarea.

---

# 8. Divulgación progresiva

Una Skill compleja no debería concentrar toda su información en un `SKILL.md` gigantesco.

El principio recomendado es:

> Mantener en `SKILL.md` solo las instrucciones esenciales y cargar el contenido adicional únicamente cuando sea necesario.

Estructura posible:

```text
my-skill/
├── SKILL.md
├── references/
│   ├── architecture-guide.md
│   └── examples.md
├── scripts/
│   └── validate.py
└── assets/
    └── template.md
```

Funciones:

* `SKILL.md`: procedimiento principal;
* `references/`: documentación extensa;
* `scripts/`: operaciones deterministas;
* `assets/`: plantillas, imágenes o recursos.

El curso recomienda mantener `SKILL.md` por debajo de unas 500 líneas.

Las referencias deben cargarse solo cuando sean relevantes.

Por ejemplo:

```markdown
Si la consulta trata sobre arquitectura, consulta `references/architecture-guide.md`.
```

---

# 9. Uso eficiente de scripts

Los scripts pueden ejecutarse sin cargar todo su código en la ventana de contexto.

Solo consume contexto su resultado.

Por eso, en `SKILL.md` conviene indicar:

> Ejecuta el script.

En lugar de:

> Lee el script completo y reproduce su lógica.

Los scripts son especialmente útiles para:

* validaciones repetibles;
* comprobaciones del entorno;
* transformaciones de datos;
* procesos que deben comportarse siempre igual;
* tareas más fiables como código probado que como instrucciones generadas.

---

# 10. Skills frente a otras funciones de Claude Code

## Skill frente a subagente

Una Skill añade conocimiento a la conversación actual.

Un subagente trabaja en un contexto separado y devuelve el resultado.

Usa una Skill cuando:

* quieres mejorar el razonamiento actual;
* el procedimiento debe aplicarse durante la conversación;
* no necesitas aislar la tarea.

Usa un subagente cuando:

* quieres delegar trabajo;
* necesitas un contexto independiente;
* quieres evitar saturar la conversación principal;
* necesitas herramientas o permisos distintos.

Resumen:

> La Skill aporta conocimiento.
> El subagente aporta aislamiento y delegación.

---

## Skill frente a Hook

Una Skill se activa según lo que pide el usuario.

Un Hook se activa cuando ocurre un evento.

Ejemplos de eventos:

* antes de usar una herramienta;
* después de modificar un archivo;
* cuando Claude intenta finalizar;
* durante una compactación.

Usa una Skill para:

* procedimientos;
* guías;
* conocimiento especializado;
* formas de razonar o presentar resultados.

Usa un Hook para:

* ejecutar un linter después de cada edición;
* impedir una acción peligrosa;
* ejecutar pruebas obligatorias;
* aplicar una regla que no se puede omitir.

Resumen:

> La Skill orienta cómo realizar una tarea.
> El Hook garantiza que algo ocurra ante un evento.

---

## Skill frente a MCP

Una Skill proporciona conocimiento e instrucciones.

Un servidor MCP proporciona herramientas, recursos o integraciones externas.

Ejemplos de MCP:

* bases de datos;
* GitHub;
* Slack;
* Google Drive;
* APIs externas.

Resumen:

> La Skill enseña cómo trabajar.
> MCP permite interactuar con sistemas externos.

---

# 11. Cómo se combinan todas las piezas

Una configuración profesional puede utilizar simultáneamente:

```text
CLAUDE.md
→ Convenciones permanentes del proyecto.

Skills
→ Procedimientos y conocimientos específicos.

Hooks
→ Garantías y automatizaciones basadas en eventos.

Subagentes
→ Trabajo delegado en contextos aislados.

MCP
→ Herramientas y servicios externos.
```

No se trata de elegir una sola función para todo.

La buena práctica es asignar cada necesidad a la herramienta adecuada.

---

# 12. Cómo compartir Skills

## Mediante el repositorio

Guardar la Skill en:

```text
.claude/skills/
```

Ventajas:

* se comparte mediante Git;
* todos reciben las actualizaciones;
* queda versionada;
* está vinculada al proyecto.

Es la mejor opción para procedimientos específicos de un repositorio.

---

## Mediante plugins

Los plugins permiten distribuir Skills entre varios proyectos, equipos o usuarios.

Son adecuados cuando la Skill:

* no depende de un único repositorio;
* puede reutilizarse en varios proyectos;
* puede ser útil para una comunidad más amplia.

---

## Mediante configuración empresarial

Las organizaciones pueden desplegar Skills obligatorias para todos los usuarios.

Son adecuadas para:

* seguridad;
* cumplimiento;
* estándares corporativos;
* procesos que deben aplicarse siempre.

Estas Skills tienen la prioridad más alta.

---

# 13. Skills y subagentes

Los subagentes no heredan automáticamente las Skills de la conversación principal.

Los subagentes personalizados deben declarar explícitamente qué Skills utilizan.

Ejemplo:

```yaml
---
name: frontend-reviewer
description: Revisa código frontend.
skills: accessibility-audit, performance-check
---
```

Puntos fundamentales:

* los agentes integrados no pueden acceder a Skills;
* los subagentes personalizados sí pueden;
* deben enumerarse explícitamente;
* en un subagente, las Skills se cargan al iniciar, no bajo demanda.

Esto permite crear especialistas:

```text
Subagente frontend
→ accesibilidad + rendimiento

Subagente backend
→ seguridad + base de datos
```

---

# 14. Cómo solucionar problemas

## La Skill no aparece

Comprobar:

* que `SKILL.md` está dentro de una carpeta;
* que el archivo se llama exactamente `SKILL.md`;
* que el YAML es válido;
* que se reinició Claude Code;
* que la ruta es correcta.

Puede utilizarse:

```bash
claude --debug
```

para consultar errores de carga.

---

## La Skill aparece, pero no se activa

La causa más probable es la descripción.

Solución:

* comparar la descripción con las frases que realmente utilizas;
* añadir palabras y expresiones habituales;
* explicar con claridad qué hace;
* indicar cuándo debe activarse.

Ejemplo de posibles frases de activación:

* «hazme un commit»;
* «prepara el mensaje del commit»;
* «revisa mis cambios de Git»;
* «qué mensaje pondrías para estos cambios».

---

## Se activa la Skill equivocada

Probablemente las descripciones sean demasiado similares.

Solución:

* hacerlas más específicas;
* separar claramente los casos de uso;
* utilizar nombres más distintivos.

---

## Una Skill personal está siendo ignorada

Puede existir otra Skill de mayor prioridad con el mismo nombre.

Solución:

* revisar la jerarquía;
* renombrar la Skill;
* consultar la configuración empresarial.

---

## La Skill se carga, pero falla

Comprobar:

* dependencias instaladas;
* permisos de ejecución;
* rutas;
* existencia de archivos;
* herramientas autorizadas.

Para scripts:

```bash
chmod +x script.sh
```

El curso recomienda utilizar barras `/` en las rutas, incluso en Windows.

---

# 15. Flujo recomendado para crear una buena Skill

```text
1. Detectar una tarea repetitiva.
2. Definir exactamente qué debe hacer.
3. Elegir si será personal o de proyecto.
4. Crear su carpeta y SKILL.md.
5. Redactar una descripción clara.
6. Mantener las instrucciones concisas.
7. Añadir referencias y scripts solo cuando sean necesarios.
8. Limitar herramientas si existe riesgo.
9. Reiniciar Claude Code.
10. Probarla con varias formas de pedir la tarea.
11. Revisar si se activa correctamente.
12. Mejorarla a partir de errores reales.
```

---

# 16. Las ideas más importantes del curso

## Primera idea

> Una Skill captura una forma repetible de trabajar.

No debes crear Skills porque la función existe, sino porque has detectado un procedimiento recurrente.

---

## Segunda idea

> La descripción decide si Claude encuentra la Skill.

Las mejores instrucciones no sirven si la descripción no activa correctamente la habilidad.

---

## Tercera idea

> Las Skills se cargan bajo demanda para ahorrar contexto.

No deben sustituir indiscriminadamente a `CLAUDE.md`.

---

## Cuarta idea

> Una Skill debe ser pequeña en su núcleo y ampliable mediante archivos auxiliares.

Eso es la divulgación progresiva.

---

## Quinta idea

> Una Skill no es siempre la herramienta correcta.

* permanente → `CLAUDE.md`;
* procedimiento contextual → Skill;
* delegación aislada → subagente;
* garantía por evento → Hook;
* integración externa → MCP.

---

## Sexta idea

> Las mejores Skills nacen de problemas reales.

No conviene crear una biblioteca enorme de Skills hipotéticas.

Es mejor observar:

* qué instrucciones repites;
* qué errores se repiten;
* qué procesos quieres estandarizar;
* qué tareas necesitas realizar siempre de la misma manera.

---

# Modelo mental final

```text
Tengo una tarea repetitiva
        ↓
La convierto en conocimiento reutilizable
        ↓
Escribo una descripción que Claude pueda reconocer
        ↓
Claude la carga solo cuando es relevante
        ↓
El procedimiento se aplica de forma consistente
        ↓
Lo pruebo, lo corrijo y lo comparto
```

# Frase para recordar

> **Una Skill no automatiza simplemente una tarea: codifica una forma de trabajar para que Claude pueda reutilizarla en el momento adecuado.**
