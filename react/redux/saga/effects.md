### 🔹 O que são?

Os efeitos (`effects`) são **comandos especiais** que o Redux Saga usa para controlar o fluxo da aplicação. Eles ajudam a lidar com chamadas assíncronas, disparar novas actions e ouvir eventos.

### 🔹 Principais efeitos:

| Efeito       | O que faz?                                            | Exemplo                                          |
| ------------ | ----------------------------------------------------- | ------------------------------------------------ |
| `call`       | Chama uma função assíncrona (ex: API)                 | `yield call(api.fetch, id)`                      |
| `put`        | Dispara uma nova action no Redux                      | `yield put({ type: 'ACTION', payload: data })`   |
| `takeEvery`  | Escuta **todas** as ações de um tipo e executa a saga | `yield takeEvery('ACTION_TYPE', sagaFunction)`   |
| `takeLatest` | Escuta apenas a **última** ação (descarta anteriores) | `yield takeLatest('ACTION_TYPE', sagaFunction)`  |
| `select`     | Acessa o estado do Redux dentro da saga               | `const user = yield select(state => state.user)` |
| `delay`      | Espera um tempo antes de continuar                    | `yield delay(1000)`                              |

### 🔹 Exemplo:

```js
import { call, put, takeLatest, delay } from 'redux-saga/effects';

function* fetchUser(action) {
  try {
    yield delay(500); // Aguarda 500ms antes de executar
    const user = yield call(api.getUser, action.payload);
    yield put({ type: 'FETCH_USER_SUCCESS', payload: user });
  } catch (error) {
    yield put({ type: 'FETCH_USER_ERROR', payload: error.message });
  }
}

export function* watchFetchUser() {
  yield takeLatest('FETCH_USER_REQUEST', fetchUser);
}
```

🔹 Aqui:

- `delay(500)`: Espera 500ms antes de chamar a API.
- `call(api.getUser, action.payload)`: Chama a API.
- `put({ type: 'FETCH_USER_SUCCESS', payload: user })`: Dispara a ação com os dados.
- `takeLatest('FETCH_USER_REQUEST', fetchUser)`: Garante que apenas a **última** requisição seja processada.