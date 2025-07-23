# `useReducer()`

O hook `useReducer` é uma alternativa ao `useState` para gerenciar lógicas de estado mais complexas em um componente. Ele é especialmente útil quando o próximo estado depende do anterior ou quando a lógica de atualização de estado é complicada.

É inspirado nos *reducers* da biblioteca Redux.

Tags: #react #hooks #state-management

---

## Sintaxe

```javascript
const [state, dispatch] = useReducer(reducer, initialArg, init);
```

- `reducer`: Uma função pura `(state, action) => newState` que recebe o estado atual e uma "ação" (um objeto que descreve a mudança) e retorna o novo estado.
- `initialArg`: O estado inicial.
- `dispatch`: Uma função que você chama para "despachar" uma ação e acionar uma atualização de estado.

---

## `useState` vs `useReducer`

- **`useState`:**
  - Mais simples para estados primitivos (string, number, boolean) ou objetos/arrays simples.
  - A lógica de atualização está diretamente no componente (ex: `setCount(count + 1)`).

- **`useReducer`:**
  - Melhor para estados complexos (objetos com múltiplas propriedades aninhadas).
  - Centraliza a lógica de atualização no `reducer`, tornando-a mais previsível e testável.
  - Otimiza a performance para componentes com muitas atualizações de estado, pois o `dispatch` é estável.

---

## Exemplo: Gerenciando um Contador

Embora seja um exemplo simples, ele ilustra bem o fluxo.

**1. Defina o Reducer**

O reducer é uma função que lida com todas as transições de estado.

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

**2. Use no Componente**

```jsx
import React, { useReducer } from 'react';

// (a função reducer de cima vai aqui)

function Counter() {
  const initialState = { count: 0 };
  const [state, dispatch] = useReducer(reducer, initialState);

  return (
    <div>
      <p>Contagem: {state.count}</p>
      {/* Despacha ações para o reducer */}
      <button onClick={() => dispatch({ type: 'increment' })}>+</button>
      <button onClick={() => dispatch({ type: 'decrement' })}>-</button>
      <button onClick={() => dispatch({ type: 'reset' })}>Resetar</button>
    </div>
  );
}
```

Quando um botão é clicado, a função `dispatch` envia um objeto de ação (ex: `{ type: 'increment' }`) para o `reducer`. O `reducer` então calcula o novo estado, e o React renderiza o componente novamente com o `state` atualizado.

---

## Links Relacionados

- [[useState]]
- [[useContext]] (frequentemente combinado com `useReducer` para criar um "mini-Redux")
- [[Redux]]