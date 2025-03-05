O memo assim como o useMemo, serve para memorizar algo, nesse caso, usamos o memo para memorizar o componente, as props dele em especifico, então no caso de termos um componente de input, vamos verificar se as props dele se alteraram, caso não, e pulada a renderização desse componente, contrario, ele sera renderizado novamente, a depender do componente o ganho de performance pode ser bem alta.

```js
function Search({ onChange }) {
	return(
		<input
			onChange={(event) => onChange(event.target.value)}
		/>
	)
}

...

export default React.memo(Search);
```