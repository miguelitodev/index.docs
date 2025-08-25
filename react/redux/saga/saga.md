---
tags:
  - react
  - redux
  - redux-saga
  - side-effects
  - asynchronous
related:
  - "[[middleware]]"
  - "[[effects]]"
  - "[[Funções Geradoras (Generator Functions)]]"
  - "[[Redux Thunk]]"
creation-date: "2025-08-25"
---

# Redux Saga

> [!NOTE] Summary
> **Redux Saga** é um [[middleware]] para o Redux que ajuda a gerenciar os efeitos colaterais (side effects) da sua aplicação, como chamadas de API, acesso ao `localStorage` e outras operações assíncronas.

## Syntax

### O que é um Saga?

Um Saga é basicamente uma **função geradora (`function*`)** que:
1.  **Observa** [[actions]] do Redux que são despachadas.
2.  **Executa** tarefas (como chamadas de API) em resposta a essas ações.
3.  **Despacha** novas ações para a [[store]] com os resultados das tarefas.

O fluxo principal é:
`Componente -> Despacha Ação -> Saga -> Chamada de API -> Saga -> Despacha Ação de Sucesso/Falha -> Reducer -> Atualiza Estado -> Componente`

## Use Cases

### Exemplo: Buscando Dados de Usuário

**1. O Componente Despacha uma Ação**

```jsx
// UserProfile.js
import React, { useEffect } from 'react';
import { useDispatch, useSelector } from 'react-redux';

const UserProfile = ({ userId }) => {
  const dispatch = useDispatch();
  const user = useSelector(state => state.user.data);

  useEffect(() => {
    // Despacha a ação que o Saga irá ouvir
    dispatch({ type: 'FETCH_USER_REQUEST', payload: { userId } });
  }, [dispatch, userId]);

  // ... renderiza o usuário
};
```

**2. O Saga Observador (Watcher Saga)**

```javascript
// userSagas.js
import { takeLatest, call, put } from 'redux-saga/effects';
import Api from './api';

// Worker Saga: faz a chamada de API
function* fetchUser(action) {
  try {
    const userData = yield call(Api.fetch, `/users/${action.payload.userId}`);
    // Despacha uma ação de sucesso com os dados
    yield put({ type: 'FETCH_USER_SUCCESS', payload: userData });
  } catch (error) {
    // Despacha uma ação de falha com o erro
    yield put({ type: 'FETCH_USER_FAILURE', payload: error.message });
  }
}

// Watcher Saga: observa as ações
function* userSaga() {
  yield takeLatest('FETCH_USER_REQUEST', fetchUser);
}

export default userSaga;
```

**3. O Reducer Atualiza o Estado**

```javascript
// userReducer.js
const initialState = { data: null, error: null, loading: false };

function userReducer(state = initialState, action) {
  switch (action.type) {
    case 'FETCH_USER_REQUEST':
      return { ...state, loading: true, error: null };
    case 'FETCH_USER_SUCCESS':
      return { ...state, loading: false, data: action.payload };
    case 'FETCH_USER_FAILURE':
      return { ...state, loading: false, error: action.payload };
    default:
      return state;
  }
}
```

## See Also

- [[middleware]]
- [[effects]]
- [[Funções Geradoras (Generator Functions)]]
- [[Redux Thunk]]

## References

- [Redux Saga Documentation](https://redux-saga.js.org/)
