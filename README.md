# apuntes_reactjs
Una breve introducción a REACT

Entorno de desarrollo:
En el navegador:
React developers tool

En la maquina:
NPM
NODE
YARN

con NPM instalar
create-react-app

luego crear un proyecto
```
create-react-app nombre_del_proyecto
```

dentro del proyecto se creara una estructura de la siguiente manera:

* proyecto
* .git
  - /archivos_para_git
* node_modules
  - /todos_los_modulos
* public
  - /favicon.ico
  - /index.html
  - /manifest.json
* src
	- /App.css
	- /App.js
	- /App.test.js
	- /index.css
	- /index.js
	- /logo.svg
	- /serviceWorker.js
* /.gitignore
* /package.json
* /README.md
* /yarn.lock

El archivo principal es el `src/index.js` que le hace render en este caso a `App.js`

Pero primero comencemos nuestro ambiente de desarrollo con
```
npm run start
```
dentro del proyecto, el iniciara react app en el navegador en la dirección por defecto:
[http://localhost:3000/](http://localhost:3000/)

Puedes editar `App.js` que está siendo renderizado por index.js, este archivo está hecho en jsx, el cual es como un preprocesador como SASS
[una breve explicación jsx](https://carlosazaustre.es/jsx-para-novatos/)


Si trabajas en el entorno de create-react-app el configura el webpack para que refresque automáticamente cuando se guarda el archivo.

también tiene a babel corriendo, para que la compatibilidad sea superior, y viene con eslint para que nos corrija errores de codificación, o mejores convenciones.


Recuerda que si no tienes la carpeta de node_modules puede instalarlas con (dentro de la carpeta):

```
npm install
```
y correr el proyecto con

`npm run start`
dentro del proyecto

## Como funciona REACT:

Hay un HTML y tambien codigo JS:

Para cargar información dentro de una `html` desde un `javascript` lo que se hace normalmente es algo como lo siguiente:


`index.html`

Si se dan cuenta el archivo HTML no trae el `JS`, `create react app` se encarga de esta parte de la magia:
```
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1, shrink-to-fit=no" />
  <title>Ejemplo REACT</title>
</head>

<body>
  <div id="app"></div>
</body>

</html>
```

`index.js`

```
// el elemento a crear
const element = document.createElement('h1');

// Lo que queremos que aparezce dentro de nuestro elemento
element.innerText = 'Hello world!';

// donde lo queremos añadir
const container = document.getElementById('app')

// añadimos dentro del contenedor el elemento
container.appendChild(element);
```

vamos al navegador y veremos el `Hello world!`

Con las herramientas de desarrollo `react developers tools` se puede ver todo lo que `create react app` hizo por nosotros

## Ahora hagamoslo con REACT JS

Usando el mismo `index.html`, solo modificamos el `index.js`

```
//importamos la librerias
// este es el analogo al createElement, habilita el jsx
import React from 'react';

//este es el analogo al appendChild
import ReactDom from 'react-dom'

// este es algo diferente (mas facil con jsx) al anterior ejemplo:
const element = <h1>Hello world!</h1>
// este es diferente al ejemplo anterior:
const container = document.getElementById('app');

// En esta ya se ve el react con su metodo render, facilitando el ejemplo anterior del appendChild:
// ReactDom.render(--que se renderizara--, donde se renderiazara--)
ReactDom.render(element, container);
```
