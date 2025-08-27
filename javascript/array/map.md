---
tags:
  - javascript
  - array
  - transformation
related:
  - "[[filter]]"
  - "[[reduce]]"
  - "[[forEach]]"
creation-date: "2025-08-26"
---

# `Array.prototype.map()`

> [!NOTE] Summary
> O método `map()` cria um **novo** array populado com os resultados da chamada de uma função de callback em cada elemento do array original. Ele é fundamental para a programação funcional e imutável.

## Syntax

```javascript
const new_array = array.map(callback(element, index, array), thisArg)
```
- `callback`: Função que produz um elemento do novo Array.

## Use Cases

- **Quando usar:** Quando você precisa transformar cada elemento de um array em outra coisa, criando um novo array com os dados transformados.
- **Exemplo:** Criar um array com o quadrado de cada número.
```javascript
const numbers = [1, 2, 3, 4];
const squares = numbers.map(num => num * num); // [1, 4, 9, 16]
```
- **Cuidado:** `map` sempre cria um novo array. Se você não precisa do array retornado e quer apenas iterar, `forEach` é mais eficiente em termos de memória.

## See Also

- [[filter]]
- [[reduce]]
- [[forEach]]

## References

- [MDN Web Docs: Array.prototype.map()](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Global_Objects/Array/map)