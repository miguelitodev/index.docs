---
tags:
  - javascript
  - array
  - search
related:
  - "[[find]]"
  - "[[indexOf]]"
creation-date: "2025-08-26"
---

# `Array.prototype.findIndex()`

> [!NOTE] Summary
> O método `findIndex()` retorna o **índice do primeiro elemento** no array que satisfaz a função de teste fornecida. Caso contrário, retorna -1, indicando que nenhum elemento passou no teste.

## Syntax

```javascript
const index = array.findIndex(callback(element, index, array), thisArg)
```

## Use Cases

- **Quando usar:** Quando você precisa da posição de um item para depois modificá-lo ou removê-lo (com `splice`, por exemplo).
- **Exemplo:** Encontrar o índice de um usuário para poder removê-lo.
```javascript
const users = [{ id: 1, name: 'Alice' }, { id: 2, name: 'Bob' }];
const index = users.findIndex(u => u.id === 1);
if (index !== -1) {
  users.splice(index, 1);
}
// users is now [{ id: 2, name: 'Bob' }]
```

## See Also

- [[find]]
- [[indexOf]]

## References

- [MDN Web Docs: Array.prototype.findIndex()](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Global_Objects/Array/findIndex)