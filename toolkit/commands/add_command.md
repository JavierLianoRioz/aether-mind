---
name: add_command
description: Crea un nuevo comando personalizado para el agente Antigravity.
triggers:
  - /add_command
  - add command
  - nuevo comando
---
# Agregar Nuevo Comando

Este comando guía al agente en la creación de nuevos comandos y workflows para Antigravity.

## Prerrequisitos

Debes obtener la siguiente información del usuario:
1.  **Nombre del Comando**: (ej. `generar-tests`, `analizar-logs`).
2.  **Descripción**: Breve descripción de lo que hace.
3.  **Triggers**: Lista de disparadores (slash commands o frases).
4.  **Instrucciones/Lógica**: Qué debe hacer el agente cuando se ejecuta este comando.

## Pasos de Creación

### 1. Crear Definición del Comando

Crea un archivo en `ai/toolkit/commands/<nombre_comando_snake_case>.md`.

**Formato:**

```markdown
---
name: <nombre_comando_snake_case>
description: <descripción>
triggers:
  - /<trigger_principal>
  - <otros triggers>
---
# <Título del Comando>

<Instrucciones detalladas para el agente>
```

### 2. Crear Workflow

Crea un archivo en `.agent/workflows/<nombre-comando-kebab-case>.md`.

**Formato:**

```markdown
---
name: <nombre-comando-kebab-case>
description: <descripción>
triggers:
  - /<trigger_principal>
---
# <Título del Workflow>

Este workflow ejecuta las instrucciones definidas en:
`ai/toolkit/commands/<nombre_comando_snake_case>.md`

Por favor, lee y sigue estrictamente las reglas definidas en ese archivo.
```

## Ejemplo

Si el usuario quiere un comando para "optimizar imágenes":

1.  **Toolkit**: `ai/toolkit/commands/optimize_images.md`
2.  **Workflow**: `.agent/workflows/optimize-images.md`

## Verificación

Confirma al usuario que los archivos han sido creados y que puede probar el comando usando `/<trigger_principal>`.
