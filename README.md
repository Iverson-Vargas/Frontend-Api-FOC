# Frontend del Sistema de Inventario FOC 2025-2

Este proyecto es una interfaz de usuario desarrollada con Vite y TypeScript, diseñada para interactuar con el sistema de inventario FOC. La aplicación consume una API REST para visualizar y gestionar las diferentes entidades del sistema, como productos, áreas, usuarios y más.

## Autores
- Iverson Vargas
- Anthony Azuaje
- Sebastian Dorante
- Johan Torres

## Guía de Instalación y Puesta en Marcha

### Requisitos Previos
- Node.js 20+
- npm 10+
- Backend en ejecución: **API FOC** o cualquier API compatible.

### Variables de Entorno

Antes de iniciar, es necesario configurar la URL del backend. Crea un archivo `.env` en la raíz del proyecto y añade la siguiente variable:

```
VITE_API_URL=http://localhost:3800/api/v1

```
### Configuración y Ejecución

Sigue estos pasos para levantar el proyecto:

1.  **Instalar dependencias:** Abre una terminal en la raíz del proyecto y ejecuta:
    ```bash
    npm install
    ```
2.  **Levantar el servidor de desarrollo:** Una vez instaladas las dependencias, inicia el frontend con:
    ```bash
    npm run dev
    ```
3.  **Acceder a la aplicación:** Abre tu navegador y visita `http://localhost:5173`.

### Migraciones

Este es un proyecto de frontend, por lo que no gestiona migraciones de base de datos. Las migraciones deben ser ejecutadas desde el proyecto del backend (**API FOC**).

## Documentación del Proyecto

### ¿Cómo funciona?

La aplicación está construida sobre Vite y TypeScript, utilizando un enfoque de "Vanilla JS" para la manipulación del DOM, sin frameworks como React o Vue. La navegación se gestiona a través de un router simple en `main.ts`, que carga dinámicamente los módulos correspondientes a cada entidad del sistema.

Cada módulo (por ejemplo, `products`, `users`) tiene un servicio asociado en `src/services/` que se encarga de la comunicación con la API REST a través de un cliente HTTP centralizado (Axios).

### Arquitectura y Stack Tecnológico

-   **Vite + TypeScript**: Bundler moderno que ofrece un desarrollo rápido con Hot Module Replacement (HMR).
-   **Vanilla TS/DOM**: Renderizado de vistas mediante manipulación directa del DOM para una mayor ligereza y control.
-   **Axios**: Cliente HTTP para consumir los endpoints de la API REST de forma centralizada (`src/services/http.service.ts`).
-   **Diseño**: Estilos globales definidos en `src/style.css`, con un tema oscuro y diseño responsivo.

### Estructura de Archivos

```
src/
 ├─ main.ts          # Punto de entrada, router y montaje de módulos.
 ├─ style.css        # Estilos globales, variables y diseño de tablas.
 ├─ modules/         # Vistas de cada entidad (productos, usuarios, etc.).
 └─ services/        # Lógica de consumo de API con Axios.
```

### Scripts Disponibles

| Script | Descripción |
| --- | --- |
| `npm run dev` | Inicia Vite con recarga en caliente |
| `npm run build` | Compila TypeScript y genera la build para producción |
| `npm run preview` | Sirve la build generada para validar la salida final |

### Endpoints de la API

La aplicación consume los siguientes endpoints para obtener los listados de cada entidad:

-   `GET /roles` — Listado de roles.
-   `GET /categories` — Listado de categorías.
-   `GET /warehouses` — Listado de almacenes.
-   `GET /users` — Listado de usuarios.
-   `GET /areas` — Listado de áreas.
-   `GET /products` — Listado de productos.
-   `GET /test` — Listado de registros de prueba.

Cada endpoint es consumido desde su respectivo servicio en `src/services/`. Si la API falla o no está disponible, la aplicación mostrará datos de respaldo (mock data) para asegurar una experiencia de usuario continua.
