---
tags:
  - javascript
  - array
  - mutation
related:
  - "[[push]]"
  - "[[shift]]"
creation-date: "2025-08-26"
---

# `Array.prototype.pop()`

> [!WARNING] Mutation
> Este método modifica o array original.

> [!NOTE] Summary
> O método `pop()` remove o **último** elemento de um array e retorna aquele elemento. Este método altera o comprimento do array.

## Syntax

```javascript
const removedElement = array.pop()
```

## Use Cases

- **Quando usar:** Para implementar uma estrutura de pilha (LIFO - Last-In, First-Out) ou para remover o último item adicionado.
- **Exemplo:** Desfazer a última ação.
```javascript
const actions = ['draw', 'paint', 'erase'];
const lastAction = actions.pop();
console.log(lastAction); // 'erase'
console.log(actions); // ['draw', 'paint']
```
- **Cuidado:** Retorna `undefined` se o array estiver vazio.

## See Also

- [[push]]
- [[shift]]

## References

- [MDN Web Docs: Array.prototype.pop()](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Global_Objects/Array/pop)