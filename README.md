# Gestión Documental de Proveedores - EPE Santa Fe

## Configuración inicial

1. Se recomienda utilizar JetBrains Webstorm como IDE de desarrollo. Puede descargar la última versión desde [aquí](https://www.jetbrains.com/es-es/webstorm/download/#section=windows).
2. Instalar NodeJS 18.16.0, el cual puede descargarse [aquí](https://nodejs.org/dist/v18.16.0/node-v18.16.0-x64.msi).
3. Instalar Nx CLI mediante el comando: `npm install -g nx`.
4. Instalar las dependencias de las aplicaciones mediante el comando: `npm install`.

### Integración con Nx

Se recomienda instalar los siguientes plugins de Webstorm para una mejor experiencia al trabajar con Nx:

- [Nx Console](https://plugins.jetbrains.com/plugin/21060-nx-console), por NxDev.
  - Este plugin permite ejecutar comandos para la generación de componentes, servicios y distinto tipo de entidades a lo largo de las aplicaciones, abstrayendo la generación de módulos para las aplicaciones frontend, backend y librerías.
  - También permite ejecutar comandos de Nx, como `nx affected:build` o `nx affected:test`, para ejecutar las pruebas y builds de las aplicaciones afectadas por los cambios realizados en el repositorio.
- [Nx Console Idea](https://plugins.jetbrains.com/plugin/15101-nx-console-idea), por iguissouma.
  - Este plugin permite ejecutar tareas y scripts relacionados a los proyectos dentro de un workspace de Nx, desde la interfaz de Webstorm.
  - Para habilitar el plugin en el IDE, se debe hacer click derecho en el archivo `nx.json` y seleccionar la opción `Show Nx Tasks`. Posteriormente, será visible la ventana `Nx` en la cajonera de la izquierda del IDE.

## Aplicaciones

<details>
  <summary>Referencia sobre ejecución de aplicaciones, librerías y scripts del proyecto</summary>

### Aplicaciones desplegables

- `/api` - Aplicación backend web en NestJS
- `/intranet` - Aplicación frontend web en Angular
- `/dmz` - Aplicación frontend web en Angular

### Aplicaciones de testing

- `/api-e2e` - Pruebas E2E para aplicación backend web
- `/dmz-e2e` - Pruebas E2E para aplicación frontend web
- `/intranet-e2e` - Pruebas E2E para aplicación frontend web

### Librerías

- `/libs/domain` - Modelos de dominio compartidos entre las aplicaciones

## Referencia de directorios

- `/apps` - Aplicaciones desplegables
- `/docs` - Documentación de la aplicación
- `/libs` - Librerías compartidas entre las aplicaciones
- `/scripts` - Scripts de utilidad para el desarrollo
- `/tools` - Herramientas de desarrollo

## Ejecución de aplicaciones, librerías y herramientas

### Desplegables

- `nx run api:serve:development` - Ejecuta la aplicación backend web en modo desarrollo.
- `nx run intranet:serve:development` - Ejecuta la aplicación frontend web en modo desarrollo (Intranet).
- `nx run dmz:serve:development` - Ejecuta la aplicación frontend web en modo desarrollo (DMZ).

### Compilaciones

#### Compilaciones de Desarrollo

- `nx run api:build` - Compila la aplicación backend web.
- `nx run intranet:build` - Compila la aplicación frontend web de Intranet.
- `nx run dmz:build` - Compila la aplicación frontend web de la DMZ.

#### Compilaciones de Producción

- `nx run api:build:production` - Compila la aplicación backend web en modo producción.
- `nx run intranet:build:production` - Compila la aplicación frontend web de Intranet en modo producción.
- `nx run dmz:build:production` - Compila la aplicación frontend web de la DMZ en modo producción.

### Testing Unitario

- `nx run api:test` - Ejecuta las pruebas unitarias para la aplicación backend web.
- `nx run intranet:test` - Ejecuta las pruebas unitarias para la aplicación frontend web de Intranet.
- `nx run dmz:test` - Ejecuta las pruebas unitarias para la aplicación frontend web de la DMZ.

### Testing E2E

- `nx run api-e2e:e2e` - Ejecuta las pruebas E2E para la aplicación backend web.
- `nx run intranet-e2e:e2e` - Ejecuta las pruebas E2E para la aplicación frontend web de Intranet
- `nx run dmz-e2e:e2e` - Ejecuta las pruebas E2E para la aplicación frontend web de la DMZ.

### Linting

- `nx run api:lint` - Ejecuta el linter para la aplicación backend web.
- `nx run intranet:lint` - Ejecuta el linter para la aplicación frontend web de Intranet.
- `nx run dmz:lint` - Ejecuta el linter para la aplicación frontend web de la DMZ.
- `nx run domain:lint` - Ejecuta el linter para la librería de modelos de dominio.

</details>
