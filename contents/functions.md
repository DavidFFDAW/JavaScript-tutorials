# Functions en JavaScript

<div id="menu"></div>

## 1. ¿Qué es una funcion?

En JavaScript como en muchos lenguajes de programación una función es un pedazo de código que puede repetirse varias veces durante la ejecución del programa y se aísla en una función para poder reutilizarla y repetirla sin tener que reescribir todo este pedazo de código una y otra vez en cada ocasión en que se requiere su utilización.

Las `recomendaciones` sobre cómo se deben escribir las funciones para que sean legibles dice que deberían tener un nombre claro y no muy extenso sobre qué es lo que se hace dentro de ellas (que sean `autodescriptivas`) y no deben tener más de tres parámetros ya que, de necesitarlos, podríamos estar ante un error de diseño.

Las funciones cumplen un papel muy importante y son un paso previo a la Programación Orientada a Objetos (`OOP`) ya que internamente una clase está formada por funciones o métodos.

En este lenguaje hay varias formas de declarar una función:

  -  [Function](#functions)
  -  [Anónima](#anonymous)
  -  [Arrow Function](#arrow)

</br>

<div id="functions"></div>

## 2. Function

La forma más común de declarar una `función` en JavaScript es usando la propia `keyword` homónima.

Si bien es una forma válida de declarar funciones hay algunas características que debemos tener en cuenta a la hora de utilizarla. A continuación lo analizamos.

Primeramente el valor del `this` interno para la función dependerá del punto y manera en la que la función es llamada ([documentación](https://stackoverflow.com/questions/133973/how-does-this-keyword-work-within-a-function)).

Por otra parte cuando se utiliza esta `keyword`, la función adquiere una característica llamada `hoisting`, que quiere decir que en tiempo de interpretación del código todas aquellas funciones declaradas con usando `function` serán "movidas" al inicio haciendo que no importe el lugar en el que se ha declarado dicha función.

Esta característica hace que sea posible aunque desaconsejable ejecutar una función antes de que haya sido declarada en código como se muestra en el siguiente snippet:

```javascript
    console.log(getHoistedNumber()); // 154487

    ...

    function getHoistedNumber () {
        return 154487;
    }
```

De la misma manera y continuando con lo que acabamos de ver si se declaran dos funciones con el mismo nombre, sólo funcionará la segunda ya que se procesa después sobreescribiendo la primera.

Recordemos que esta característica (`hoisting`) es propia de `function` y `var` y puede ser causante de errores si no se tiene una buena organización.

```javascript
    function getTotalSongs(){ 
        return 3;
    }
    console.log(getTotalSongs()) // <-- 7

    function getTotalSongs(){
        return 7;
    };
    console.log(getTotalSongs()) // <-- 7
```

[Volver arriba](#menu)

</br>

<div id="anonymous"></div>

## 3. Anonymous Functions

Estas funciones se llaman de esta manera porque no se especifica ningún nombre para la función y se declaran también utilizando `function` pero se almacenan en una variable y, al hacerlo, hemos eliminado la característica del `hoisting` y ya no podremos ejecutar funciones antes de su declaración. 

Además de esto ahora sí podremos modificar una función a lo largo de la ejecución con resultados diferentes:

```javascript
    let getNumber = function () {
        return 5;
    }
    console.log(getNumber()); // 5

    getNumber = function() {
        return 54648;
    }
    console.log(getNumber()); // 54648
```

[Volver arriba](#menu)

</br>

<div id="arrow"></div>

## 4. Arrow Functions


Estas funciones son muy similares a las anteriores (anónimas) con algunas peculiaridades a tener en cuenta con respecto a las `function`.

La principal diferencia y la más evidente es la sintaxis de estas funciones en las que se prescinde de la palabra `function`.

En estas funciones los parámetros van entre paréntesis sólo cuando son más de uno, además si no hay parámetros se puede utilizar `_` o `()` para indicar que no requiere parámetros.

La sintaxis para escribir una arrow function es la siguiente. Es recomendable guardarlas en `const` para evitar una posible sobreescritura del cuerpo de la función.

A estas funciones muchas veces se las llama también `callbacks`.

Cabe destacar que en contraposición a las otras dos tipos de funciones que hemos visto anteriormente, en este tipo si es una única línea se puede devolver el valor sin escribir un `return` puesto que va implícito en este tipo de funciones. Por ejemplo estas dos funciones son equivalentes:

```javascript
const getArrowNumberImplicit = _ => 154;

const getArrowNumberExplicit = () => {
    return 154;
}

console.log(getArrowNumberImplicit() === getArrowNumberExplicit()) // <-- True
```

Alguno ejemplos de funciones con parámetros son:

```javascript
// Tomo un valor y le sumo su doble
const addDoubleOf = num => num + (num * 2);

// Tomo dos valores, al que sacaré el doble y al que se lo sumaré
const addDoubleOfTo = (toDouble, addition) => addition + (toDouble * 2);

console.log(addDoubleOf(4)) // <-- 4 + (4*2) = 12
console.log(addDoubleOfTo(4, 12)) // <-- 12 + (4*2) = 20
```

Las principales diferencias técnicas con respecto a las [`funciones`](#functions) son:

  -  No tiene enlaces propios para `this` o `super`.
  -  No tiene argumentos o palabras clave `new`.
  -  No se pueden usar los métodos `apply`, `bind` o `call` con este tipo de funciones, ya que no generan un scope distinto para `this`.
  -  No se pueden utilizar como `constructor`.
  -  No se puede utilizar `yield` en el cuerpo de estas funciones.

[Volver al menú](#menu)