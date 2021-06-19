# Curso Practico de ReactJS

## ¿Qué es ReactJS?

* Es una librería o biblioteca de JS para construir interfaces de usuario
* Características:
  * Declarativo, permite crear interfaces de usuario amigables
  * Basado en componentes, separación cada uno de los elementos de la pagina web
  * Se puede usar para la web, aplicaciones de escritorio y aplicaciones mobile.
* Nace dentro del equipo de Instagram y fue liberado a la comunidad y facebook la mantiene con ing encargados de esto
* Empresas como AirBnb, Netflix,  WhatsappWeb, Platzi, landingpage de Uber etc.

## DOM, Virtual DOM y React DOM

#### **¿Qué es el Virtual DOM?**

Es una herramienta que usar ReactJS para darle _**performance y velocidad**_ a nuestro desarrollo, por lo cuál nosotros tenemos una copia fiel de lo que es el DOM, lo cual permite identificar que elementos han sido actualizados y refrescar el boque actualizado, sin necesidad de refrescar toda la vista como sucedería normalmente.

![](../.gitbook/assets/image.png)

## Create React App

_**Create React App**_ es un modulo que nos genera un proyecto con toda la configuración de ReactJS para empezar a trabajar inmediatamente.

### **Creación del proyecto**

```text
npx create-react-app name-app
cd name-app
npm run start
```

### **Estructura del proyecto**

![](../.gitbook/assets/image%20%282%29.png)

* node\_modules: todos los elementos que requiere react para trabajar y los elementos que vayamos añadiendo. **Nunca se debe subir al entorno de producción.**
* public: Archivos públicos para enviar a producción.
* src: Donde se encuentra toda la aplicación como los componentes por ejemplo. \(**Importante\)**
* package.json: Archivo de configuración de nuestro proyecto.

## Componentes

Los componentes se almacenan en src/components

![](../.gitbook/assets/image%20%283%29.png)

{% hint style="warning" %}
El nombre de los archivos de los componentes debe iniciar en mayúscula, al igual que cada nueva palabra del componente. \(PascalCase\)
{% endhint %}

### Componente Stateful

Componente con ciclo de vida, eventos y estado

```jsx
//Stateful.jsx
import React, { Component } from "react";

class Stateful extends Component {
  constructor(props) {
    super(props);
    this.state = {
      hello: 'Hola Mundo'
    }
  }
  render() {
    return <h1> {this.state.hello}</h1>;
  }
}

export default Stateful;
```

### Componente  **Stateless**

No depende de tener un estado o ciclo de vida, solo presenta la lógica, son mas utilizados puesto que trabajan con la parte funcional.

```jsx
//Stateless.jsx
import React from 'react'

const Stateless = () => {
  return(
    <h1>Hola Mundo</h1>
  )
}

export default Stateless
```

### Componente Presentacional

Componentes con una parte muy particular de html que se vera en el navegador

```jsx
//Presentacional.jsx
import React from 'recapt'

const Presentacional = () => <h1>Hola Mundo</h1>

export default Presentacional;
```

## JSX: JavaScript + HTML

Es una sintaxis que mezcla un poco de html y JS. De esta forma react consigue que todo este dentro del mismo componente. Tanto la lógica con JS como la estructura con HTML

```jsx
//HolaMundo.jsx
import React from 'react'

const HolaMundo = () => {
  //Esto es JS
  const Hello = 'Hola Mundo';
  const isTrue = true;
  // Esto es JSX (HTML + JavaScript):
  return (
    <div className = "HolaMundo"> 
      <h1>{Hello}</h1>
      <h2>Curso Esencial de React</h2>
      <img src = "https://arepa.s3.amazonaws.com/react.png" alt = "React" />
      {isTrue ? <h4>Esto es verdadero</h4> : <h5>Soy Falso</h5>}
      {isTrue && <h4>Soy verdadero</h4>}
    </div>
  );
};

export default HolaMundo;
```

## Props: Comunicación entre Componentes

Los props son la forma de comunicación entre los componentes y el resto de la aplicación. Y para introducirlos dentro de un componente se realiza de forma similar a como se haría con los argumentos de una función

* El componente Button se le inserta información del resto de la aplicación usando props:

```jsx
//Button.jsx
import React from "react";

const Button = props => {
  const { text } = props;
  return (
    <div>
      <button type="button">{text}</button>
    </div>
  );
};

export default Button;
```

En el index se añade el componente Button y se inserta el props correspondiente

```jsx
//index.js
import React from 'react';
import Button from './components/Button';

ReactDOM.render(
  <React.StrictMode>
    <HolaMundo/>
    <Button text= "Click"/>
  </React.StrictMode>,
  document.getElementById('root')
);
```

## ¿Qué son los métodos del ciclo de vida?

