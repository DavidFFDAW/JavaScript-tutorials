# Variables

En JavaScript hay tres tipos de variables sin importar el tipo que vayan a almacenar en su interior puesto que es un lenguaje de tipado débil por lo que aquí no hacemos cosas como:

```java
String word = new String('My phrase'); 
```

Los distintos tipos de variables que existen en este lenguaje son tres y cada uno tiene sus características propias que veremos a continuación: 

  -  `var`
  -  `let`
  -  `const`

</br>
</br>

## 1. Var (deprecated)

Comenzaremos hablando de `var` e iremos hacia abajo. Este tipo de variable tiene varias cosas que hacen que sea poco recomendable utilizarla. `var` tiene scope global.

La principal característica que nos echa para atrás y hace que sea desaconsejable utilizarla es que, al igual que las [funciones](/contents/functions.md), tiene [`hoisting`](https://developer.mozilla.org/es/docs/Glossary/Hoisting).

En este caso el hoisting se refiere a que la variable puede ser declarada en cualquier punto del script y será movida al inicio del mismo por lo que será utilizable desde cualquier punto, haciendo de esto una muy mala praxis. Un ejemplo sería el siguiente en el que, utilizando `let` o `const` saltaría un error `ReferenceError` al intentar acceder a una variable que no ha sido declarada.

```js
console.log(declaredVariable); // <-- undefined

var declaredVariable = 6;

console.log(declaredVariable); // <-- 6
```

Cabe destacar que lo que se mueve al inicio es la declaración de la variable y no la inicialización, es decir que la variable será utilizable en todo el script porque se declara al inicio, aunque su valor se le asigna en el mismo punto en que está escrito en el programa.
Como en el ejemplo anterior que en un inicio la variable `declaredVariable` tiene un valor `undefined` porque no se le ha asignado ningún valor, pero a partir que pasamos la asignación `declaredVariable = 6;` esa misma variable pasa a tener este valor.

Como adición a esto cabe aclarar que `var` es reasignable, es decir, su valor puede cambiar su valor a lo largo del programa.

</br>

## 2. Let

Esta tipo de variable es una variable reasignable con scope de bloque por lo que será accesible desde el punto en que es declarada hacia abajo.
Si es declarada dentro de una función será utilizable únicamente dentro de esta función y no se podrá acceder a ella desde fuera de dicha función.

Un ejemplo utilizando esta variable sería:

```js
let reasignableVariable = 0;

console.log(reasignableVariable); // <-- 0

reasignableVariable = 60;

console.log(reasignableVariable); // <-- 60

reasignableVariable = 450;

console.log(reasignableVariable); // <-- 450

reasignableVariable = 6;

console.log(reasignableVariable); // <-- 6
```

</br>

## 3. Const

Este tipo de variable, como su nombre indica, es una constante, lo que quiere decir que toma un valor y solo un valor durante toda la ejecución del programa y no es reasignable en absoluto.
De hecho si se trata de asignarle un nuevo valor a una variable de tipo `const` lanzará un error **`TypeError: Assignment to constant variable.`**

Este tipo de variable también tiene scope de bloque como tiene `let`.

La característica de que no pueden variar su valor interno una vez ha sido asignado las hacen idóneas para ser utilizadas como variables de uso cotidiano puesto que, de esta manera, nos aseguramos de que no estamos asignando valores a una variable que no era o que lo modificamos sin darnos cuenta en algún punto de la ejecución.

Por ejemplo:

```js
function getPatientFromList (id) {
    const patient = list.find(it => it.patient.id === id);

    return patient || false;
}
```

Este tipo de variable está estandarizada y es recomendable su utilización para producir código limpio.

</br>

## 4. Anexo

### Let VS Const

Vale hemos visto ya las variables que tenemos disponibles y nos ha quedado claro que no debemos ni queremos utilizar `var` porque la han cancelado en Twitter por lo tant nos surge una pregunta: ***```¿Debo utilizar const o let?```***.

Pues bien la respuesta a esta pregunta es bien sencilla y es que lo recomendable sería utilizar `const` para todas aquellas variables que no necesitamos que tomen valores distintos a lo largo del programa y `let` lo utilizaremos precisamente para estos valores que precisan una modificación durante el ciclo de vida del programa que estamos escribiendo.

</br>
</br>

<div style="position: absolute; width: 90% ;height: 50px">
    <a href="/contents/cleancode.md" 
        style="float: left;">
        ← Clean Code
    </a>
    <a href="/contents/stringmethods.md"
        style="float: right;">
        String Functions →
    </a>
</div>