# Test Driven Development (TDD)

Este proyecto fomenta el uso de TDD (Desarrollo Guiado por Pruebas) para asegurar la calidad y robustez del código desde el inicio.

## El Ciclo Red-Green-Refactor

1.  **Red (Rojo)**:
    -   Escribe una prueba unitaria que falle para la nueva funcionalidad o corrección de error.
    -   Asegúrate de que la prueba falle por la razón correcta (la funcionalidad aún no existe).

2.  **Green (Verde)**:
    -   Escribe la cantidad mínima de código necesaria para hacer pasar la prueba.
    -   No te preocupes por la perfección o la limpieza del código en este paso, solo haz que funcione.

3.  **Refactor (Refactorizar)**:
    -   Mejora el código que acabas de escribir sin cambiar su comportamiento.
    -   Aplica principios de Clean Code, elimina duplicación y optimiza la estructura.
    -   Asegúrate de que todas las pruebas sigan pasando después de refactorizar.

## Beneficios

-   **Confianza**: Sabes que tu código hace lo que debe hacer.
-   **Diseño Modular**: TDD tiende a conducir a un código más desacoplado y comprobable.
-   **Documentación Viva**: Las pruebas actúan como especificaciones y ejemplos de uso del código.
