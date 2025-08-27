---
tags:
  - javascript
  - array
  - mutation
related:
  - "[[unshift]]"
  - "[[pop]]"
creation-date: "2025-08-26"
---

# `Array.prototype.shift()`

> [!WARNING] Mutation
> Este método modifica o array original.

> [!NOTE] Summary
> O método `shift()` remove o **primeiro** elemento de um array e retorna esse elemento. Este método altera o comprimento do array.

## Syntax

```javascript
const removedElement = array.shift()
```

## Use Cases

- **Quando usar:** Para implementar uma estrutura de fila (FIFO - First-In, First-Out), processando o primeiro item da lista.
- **Exemplo:** Atender o próximo cliente de uma fila.
```javascript
const queue = ['Cliente A', 'Cliente B', 'Cliente C'];
const nextInLine = queue.shift();
console.log(nextInLine); // 'Cliente A'
console.log(queue); // ['Cliente B', 'Cliente C']
```
- **Cuidado:** É uma operação lenta (complexidade O(n)) em arrays grandes, pois todos os elementos restantes precisam ser re-indexados.

## See Also

- [[unshift]]
- [[pop]]

## References

- [MDN Web Docs: Array.prototype.shift()](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Global_Objects/Array/shift)