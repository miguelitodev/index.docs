---
tags:
  - javascript
  - array
  - conversion
  - string
related:
  - "[[split]]"
creation-date: "2025-08-26"
---

# `Array.prototype.join()`

> [!TIP] Immutability
> Este método não modifica o array original.

> [!NOTE] Summary
> O método `join()` junta todos os elementos de um array em uma string e retorna esta string. É o inverso do método `split()` de strings.

## Syntax

```javascript
const str = array.join(separator)
```
- `separator` (opcional): Uma string para separar cada par de elementos adjacentes. Se omitido, os elementos são separados por uma vírgula (`,`).

## Use Cases

- **Quando usar:** Para criar uma string a partir de um array, como uma lista de tags para exibição ou uma sentença.
- **Exemplo:** Criar uma URL a partir de segmentos.
```javascript
const parts = ['api', 'users', '123'];
const urlPath = parts.join('/');
console.log(urlPath); // "api/users/123"
```

## See Also

- [[split]]

## References

- [MDN Web Docs: Array.prototype.join()](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Global_Objects/Array/join)