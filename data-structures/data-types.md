## Primitivos

São muito simples, usamos diariamente, não são objetos e muito menos possuem métodos.

Exemplos: `numbers`, `string`, `boolean`, `null`, `undefined`, `symbols`

Mas `strings`, não tem métodos? Sim, mas é uma conversão que o Javascript faz de **strings primitivas** -> **objetos string**, ai se torna possível utilizar métodos.

Quando declaramos um tipo de dado primitivo, ele vai ser armazenado na memória Stack, a famosa pilha, e lá ele vai ser identificado pelo nome da variável que tu declarou. Idenpendente se eu declaro várias com o mesmo valor, para cada variável, ou melhor, para cada dado primitivo que eu for utilizar, ele vai utilizar um espaço individual na stack. E como cada um tem seu espaço na pilha, se eu alterar o valor

## Bibliografia
- [Primitive vs Reference Data Types in JavaScript](https://www.freecodecamp.org/news/primitive-vs-reference-data-types-in-javascript/)
- 