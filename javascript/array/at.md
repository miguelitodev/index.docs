---
tags:
  - javascript
  - array
  - access
related:
  - 
creation-date: "2025-08-26"
---

# `Array.prototype.at()`

> [!NOTE] Summary
> O método `at()` recebe um valor inteiro e retorna o item naquele índice. A principal vantagem é que ele permite índices positivos e negativos. Índices negativos contam a partir do final do array.

## Syntax

```javascript
const item = array.at(index)
```

## Use Cases

- **Quando usar:** Para pegar elementos do final do array de forma concisa e legível.
- **Exemplo:** Pegar o último elemento de um array.
```javascript
const numbers = [5, 12, 8, 130, 44];
const lastElement = numbers.at(-1); // 44
// Em vez de: numbers[numbers.length - 1]
```
- **Cuidado:** É um método mais recente (ES2022), então verifique a compatibilidade com ambientes mais antigos.

## See Also

- 

## References

- [MDN Web Docs: Array.prototype.at()](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Global_Objects/Array/at)