# Effects no Redux Saga

No Redux Saga, **Effects** são objetos simples de JavaScript que contêm instruções a serem executadas pelo middleware do Saga. Eles são como as [[actions]] do Redux, mas para Sagas: em vez de despachar uma intenção de mudar o estado, você "produz" (yield) um Efeito que descreve a operação que você quer realizar.

Isso torna os Sagas extremamente fáceis de testar, pois você pode simplesmente verificar se o Saga produziu o Efeito correto, sem precisar mockar chamadas de API ou outras operações complexas.

Tags: #react #redux #redux-saga #side-effects

---

## Effects Declarativos

O poder dos Sagas vem de sua natureza declarativa. Sua função geradora (`function*`) não executa a chamada de API diretamente. Em vez disso, ela produz um objeto que descreve a chamada.

- **Você diz:** `yield call(Api.fetch, '/')`
- **O que significa:** "Middleware do Saga, por favor, execute a função `Api.fetch` com o argumento `'/'` e me devolva o resultado quando estiver pronto."

---

## Effects Comuns

### `call`

Usado para chamar uma função. Se a função retornar uma Promessa, o Saga pausa até que a Promessa seja resolvida.

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

### `put`

Usado para despachar uma [[actions|ação]] para a Store do Redux. É o análogo do `dispatch` dentro de um Saga.

```javascript
import { put } from 'redux-saga/effects';

yield put({ type: 'INCREMENT' });
```

### `takeEvery`

Escuta por uma ação específica e executa um Saga para *cada* ação desse tipo que for despachada.

```javascript
import { takeEvery } from 'redux-saga/effects';

function* watchFetchUser() {
  yield takeEvery('FETCH_USER_REQUEST', fetchUserData);
}
```

### `takeLatest`

Similar ao `takeEvery`, mas só permite que uma única instância do Saga seja executada por vez. Se uma nova ação for despachada enquanto um Saga anterior ainda estiver em execução, o anterior é cancelado e um novo é iniciado.

Útil para evitar condições de corrida, como quando um usuário clica rapidamente em um botão de busca.

```javascript
import { takeLatest } from 'redux-saga/effects';

function* watchFetchUser() {
  yield takeLatest('FETCH_USER_REQUEST', fetchUserData);
}
```

### `select`

Permite que um Saga acesse o estado atual da Store do Redux.

```javascript
import { select } from 'redux-saga/effects';

const getCart = state => state.cart;

function* checkout() {
  const cart = yield select(getCart);
  // ... faz algo com o carrinho
}
```

### `all`

Executa múltiplos Efeitos em paralelo e espera que todos eles terminem. Similar a `Promise.all()`.

```javascript
import { all, call } from 'redux-saga/effects';

function* fetchAll() {
  const [users, products] = yield all([
    call(Api.fetchUsers),
    call(Api.fetchProducts)
  ]);
}
```

---

## Links Relacionados

- [[saga]]
- [[middleware]]
- [[Funções Geradoras (Generator Functions)]]
