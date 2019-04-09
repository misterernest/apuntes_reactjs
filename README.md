# APUNTES REACT JS

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

`create-react-app nombre_del_proyecto`

dentro del proyecto se creara una estructura de la siguiente manera:

- proyecto
- .git
  - /archivos_para_git
- node_modules
  - /todos_los_modulos
- public
  - /favicon.ico
  - /index.html
  - /manifest.json
- src - /App.css - /App.js - /App.test.js - /index.css - /index.js - /logo.svg - /serviceWorker.js
- /.gitignore
- /package.json
- /README.md
- /yarn.lock

El archivo principal es el `src/index.js` que le hace render en este caso a `App.js`

Pero primero comencemos nuestro ambiente de desarrollo con

`npm run start`

dentro del proyecto, el iniciara react app en el navegador en la dirección por defecto:
[http://localhost:3000/](http://localhost:3000/)

Puedes editar `App.js` que está siendo renderizado por index.js, este archivo está hecho en jsx, el cual es como un preprocesador como SASS
[una breve explicación jsx](https://carlosazaustre.es/jsx-para-novatos/)

Si trabajas en el entorno de create-react-app el configura el webpack para que refresque automáticamente cuando se guarda el archivo.

también tiene a babel corriendo, para que la compatibilidad sea superior, y viene con eslint para que nos corrija errores de codificación, o mejores convenciones.

Recuerda que si no tienes la carpeta de node_modules puede instalarlas con (dentro de la carpeta):

`npm install`

y correr el proyecto con

`npm run start`
dentro del proyecto

## Como funciona REACT

Hay un HTML y tambien codigo JS:

Para cargar información dentro de una `html` desde un `javascript` lo que se hace normalmente es algo como lo siguiente:

`index.html`

Si se dan cuenta el archivo HTML no trae el `JS`, `create react app` se encarga de esta parte de la magia:

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="utf-8" />
    <meta
      name="viewport"
      content="width=device-width, initial-scale=1, shrink-to-fit=no"
    />
    <title>Ejemplo REACT</title>
  </head>

  <body>
    <div id="app"></div>
  </body>
</html>
```

`index.js`

```js
// el elemento a crear
const element = document.createElement("h1");

// Lo que queremos que aparezce dentro de nuestro elemento
element.innerText = "Hello world!";

// donde lo queremos añadir
const container = document.getElementById("app");

// añadimos dentro del contenedor el elemento
container.appendChild(element);
```

vamos al navegador y veremos el `Hello world!`

Con las herramientas de desarrollo `react developers tools` se puede ver todo lo que `create react app` hizo por nosotros

## Ahora hagamoslo con REACT JS

Usando el mismo `index.html`, solo modificamos el `index.js`

```js
//importamos la librerias
// este es el analogo al createElement, habilita el jsx
import React from "react";

//este es el analogo al appendChild
import ReactDom from "react-dom";

// este es algo diferente (mas facil con jsx) al anterior ejemplo:
const element = <h1>Hello world!</h1>;
// este es diferente al ejemplo anterior:
const container = document.getElementById("app");

// En esta ya se ve el react con su metodo render, facilitando el ejemplo anterior del appendChild:
// ReactDom.render(--que se renderizara--, donde se renderiazara--)
ReactDom.render(element, container);
```

### JSX O React.createElement

JSX es pure sugar syntax (azucar sintetica)

- JSX es mas legible
- JSX es max expresivo

Las dos tienen poder y las misma capacidad.

con React.createElement

```js
import React from "react";
import ReactDOM from "react-dom";

// React.createElement('la etiqueta', {los atributos}, 'lo que va dentro')
const element = React.createElement("h1", {}, "Hola! Soy los children");
const container = document.getElementById("app");
ReactDOM.render(element, container);
```

Un ejemplo con atributos:

```js
import React from "react";
import ReactDOM from "react-dom";
// React.createElement('la etiqueta', {los atributos}, 'lo que va dentro')

const element = React.createElement(
  "a",
  { href: "https://misterernest.com" },
  "Ir a misterernest.com"
);
const container = document.getElementById("app");
ReactDOM.render(element, container);
```

Ahora un ejemplo, pero con variables, manejando `React.createElement`:

```js
import React from "react";
import ReactDOM from "react-dom";
// React.createElement('la etiqueta', {los atributos}, 'lo que va dentro')
const name = "misterernest";
const element = React.createElement("h1", {}, `Hola soy ${name}`);
const container = document.getElementById("app");
ReactDOM.render(element, container);
```

La verdad no es complejo, pero que tal si es mas facil con `JSX`?
Intentemoslo:

```js
import React from "react";
import ReactDOM from "react-dom";

// variable
const name = "misterernest";
// jsx - mas sencillo aún, mas facil de recordar
const jsx = <h1>hola soy {name}</h1>;

const container = document.getElementById("app");
//renderizamos
ReactDOM.render(jsx, container);
```

La regla es mucho mas sencilla y con menos caracteres, es mas natural el `html`.

Ademas dentro de las llaves puedes colocar la expresión que desees, y se imprimen, a menos que sean undefined.

probemos otro ejemplo:

```js
import React from "react";
import ReactDOM from "react-dom";

// variable
const name = "misterernest";
// jsx - mas sencillo aún, mas facil de recordar
const jsx = (
  <h1>
    hola soy {name} y mi edad es : {15 + 12}
  </h1>
);

const container = document.getElementById("app");
//renderizamos
ReactDOM.render(jsx, container);
```

Otro ejemplo mas complejo:

_Primero con `React.createElement`_

```js
import React from "react";
import ReactDOM from "react-dom";
// variable
// jsx - mas sencillo aún, mas facil de recordar
const name = "misterernest";
const element = React.createElement(
  "div",
  {},
  React.createElement("h1", {}, `hola soy ${name}`),
  React.createElement("h4", {}, `hola soy ${name}`)
);

const container = document.getElementById("app");
//renderizamos
ReactDOM.render(element, container);
```

los anidamientos se vuelven mucho mas complejo...

_Y ahora con `JSX`_

```js
import React from "react";
import ReactDOM from "react-dom";
// variable
// jsx - mas sencillo aún, mas facil de recordar
const name = "misterernest";
const jsx = (
  <div>
    <h1>hola soy {name}</h1>
    <h4>y soy desarrollador front-end</h4>
  </div>
);

const container = document.getElementById("app");
//renderizamos
ReactDOM.render(jsx, container);
```

Cuando es anidado, es mucho mas facil, legible y claro.

Vamos a trabajar en `JSX`, ya que es mucho mas facil.

Queda claro que `REACT JS` es `Javascript`, que por medio de `webpack`, `babel` y `create react app`, `jsx` termina siendo `JS`

## Componentes

Que son los componentes:
Unidad básica de desarrollo, se puede asemejar con un bloque lego, barras de busqueda, header, footer, aside, etc...

Siendo un poco mas tecnicos, viendo la programación orientada a objetos:
`COMPONENTES = CLASES`
`ELEMENTOS = OBJETOS`
El elemento sale de un componente.

Algo primordial que lo ira dando la experiencia es identificar componentes:
Para esto hay un par de preguntas que te pueden ayudar:

- ¿Qué elementos se repiten?
- ¿Que elementos cumplen una función muy especifica?

Si cumple cualquiera de estas dos, son candidatos a COMPONENTE.

Miremos una tienda virtual.

Cada elemento de la tienda, aunque no se repite, siempre es la misma caja con la misma estructura. Osea que este elemento se esta repitiendo, de manera visual o de funcionalidad, maneja foto, precio, cantidad y descripción.

Ahora veamos lo elementos que cumplen un función muy especifia:

- Sirven para encapsular una lógica.
- Permiten juntar muchos comportamientos y aspectos visuales en un solo lugar.

el buscador de una tienda virtual, es un componente complejo, salen resultado, devuelven peticiones, maneja funciones muy especificas y nuestros componentes van ha hacer lo mismo.

Ahora hagamos nuestro primer componente:

Esta parte no es obligatorias pero son convensiones que ayudan mucho en el momento del mantenimiento y la colaboración en un grupo de desarrollo.
dentro de la carpeta src, se puede crear una carpeta llamada `components` que es donde viven nuestros componentes.

Dentro de este colocamos el primer componente, es un `batch.js`

En el archivo va haber un codigo tipo react.js de la siguiente manera:

```js
import React from "react";
// esta es la clase que hereda de React.Component para volversre un componente
class Badge extends React.Component {
  // este es el metodo que todo compoente debe tener
  render() {
    return <h1>Badges</h1>;
  }
}
// Esto es lo que permite que nuestro componente sea exportado
export default Badge;
```

y lo importamos desde nuestro `index.js`

```js
import React from "react";
import ReactDOM from "react-dom";
import Badge from "./components/Badge";

const container = document.getElementById("app");
// Aquí llamamos nuestra importaión y estamos asegurando que lo que llega es un elemento.
ReactDOM.render(<Badge />, container);
```

Recomendamos tener el scetch del proyecto para poder realizar el trabajo, facilita el objetivo del proyecto e ir construyendo seguún nuestro mapa.

En este caso solo es practica, no contamos con uno.
