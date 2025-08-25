---
tags:
  - react
  - redux
  - state-management
  - store
related:
  - "[[actions]]"
  - "[[reducers]]"
  - "[[dispatch]]"
  - "[[Redux Toolkit]]"
  - "[[Provider (react-redux)]]"
creation-date: "2025-08-25"
---

# Store no Redux

> [!NOTE] Summary
> A **Store** é o objeto que une [[actions]] e [[reducers]]. É o coração de uma aplicação Redux, pois ela contém e gerencia a árvore de estado da aplicação. Só deve haver uma única `store` em uma aplicação Redux.

## Syntax

### Criando uma Store

You cria uma `store` usando a função `createStore` do Redux, passando o seu [[reducers|reducer]] raiz como argumento. Middleware, como o `applyMiddleware` para [[Redux Thunk]], é passado como um segundo argumento.

**Atenção:** A função `createStore` está sendo desencorajada em favor do `configureStore` do [[Redux Toolkit]], que é mais moderno e simples.

### Exemplo com `createStore` (Abordagem Antiga)

```javascript
import { createStore, applyMiddleware } from 'redux';
import thunk from 'redux-thunk';
import rootReducer from './reducers'; // Seu reducer raiz combinado

// O segundo argumento (enhancer) é opcional
const store = createStore(
  rootReducer,
  applyMiddleware(thunk)
);

export default store;
```

### Exemplo com `configureStore` (Abordagem Recomendada)

O [[Redux Toolkit]] simplifica muito essa configuração.

```javascript
// app/store.js
import { configureStore } from '@reduxjs/toolkit';
import todosReducer from '../features/todos/todosSlice';
import visibilityFilterReducer from '../features/filters/filtersSlice';

export const store = configureStore({
  reducer: {
    // O `configureStore` chama `combineReducers` automaticamente
    todos: todosReducer,
    visibilityFilter: visibilityFilterReducer,
  },
  // O middleware Thunk já vem incluído por padrão no configureStore
});
```

## Use Cases

### Responsabilidades da Store

- **Manter o estado da aplicação:** A `store` possui o objeto de estado global.
- **Permitir o acesso ao estado:** Através do método `getState()`.
- **Permitir que o estado seja atualizado:** Através do método `dispatch(action)`.
- **Registrar listeners:** Através do método `subscribe(listener)`.
- **Cancelar o registro de listeners:** Através da função retornada por `subscribe(listener)`.

### Fornecendo a Store ao React

Para que os componentes React tenham acesso à `store`, você usa o componente `Provider` da biblioteca `react-redux`, envolvendo seu aplicativo principal (`App`).

```jsx
// index.js
import React from 'react';
import ReactDOM from 'react-dom';
import { Provider } from 'react-redux';
import store from './app/store'; // A store que você acabou de criar
import App from './App';

ReactDOM.render(
  <React.StrictMode>
    <Provider store={store}>
      <App />
    </Provider>
  </React.StrictMode>,
  document.getElementById('root')
);
```

## See Also

- [[actions]]
- [[reducers]]
- [[dispatch]]
- [[Redux Toolkit]]
- [[Provider (react-redux)]]

## References

- [Redux Docs: Store](https://redux.js.org/api/store)