# Gestor de Paquetes

Este proyecto utiliza estrictamente **pnpm** como gestor de paquetes para asegurar una instalación rápida, eficiente y consistente de las dependencias.

## Reglas Obligatorias

1.  **Uso Exclusivo de pnpm**: Queda prohibido el uso de `npm` o `yarn` para la gestión de dependencias.
2.  **Lockfile Único**: El único archivo de bloqueo permitido en el repositorio es `pnpm-lock.yaml`.
    -   No commitear `package-lock.json` ni `yarn.lock`.
3.  **Comandos Estándar**:
    -   Instalar dependencias: `pnpm install`
    -   Añadir dependencia: `pnpm add <paquete>`
    -   Añadir dependencia de desarrollo: `pnpm add -D <paquete>`
    -   Ejecutar scripts: `pnpm run <script>` o `pnpm <script>`

## Por qué pnpm?

-   **Eficiencia de Espacio**: Utiliza un almacén direccionable por contenido, evitando duplicar paquetes en el disco.
-   **Velocidad**: Es significativamente más rápido que las alternativas.
-   **Estrictez**: Evita el acceso a dependencias "fantasma" que no están explícitamente listadas en el `package.json`.
