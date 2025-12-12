---
name: git_commit
description: Realiza un commit siguiendo Conventional Commits y buenas prácticas.
triggers:
  - /git_commit
  - git commit
---

# Git Commit Command

Este comando instruye al agente para realizar commits siguiendo estrictamente las reglas de atomicidad y lógica defindas por el usuario.

## Reglas Fundamentales

1.  **Atomicidad Estricta**: Los commits deben hacerse UNO POR UNO. Cada commit debe representar un único cambio lógico.
2.  **Agrupación Lógica**:
    - **NO** agrupar archivos que no tengan relación entre sí.
    - **NO** separar archivos que dependan lógicamente el uno del otro (ej. un test y la funcionalidad que prueba).
3.  **Conventional Commits**: `tipo(alcance): descripción`.
    - Tipos: `feat`, `fix`, `docs`, `style`, `refactor`, `perf`, `test`, `chore`.
    - Ejemplo: `feat(auth): implementa login con google`.
4.  **Descripción**: Imperativo, claro, sin puntos finales, en **Español**.

## Pasos para el Agente

1.  **Análisis de Cambios**:

    - Ejecuta `git status` y `git diff` para entender todos los cambios pendientes.
    - Identifica mentalmente los grupos de archivos que deben ir juntos en un mismo commit.

2.  **Ejecución de Commits (Iterativo)**:

    - Para CADA grupo lógico de cambios identificado:
      a. Selecciona los archivos específicos: `git add <archivo1> <archivo2> ...` (NUNCA usar `git add .` a menos que TODOS los archivos sean parte del mismo cambio lógico único).
      b. Realiza el commit: `git commit -m "tipo(alcance): descripción"`.
    - Repite este proceso hasta que no queden cambios pendientes por commitear (working tree clean).

3.  **Verificación**:
    - Asegúrate de que `git status` indique que no hay nada más pendiente.
