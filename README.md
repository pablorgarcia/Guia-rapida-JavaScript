# Guía rápida - JavaScript

## 9 Tipos de datos
Tipos primitivos
1. `Number` 
2. `String` 
3. `Boolean` 
4. `Null` es algo que no tiene valor
5. `Undefined` es algo que no está definido
6. `Bigint` 
7. `Symbol` 

Tipos no primitivos
1. `Object` 
2. `Function`

### Bug en JavaScript
`typeof null // Object (❌ y debería ser null)`

Para ver si algo responde null:
```
const foo = null
foo === null // true
```

## Operadores de comparación
1. `<` menor que
2. `>` mayor que
3. `==` igual
4. `===` igual, con tipado
5. `!==` diferente

## Operadores lógicos
1. `&&` y
2. `||` o
3. `!` no

## Function expression
Es una función que se declara dentro de una variable

`const sum = function() { return a + b }`

## Hosting
Es un término que se usa para describir cómo JavaScript parece que mueve las declaraciones funciones al principio del código, para que las puedas usar incluso antes de declararlas.

Aquí usamos la función y la declaramos luego. El Hosting "sube la función" (la guarda en memoria) antes de ejecutarla (hoisted)
```
sum(1, 2) // 3

function sum(a, b) { return a + b }
```

En cambio el Hosting no funciona con Function Expression porque JS no toma como definición una variable 
```
sum(1, 2) // ❌ ReferenceError: sum is not defined

const sum = function (a, b) { return a + b }
```

## Arrow function 
Las funciones flecha tienen varias ventajas sobre las funciones regulares en JavaScript. Algunas son:
- Sintaxis más concisa y más fácil de leer que la sintaxis de las funciones regulares, especialmente cuando se trabaja con funciones de una sola línea.
- Return implícito: las funciones flecha puede devolver el valor de la expresión sin usar la palabra clave return cuando son de una sola línea. Esto hace que sean aún más cortas y más fáciles de leer.
- Funciones anónimas más legibles: son una forma más legible y concisa lo cual puede hacer que nuestro código sea más fácil de entender.

Cuando tiene una sola expresión podemos omitir las llaves {} y no necesitaremos escribir return porque está implícito.
```
// Declaración de función regular
function sumar(a, b) {
  return a + b
}

// Función flecha
const sumarFlecha = (a, b) => {
  return a + b
}

// Función flecha con return implícito
const sumarFlecha = (a, b) => a + b
```

## Recursividad
Es una técnica de programación que consiste en que una función se llame a sí misma.
Para evitar crear un bucle infinito hay que añadir una condición base para salir del bucle al principio.
```
function cuentaAtras(numero) {
  // Condición base: Si el número que recibe es
  // menor de 0 entonces salimos de la función
  if (numero < 0) { return }

  // Si el número era mayor o igual a 0, lo mostramos
  console.log(numero)

  // Y llamamos a la función con el número anterior
  cuentaAtras(numero - 1)
}

cuentaAtras(3)
// -> 3
// -> 2
// -> 1
// -> 0
```
Otro ejemplo. Sacamos el número factorial. El factorial de un número es el resultado de multiplicar ese número por todos los anteriores hasta llegar a 1.
El factorial de 5 es 5 * 4 * 3 * 2 * 1 = 120
```
function factorial(n) {
  // Condición base: Si el número es 0 o 1, devolvemos 1
  // y no llamamos a la función de nuevo
  if (n === 0 || n === 1) {
    return 1
  } else {
    // Si el número es mayor que 1, llamamos a la función
    return n * factorial(n - 1)
  }
}

factorial(5) // Resultado: 120
factorial(3) // Resultado: 6
```

Otro ejemplo. Escribimos una función que calcule la suma de los primeros n números enteros de forma recursiva
```
function sumRecursive(n) {
  if (n === 0) {
    return 0
  } else {
    return n + sumRecursive(n - 1)
  }
}

sumRecursive(3) // 6
```

## Métodos de un Array
Cuando trabajamos con colecciones de elementos, vamos a querer hacer cosas con ellos. Por ejemplo: añadir un elemento, eliminarlo, buscarlo, etc. Para ello, los arrays tienen una serie de métodos que nos permiten hacer estas operaciones:

### push
Añade un elemento al final de un array
```
const frutas = ["plátano", "fresa"]
frutas.push("naranja")
console.log(frutas) // ["plátano", "fresa", "naranja"]
```
devuelve la nueva longitud del array:
```
const frutas = ["plátano", "fresa"]
console.log(frutas.length) // 2

const newLength = frutas.push("naranja")
console.log(newLength) // 3
console.log(frutas) // ["plátano", "fresa", "naranja"]
```

### pop
Elimina y devuelve el último elemento de un array:
```
const frutas = ["plátano", "fresa", "naranja"]
const ultimaFruta = frutas.pop()

console.log(frutas) // ["plátano", "fresa"]
console.log(ultimaFruta) // "naranja"
```

