---
tags:
  - javascript
  - array
  - iteration
related:
  - "[[map]]"
  - "[[filter]]"
creation-date: "2025-08-26"
---

# `Array.prototype.forEach()`

> [!NOTE] Summary
> O método `forEach()` executa uma função (um "callback") uma vez para cada elemento do array. É usado principalmente para executar "efeitos colaterais" (como logs ou atualizações de UI) e não retorna nenhum valor (`undefined`).

## Syntax

```javascript
array.forEach(callback(element, index, array), thisArg)
```
- `callback`: A função a ser executada para cada elemento.
- `element`: O valor do elemento atual.
- `index` (opcional): O índice do elemento atual.
- `array` (opcional): O array no qual `forEach()` foi chamado.
- `thisArg` (opcional): Valor a ser usado como `this` ao executar o callback.

## Use Cases

- **Quando usar:** Para executar uma operação em cada item de um array quando você não precisa criar um novo array.
- **Exemplo:** Imprimir cada item de uma lista no console.
```javascript
const items = ['item1', 'item2', 'item3'];
items.forEach(item => console.log(item));
```
- **Quando não usar:** Não use `forEach` se você precisa de um novo array com os resultados (use `map`). Ele não pode ser interrompido (com `break` ou `return`); ele sempre percorrerá todos os elementos.

## See Also

- [[map]]
- [[filter]]
- [[reduce]]

## References

- [MDN Web Docs: Array.prototype.forEach()](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Global_Objects/Array/forEach)