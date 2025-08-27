---
tags:
  - javascript
  - array
  - search
related:
  - "[[filter]]"
  - "[[findIndex]]"
  - "[[some]]"
creation-date: "2025-08-26"
---

# `Array.prototype.find()`

> [!NOTE] Summary
> O método `find()` retorna o **valor do primeiro elemento** no array que satisfaz a função de teste fornecida. Se nenhum valor satisfizer a função de teste, `undefined` é retornado.

## Syntax

```javascript
const found = array.find(callback(element, index, array), thisArg)
```
- `callback`: Função para executar em cada valor do array.

## Use Cases

- **Quando usar:** Para encontrar um objeto específico em um array baseado em uma de suas propriedades.
- **Exemplo:** Encontrar um usuário pelo seu ID.
```javascript
const users = [{ id: 1, name: 'Alice' }, { id: 2, name: 'Bob' }];
const user = users.find(u => u.id === 2); // { id: 2, name: 'Bob' }
```
- **Cuidado:** Retorna o elemento em si, não sua posição. Se precisar do índice, use `findIndex()`.

## See Also

- [[findIndex]]
- [[filter]]

## References

- [MDN Web Docs: Array.prototype.find()](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Global_Objects/Array/find)