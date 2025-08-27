---
tags:
  - javascript
  - array
  - immutability
related:
  - "[[splice]]"
  - "[[slice]]"
creation-date: "2025-08-26"
---

# `Array.prototype.with()`

> [!TIP] Immutability
> Este método retorna uma cópia do array com a modificação, não altera o original.

> [!NOTE] Summary
> O método `with()` é a contraparte imutável da notação de colchetes (`[]`). Ele retorna uma **cópia** do array com o valor em um índice especificado substituído pelo novo valor.

## Syntax

```javascript
const new_array = array.with(index, value)
```

## Use Cases

- **Quando usar:** Para atualizar um item em um array de forma imutável, o que é uma prática comum em frameworks como React.
- **Exemplo:** Atualizar o status de uma tarefa em uma lista.
```javascript
const tasks = [
  { id: 1, text: 'Estudar', status: 'pending' },
  { id: 2, text: 'Correr', status: 'pending' },
];

const updatedTasks = tasks.with(1, { ...tasks[1], status: 'done' });

// tasks não foi modificado
// updatedTasks é a nova lista com o item atualizado
```
- **Cuidado:** É um método novo (ES2023), verifique a compatibilidade do ambiente.

## See Also

- [[splice]]

## References

- [MDN Web Docs: Array.prototype.with()](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Global_Objects/Array/with)