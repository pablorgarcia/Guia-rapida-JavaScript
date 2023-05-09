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
1. Objectos
2. Funciones

### Bug en JavaScript
`
typeof null // Object
`
Para ver si algo responde null:
`
const foo = null
foo === null // true
`

## Operadores de comparación
`<` menor que
`>` mayor que
`==` igual
`===` igual, con tipado
`!==` diferente

## Operadores lógicos
`&&` y
`||` o
`!` no

## Function expression
Es una función que se declara dentro de una variable
`
const sum = function() { return a + b }
`

## Hosting
Es un término que se usa para describir cómo JavaScript parece que mueve las declaraciones funciones al principio del código, para que las puedas usar incluso antes de declararlas.

Aquí usamos la función y la declaramos luego. El Hosting "sube la función" (la guarda en memoria) antes de ejecutarla (hoisted)
`
sum(1, 2) // 3

function sum(a, b) { return a + b }
`

En cambio el Hosting no funciona con Function Expression porque JS no toma como definición una variable 
`
sum(1, 2) // ❌ ReferenceError: sum is not defined

const sum = function (a, b) { return a + b }
`

## Arrow function 
Las funciones flecha tienen varias ventajas sobre las funciones regulares en JavaScript. Algunas son:
- Sintaxis más concisa y más fácil de leer que la sintaxis de las funciones regulares, especialmente cuando se trabaja con funciones de una sola línea.
- Return implícito: las funciones flecha puede devolver el valor de la expresión sin usar la palabra clave return cuando son de una sola línea. Esto hace que sean aún más cortas y más fáciles de leer.
- Funciones anónimas más legibles: son una forma más legible y concisa lo cual puede hacer que nuestro código sea más fácil de entender.

Cuando tiene una sola expresión podemos omitir las llaves {} y no necesitaremos escribir return porque está implícito.
`
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
`


