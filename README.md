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

## Proceso de Desarrollo

<details>

<summary>Nociones sobre el proceso de desarrollo y cómo realizar las contribuciones de código y documentación del proyecto</summary>
### Consejos para generación de commits

- Hacer commits pequeños y frecuentes, para facilitar la revisión de los cambios.
  - Ejemplo: Si se está trabajando en una funcionalidad que requiere de 3 commits, se deberán realizar 3 commits, en lugar de realizar un commit con los 3 cambios.
  - Esto facilita la revisión de los cambios, ya que se puede revisar cada commit por separado.
  - Además, permite que si se encuentra un error en un commit, se pueda revertir ese commit sin afectar los demás.
- Escribir los mensajes de commits de forma breve y concisa, en tiempo presente.
  - 👌 Ejemplo: `[FE-#19] - Agrega componente de login`
  - ⛔ No: `[FE-#19] - Agregué componente de login`

#### Mensajes de commits

Para una mejor referencia de cuál es el área a la que contribuye un commit, se deben utilizar los siguientes prefijos en los mensajes de commits, acompañados por el ID correspondiente al issue al que pertenecen.

- **[AR]** - Arquitectura
- **[BE]** - Backend
- **[DM]** - Modelos de dominio
- **[DOCS]** - Documentación
- **[FE]** - Frontend
- **[TOOL]** - Herramientas de desarrollo

#### Ejemplos de mensaje de commits

- `[FE-#47] - Agrega componente de login`
- `[BE-#93] - Agrega endpoint de login`
- `[TOOL-#7] - Agrega librería @ngrx/store`

### Ramas de desarrollo (Branches)

