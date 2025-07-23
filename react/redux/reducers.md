# Reducers no Redux

Um **Reducer** é uma função pura que especifica como o estado de uma aplicação muda em resposta a uma [[actions|ação]]. A função `reducer` recebe dois argumentos: o estado atual (`state`) e uma `action`, e deve retornar o próximo estado (`newState`).

`(currentState, action) => newState`

Reducers são o coração da lógica do Redux.

Tags: #react #redux #state-management #reducers

---

## Princípios de um Reducer

1.  **Função Pura:**
    - Dado o mesmo `state` e `action`, deve sempre retornar o mesmo `newState`.
    - Não deve ter efeitos colaterais (side effects), como chamadas de API ou mutações fora de seu escopo.
    - Não deve modificar o `state` original. Em vez disso, deve retornar uma cópia nova e atualizada.

2.  **Imutabilidade:**
    - Nunca mude o objeto `state` ou o array `state` diretamente. Crie sempre uma cópia.
    - Para objetos, use `...` (spread syntax) ou `Object.assign()`.
    - Para arrays, use `...` (spread syntax), `.map()`, `.filter()`, etc.

---

## Exemplo de um Reducer

Vamos criar um reducer para gerenciar uma lista de tarefas (todos).

```javascript
import { ADD_TODO, TOGGLE_TODO } from './actions';

// O estado inicial da aplicação para este reducer
const initialState = {
  todos: []
};

// A função reducer
function todoAppReducer(state = initialState, action) {
  switch (action.type) {
    case ADD_TODO:
      // Retorna um NOVO objeto de estado
      return {
        // Copia as outras propriedades do estado (se houver)
        ...state,
        // Cria um NOVO array de todos, com o novo todo no final
        todos: [
          ...state.todos,
          {
            id: action.payload.id,
            text: action.payload.text,
            completed: false
          }
        ]
      };

    case TOGGLE_TODO:
      return {
        ...state,
        todos: state.todos.map(todo =>
          // Se o ID corresponder, cria um NOVO objeto todo
          (todo.id === action.payload.id)
            ? { ...todo, completed: !todo.completed }
            : todo // Caso contrário, retorna o todo original
        )
      };

    // Se a ação não for reconhecida, retorna o estado atual
    default:
      return state;
  }
}

export default todoAppReducer;
```

---

## `combineReducers`

À medida que a aplicação cresce, é comum dividir a lógica de redução em múltiplos reducers, cada um gerenciando uma parte do estado. A função `combineReducers` do Redux ajuda a combinar esses reducers em um único reducer raiz.

### Exemplo

```javascript
import { combineReducers } from 'redux';

// Reducer que gerencia apenas a lista de todos
function todos(state = [], action) { /* ... */ }

// Reducer que gerencia apenas o filtro de visibilidade
function visibilityFilter(state = 'SHOW_ALL', action) { /* ... */ }

// Combina os dois em um reducer raiz
const rootReducer = combineReducers({
  todos: todos, // a chave `todos` no estado será gerenciada pelo reducer `todos`
  visibilityFilter: visibilityFilter // a chave `visibilityFilter` será gerenciada por `visibilityFilter`
});

export default rootReducer;
```

O estado global agora terá a forma: `{ todos: [...], visibilityFilter: '...' }`.

---

## Links Relacionados

- [[actions]]
- [[store]]
- [[Imutabilidade]]
- [[Redux Toolkit]] (que simplifica a escrita de reducers com `createSlice`)