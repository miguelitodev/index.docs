---
tags:
  - javascript
  - array
  - immutability
  - transformation
related:
  - "[[flatMap]]"
creation-date: "2025-08-26"
---

# `Array.prototype.flat()`

> [!TIP] Immutability
> Este método retorna um novo array e não modifica o original.

> [!NOTE] Summary
> O método `flat()` cria um novo array com todos os elementos de sub-arrays concatenados nele recursivamente até uma profundidade especificada.

## Syntax

```javascript
const new_array = array.flat(depth)
```
- `depth` (opcional): O nível de profundidade que especifica o quão aninhado o array deve ser "achatado". O padrão é 1.

## Use Cases

- **Quando usar:** Para simplificar um array de arrays em um único array.
- **Exemplo:** Achatar um array de resultados que vêm em blocos.
```javascript
const arr1 = [1, 2, [3, 4]];
console.log(arr1.flat()); // [1, 2, 3, 4]

const arr2 = [1, 2, [3, 4, [5, 6]]];
console.log(arr2.flat(2)); // [1, 2, 3, 4, 5, 6]
```
- **Dica:** Use `Infinity` como profundidade para achatar todos os níveis: `arr.flat(Infinity)`.

## See Also

- [[flatMap]]

## References

- [MDN Web Docs: Array.prototype.flat()](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Global_Objects/Array/flat)