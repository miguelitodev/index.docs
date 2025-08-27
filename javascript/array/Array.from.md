---
tags:
  - javascript
  - array
  - conversion
  - static-method
related:
  - "[[Array.of]]"
creation-date: "2025-08-26"
---

# `Array.from()`

> [!NOTE] Summary
> O método estático `Array.from()` cria uma nova instância de `Array` a partir de um objeto "array-like" (com propriedade `length` e elementos indexados) ou um objeto iterável (como `Map`, `Set`, `String`).

## Syntax

```javascript
const new_array = Array.from(arrayLike, mapFn, thisArg)
```
- `arrayLike`: O objeto a ser convertido em um array.
- `mapFn` (opcional): Função `map` a ser chamada em cada elemento do array.

## Use Cases

- **Quando usar:** Para converter estruturas que se parecem com arrays, mas não são, em arrays de verdade para poder usar métodos como `map`, `filter`, etc.
- **Exemplo:** Converter uma `NodeList` (retornada por `querySelectorAll`) em um array.
```javascript
// Suponha que no DOM existam vários <p>
const nodeList = document.querySelectorAll('p');
const pArray = Array.from(nodeList);
pArray.forEach(p => console.log(p.textContent));
```

## See Also

- [[Array.of]]

## References

- [MDN Web Docs: Array.from()](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Global_Objects/Array/from)