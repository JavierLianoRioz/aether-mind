---
name: git_commit
description: Realiza un commit siguiendo Conventional Commits y buenas prácticas.
triggers:
  - /git_commit
  - git commit
---
# Git Commit Command

Este comando instruye al agente para realizar un commit siguiendo las estrictas reglas de calidad del repositorio Iris y gestionar la integración de la rama.

## Reglas Fundamentales

1.  **Atomicidad**: El commit debe contener un único cambio lógico.
2.  **Conventional Commits**: `tipo(alcance): descripción`.
    -   Tipos: `feat`, `fix`, `docs`, `style`, `refactor`, `perf`, `test`, `chore`.
    -   Ejemplo: `feat(auth): implementa login con google`.
3.  **Descripción**: Imperativo, claro, sin puntos finales, en **Español**.
4.  **Flujo de Trabajo**: NO hacer `git push`. Se debe hacer commit en la rama actual y luego fusionar (merge) en la rama dependiente (ej. `develop` o `main`).

## Pasos para el Agente
1.  **Estado**: Revisa cambios (`git status`, `git diff`).
2.  **Commit**:
    ```bash
    git add .
    git commit -m "tipo(alcance): descripción"
    ```
3.  **Integración**:
    -   Identifica la ramas de destino (rama padre/dependiente, usualmente `develop`).
    -   Cambia a la rama destino: `git checkout develop` (o la que corresponda).
    -   Fusiona la rama de trabajo: `git merge <rama-origen>`.
    -   **Nota**: Si hay conflictos, resuélvelos antes de completar el merge.
