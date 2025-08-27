---
tags:
  - javascript
  - array
  - immutability
  - sort
related:
  - "[[sort]]"
creation-date: "2025-08-26"
---

# `Array.prototype.toSorted()`

> [!TIP] Immutability
> Este método retorna uma cópia do array e não modifica o original.

> [!NOTE] Summary
> O método `toSorted()` é a versão imutável do método `sort()`. Ele retorna um novo array com os elementos ordenados em ordem ascendente, sem modificar o array original.

## Syntax

```javascript
const sorted_array = array.toSorted(compareFunction)
```

## Use Cases

- **Quando usar:** Para ordenar um array quando a imutabilidade é importante, como em estados de aplicações React.
- **Exemplo:** Ordenar uma lista de produtos sem alterar a lista original.
```javascript
const products = [
  { name: 'Laptop', price: 1200 },
  { name: 'Mouse', price: 25 },
  { name: 'Keyboard', price: 100 },
];
const sortedByPrice = products.toSorted((a, b) => a.price - b.price);
// products permanece inalterado
```
- **Cuidado:** É um método novo (ES2023), verifique a compatibilidade.

## See Also

- [[sort]]

## References

- [MDN Web Docs: Array.prototype.toSorted()](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Global_Objects/Array/toSorted)