---
tags:
  - javascript
  - array
  - search
related:
  - "[[some]]"
  - "[[indexOf]]"
creation-date: "2025-08-26"
---

# `Array.prototype.includes()`

> [!NOTE] Summary
> O método `includes()` determina se um array contém um determinado elemento, retornando `true` ou `false`. É mais intuitivo que `indexOf()` para checagens de existência.

## Syntax

```javascript
const hasElement = array.includes(valueToFind, fromIndex)
```

## Use Cases

- **Quando usar:** Para uma verificação simples e legível de existência, sem se importar com a posição.
- **Exemplo:** Checar se um usuário tem uma determinada permissão.
```javascript
const permissions = ['read', 'write', 'delete'];
const canWrite = permissions.includes('write'); // true
```
- **Cuidado:** Também compara por referência para objetos. Uma vantagem sobre `indexOf` é que `includes` consegue encontrar `NaN` em um array.

## See Also

- [[some]]
- [[indexOf]]

## References

- [MDN Web Docs: Array.prototype.includes()](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Global_Objects/Array/includes)