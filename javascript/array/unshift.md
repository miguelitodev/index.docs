---
tags:
  - javascript
  - array
  - mutation
related:
  - "[[shift]]"
  - "[[push]]"
creation-date: "2025-08-26"
---

# `Array.prototype.unshift()`

> [!WARNING] Mutation
> Este método modifica o array original.

> [!NOTE] Summary
> O método `unshift()` adiciona um ou mais elementos ao **início** de um array e retorna o novo comprimento do array.

## Syntax

```javascript
const newLength = array.unshift(element1, ..., elementN)
```

## Use Cases

- **Quando usar:** Para adicionar um item com alta prioridade no topo de uma lista.
- **Exemplo:** Adicionar uma tarefa urgente no início da lista.
```javascript
const tasks = ['Comprar pão', 'Pagar contas'];
tasks.unshift('Ligar para o médico - URGENTE');
console.log(tasks); // ['Ligar para o médico - URGENTE', 'Comprar pão', 'Pagar contas']
```
- **Cuidado:** Assim como `shift()`, é uma operação lenta (complexidade O(n)) em arrays grandes.

## See Also

- [[shift]]
- [[push]]

## References

- [MDN Web Docs: Array.prototype.unshift()](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Global_Objects/Array/unshift)