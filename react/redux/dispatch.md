# `dispatch` no Redux

A função `dispatch` é o método que você usa para enviar (ou "despachar") [[actions]] para a `store` do Redux. É a única maneira de acionar uma mudança de estado.

Quando você chama `dispatch(action)`, a `store` do Redux executa o [[reducers|reducer]] raiz, passando o estado atual e a `action` que você despachou. O reducer então calcula o próximo estado.

Tags: #react #redux #state-management #dispatch

---

## Como Funciona

O fluxo é o seguinte:

1.  Você chama `dispatch(action)` de algum lugar na sua UI (por exemplo, um `onClick` de um botão).
2.  A `store` do Redux recebe a ação.
3.  A `store` chama a função `reducer` com os argumentos `(currentState, action)`.
4.  O `reducer` avalia a ação e retorna o `nextState`.
5.  A `store` salva o `nextState` e notifica todos os componentes inscritos (conectados) sobre a mudança.
6.  Os componentes conectados re-renderizam com os novos dados do estado.

---

## Obtendo o `dispatch`

Em uma aplicação React com `react-redux`, você não acessa o `dispatch` diretamente da `store`. Em vez disso, você usa o hook `useDispatch`.

### Exemplo com o hook `useDispatch`

```jsx
import React from 'react';
import { useDispatch } from 'react-redux';
import { addTodo } from './actions'; // Importa um Action Creator

const AddTodoInput = () => {
  const [text, setText] = React.useState('');
  // 1. Pega a função dispatch usando o hook
  const dispatch = useDispatch();

  const handleAdd = () => {
    if (text.trim()) {
      // 2. Cria a ação usando o Action Creator
      const action = addTodo(text);
      // 3. Despacha a ação para a store
      dispatch(action);
      setText('');
    }
  };

  return (
    <div>
      <input value={text} onChange={e => setText(e.target.value)} />
      <button onClick={handleAdd}>Adicionar Tarefa</button>
    </div>
  );
};
```

---

## `mapDispatchToProps` (Abordagem Antiga com `connect`)

Antes dos hooks, em componentes de classe, a função `mapDispatchToProps` era usada com o HOC `connect` para injetar `dispatch` ou `action creators` pré-vinculados como props no componente.

```javascript
import { connect } from 'react-redux';
import { addTodo } from './actions';

// ... (Componente de classe)

const mapDispatchToProps = dispatch => {
  return {
    // `onAddTodo` se torna uma prop no componente
    onAddTodo: text => dispatch(addTodo(text))
  };
};

export default connect(null, mapDispatchToProps)(MyComponent);
```

Embora ainda funcione, a abordagem com o hook `useDispatch` é considerada mais moderna e simples.

---

## Links Relacionados

- [[actions]]
- [[reducers]]
- [[store]]
- [[useDispatch]] (hook do `react-redux`)