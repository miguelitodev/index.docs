---
tags:
  - javascript
  - array
  - mutation
related:
  - "[[toReversed]]"
creation-date: "2025-08-26"
---

# `Array.prototype.reverse()`

> [!WARNING] Mutation
> Este método modifica o array original.

> [!NOTE] Summary
> O método `reverse()` inverte a ordem dos elementos de um array. O primeiro elemento se torna o último, e o último, o primeiro.

## Syntax

```javascript
array.reverse()
```

## Use Cases

- **Quando usar:** Para inverter a ordem de uma lista, como uma lista de comentários para mostrar os mais recentes primeiro.
- **Exemplo:**
```javascript
const numbers = [1, 2, 3, 4, 5];
numbers.reverse();
console.log(numbers); // [5, 4, 3, 2, 1]
```

## See Also

- [[toReversed]]

## References

- [MDN Web Docs: Array.prototype.reverse()](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Global_Objects/Array/reverse)