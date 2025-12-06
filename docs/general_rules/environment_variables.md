# Gestión de Variables de Entorno y Secretos

Para garantizar la seguridad y la flexibilidad de la aplicación en diferentes entornos (desarrollo, pruebas, producción), seguimos estrictas reglas sobre el manejo de configuraciones.

## Reglas Principales

1.  **Cero Secretos en el Código**: Nunca hardcodees contraseñas, tokens de API, claves privadas o cualquier información sensible directamente en el código fuente.
2.  **Uso de Archivos `.env`**: Utiliza archivos `.env` para almacenar variables de configuración que pueden cambiar entre entornos o que son sensibles.
3.  **Configuración vs Código**: Mantén la configuración separada de la lógica del código. Si un valor puede cambiar (URLs de API, puertos, timeouts), debe ser una variable de entorno.

## Archivos `.env.example`

-   Todo repositorio debe incluir un archivo `.env.example` (o `.env.template`).
-   Este archivo debe listar todas las variables de entorno requeridas por la aplicación.
-   **NO** debe contener valores reales de secretos. Usa valores de ejemplo o marcadores de posición (ej. `API_KEY=your_api_key_here`).

## Acceso en el Código

-   Utiliza las bibliotecas apropiadas para cargar estas variables en tu entorno de ejecución (ej. `dotenv` en Node.js, `os.environ` en Python).
-   Valida la existencia de las variables críticas al inicio de la aplicación para evitar fallos en tiempo de ejecución.
