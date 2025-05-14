<p align="center"> <img src="public/logo.png" alt="Bodytech" width="300"> </p> <h1 align="center">root-config - Orquestador</h1>
Este repositorio contiene la configuración principal de rutas y el registro de microfrontends para una arquitectura basada en single-spa. Su función principal es montar dinámicamente las aplicaciones correspondientes según la ruta actual del navegador.

Este root-config actúa como orquestador, asegurando que cada microfrontend se cargue en el momento adecuado y dentro del contexto correcto de la aplicación.

## 🚀 Instalación y ejecución
```bash
npm install
npm run start
```
Esto ejecutará el root-config de forma local. Para que el sistema funcione correctamente, los microfrontends también deben estar corriendo localmente en paralelo.

## ⚠️ Importante
- Asegúrse de tener en ejecución todos los microfrontends necesarios, ya que este repositorio solo se encarga de orquestarlos, no de servirlos.

- Las URLs de los microfrontends deben estar correctamente configuradas en el archivo de rutas correspondiente.

- Si estás en desarrollo local, verificar que los puertos de cada microfrontend coincidan con los definidos en las importaciones.

## 📁 Estructura del Proyecto

- `public/`
  - `logo.png`: Imagen del logo de la aplicación.
  - `favicon.ico`: Icono de la aplicación para la pestaña del navegador.
  
- `src/`
  - `index.ejs`: Este archivo contiene las importaciones de los microfrontends y los CDNs requeridos.
  - `microfrontend-layout.html`: Se encarga de cargar y vincular los microfrontends a sus respectivas rutas.
  - `MyBodytech-root-config.js`: Este archivo inicializa la aplicación y maneja la configuración de los microfrontends.
  
## Ejemplos
Estas son las importaciones locales necesarias. Sin ellas, los microfrontends no podrán montarse correctamente.
```Markdown
  <% if (isLocal) { %>
  <script type="injector-importmap">
    {
      "imports": {
        "@MyBodytech/root-config": "//localhost:9000/MyBodytech-root-config.js",
        "@MyBodytech/mf-store-auth": "//localhost:8500/MyBodytech-mf-store-auth.js",
        "@MyBodytech/mf-login": "//localhost:8530/Mybodytech-mf-Auth.js",
        "@MyBodytech/mf-navbar": "//localhost:8510/MyBodytech-mf-navbar.js",
        "@MyBodytech/mf-home": "//localhost:8520/single-spa-mf-home.js"
      }
    }
  </script>
  <% } %>
```
