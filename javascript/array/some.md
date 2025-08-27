---
tags:
  - javascript
  - array
  - validation
related:
  - "[[every]]"
  - "[[find]]"
  - "[[includes]]"
creation-date: "2025-08-26"
---

# `Array.prototype.some()`

> [!NOTE] Summary
> O método `some()` testa se **pelo menos um** elemento no array passa no teste implementado pela função fornecida. Ele para a execução assim que encontra um resultado `true`.

## Syntax

```javascript
const result = array.some(callback(element, index, array), thisArg)
```
- `callback`: Função que testa cada elemento.

## Use Cases

- **Quando usar:** Para verificar de forma eficiente se um item que satisfaz uma condição existe no array.
- **Exemplo:** Checar se há algum número negativo em uma lista.
```javascript
const numbers = [1, 5, -3, 8];
const hasNegative = numbers.some(num => num < 0); // true
```
- **Cuidado:** Não informa *qual* ou *quantos* itens passaram no teste, apenas se algum passou.

## See Also

- [[every]]
- [[includes]]

## References

- [MDN Web Docs: Array.prototype.some()](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Global_Objects/Array/some)