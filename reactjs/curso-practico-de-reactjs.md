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

###  Componente  **Stateless**

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
Implementamos  la configuración básica 

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



