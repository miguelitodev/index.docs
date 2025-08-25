---
tags:
  - react
  - redux
  - redux-saga
  - side-effects
related:
  - "[[saga]]"
  - "[[middleware]]"
  - "[[Funções Geradoras (Generator Functions)]]"
creation-date: "2025-08-25"
---

# Effects no Redux Saga

> [!NOTE] Summary
> No Redux Saga, **Effects** são objetos simples de JavaScript que contêm instruções a serem executadas pelo middleware do Saga. Eles são como as [[actions]] do Redux, mas para Sagas: em vez de despachar uma intenção de mudar o estado, você "produz" (yield) um Efeito que descreve a operação que você quer realizar.

## Syntax

### Effects Declarativos

O poder dos Sagas vem de sua natureza declarativa. Sua função geradora (`function*`) não executa a chamada de API diretamente. Em vez disso, ela produz um objeto que descreve a chamada.

- **Você diz:** `yield call(Api.fetch, '/')`
- **O que significa:** "Middleware do Saga, por favor, execute a função `Api.fetch` com o argumento `'/'` e me devolva o resultado quando estiver pronto."

## Use Cases

### Effects Comuns

- **`call`**: Usado para chamar uma função. Se a função retornar uma Promessa, o Saga pausa até que a Promessa seja resolvida.
- **`put`**: Usado para despachar uma [[actions|ação]] para a Store do Redux. É o análogo do `dispatch` dentro de um Saga.
- **`takeEvery`**: Escuta por uma ação específica e executa um Saga para *cada* ação desse tipo que for despachada.
- **`takeLatest`**: Similar ao `takeEvery`, mas só permite que uma única instância do Saga seja executada por uma vez. Se uma nova ação for despachada enquanto um Saga anterior ainda estiver em execução, o anterior é cancelado e um novo é iniciado.
- **`select`**: Permite que um Saga acesse o estado atual da Store do Redux.
- **`all`**: Executa múltiplos Efeitos em paralelo e espera que todos eles terminem. Similar a `Promise.all()`.

### Exemplo com `call`

```javascript
import { call, put } from 'redux-saga/effects';
import Api from './api';

function* fetchUserData(action) {
  try {
    // Pausa o Saga até que a chamada de API retorne
    const userData = yield call(Api.fetchUser, action.payload.userId);
    yield put({ type: 'FETCH_USER_SUCCESS', payload: userData });
  } catch (error) {
    yield put({ type: 'FETCH_USER_FAILURE', payload: error.message });
  }
}
```

### Exemplo com `put`

```javascript
import { put } from 'redux-saga/effects';

yield put({ type: 'INCREMENT' });
```

### Exemplo com `takeEvery`

```javascript
import { takeEvery } from 'redux-saga/effects';

function* watchFetchUser() {
  yield takeEvery('FETCH_USER_REQUEST', fetchUserData);
}
```

### Exemplo com `takeLatest`

```javascript
import { takeLatest } from 'redux-saga/effects';

function* watchFetchUser() {
  yield takeLatest('FETCH_USER_REQUEST', fetchUserData);
}
```

### Exemplo com `select`

```javascript
import { select } from 'redux-saga/effects';

const getCart = state => state.cart;

function* checkout() {
  const cart = yield select(getCart);
  // ... faz algo com o carrinho
}
```

### Exemplo com `all`

```javascript
import { all, call } from 'redux-saga/effects';

function* fetchAll() {
  const [users, products] = yield all([
    call(Api.fetchUsers),
    call(Api.fetchProducts)
  ]);
}
```

## See Also

- [[saga]]
- [[middleware]]
- [[Funções Geradoras (Generator Functions)]]

## References

- [Redux Saga Docs: Effects](https://redux-saga.js.org/docs/api/effects)