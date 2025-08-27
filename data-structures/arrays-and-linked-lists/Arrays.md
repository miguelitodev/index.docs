---
tags:
  - array
  - javascript
  - index
related:
  - "[[data-structures/complexity-and-memory/big-o-notation]]"
creation-date: "2025-08-26"
---

# Métodos de Array em JavaScript

> [!NOTE] Summary
> Esta é uma nota de índice. Arrays em JavaScript são objetos de protótipo com um vasto conjunto de métodos para iteração, mutação e manipulação de dados. Cada método listado abaixo tem sua própria nota detalhada.

## Índice de Métodos

### Iteração e Transformação

- [[javascript/array/forEach|forEach()]]: Executa uma função para cada elemento.
- [[javascript/array/map|map()]]: Cria um novo array transformando cada elemento.
- [[javascript/array/filter|filter()]]: Cria um novo array com elementos que passam em um teste.
- [[javascript/array/reduce|reduce()]]: Reduz o array a um único valor.
- [[javascript/array/some|some()]]: Testa se pelo menos um elemento passa no teste.
- [[javascript/array/every|every()]]: Testa se todos os elementos passam no teste.

### Busca e Localização

- [[javascript/array/find|find()]]: Retorna o primeiro elemento que passa no teste.
- [[javascript/array/findIndex|findIndex()]]: Retorna o índice do primeiro elemento que passa no teste.
- [[javascript/array/indexOf|indexOf()]]: Retorna o primeiro índice de um valor.
- [[javascript/array/includes|includes()]]: Verifica se o array contém um valor.
- [[javascript/array/at|at()]]: Acessa um elemento por índice (inclusive negativos).

### Adição e Remoção (Mutação)

> [!WARNING]
> Os métodos a seguir modificam o array original.

- [[javascript/array/push|push()]]: Adiciona elementos no final.
- [[javascript/array/pop|pop()]]: Remove o elemento do final.
- [[javascript/array/shift|shift()]]: Remove o elemento do início.
- [[javascript/array/unshift|unshift()]]: Adiciona elementos no início.
- [[javascript/array/splice|splice()]]: Remove, substitui ou adiciona elementos em qualquer posição.

### Cópia e Imutabilidade

- [[javascript/array/slice|slice()]]: Retorna uma cópia superficial de uma porção do array.
- [[javascript/array/concat|concat()]]: Junta arrays, retornando um novo.
- [[javascript/array/flat|flat()]]: "Achata" um array de arrays.
- [[javascript/array/with|with()]]: Retorna uma cópia do array com um valor substituído em um índice.

### Ordenação e Inversão

- [[javascript/array/sort|sort()]]: Ordena o array (muta o original).
- [[javascript/array/toSorted|toSorted()]]: Retorna uma cópia ordenada do array.
- [[javascript/array/reverse|reverse()]]: Inverte o array (muta o original).
- [[javascript/array/toReversed|toReversed()]]: Retorna uma cópia invertida do array.

### Conversão e Criação (Estáticos)

- [[javascript/array/join|join()]]: Junta os elementos de um array em uma string.
- [[javascript/array/Array.from|Array.from()]]: Cria um array a partir de um objeto "array-like".
- [[javascript/array/Array.of|Array.of()]]: Cria um array a partir de argumentos.

## See Also

- [[data-structures/complexity-and-memory/big-o-notation]]