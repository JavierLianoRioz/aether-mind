---
name: research_resource
description: Investiga un recurso tecnológico, recopila ejemplos de implementación y fuentes clave.
triggers:
  - /research
  - /investigate
  - /learn
  - investigar recurso
---
# Investigar Recurso

Este comando guía al agente para realizar una investigación profunda sobre una tecnología o recurso específico proporcionado por el usuario (ej: AstroJS, Docker, React Query).

## Objetivos
1.  Comprender cómo funciona la tecnología (arquitectura/conceptos).
2.  Obtener ejemplos prácticos de implementación.
3.  Identificar datos clave o "gotchas".
4.  Proporcionar fuentes oficiales y fiables.

## Lógica de Ejecución

### Caso 1: Múltiples Recursos
Si el usuario solicita investigar varios recursos a la vez (ej: "investiga React, Vue y Angular"):

1.  **Crear Plan de Investigación (`research_plan.md`)**:
    *   Crea un archivo llamado `research_plan.md` en el directorio de artefactos (`<appDataDir>/brain/<conversation-id>/research_plan.md`).
    *   Lista los recursos a investigar como tareas:
        ```markdown
        # Plan de Investigación
        - [ ] Investigar [Recurso 1]
        - [ ] Investigar [Recurso 2]
        ...
        ```
    *   Notifica al usuario que has creado el plan.

2.  **Ejecución Secuencial**:
    *   Itera sobre cada item del plan:
        1.  Marca la tarea como "en progreso" `[/]`.
        2.  Ejecuta el proceso de **Investigación Individual** para ese recurso.
        3.  Marca la tarea como "completada" `[x]`.
    *   Continúa hasta completar todos los items.

### Caso 2: Investigación Individual (Un solo recurso)

1.  **Búsqueda Inicial**:
    *   Usa `search_web` para encontrar la documentación oficial y tutoriales de alta calidad.
    *   Identifica qué es y para qué sirve principalmente.

2.  **Profundización (Deep Dive)**:
    *   Usa `read_url_content` en las páginas de documentación más relevantes para entender la sintaxis y patrones.
    *   Busca específicamente: "Quickstart", "Core Concepts", "Best Practices".

3.  **Recopilación de Ejemplos**:
    *   Extracta bloques de código que muestren cómo configurar y usar la tecnología.
    *   Busca ejemplos de casos de uso comunes.

4.  **Generación de Informe**:
    *   **Ubicación Obligatoria**: Todo contenido generado debe ir en `ai/docs/libraries`.
    *   **Estructura de Archivos**:
        *   **Recurso Simple**: Crea un único archivo markdown: `ai/docs/libraries/<recurso_snake_case>.md`.
        *   **Recurso Complejo/Extenso**: Si hay muchos ejemplos o secciones distintas, crea una subcarpeta: `ai/docs/libraries/<recurso_snake_case>/`.
            *   Ejemplo: `ai/docs/libraries/astrojs/README.md`, `ai/docs/libraries/astrojs/routing_examples.md`.
    *   **Contenido del Informe**:
        *   **Resumen Ejecutivo**: ¿Qué es y por qué usarlo?
        *   **Conceptos Clave**: Lista de términos y funcionamiento interno.
        *   **Guía de Implementación**:
            *   Instalación/Configuración.
            *   Ejemplo "Hola Mundo" o caso base.
            *   Ejemplo Avanzado o caso de uso real.
        *   **Fuentes**: Lista de URLs visitadas y recomendadas.

## Consejos Adicionales
*   Si la tecnología es una librería de UI, busca cómo se integra con el stack actual del usuario si es posible.
*   Prioriza siempre la documentación oficial sobre artículos de terceros.
