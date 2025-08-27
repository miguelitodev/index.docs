---
tags:
  - javascript
  - array
  - immutability
related:
  - "[[push]]"
creation-date: "2025-08-26"
---

# `Array.prototype.concat()`

> [!TIP] Immutability
> Este método não modifica os arrays originais; ele retorna um novo array.

> [!NOTE] Summary
> O método `concat()` é usado para juntar dois ou mais arrays. Este método retorna um novo array contendo os elementos dos arrays originais.

## Syntax

```javascript
const new_array = old_array.concat(array2, array3, ..., arrayN)
```

## Use Cases

- **Quando usar:** Para combinar múltiplos arrays em um só.
- **Exemplo:** Combinar duas listas de usuários.
```javascript
const groupA = ['Alice', 'Bob'];
const groupB = ['Charlie', 'David'];
const allUsers = groupA.concat(groupB);
console.log(allUsers); // ['Alice', 'Bob', 'Charlie', 'David']
```
- **Alternativa:** Hoje em dia, o operador Spread (`...`) é frequentemente preferido por ser mais conciso:
```javascript
const allUsersSpread = [...groupA, ...groupB];
```

## See Also

- [[push]]

## References

- [MDN Web Docs: Array.prototype.concat()](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Global_Objects/Array/concat)