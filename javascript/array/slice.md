---
tags:
  - javascript
  - array
  - immutability
  - copy
related:
  - "[[splice]]"
creation-date: "2025-08-26"
---

# `Array.prototype.slice()`

> [!TIP] Immutability
> Este método não modifica o array original; ele retorna uma cópia.

> [!NOTE] Summary
> O método `slice()` retorna uma **cópia superficial (shallow copy)** de uma porção do array em um novo array. Você pode especificar o início e o fim da porção a ser copiada.

## Syntax

```javascript
const new_array = array.slice(start, end)
```
- `start` (opcional): O índice de início da extração.
- `end` (opcional): O índice final da extração (o elemento neste índice não é incluído).

## Use Cases

- **Quando usar:** Para criar um sub-array ou, mais comumente, para criar uma cópia de um array sem modificar o original.
- **Exemplo:** Criar uma cópia de um array para poder modificá-la com segurança.
```javascript
const numbers = [1, 2, 3, 4, 5];
const copy = numbers.slice();
copy.push(6); // Modifica apenas a cópia
console.log(numbers); // [1, 2, 3, 4, 5]
console.log(copy);    // [1, 2, 3, 4, 5, 6]
```
- **Cuidado:** A cópia é "superficial". Se o array contém objetos, a cópia conterá referências aos mesmos objetos, não cópias deles.

## See Also

- [[splice]]

## References

- [MDN Web Docs: Array.prototype.slice()](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Global_Objects/Array/slice)