O mais simples de todos kkk, ele gera um Id único, basicamente, se temos que listar componentes e tem que ter ids diferentes de alguma forma, em vez de fazer uma volta usando props editando o nome algo do tipo, podemos utilizar ele. Geralmente teremos um problema do tipo utilizando formulários.

```js
const id = React.useId();

...

<label htmlFor={id}>Nome:</label>
<input
	id={id}
	placeholder="Nome"
/>
```
