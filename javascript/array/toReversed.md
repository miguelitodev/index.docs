---
tags:
  - javascript
  - array
  - immutability
related:
  - "[[reverse]]"
creation-date: "2025-08-26"
---

# `Array.prototype.toReversed()`

> [!TIP] Immutability
> Este método retorna uma cópia do array e não modifica o original.

> [!NOTE] Summary
> O método `toReversed()` é a versão imutável do método `reverse()`. Ele retorna um novo array com os elementos em ordem invertida.

## Syntax

```javascript
const reversed_array = array.toReversed()
```

## Use Cases

- **Quando usar:** Para obter uma versão invertida de um array sem modificar o original.
- **Exemplo:**
```javascript
const numbers = [1, 2, 3, 4, 5];
const reversedCopy = numbers.toReversed();
console.log(numbers); // [1, 2, 3, 4, 5]
console.log(reversedCopy); // [5, 4, 3, 2, 1]
```
- **Cuidado:** É um método novo (ES2023), verifique a compatibilidade.

## See Also

- [[reverse]]

## References

- [MDN Web Docs: Array.prototype.toReversed()](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Global_Objects/Array/toReversed)