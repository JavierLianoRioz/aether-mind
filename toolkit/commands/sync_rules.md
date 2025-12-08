---
name: sync_rules
description: Convierte y sincroniza las reglas de documentación a la carpeta de reglas del agente.
triggers:
  - /sync-rules
  - sincronizar reglas
  - actualizar reglas
---

# Sincronizar Reglas

Este comando encarga al agente la tarea de asegurar que las reglas del proyecto estén disponibles en el formato que el agente consume.

## Objetivo

Leer los archivos de reglas en `aether-mind/docs/general_rules/` y `aether-mind/docs/proyect_rules/` y crear copias o versiones consolidadas en `.agent/rules/` (situado en la raíz del proyecto).

## Instrucciones para el Agente

1.  **Analizar Reglas**:

    - Escanea los directorios `aether-mind/docs/general_rules/` y `aether-mind/docs/proyect_rules/`.
    - Identifica todos los archivos `.md`.

2.  **Sincronizar**:

    - Asegúrate de que el directorio `.agent/rules/` exista en la raíz del proyecto (no dentro de `aether-mind`).
    - Para cada archivo de regla encontrado:
      - Copia el contenido al directorio `.agent/rules/`.
      - Puedes mantener el nombre original del archivo.
      - Asegúrate de que el contenido sea legible y mantenga el formato Markdown.

3.  **Confirmación**:
    - Lista las reglas que han sido sincronizadas.
