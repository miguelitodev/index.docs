---
tags:
  - javascript
  - array
  - transformation
  - aggregation
related:
  - "[[map]]"
  - "[[filter]]"
creation-date: "2025-08-26"
---

# `Array.prototype.reduce()`

> [!NOTE] Summary
> O método `reduce()` executa uma função "redutora" em cada elemento do array, resultando em um único valor de saída. É um dos métodos mais poderosos e versáteis de array.


## Syntax

```javascript
const result = array.reduce(callback(accumulator, currentValue, index, array), initialValue)
```
- `accumulator`: O valor acumulado. Em cada chamada, é o valor retornado pela chamada anterior.
- `currentValue`: O elemento atual sendo processado.
- `initialValue` (opcional): Um valor para ser usado como o primeiro `accumulator`.

## Use Cases

- **Quando usar:** Para "resumir" um array em um único valor (soma, média) ou para agrupar itens de forma complexa.
- **Exemplo:** Somar todos os valores de um array.
```javascript
const numbers = [1, 2, 3, 4];
const sum = numbers.reduce((acc, current) => acc + current, 0); // 10
```
- **Cuidado:** Pode ser difícil de ler se a lógica do redutor for complexa. Para transformações simples, `map` ou `filter` são mais claros.

## See Also

- [[map]]
- [[filter]]

## References

- [MDN Web Docs: Array.prototype.reduce()](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Global_Objects/Array/reduce)