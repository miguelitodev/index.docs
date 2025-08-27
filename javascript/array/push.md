---
tags:
  - javascript
  - array
  - mutation
related:
  - "[[pop]]"
  - "[[unshift]]"
  - "[[concat]]"
creation-date: "2025-08-26"
---

# `Array.prototype.push()`

> [!WARNING] Mutation
> Este método modifica o array original.

> [!NOTE] Summary
> O método `push()` adiciona um ou mais elementos ao **final** de um array e retorna o novo comprimento do array.

## Syntax

```javascript
const newLength = array.push(element1, ..., elementN)
```

## Use Cases

- **Quando usar:** É a forma mais comum e eficiente de adicionar um item no final de uma lista.
- **Exemplo:** Adicionar um novo item a uma lista de tarefas.
```javascript
const tasks = ['Lavar a louça'];
const count = tasks.push('Tirar o lixo');
console.log(count); // 2
console.log(tasks); // ['Lavar a louça', 'Tirar o lixo']
```

## See Also

- [[pop]]
- [[unshift]]

## References

- [MDN Web Docs: Array.prototype.push()](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Global_Objects/Array/push)