# Actions (Ações) no Redux

No Redux, **Actions** (Ações) são objetos simples de JavaScript que representam a intenção de mudar o estado. Elas são a única fonte de informação para a `store`.

Uma ação é um "payload" de informação que envia dados da sua aplicação para a sua store. Você as envia para a store usando o método `store.dispatch()`.

Tags: #react #redux #state-management #actions

---

## Estrutura de uma Ação

Por convenção, uma ação deve ter uma propriedade `type`, que geralmente é uma string constante. O `type` descreve a ação que está sendo realizada.

```javascript
{
  type: 'ADD_TODO',
  payload: { text: 'Aprender Redux', id: 1 }
}
```

- **`type` (Obrigatório):** Uma string que descreve a ação. É comum usar constantes para evitar erros de digitação (ex: `const ADD_TODO = 'ADD_TODO';`).
- **`payload` (Opcional):** Contém os dados necessários para executar a ação. Pode ser qualquer tipo de dado (objeto, string, número).

---

## Action Creators (Criadores de Ação)

**Action Creators** são funções que criam e retornam objetos de ação. É uma boa prática usá-los em vez de escrever o objeto da ação manualmente toda vez. Isso ajuda a manter o código consistente e mais fácil de entender.

### Exemplo de Action Creator

```javascript
// Constante para o tipo da ação
export const ADD_TODO = 'ADD_TODO';

// Action Creator
export function addTodo(text) {
  return {
    type: ADD_TODO,
    payload: {
      id: Math.random().toString(36).substr(2, 9), // ID simples
      text: text,
      completed: false
    }
  };
}
```

Agora, para criar a ação, você simplesmente chama a função:

```javascript
import { addTodo } from './actions';

const addAction = addTodo('Criar um exemplo de Action Creator');

// O resultado de `addAction` será:
// {
//   type: 'ADD_TODO',
//   payload: { id: '...', text: 'Criar um exemplo...', completed: false }
// }
```

---

## Ações Assíncronas

Ações, por si só, são síncronas. Para lidar com operações assíncronas (como chamadas de API), você usa um middleware como o [[Redux Thunk]] ou [[Redux Saga]].

Com o Thunk, um Action Creator pode retornar uma função em vez de um objeto. Essa função recebe `dispatch` e `getState` como argumentos.

### Exemplo com Thunk (simplificado)

```javascript
function fetchTodos() {
  // Retorna uma função em vez de um objeto
  return function(dispatch) {
    dispatch({ type: 'FETCH_TODOS_REQUEST' });
    return fetch('/api/todos').then(
      response => response.json(),
      error => dispatch({ type: 'FETCH_TODOS_FAILURE', payload: error })
    ).then(
      data => dispatch({ type: 'FETCH_TODOS_SUCCESS', payload: data })
    );
  }
}
```

---

## Links Relacionados

- [[reducers]] (que interpretam as ações para mudar o estado)
- [[dispatch]] (a função que envia as ações)
- [[store]] (o objeto que mantém o estado)
- [[Redux Thunk]]
- [[Redux Saga]]
