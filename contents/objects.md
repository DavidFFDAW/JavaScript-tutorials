# Objetos en JavaScript

## 1. ¿Qué es un objeto?

En JavaScript un objeto no es más que un conjunto clave-valor que se suelen delimitar entre `{` `}`.

Cada par está compuesto por un identificador global que suelen recibir el nombre de `propiedad` o `key` y el valor que se almacena para la clave anterior (`valores` o `values`).

Para instanciar lo que denominamos un objeto en JavaScript se utilizan las `llaves` y un ejemplo de un objeto sería:

```javascript 
{ name: 'Peter', surname: 'Parker', age: 25, job: 'hero' }
```

En este caso las claves o `keys` serían `name,surname,age,job` mientras que los valores serían cada uno de los propios valores que toma cada una de las claves mencionadas anteriormente.

</br>

## 2. Tipos permitidos

Los tipos permitidos para ser declarados dentro de un objeto son todos. Como el propio JavaScript, no tiene restricción para los tipos que se utilizan en su interior.

</br>

## 3. Acceso a los valores

Tomaremos como ejemplo la siguiente pieza de código: 

```javascript 
const superObj = { name: 'Peter', surname: 'Parker', age: 25, job: 'hero' };
```
</br>

### 3.1.  Como podemos acceder a los valores:

Para acceder a un valor de un objeto hay varias formas. La más simple de ellas es conociendo la `key` exacta del objeto:

```javascript
    superObj.name // <-- Peter
```

Si no conocemos el nombre de la propiedad o es un nombre variable que viene desde otro lugar podremos hacerlo con esta otra sintaxis:

```javascript
    const key = 'job';
    superObj[key] // <-- hero
```
</br>

### 3.2. Comprobación si la propiedad existe:

Para evitar posibles errores o valores `undefined` podemos tener en cuenta si la propiedad existe y si no existe devolver un valor por defecto en su lugar. Aunque esto ya depende un poco más de la lógica que se quiera implementar.

En este caso se puede comprobar directamente si existe valor o utilizar un método propio de la clase `Object` que nos permite comprobar esto mismo. Para introducir un valor por defecto podremos emplear la [ternaria](http://slashdot.org) o bien el [operador de cortocircuito](http://slashdot.org). A continuación se muestran dos ejemplos con las dos posibilidades:

Utilizando [`hasOwnProperty()`](https://developer.mozilla.org/es/docs/Web/JavaScript/Reference/Global_Objects/Object/hasOwnProperty) y la ternaria:

```javascript
    const key = 'time';
    const heroTime = superObj.hasOwnProperty(key) ? superObj[key] : 'not-time';
    return heroTime; // <-- 'not-time'
```

Utilizando la comprobación por valor y el [`operador de cortocircuito`](https://developer.mozilla.org/es/docs/Web/JavaScript/Guide/Expressions_and_Operators#comparacion):


```javascript
    const key = 'time';
    return superObj[key] || 'not-time'; // <-- 'not-time'
```

</br>


### 3.3. Como obtengo solo las propiedades:

Pongamos que del objeto original quiero obtener un array con todas las `keys` que tiene dicho objeto para utilizarlas posteriormente en alguna otra función.

Podríamos hacerlo con un `for (... in superObj)` e ir almacenando en un array inicializado anteriormente todas las claves del objeto. Pero `Object` ya tiene un método que te permite hacer esto mismo sin necesidad de tener que reinventar la rueda.

```javascript
    Object.keys(superObj) // <-- ['name','surname','age','job']
```

### 3.4. Como obtengo solo los valores:

Aplicando la lógica anterior también existe un método nativo que nos permite obtener solo los valores de un objeto:

```javascript
    Object.values(superObj) // <-- ['Peter','Parker',25,'hero']
```

</br>

## 4. Declaración de propiedades:

Para declarar nuevas propiedades se utiliza una sintaxis similar a la que usamos para acceder a las propiedades.


### 4.1. Como declaro una nueva propiedad:

Para añadir una nueva propiedad `id` con su respectivo valor hay varias formas de hacerlo como se muestra a continuación:


```javascript
    // Forma 1
    superObj.id = 'a3f5c896-7f48-4212-9931-d6e6b753cff3';

    // Forma 2
    superObj['id'] = 'a3f5c896-7f48-4212-9931-d6e6b753cff3';
```

En cualquier caso el resultado será que el objeto anterior tendrá una nueva propiedad `id` con el valor `a3f5c896-7f48-4212-9931-d6e6b753cff3`.

</br>

### 4.2. Spread Operator `(...)` con objetos:

Al utilizar este operador podremos recoger los elementos de un conjunto iterable (en este caso un objeto) y lo podremos utilizar por ejemplo para clonar el contenido de un objeto en otro añadiendo nuevas propiedades:

```javascript
    const obj = { name: 'Example' }
    const objNew = { ...obj, id: 396840 };

    console.log(obj); // <-- { name: 'Example' }
    console.log(objNew); // <-- { name: 'Example', id: 396840 }
```

</br>

### 4.3. Que pasa si declaro dos veces una propiedad:

Teniendo un objeto ya declarado como el inicial con el que estamos trabajando y vuelvo a declarar una propiedad como por ejemplo el nombre con la misma `key` lo que haremos será sobreescribir el valor que tuviera esta almacenada anteriormente.

Un objeto no puede tener múltiples claves con el mismo nombre, pues estas actúan como identificador único.
A continuación se muestra un ejemplo de este comportamiento:

```javascript
    // ORIGINAL
    console.log(superObj.name); // <-- Peter

    // CAMBIO
    superObj.name = 'Manolo';

    console.log(superObj.name); // <-- Manolo

```