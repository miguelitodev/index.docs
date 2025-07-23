# Middleware do Redux Saga

O Redux Saga é implementado como um **middleware** do Redux. Um middleware fornece um ponto de extensão de terceiros entre o despacho de uma [[actions|ação]] e o momento em que ela atinge o [[reducers|reducer]].

É o lugar perfeito para colocar lógica que não pertence à UI (componentes) nem à lógica de atualização de estado (reducers), como chamadas de API, acesso ao `localStorage`, etc.

Tags: #react #redux #redux-saga #middleware #side-effects

---

## Como o Middleware Funciona

Quando você despacha uma ação, ela passa por uma cadeia de middlewares antes de chegar ao reducer.

`Dispatching Action -> Middleware 1 -> Middleware 2 -> ... -> Reducers`

Cada middleware pode:
1.  Deixar a ação passar para o próximo middleware.
2.  Modificar a ação.
3.  Consumir a ação (impedindo que ela chegue ao reducer).
4.  Despachar novas ações.
5.  Pausar e esperar por operações assíncronas.

O Redux Saga usa essa capacidade para observar ações específicas e executar [[saga|sagas]] em resposta a elas.

---

## Configurando o Middleware do Saga

Para usar o Redux Saga, você precisa conectá-lo à [[store]] do Redux usando a função `applyMiddleware`.

**1. Crie a instância do middleware**

Primeiro, você cria uma instância do middleware do Saga usando `createSagaMiddleware()`.

```javascript
// app/saga.js
import { all } from 'redux-saga/effects';
import userSagas from '../features/users/userSagas';
import productSagas from '../features/products/productSagas';

// Saga Raiz (rootSaga)
// Combina todos os sagas da aplicação
export default function* rootSaga() {
  yield all([
    ...userSagas,
    ...productSagas,
  ]);
}
```

**2. Conecte à Store**

Em seguida, ao configurar sua store, você aplica o middleware.

```javascript
// app/store.js
import { configureStore } from '@reduxjs/toolkit';
import createSagaMiddleware from 'redux-saga';
import rootReducer from './reducers'; // Seus reducers combinados
import rootSaga from './saga'; // Sua saga raiz

// Cria a instância do middleware
const sagaMiddleware = createSagaMiddleware();

export const store = configureStore({
  reducer: rootReducer,
  // Adiciona o middleware do saga à lista de middlewares
  // O Redux Toolkit já inclui o thunk, então você precisa concatenar
  middleware: (getDefaultMiddleware) => 
    getDefaultMiddleware().concat(sagaMiddleware),
});

// 3. Execute a saga raiz
// Isso deve ser feito DEPOIS que o middleware foi conectado à store
sagaMiddleware.run(rootSaga);
```

**Explicação:**
1.  `createSagaMiddleware()`: Cria a instância do middleware.
2.  `middleware: ...`: O `configureStore` do Redux Toolkit permite que você adicione middlewares customizados. Nós pegamos os middlewares padrão (`getDefaultMiddleware()`) e adicionamos o `sagaMiddleware`.
3.  `sagaMiddleware.run(rootSaga)`: Inicia a sua `rootSaga`. A partir deste ponto, a `rootSaga` estará em execução, pronta para observar ações e executar outros sagas.

---

## Links Relacionados

- [[saga]]
- [[effects]]
- [[store]]
- [[Redux Thunk]] (outra opção popular de middleware para efeitos colaterais)