### shift
Elimina y devuelve el primer elemento de un array. Es lo mismo que `pop`, pero con el primer elemento en lugar del último:
```
const frutas = ["plátano", "fresa", "naranja"]
const primeraFruta = frutas.shift()

console.log(frutas) // ["fresa", "naranja"]
console.log(primeraFruta) // "plátano"
```

### unshift
Añade un elemento al principio de un array. Es lo mismo que `push`, pero con el primer elemento en lugar del último:
```
const frutas = ["plátano", "fresa", "naranja"]
frutas.unshift("manzana")

console.log(frutas) // ["manzana", "plátano", "fresa", "naranja"]
```

### concat
Nos va a devolver un nuevo array que va a concatenar el primer array con el segundo 
```
const numbers = [1, 2, 3]
const numbers2 = [4, 5]

const allNumbers = numbers.concat(numbers2)

console.log(allNumbers) // [1, 2, 3, 4, 5]
```
Otra forma de concatenar arrays es usando el operador `...` (spread operator). Este operador propaga los elementos de un array. Así que podríamos hacer lo siguiente:
```
const numbers = [1, 2, 3]
const numbers2 = [4, 5]

//                    1, 2, 3        4, 5                     
const allNumbers = [...numbers, ...numbers2]

console.log(allNumbers) // [1, 2, 3, 4, 5]
```

## Recorrer un Array

### Bucle while
Ejecuta un bloque de código mientras una condición era verdadera. En el caso de la iteración de arrays, la condición generalmente se basa en el índice del elemento.

Podemos, por ejemplo, crear una variable con `let` para guardar un puntero al índice del elemento que estamos iterando. En cada iteración, podemos incrementar el valor de la variable en 1, para que en la siguiente iteración se imprima el siguiente elemento.
```
let frutas = ['🍎', '🍌', '🍓']
let i = 0 // lo usaremos como índice

while (i < frutas.length) {
  console.log(frutas[i]) // imprime el elemento en la posición i
  i++ // incrementamos el índice en 1 para la siguiente iteración
}
```

### Bucle for
Ejecuta un bloque de código un número determinado de veces. En el caso de la iteración de arrays, podemos usarlo para recorrer cada uno de los elementos del array, usando la longitud del array como condición.
```
let frutas = ['🍎', '🍌', '🍓']

for (let i = 0; i < frutas.length; i++) {
  console.log(frutas[i]) // imprime el elemento en la posición i
}
```
También podrías recorrer el array en orden inverso, empezando desde el último elemento hasta el primero, usando i-- en lugar de i++.
```
let frutas = ['🍎', '🍌', '🍓']

for (let i = frutas.length - 1; i >= 0; i--) {
  console.log(frutas[i]) // imprime el elemento en la posición i
}
```

### Bucle for...of
Esta estructura de control es más simple que for, ya que no necesitamos crear una variable para guardar el índice del elemento que estamos iterando.

Es más fácil de usar cuando solo necesitas los valores de un array y no te importa el índice. Es especialmente útil también cuando estás trabajando con iterables que no son arrays, como las cadenas de caracteres o los conjuntos (sets).

Hay algunas limitaciones, por ejemplo, no podemos usarlo para recorrer un array en orden inverso y tampoco tenemos acceso al índice del elemento que estamos iterando.
```
let frutas = ['🍎', '🍌', '🍓']

for (let fruta of frutas) {
  console.log(fruta) // imprime el elemento en la posición i
}
```

### El método array.forEach()
Permite ejecutar una function para cada uno de los elementos del array. Esta función recibe como parámetros el elemento que se está iterando en ese momento, el índice del elemento y el propio array.
`forEach` es una forma muy eficiente y legible de iterar sobre un array si no necesitas `break` y si no necesitas controlar manualmente el índice.
Importante: no devuelve nada, por lo que no podemos asignar el resultado a una variable.
```
let frutas = ['🍎', '🍌', '🍓']

frutas.forEach(function (fruta, index, originalArray) {
  console.log(fruta) // imprime el elemento en la posición i
})
```
Usando una arrow function e indicando sólo los parámetros que necesitamos de nuestra función podemos simplificarlo aún más:
```
let frutas = ['🍎', '🍌', '🍓']

frutas.forEach((fruta) => {
  console.log(fruta) // imprime el elemento en la posición i
})
```

## Búsqueda en Arrays con sus métodos

### indexOf ¿En qué posición está el elemento?
Encuentra la posición de un elemento dentro de un array. Si el elemento no existe, entonces retorna -1.
```
const emojis = ['✨', '🥑', '😍']

const posicionCorazon = emojis.indexOf('😍')

console.log(posicionCorazon) // -> 2
```

