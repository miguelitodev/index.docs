---
tags:
  - javascript
  - array
  - creation
  - static-method
related:
  - "[[Array.from]]"
creation-date: "2025-08-26"
---

# `Array.of()`

> [!NOTE] Summary
> O método estático `Array.of()` cria uma nova instância de `Array` com um número variável de argumentos, independentemente do número ou tipo dos argumentos.

## Syntax

```javascript
const new_array = Array.of(element0, element1, ..., elementN)
```

## Use Cases

- **Quando usar:** A principal diferença entre `Array.of()` e o construtor `Array()` está no tratamento de argumentos inteiros. `Array.of(7)` cria um array com um único elemento, `7`, enquanto `new Array(7)` cria um array vazio com a propriedade `length` de 7.
- **Exemplo:** Criar um array de forma previsível.
```javascript
Array.of(7);       // [7]
Array.of(1, 2, 3); // [1, 2, 3]

new Array(7);       // array de 7 posições vazias
new Array(1, 2, 3); // [1, 2, 3]
```

## See Also

- [[Array.from]]

## References

- [MDN Web Docs: Array.of()](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Global_Objects/Array/of)