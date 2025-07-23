É o método usado para enviar uma action para o Redux, que vai passar pela `store` e ser processada pelos reducers. 

Exemplo de como disparar uma action:

```js
store.dispatch({ type: 'INCREMENT' });
```