- **main** - Rama principal del proyecto. Contiene la última versión estable del proyecto.
- **release/**_[numero_de_version]_ - Rama de lanzamiento de una versión. Contiene la última versión de la aplicación en producción.
  - Por ejemplo: `release/0.0.1` es la rama correspondiente a la versión 1.0.0 de la aplicación. A esta rama se deberán realizar los merges de las ramas de desarrollo de las nuevas funcionalidades previo al lanzamiento de esta versión.
- **feature/**_[id_issue][nombre_de_la_funcionalidad]_ - Rama de desarrollo de una funcionalidad, correspondiente a un issue determinado.
  - Por ejemplo: `feature/57-login` es la rama correspondiente al desarrollo de la funcionalidad de login, correspondiente al issue #57 en el repositorio.
- **bugfix/**_[id_issue][nombre_del_bug]_ - Rama de desarrollo de un bug, correspondiente a un issue determinado.
  - Por ejemplo: `bugfix/49-bug-flicker-en-header` es la rama correspondiente al desarrollo de la corrección de un bug de flicker en el header de la aplicación, correspondiente al issue #49 en el repositorio.

#### Manejo de ramas de desarrollo

Para más facilidad en el manejo de las ramas de desarrollo, se recomienda utilizar el módulo incorporado de Git en WebStorm, al cual puede accederse haciendo click en la opción `Git` en la barra de menú superior y en el botón de la esquina inferior derecha del IDE, donde se visualiza la rama activa actual.

- Para crear una nueva rama de desarrollo, se debe hacer checkout de la rama `release/[numero_de_version]` vigente y crear (hacer checkout de) una nueva rama a partir de esta.
  - `git checkout release/[numero_de_version]
  - `git checkout -b feature/57-login`
- Para actualizar una rama de desarrollo, se debe hacer checkout de la rama `release/[numero_de_version]` vigente y realizar un merge hacia la rama de desarrollo correspondiente.
  - `git checkout release/[numero_de_version]`
  - `git pull'`
  - `git checkout feature/57-login`
  - `git merge release/[numero_de_version]`
  - `git push`
- Para actualizar una rama de desarrollo, se debe crear una nueva Pull Request desde la rama `release/[numero_de_version]` hacia la rama de desarrollo correspondiente.
- Para actualizar la rama `main`, se debe hacer checkout de la rama `main` y realizar un pull desde la rama `release/[numero_de_version]`.
  - `git checkout main`
  - `git pull release/[numero_de_version]`

#### Pull Requests

Para realizar un Pull Request, se debe crear una nueva Pull Request desde la rama `release/[numero_de_version]` hacia la rama de desarrollo correspondiente, utilizando el dashboard de pull requests

Los mensajes de cada Pull Request deben incluir el ID del issue al que pertenece, el nombre de la funcionalidad que se está desarrollando y el prefijo de las áreas del proyecto que modifican.

- Ejemplo: `[#57-FE] - Agrega componente de login`
- Ejemplo: `[#93-BE] - Agrega endpoint de login`
- Ejemplo: `[#7-TOOL] - Agrega librería @ngrx/store`
- Ejemplo: `[#49-FE] - Corrige bug de flicker en header`
- Ejemplo: `[#73-DM] - Agrega modelo User`

En el caso de que una PR modifique varias áreas del proyecto, se deberá incluir el prefijo de cada área modificada, separada por comas.

- Ejemplo: `[#93-BE,FE] - Agrega nuevo parámetro para request de login.`
- Ejemplo: `[#93-BE,FE,DM] - Agrega nuevo atributo al modelo Provider y lo utiliza en el request de login y su procesamiento.`
</details>

## Herramientas de desarrollo

<details>
<summary>Listado de las herramientas y tecnologías usadas para el desarrollo</summary>
#### Herramientas de desarrollo

- [NodeJS 18.16.0](https://nodejs.org/es/) - Entorno de ejecución para JavaScript.
- [WebStorm 2023] - IDE para desarrollo de aplicaciones web.
- [Git](https://git-scm.com/) - Sistema de control de versiones.
- [GitHub](https://github.com) - Plataforma de desarrollo colaborativo.
- [Github Projects](https://github.com) - Plataforma de gestión de proyectos.
- [Postman](https://www.postman.com/) - Herramienta para realizar pruebas de API.
- [DBeaver](https://dbeaver.io/) - Herramienta para administración de bases de datos.
- [Oracle DB](https://www.oracle.com/database/) - Base de datos relacional.

#### Despliegue de versiones de desarrollo

- [Vercel](https://vercel.com/) - Plataforma de hosting de aplicaciones web.
  - Para aplicaciones de frontend.
- [Render](https://render.com/) - Plataforma de hosting de aplicaciones web.
  - Para aplicaciones de backend.

#### Lenguajes de programación

- [HTML](https://developer.mozilla.org/es/docs/Web/HTML) - Lenguaje de marcado para desarrollo web en frontend y backend.
- [TypeScript](https://www.typescriptlang.org/) - Lenguaje de programación para desarrollo web en frontend y backend.
  - Versión: 4.9.5
- [PL/SQL](https://www.oracle.com/database/technologies/appdev/plsql.html) - Lenguaje de programación para desarrollo de procedimientos almacenados en Oracle DB.
- [SCSS](https://sass-lang.com/) - Lenguaje de programación para desarrollo de estilos en CSS.

#### Tecnologías de Backend

- [NestJS](https://nestjs.com/) - Framework para desarrollo de aplicaciones backend.
  - Versión: 7.6.15
- [Express](https://expressjs.com/) - Framework de backend para desarrollo de aplicaciones web. Utilizado mediante la librería [NestJS Express](https://docs.nestjs.com/techniques/express).
  - Versión: 9.4.0 (@nestjs/platform-express)
- [Oracle DB](https://www.oracle.com/database/) - Base de datos Oracle.

#### Tecnologías de Frontend

- [Angular](https://angular.io/) - Framework para desarrollo de aplicaciones frontend web.
  - Versión: 15.2.7
- [NgRx](https://ngrx.io/) - Librería para manejo de estado en aplicaciones frontend web.
- [RxJS](https://rxjs.dev/) - Librería para manejo de eventos asíncronos en aplicaciones frontend web.
  - Versión: 7.8.0
- [SASS](https://sass-lang.com/) - Preprocesador de CSS.

</details>
