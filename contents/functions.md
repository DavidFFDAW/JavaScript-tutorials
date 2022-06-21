# Functions en JavaScript

## 1. ¿Qué es una funcion?

En JavaScript como en muchos lenguajes de programación una función es un pedazo de código que puede repetirse varias veces durante la ejecución del programa y se aísla en una función para poder reutilizarla y repetirla sin tener que reescribir todo este pedazo de código.

Las `recomendaciones` sobre cómo se deben escribir las funciones para que sean legibles dice que deberían tener un nombre claro y no muy extenso sobre qué es lo que hace y no deben tener más de tres parámetros, ya que de necesitarlos podríamos estar ante un error de diseño.

Las funciones cumplen un papel muy importante y son un paso previo a la Programación Orientada a Objetos (`OOP`) ya que internamente una clase está formada por funciones o métodos.

En este lenguaje hay varias formas de declarar una función:

  -  [Function](#2.-function)
  -  [Anónima](#3.-anonymous-functions)
  -  [Arrow Function](#arrow)

</br>

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

</br>

## 3. Anonymous functions

Estas funciones se declaran también utilizando `function` pero se almacenan en una variable pero al hacerlo de esta manera hemos eliminado la característica del `hoisting` y ya no podremos ejecutar funciones antes de su declaración. 

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