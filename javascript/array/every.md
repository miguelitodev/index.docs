---
tags:
  - javascript
  - array
  - validation
related:
  - "[[some]]"
creation-date: "2025-08-26"
---

# `Array.prototype.every()`

> [!NOTE] Summary
> O método `every()` testa se **todos** os elementos no array passam no teste implementado pela função fornecida. Ele para a execução assim que encontra um resultado `false`.

## Syntax

```javascript
const result = array.every(callback(element, index, array), thisArg)
```
- `callback`: Função que testa cada elemento.

## Use Cases

- **Quando usar:** Para validar se todos os itens de um array seguem uma regra específica.
- **Exemplo:** Validar se todos os números em um array são positivos.
```javascript
const numbers = [1, 5, 8, 12];
const allPositive = numbers.every(num => num > 0); // true
```

## See Also

- [[some]]

## References

- [MDN Web Docs: Array.prototype.every()](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Global_Objects/Array/every)