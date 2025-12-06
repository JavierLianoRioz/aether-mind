---
name: create_plan
description: Analiza la tarea solicitada y genera un archivo implementation_plan.md detallado.
triggers:
  - /create-plan
  - /plan
  - crear plan
  - create plan
---
# Crear Plan de Implementación

Este comando instruye al agente para crear un plan de implementación detallado para una tarea específica.

## Instrucciones

1.  **Analizar la Tarea**:
    *   Lee los `Additional Context` y el historial de la conversación para entender completamente qué se necesita hacer.
    *   **Revisión de Documentación**: Verifica si existen carpetas o archivos relevantes en `ai/docs/libraries` para las tecnologías involucradas.
    *   **Revisión de Reglas**: Verifica `ai/docs/general_rules` y `ai/docs/project_rules` para aplicar estándares y normativas del proyecto.
    *   Si hay ambigüedades, asume un enfoque estándar o anota las dudas en la sección de revisión.

2.  **Generar `implementation_plan.md`**:
    *   Crea (o sobrescribe si así se solicita explícitamente y es seguro) el archivo `implementation_plan.md` en el directorio de artefactos de la conversación actual (`<appDataDir>/brain/<conversation-id>/implementation_plan.md`).
    *   **NO** uses `TargetFile` con una ruta relativa. Usa la ruta absoluta del artefacto.

3.  **Estructura del Plan**:
    El contenido del archivo debe seguir estrictamente este formato Markdown:

    ```markdown
    # Goal: [Título Breve de la Tarea]

    [Descripción concisa del objetivo y el contexto]

    ## Relevant Documentation
    [Lista aquí las tecnologías clave utilizadas]
    - [Nombre Tecnología]: [Enlace a ai/docs/libraries/...] (Si existe)
    - [Nombre Tecnología]: **MISSING DOCUMENTATION** (Si debería existir pero no está en ai/docs/libraries)

    ## Relevant Rules
    [Revisar `ai/docs/general_rules` y `ai/docs/project_rules` y listar las reglas aplicables]
    - [Nombre Regla]: [Enlace a ai/docs/..._rules/...]


    ## User Review Required
    [Lista cualquier decisión de diseño importante, cambios disruptivos, o dudas que requieran confirmación del usuario. Si no hay nada crítico, pon "None."]

    ## Proposed Changes
    [Estructura los cambios por componente o área]

    ### [Nombre del Componente/Área]
    #### [NEW] [nombre_archivo](file:///ruta/absoluta)
    - Descripción de lo que contendrá este nuevo archivo.
    #### [MODIFY] [nombre_archivo](file:///ruta/absoluta)
    - Puntos clave de las modificaciones a realizar.

    ## Verification Plan
    ### Automated Tests
    - [Comandos para correr tests existentes o nuevos]
    ### Manual Verification
    - [Pasos para verificar que los cambios funcionan como se espera]
    ```

4.  **Confirmación**:
    *   Notifica al usuario que el plan ha sido creado y pide su revisión usando `notify_user` con `PathsToReview`.
