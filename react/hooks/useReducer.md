---
tags:
  - react
  - hooks
  - state-management
related:
  - "[[useState]]"
  - "[[useContext]]"
  - "[[Redux]]"
creation-date: "2025-08-25"
---

# `useReducer()`

> [!NOTE] Summary
> O hook `useReducer` é uma alternativa ao `useState` para gerenciar lógicas de estado mais complexas em um componente. Ele é especialmente útil quando o próximo estado depende do anterior ou quando a lógica de atualização de estado é complicada.

## Syntax

```javascript
const [state, dispatch] = useReducer(reducer, initialArg, init);
```

- `reducer`: Uma função pura `(state, action) => newState` que recebe o estado atual e uma "ação" (um objeto que descreve a mudança) e retorna o novo estado.
- `initialArg`: O estado inicial.
- `dispatch`: Uma função que você chama para "despachar" uma ação e acionar uma atualização de estado.

## Use Cases

- **Estados complexos:** Melhor para estados complexos (objetos com múltiplas propriedades aninhadas).
- **Lógica centralizada:** Centraliza a lógica de atualização no `reducer`, tornando-a mais previsível e testável.
- **Otimização de performance:** Otimiza a performance para componentes com muitas atualizações de estado, pois o `dispatch` é estável.

### `useState` vs `useReducer`

- **`useState`:**
  - Mais simples para estados primitivos (string, number, boolean) ou objetos/arrays simples.
  - A lógica de atualização está diretamente no componente (ex: `setCount(count + 1)`).

- **`useReducer`:**
  - Melhor para estados complexos (objetos com múltiplas propriedades aninhadas).
  - Centraliza a lógica de atualização no `reducer`, tornando-a mais previsível e testável.
  - Otimiza a performance para componentes com muitas atualizações de estado, pois o `dispatch` é estável.

### Exemplo: Gerenciando um Contador

```javascript
function reducer(state, action) {
  switch (action.type) {
    case 'increment':
      return { count: state.count + 1 };
    case 'decrement':
      return { count: state.count - 1 };
    case 'reset':
      return { count: 0 };
    default:
      throw new Error();
  }
}
```

```jsx
import React, { useReducer } from 'react';

function Counter() {
  const initialState = { count: 0 };
  const [state, dispatch] = useReducer(reducer, initialState);

  return (
    <div>
      <p>Contagem: {state.count}</p>
      <button onClick={() => dispatch({ type: 'increment' })}>+</button>
      <button onClick={() => dispatch({ type: 'decrement' })}>-</button>
      <button onClick={() => dispatch({ type: 'reset' })}>Resetar</button>
    </div>
  );
}
```

## See Also

- [[useState]]
- [[useContext]]
- [[Redux]]

## References

- [React Docs: `useReducer`](https://react.dev/reference/react/useReducer)
