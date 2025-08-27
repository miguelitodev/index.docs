---
tags:
  - javascript
  - array
  - mutation
  - sort
related:
  - "[[toSorted]]"
creation-date: "2025-08-26"
---

# `Array.prototype.sort()`

> [!WARNING] Mutation
> Este método modifica o array original.

> [!NOTE] Summary
> O método `sort()` ordena os elementos do próprio array e retorna o array ordenado. A ordenação padrão é ascendente, convertendo os elementos em strings e comparando suas sequências de valores de unidades de código UTF-16.

## Syntax

```javascript
array.sort(compareFunction)
```
- `compareFunction` (opcional): Uma função que define a ordem de ordenação. Se omitida, o array é ordenado com base na conversão de cada elemento para string.

## Use Cases

- **Quando usar:** Para ordenar uma lista de itens no lugar (modificando o array original).
- **Exemplo:** Ordenar um array de números.
```javascript
const numbers = [4, 2, 5, 1, 3];
numbers.sort((a, b) => a - b); // Força a ordenação numérica
console.log(numbers); // [1, 2, 3, 4, 5]
```
- **Cuidado:** A ordenação padrão pode não ser o que você espera para números (`[1, 10, 2]` se torna `[1, 10, 2]`). **Sempre** forneça uma função de comparação ao ordenar números.

## See Also

- [[toSorted]]

## References

- [MDN Web Docs: Array.prototype.sort()](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Global_Objects/Array/sort)