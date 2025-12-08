---
name: sync_commands
description: Sincroniza los comandos definidos en toolkit/commands con los workflows de Antigravity.
triggers:
  - /sync-commands
  - sincronizar comandos
  - actualizar workflows
---

# Sincronizar Comandos

Este comando encarga al agente la tarea de asegurar que todos los comandos definidos en el toolkit tengan su correspondiente workflow operativo.

## Objetivo

Leer todos los archivos de definición de comandos en `aether-mind/toolkit/commands/` y generar o actualizar los archivos de workflow correspondientes en `.agent/workflows/` (situado en la raíz del proyecto, fuera de `aether-mind`).

## Instrucciones para el Agente

1.  **Analizar Comandos**:

    - Lee todos los archivos `.md` existentes en `aether-mind/toolkit/commands/`.
    - Para cada archivo, extrae:
      - El nombre del comando (del frontmatter `name`).
      - El trigger principal (el primero en la lista `triggers` del frontmatter).
      - La descripción.

2.  **Generar/Actualizar Workflows**:

    - Para cada comando encontrado, verifica si existe un archivo correspondiente en `.agent/workflows/<nombre-comando-kebab-case>.md` (en la raíz del repositorio).
    - Si no existe, o si necesita actualización, crea/sobrescribe el archivo con el siguiente contenido:

    ```markdown
    ---
    name: <nombre-comando-kebab-case>
    description: <descripción del comando>
    triggers:
      - <trigger_principal>
    ---

    # <Título del Workflow (Nombre legible)>

    Este workflow ejecuta las instrucciones definidas en:
    `aether-mind/toolkit/commands/<nombre_archivo_original>.md`

    Por favor, lee y sigue estrictamente las reglas definidas en ese archivo.
    ```

3.  **Confirmación**:
    - Lista los comandos que han sido sincronizados (creados o actualizados).
