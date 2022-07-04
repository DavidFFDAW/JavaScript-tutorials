# Clean Code

## 1. ¿Qué es el Código Limpio?

Consideramos "código limpio" a aquel código que es legible y entendible a simple vista sin necesidad de leer comentarios dentro del código además de que resuelve los problemas planteados sin añadir capas de complejidad innecesarias y permite, de esta manera, un mejor, más rápido y sencillo mantenimiento del propio código.

Teniendo en cuenta que los que van a mantener y escribir el código somos humanos se le da bastante importancia a escribir un código legible, es decir, que los humanos podamos leer y entender qué está pasando en cada momento sin tener que entrar en demasiados detalles ni analizar exhaustivamente el código para ver cómo funciona.

El término "Clean Code" fue acuñado por Robert C Martin también conocido como Uncle Bob, ingeniero de software experimentado el cual es reconocido por desarrollar varios principios de diseño y arquitectura de software. Es también autor de varios libros entre los que figura uno con el nombre del tema que nos atañe.

Para poder escribir código limpio hay que conocer una serie de principios, reglas y consejos que nos permiten producir un mejor código, los cuales veremos a continuación.

</br>

## 2. Principios para producir "Clean Code".

A continuación veremos algunos de los principales consejos y recomendaciones para la producción de este tipo de código:

#### 2.1. Nombres autodescriptivos.

Algo tan sencillo como poner nombres adecuados a las variables y funciones puede hacer que un código sea mucho más entendible.

Por ejemplo en el siguiente código tenemos varias variables que van a coger un string y lo van a separar por un parametro indicado. Se muestra un ejemplo donde no se sabe a simple vista lo que esta ocurriendo y otro ejemplo donde los nombres están escogidos de forma que sea sencillo entender lo que ocurre.

  - Sin utilizar nombres descriptivos 

```javascript
function haceUnaCosa(param1, param2) { 
    return param1.split(param2);
}
const p = 'Frase original';

const p2 = haceUnaCosa(p,''); // ¿ pero que hace ?
```

  -  Utilizando nombres descriptivos

```javascript
function splitStringBy(string, splitBy) { 
    return string.split(splitBy);
}
const splitByLetter = '';
const originalString = 'Frase original';

const splittedLetters = splitStringBy(originalString, splitByLetter); 
```

</br>

#### 2.2. Utilizar lineas vacías para dar espacio.

Parece algo obvio pero no es lo mismo ver un código sin ningún tipo de espaciado con todas las funciones acumuladas que verlo con mas espaciado. Por ejemplo utilizando el código anterior hacemos una comparativa:

```javascript
function splitStringBy(string, splitBy) { 
    return string.split(splitBy);
}
const splitByLetter = '';
const originalString = 'Frase original';
const splittedLetters = splitStringBy(originalString, splitByLetter); 
```

No es lo mismo que

```javascript

const splitByLetter = '';
const originalString = 'Frase original';


function splitStringBy(string, splitBy) { 
    return string.split(splitBy);
}

const splittedLetters = splitStringBy(originalString, splitByLetter); 
```
</br>

#### 2.3. No utilizar más de tres parametros.

Se dice que si una función requiere más parámetros que tres es posible que estemos ante un error de diseño y es posible que se puedies afrontar de otra manera o bien separando el código en más capas.

Es más sencillo mantener un control de que ocurre dentro de una función cuanto menor es el número de parámetros, además será más sencillo de escribir y de leer. Por ejemplo tenemos una función `createFullAddress` que recibe originalmente cada campo por separado y para evitar una función con demasiados parámetros vamos a pasar como parámetro un único objeto `address` que contiene todos los datos:

```javascript
function createFullAddress (street, number, floor, door, cp, city, country) {
    ...
} 
```

Lo cambiaremos por un objeto:

```javascript
const address = { street: 'C Piruleta', number: 3, city: 'Madrid', country: 'Spain' }

function createFullAddress (address) {
    console.log(address.city); // <-- Málaga
    ...
} 
```

</br>

#### 2.4. Las funciones deberían hacer una única cosa.

A la hora de hacer review de un código y saber que está haciendo cada cosa sería interesante que cada función fuese una `función especialista` y ¿a qué me refiero con esto? te estarás preguntando. Pues bien, a lo que me refiero es que una función debería centrarse en hacer una cosa, una única cosa pero hacerla espectacularmente bien, es decir, que una función tiene una única responsabilidad.

Por ejemplo esta función hace demasiadas cosas:

```javascript
function createAppointment (appointment) {
    const clientList = getClientList();
    const client = clientList.find(it => it.id === appointment.client.id);

    const doctor = doctorList.find(it => it.id === appointment.doctor.id);

    const location = locationList.find(it => it.id === appointment.location.id);
    
    return internallyCreateAppointment(client,doctor,location);
} 
```

Sin embargo esta otra se centra en hacer una única cosa:

```javascript
function getDoctorFromAppointmentList (doctorId) {

    return doctorList.find(it => it.id === appointment.doctor.id);
} 
```

</br>

#### 2.5. Las funciones deben ser pequeñas.

El motivo de esta es muy simple y es que nadie quiere leer una función que tiene, solo la función 500 líneas escritas y mucho menos llevar un control y debuggear por partes la función.

Por este motivo se recomienda que las funciones no excedan de las 25 líneas aproximadamente, para que no sean muy extensas y se entienda bien todo lo que figura en ellas.

Muy habitualmente un exceso en el número de líneas indica un incumplimiento en la regla anterior y una función está haciendo más de una única cosa.

</br>


#### 2.6. Intentar reducir los caracteres por línea.

Siguiendo con la parte que se ha comentado anteriormente nadie quiere tampoco leer una línea de los antiguos 140 carácteres de twitter y tener que hacer scroll para leer el nombre de una función o toda una línea de procesos.

Un ejemplo de lo que se debe evitar sería:

```javascript
const doctorWhoAttendedThisPatient = getDoctorBasedOnPatientAndLocationAndIfHeOrShePaidAndCouldAffordTheServiceOfBeingInTheHospital(patient).patient.doctor.id;
```
</br>

#### 2.7. Evitar utilizar comentarios.

Esta será polémica ya que mucha gente defiende el uso de los comentarios y está bien usarlos pero solo cuando son imprescindibles pero no para cada línea porque muchas veces acaban "guarreando" el código y haciendo que tengas menos ganas de leerlo. Además si hay mucho que explicar es porque hay algo que se está haciendo mal.

El propio código debería ser autoexplicativo y no debería requerir que yo deje comentarios de qué es cada cosa o como funciona. El objetivo del código es evitar el uso de comentarios porque no sean necesarios para entender el propio contexto del código.


<!-- #### 2.8. Utilizar mensajes descriptivos en commits. -->



<!-- #### 2.9. Aprender patrones de diseño. -->


</br>

<div style="position: absolute; right: 30px; height: 50px">
    <span style="float: left;"></span>
    <a style="float: right;" href="/contents/variables.md">Variables →</a>
</div>