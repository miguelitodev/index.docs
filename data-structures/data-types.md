## Primitivos

São muito simples, usamos diariamente, não são objetos e muito menos possuem métodos.

Exemplos: `numbers`, `string`, `boolean`, `null`, `undefined`, `symbols`

Mas `strings`, não tem métodos? Sim, mas é uma conversão que o Javascript faz de **strings primitivas** -> **objetos string**, ai se torna possível utilizar métodos.

Quando declaramos um tipo de dado primitivo, ele vai ser armazenado na memória Stack, a famosa pilha, e lá ele vai ser identificado pelo nome da variável que tu declarou. Idenpendente se eu declaro várias com o mesmo valor, para cada variável, ou melhor, para cada dado primitivo que eu for utilizar, ele vai utilizar um espaço individual na stack. E como cada um tem seu espaço na pilha, se eu alterar o valor de um, não vai alterar o valor do outro.

```js
let numOne = 50;
let numTwo = numOne; // numTwo -> numOne -> 50

numOne = 100;

console.log(numOne); // outputs 100
console.log(numTwo); // outputs 50
```

![[stack.png]]

## Referência
Diferente dos dados primitivos, os de referência são fixos por natureza, ou seja, não tem tamanho fixo. E a maioria é considerada um Objeto, então possuem métodos.

Exemplos: `Objects`, `Functions`, `Collections`, `Arrays`, `Dates`, etc..

A principal diferença é que quando você declara esse tipo de dado, o computador não vai armazenar diretamente aquela informação, ele armazena a referência daquele valor, basicamente cria um ponteiro apontando para aquela informação.

![[Pasted image 20250820070242.png]]

## Bibliografia
- [Primitive vs Reference Data Types in JavaScript](https://www.freecodecamp.org/news/primitive-vs-reference-data-types-in-javascript/)
- 