---
tags:
  - javascript
  - array
  - selection
related:
  - "[[map]]"
  - "[[reduce]]"
  - "[[find]]"
creation-date: "2025-08-26"
---

# `Array.prototype.filter()`

> [!NOTE] Summary
> O método `filter()` cria um **novo** array com todos os elementos que passam no teste implementado pela função de callback fornecida. É uma forma declarativa e imutável de selecionar dados.

## Syntax

```javascript
const new_array = array.filter(callback(element, index, array), thisArg)
```
- `callback`: Função para testar cada elemento do array. Retorna `true` para manter o elemento, `false` caso contrário.

## Use Cases

- **Quando usar:** Para selecionar um subconjunto de elementos de um array que atendem a um critério específico.
- **Exemplo:** Filtrar apenas os números pares de um array.
```javascript
const numbers = [1, 2, 3, 4, 5, 6];
const evens = numbers.filter(num => num % 2 === 0); // [2, 4, 6]
```
- **Cuidado:** Se você precisa apenas encontrar o *primeiro* elemento que corresponde à condição, `find()` é mais performático.

## See Also

- [[map]]
- [[find]]
- [[some]]

## References

- [MDN Web Docs: Array.prototype.filter()](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Global_Objects/Array/filter)