[Diagrama de los ciclos de vida](https://projects.wojtekmaj.pl/react-lifecycle-methods-diagram/)

![Tomado de https://projects.wojtekmaj.pl/react-lifecycle-methods-diagram/](../.gitbook/assets/image%20%284%29.png)

## State - Events

El _**estado**_ en React es un objeto al cual podemos definirle variables de tipo string, boolean, numero o funciones y podremos acceder desde nuestro componente en el momento en el cual se inicializa.

En React podemos usar los eventos predefinidos que se usan en HTML, como onclick

{% hint style="info" %}
Los eventos en React son llamados en formato camelCase. Por ejemplo: **onClick**
{% endhint %}

```jsx
//Button.jsx
import React from "react";

class Button extends React.Component {
  state = {  //Estado
    count: 0,
  };
  handleClick = () => {  //Evento que actualiza
    this.setState({
      count: this.state.count + 1,
    });
  };
  render() {
    const { count } = this.state;
    return (
      <div>
        <h1> Manzanas: {count} </h1>
        <button type="button" onClick={this.handleClick}>
          Agregar
        </button>
      </div>
    );
  }
}
```

## Instalación y configuración de entorno

{% tabs %}
{% tab title="Paso 1" %}
Inicializar el repo

```jsx
git init
```
{% endtab %}

{% tab title="Paso 2" %}
Inicializar proyecto

```jsx
npm init -y
```
{% endtab %}

{% tab title="Paso 3" %}
Implementamos la configuración básica

![](../.gitbook/assets/image%20%285%29.png)
{% endtab %}

{% tab title="Paso 4" %}
Instalación de React en el proyecto

```jsx
npm install react react-dom
```
{% endtab %}
{% endtabs %}

## Agregando compatibilidad con todos los navegadores usando Babel

Babel es una herramienta que permite usar JS moderno y transformarlo a JS que sea compatible con todos los navegadores.

Instalación de _babel_ y guardado como dependencia de desarrollo

```jsx
 npm install @babel/core babel-loader @babel/preset-env @babel/preset-react --save-dev
```

* babel/core: incluye todas las herramientas para transformar el JS moderno 
* babel-loader: encargado de trabajar con webpack
* presets: ayuda a entender nuestro código en este caso de JS \(env\) y de React \(react\)

Creamos un archivo llamado _**.babelrc**_ y establecemos la configuración según las dependencias que elegimos instalar previament

```jsx
//.babelrc
{
  "presets": ["@babel/preset-env","@babel/preset-react"]
}
```

## Webpack: 

### Empaquetando nuestros módulos

Webpack se encarga de que todos nuestro recursos de JS, HTML,CSS y multimedia los agrupa y los pone listos y optimizados para enviar a producción y crear este entorno de trabajo optimo.

{% tabs %}
{% tab title="Paso 1" %}
Instalación de webpack y guardado como dependencia de desarrollo

```jsx
 npm install webpack webpack-cli html-webpack-plugin html-loader --save-dev
```
{% endtab %}

{% tab title="Paso 2" %}
Configuración del archivo maestro de configuración de webpack

```jsx
//webpack.config.js
const path = require("path");
const HtmlWebPackPlugin = require("html-webpack-plugin");
module.exports = {
  entry: "./src/index.js",
  output: {
    //directorio en el que guardaremos los archivos
    path: path.resolve(__dirname, "dist"), 
    //nombre del archivo principal
    filename: "bundle.js",
  },
  resolve: {
    extensions: [".js", ".jsx"],
  },
  //modulo con las reglas necesarias
  module: {
    rules: [
      {
        //identificación de los archivos js y jsx
        test: /\.(js|jsx)$/,
        //exclusion de la carpeta node_modules
        exclude: /node_modules/,
        use: {
          loader: "babel-loader",
        },
      },
      {
        //Trabajar con los archivos html
        test: /\.html$/,
        use: [
          {
            loader: "html-loader",
          },
        ],
      },
    ],
  },
  plugins: [
    new HtmlWebPackPlugin({
      template: "./public/index.html",
      filename: "./index.html",
    }),
  ],
};
```
{% endtab %}

{% tab title="Paso 3" %}
Configuramos el script en el archivo de package.json

```jsx
"scripts": {
    "test": "echo \"Error: no test specified\" && exit 1",
    //Script de compilación
    "build": "weppack --mode production"
  },
```
{% endtab %}

{% tab title="Paso 4" %}
Compilamos el proyecto

```jsx
npm run build
```
{% endtab %}

{% tab title="Paso 5" %}
Visualizamos que se genero una nueva carpeta con la compilación del proyecto

![](../.gitbook/assets/image%20%286%29.png)
{% endtab %}
{% endtabs %}

### Dev Server: Reporte de errores y Cambios en tiempo real

Esta herramienta nos permite editar y que de forma automática webpack compile el programa y poder probar los cambios al instante en nuestro entorno de desarrollo local.

{% tabs %}
{% tab title="Paso 1" %}
Instalación de la dependencia que permite correr un entorno de desarrollo local

```jsx
npm install webpack-dev-server --save-dev
```
{% endtab %}

{% tab title="Paso2" %}
Creamos el script para correr nuestro entorno de desarrollo local

```jsx
//package.json
"scripts": {
    "test": "echo \"Error: no test specified\" && exit 1",
    "build": "webpack --mode production",
    "start":  "webpack serve --mode development --env development"
  }
```
{% endtab %}

{% tab title="Paso 3" %}
Ejecutamos el script

```jsx
npm run start
```
{% endtab %}
{% endtabs %}

## Estilos con SASS

{% tabs %}
{% tab title="Paso 1" %}
Instalación de las dependencias necesarias para trabajar con sass y guardado como dependencia de desarrollo

```jsx
npm install mini-css-extract-plugin css-loader node-sass sass-loader --save-dev
```
{% endtab %}

{% tab title="Paso 2" %}
Configuración del webpack.config.js con la nueva regla para que compile los archivos de css y añadimos el plugin

```jsx
//webpack.config.js
test: /\.(s*)css$/,
        use: [
          {
            loader: MiniCssExtractPlugin.loader,
          },
          'css-loader',
          'sass-loader'
        ]
/////////////
plugins: [
    new MiniCssExtractPlugin({
      filename: "./assets/[name].css"
    })
]      
C
```
{% endtab %}

{% tab title="Paso 3" %}
Creamos la carpeta assets/styles

![](../.gitbook/assets/image%20%2811%29.png)
{% endtab %}
{% endtabs %}

## Configuración final: ESLint y Git Ignore

#### ESLint

ESLint es una herramienta que nos ayuda a detectar de forma rapida bugs o typos, o ayudarnos a tener un estandar dentro de nuestro código

{% tabs %}
{% tab title="Paso 1" %}
Instalación de los paquetes necesarios para usar ESLint

```jsx
npm install eslint babel-eslint eslint-config-airbnb eslint-plugin-import eslint-plugin-react eslint-plugin-jsxa11y
```
{% endtab %}

{% tab title="Paso 2" %}
Añadimos el archivo de configuración de ESLint

![](../.gitbook/assets/image%20%2810%29.png)
{% endtab %}

{% tab title="Paso 3" %}
Sobreescribimos el archivo .eslintrc con la configuración de este [gist](https://gist.github.com/gndx/60ae8b1807263e3a55f790ed17c4c57a)
{% endtab %}
{% endtabs %}

#### Git Ignore

En el archivo .gitignore sobreescribimos con la configuración de este [gist](https://gist.github.com/gndx/747a8913d12e96ff8374e2125efde544)

## Arquitectura de componentes para Platzi Video

{% tabs %}
{% tab title="First Tab" %}
![](../.gitbook/assets/image%20%287%29.png)

## Estructura del Header
{% endtab %}

{% tab title="Second Tab" %}
![](../.gitbook/assets/image%20%289%29.png)
{% endtab %}
{% endtabs %}

{% tabs %}
{% tab title="Paso 1" %}
En el componente Header

```jsx
//Header.jsx
import React from "react";

const Header = () => (
  <header className="header">
    <img
      className="header__img"
      src="../assets/logo-platzi-video-BW2.png"
      alt="Platzi Video"
    />
    <div className="header__menu">
      <div className="header__menu--profile">
        <img src="../assets/user-icon.png" alt="" />
        <p>Perfil</p>
      </div>
      <ul>
        <li>
          <a href="/">Cuenta</a>
        </li>
        <li>
          <a href="/">Cerrar Sesión</a>
        </li>
      </ul>
    </div>
  </header>
);

export default Header;
```
{% endtab %}

{% tab title="Paso 2" %}
Creamos el archivo App.jsx para que funcione como contenedor de nuestra app

![](../.gitbook/assets/image%20%2813%29.png)
{% endtab %}

{% tab title="Paso 3" %}
```jsx
//App.jsx
import React from "react";
import Header from "../components/Header"

const App = ()=> (
  <div className="App">
    <Header/>
  </div>
)

export default App
```
{% endtab %}

{% tab title="Paso 4" %}
Importamos la App al index.js

```jsx
//index.js
import React from "react";
import ReactDOM from "react-dom";
import App from "./containers/App";

ReactDOM.render(<App />, document.getElementById('app'));
```
{% endtab %}

{% tab title="Paso 5" %}
Creamos la siguiente estructura de archivos para los estilos de la aplicación

![](../.gitbook/assets/image%20%2812%29.png)
{% endtab %}
{% endtabs %}

