### 🔹 O que é?

Redux Saga é um **middleware** que permite lidar com ações assíncronas de forma mais estruturada usando **funções geradoras (`function*`)**.

Em vez de fazer chamadas diretas dentro das actions ou reducers, o Redux Saga intercepta determinadas actions e executa tarefas assíncronas, como **buscar dados de uma API, esperar por um evento ou reagendar uma operação**.

### 🔹 Diferença entre Saga e Thunk

- **Redux Thunk**: Usa funções normais para lidar com assíncronos, tornando a lógica acoplada à action.
- **Redux Saga**: Usa **funções geradoras**, que facilitam a organização do código e tornam a execução mais previsível.

### 🔹 Exemplo de um Saga:

```js
function* fetchData(action) {
  try {
    const data = yield call(api.fetch, action.payload);
    yield put({ type: 'FETCH_SUCCESS', payload: data });
  } catch (error) {
    yield put({ type: 'FETCH_ERROR', payload: error.message });
  }
}
```

🔹 Aqui, a função geradora `fetchData`:

1. **Chama** a API (`call(api.fetch, action.payload)`)
2. **Despacha** uma ação de sucesso (`put({ type: 'FETCH_SUCCESS', payload: data })`)
3. Se houver erro, despacha uma ação de erro (`put({ type: 'FETCH_ERROR', payload: error.message })`)
