---
tags:
  - javascript
  - array
  - search
related:
  - "[[findIndex]]"
  - "[[includes]]"
creation-date: "2025-08-26"
---

# `Array.prototype.indexOf()`

> [!NOTE] Summary
> O método `indexOf()` retorna o primeiro índice no qual um determinado elemento pode ser encontrado no array, ou -1 se não estiver presente. A busca é feita com comparação estrita (`===`).

## Syntax

```javascript
const index = array.indexOf(searchElement, fromIndex)
```
- `searchElement`: Elemento a ser localizado no array.
- `fromIndex` (opcional): O índice a partir do qual iniciar a busca.

## Use Cases

- **Quando usar:** Para encontrar a posição de valores primitivos (string, número, booleano).
- **Exemplo:** Verificar se um item existe e obter sua posição.
```javascript
const beasts = ['ant', 'bison', 'camel', 'duck', 'bison'];
console.log(beasts.indexOf('bison')); // 1
```
- **Cuidado:** Não funciona para objetos, arrays ou outras estruturas complexas, pois compara por referência, não por valor. Use `findIndex()` para esses casos.

## See Also

- [[findIndex]]
- [[includes]]

## References

- [MDN Web Docs: Array.prototype.indexOf()](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Global_Objects/Array/indexOf)