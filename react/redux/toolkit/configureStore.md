# `configureStore` do Redux Toolkit

`configureStore` é a função principal do [[Redux Toolkit]] para criar a [[store]] do Redux. Ela substitui a função `createStore` original do Redux e simplifica muito o processo de configuração, incluindo padrões recomendados por padrão.

Tags: #react #redux #redux-toolkit #store #state-management

---

## O que `configureStore` Faz?

Ao usar `configureStore`, você obtém automaticamente:

1.  **`combineReducers`:** Você pode passar um objeto de "slice reducers" para a opção `reducer`, e `configureStore` os combinará para você.
2.  **`redux-thunk`:** O middleware [[Redux Thunk]] é adicionado por padrão, permitindo a lógica assíncrona básica.
3.  **Redux DevTools Extension:** O suporte para a popular extensão de navegador é configurado automaticamente.
4.  **Middlewares de Verificação:** Vários middlewares que verificam erros comuns, como mutação acidental do estado, são adicionados em ambiente de desenvolvimento.

---

## Sintaxe

```javascript
import { configureStore } from '@reduxjs/toolkit';
import usersReducer from '../features/users/usersSlice';
import postsReducer from '../features/posts/postsSlice';

export const store = configureStore({
  // A opção `reducer` pode ser um único reducer ou um objeto de slice reducers
  reducer: {
    users: usersReducer,
    posts: postsReducer,
  },
  // A opção `middleware` permite customizar a cadeia de middlewares
  middleware: (getDefaultMiddleware) => getDefaultMiddleware().concat(myCustomMiddleware),
  // A opção `devTools` pode ser `false` para desabilitar em produção
  devTools: process.env.NODE_ENV !== 'production',
});
```

---

## Exemplo com `createSlice`

`configureStore` é projetado para funcionar perfeitamente com `createSlice`, outra API do Redux Toolkit que gera [[actions]] e [[reducers]] a partir de um nome de slice e um objeto de funções redutoras.

**1. Crie um Slice**

```javascript
// features/counter/counterSlice.js
import { createSlice } from '@reduxjs/toolkit';

const initialState = { value: 0 };

const counterSlice = createSlice({
  name: 'counter',
  initialState,
  reducers: {
    increment(state) {
      // Com o Immer (incluído no Toolkit), você pode "mutar" o estado aqui
      state.value++;
    },
    decrement(state) {
      state.value--;
    },
  },
});

// Exporta os action creators gerados automaticamente
export const { increment, decrement } = counterSlice.actions;

// Exporta o reducer gerado
export default counterSlice.reducer;
```

**2. Configure a Store**

```javascript
// app/store.js
import { configureStore } from '@reduxjs/toolkit';
import counterReducer from '../features/counter/counterSlice';

export const store = configureStore({
  reducer: {
    counter: counterReducer,
  },
});
```

Essa configuração é muito mais concisa e menos propensa a erros do que a abordagem manual com `createStore` e `combineReducers`.

---

## Links Relacionados

- [[Redux Toolkit]]
- [[createSlice]]
- [[store]]
- [[reducers]]
- [[Redux Thunk]]