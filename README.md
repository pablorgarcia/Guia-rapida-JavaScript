# Guia-rapida-para-JavaScript

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
`typeof null // Object (y debería ser null)`

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
Por ejemplo, el factorial de 5 es 5 * 4 * 3 * 2 * 1 = 120
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

Otro ejemplo:
```
function recursive(n) {
  if (n === 0) {
    return 0
  } else {
    return n + recursive(n - 1)
  }
}

recursive(3) // 6
```
