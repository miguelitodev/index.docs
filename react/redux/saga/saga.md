# Redux Saga

**Redux Saga** é um [[middleware]] para o Redux que ajuda a gerenciar os efeitos colaterais (side effects) da sua aplicação, como chamadas de API, acesso ao `localStorage` e outras operações assíncronas.

Ele faz isso utilizando **Funções Geradoras** (Generator Functions) do ES6, que permitem escrever código assíncrono que parece síncrono, tornando-o mais fácil de ler, escrever e testar.

Tags: #react #redux #redux-saga #side-effects #asynchronous

---

## O que é um Saga?

Um Saga é basicamente uma **função geradora (`function*`)** que:
1.  **Observa** [[actions]] do Redux que são despachadas.
2.  **Executa** tarefas (como chamadas de API) em resposta a essas ações.
3.  **Despacha** novas ações para a [[store]] com os resultados das tarefas.

O fluxo principal é:
`Componente -> Despacha Ação -> Saga -> Chamada de API -> Saga -> Despacha Ação de Sucesso/Falha -> Reducer -> Atualiza Estado -> Componente`

---

## Exemplo: Buscando Dados de Usuário

Vamos ver um ciclo completo.

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

Este Saga usa o [[effects|efeito]] `takeLatest` para ouvir a ação `FETCH_USER_REQUEST` e chamar outro Saga (worker) para fazer o trabalho.

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

O reducer ouve as ações de sucesso ou falha despachadas pelo Saga.

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

---

## Vantagens do Redux Saga

- **Testabilidade:** Como Sagas usam [[effects|efeitos declarativos]], você pode testar a lógica do seu gerador passo a passo, sem mockar APIs. Você apenas verifica se o Saga produziu o efeito correto.
- **Código Limpo:** Mantém a lógica de efeitos colaterais completamente separada dos seus componentes e até mesmo dos seus [[actions|action creators]].
- **Gerenciamento Avançado de Fluxo:** Permite implementar cenários complexos como debouncing, throttling, cancelamento de tarefas e corridas de ações de forma mais fácil do que com outras bibliotecas como o [[Redux Thunk]].

---

## Links Relacionados

- [[middleware]]
- [[effects]]
- [[Funções Geradoras (Generator Functions)]]
- [[Redux Thunk]] (alternativa)