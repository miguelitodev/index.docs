---
tags:
  - javascript
  - array
  - mutation
related:
  - "[[slice]]"
creation-date: "2025-08-26"
---

# `Array.prototype.splice()`

> [!WARNING] Mutation
> Este método modifica o array original.

> [!NOTE] Summary
> O método `splice()` altera o conteúdo de um array removendo, substituindo ou adicionando elementos. É um "canivete suíço" para manipulação de arrays.

## Syntax

```javascript
const removedElements = array.splice(start, deleteCount, item1, ..., itemN)
```
- `start`: O índice a partir do qual alterar o array.
- `deleteCount` (opcional): O número de elementos a serem removidos.
- `item1, ..., itemN` (opcional): Os elementos a serem adicionados ao array.

## Use Cases

- **Quando usar:** Para remover, adicionar ou substituir itens em qualquer ponto do array.
- **Exemplo:** Remover 2 itens a partir do índice 1 e adicionar um novo.
```javascript
const months = ['Jan', 'March', 'April', 'June'];
months.splice(1, 2, 'Feb');
console.log(months); // ["Jan", "Feb", "June"]
```
- **Cuidado:** Sua sintaxe é poderosa, mas pode ser complexa e levar a erros. Retorna um array com os elementos removidos, não o array modificado.

## See Also

- [[slice]]
- [[with]]

## References

- [MDN Web Docs: Array.prototype.splice()](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Global_Objects/Array/splice)