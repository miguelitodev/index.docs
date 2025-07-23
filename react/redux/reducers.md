São funções puras que definem como o estado da aplicação muda em resposta a uma action. Elas pegam o estado atual e a action como argumentos e retornam um novo estado. 

Exemplo de um reducer simples:

```js
const counterReducer = (state = 0, action) => {
  switch (action.type) {
		case 'INCREMENT':
			return state + 1;
		case 'DECREMENT':
			return state - 1;
		default:
			return state;
  }
};
```