### includes
Determina si un array incluye un determinado elemento, devolviendo true o false según corresponda.
Es la forma más sencilla y corta de buscar un elemento específico. Sin embargo, si queremos revisar si un array contiene un elemento que cumpla con una condición, entonces tenemos que utilizar otros métodos.
También funciona con las cadenas de texto. Puedes utilizarlo para buscar una subcadena dentro de una cadena de texto: `'Hola mundo'.includes('Hola') // -> true`
```
const emojis = ['✨', '🥑', '😍']

const tieneCorazon = emojis.includes('😍')

console.log(tieneCorazon) // -> true
```

### some ¿Alguno de los elementos cumple con la condición?
Verifica si al menos uno de los elementos de un array cumple con una condición.

Se le pasas una función como argumento. Esta función recibe como argumento cada uno de los elementos del array y debe retornar un valor booleano.

Si al menos uno de los elementos retorna true, entonces el método some retorna true. Si ninguno de los elementos retorna true, entonces el método some retorna false.
```
const emojis = ['✨', '🥑', '😍']

const tieneCorazon = emojis.some(emoji => emoji === '😍')
console.log(tieneCorazon) // -> true
```
Esto ya lo podíamos hacer con `includes` Sí, pero `some` es mucho más potente

Podemos crear una función que verifique si un array contiene un elemento que sea un string de más de 3 caracteres.
```
const names = ['Leo', 'Isa', 'Ían', 'Lea']

const tieneNombreLargo = names.some(name => name.length > 3)
console.log(tieneNombreLargo) // -> false
```
Importante: Deja de iterar sobre el array en cuanto encuentra un elemento que cumple con la condición. Por ejemplo, si tenemos un array de 10 elementos y el elemento número 3 cumple con la condición, el método `some` no va a iterar sobre los 7 elementos restantes:
```
const numbers = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]

const tieneNumeroMayorA5 = numbers.some(number => {
  console.log(`Estoy iterando sobre el número ${number}`) // -> Imprime hasta el número 6
  return number > 5
})

console.log(tieneNumeroMayorA5) // -> true
```

### every ¿Todos los elementos cumplen con la condición?
Verifica si todos los elementos de un array cumplen con una condición. Es similar a `some`, pero en lugar de verificar si al menos uno de los elementos cumple con la condición, los verifica todos.

Para utilizarlo, le pasas una función como argumento. Esta función recibe como argumento el elemento del array que está iterando en ese momento y debe retornar un valor booleano para saber si el elemento cumple con la condición.

Si todos los elementos retornan true, entonces el método every retorna true. Si al menos uno de los elementos retorna false, entonces el método every retorna false.
```
// ¿Todos los emojis son felices?
const emojis = ['😀', '😂', '😍', '😭', '🥺', '😎']
const todosSonFelices = emojis.every(emoji => emoji === '😀')
console.log(todosSonFelices) // -> false

// ¿Todos los números son pares?
const numbers = [2, 4, 7, 10, 12]
const todosSonPares = numbers.every(number => number % 2 === 0)
console.log(todosSonPares) // -> false

// ¿Todos los strings son mayores a 3 caracteres?
const names = ['Miguel', 'Juan', 'Itziar', 'Isabel']
const todosLosNombresSonLargos = names.every(name => name.length > 3)
console.log(todosLosNombresSonLargos) // -> true
```
Al igual que `some`, el método every deja de iterar sobre el Array en cuanto encuentra un elemento que no cumple con la condición.


### find devuelve el primer elemento que cumple con la condición
Encuentra el primer elemento que cumple con una condición. Lo interesante es que este método te devuelve el elemento en sí, no un valor booleano como some y every. Aunque el funcionamiento es igual: hay que pasarle una función como argumento que retorne un valor booleano.
```
const numbers = [13, 27, 44, -10, 81]
// encuentra el primer número negativo
const firstNegativeNumber = numbers.find(number => number < 0)

console.log(firstNegativeNumber) // -> -10
```
Si no encuentra ningún elemento que cumpla con la condición, el método find retorna undefined.
```
const numbers = [13, 27, 44, 81]
// encuentra el primer número negativo
const firstNegativeNumber = numbers.find(number => number < 0)

console.log(firstNegativeNumber) // -> undefined
```
Igual que `some` y `every`, el método `find` deja de iterar sobre el array en cuanto encuentra un elemento que cumple con la condición.

### findIndex devuelve el índice del primer elemento que cumple con la condición
Es similar a `find`, pero en lugar de devolver el elemento que cumple con la condición, devuelve el índice de ese elemento.
```
const numbers = [13, 27, 44, -10, 81]

// encuentra el índice del primer número negativo
const firstNegativeNumberIndex = numbers.findIndex(number => number < 0)

console.log(firstNegativeNumberIndex) // -> 3

// ahora puedes usar el índice para acceder al elemento
console.log(numbers[firstNegativeNumberIndex]) // -> -10
```
Si no encuentra ningún elemento que cumpla con la condición, el método `findIndex` retorna -1.
```
const numbers = [13, 27, 44, 81]

// encuentra el índice del primer número negativo
const firstNegativeNumberIndex = numbers.findIndex(number => number < 0)

console.log(firstNegativeNumberIndex) // -> -1
```


