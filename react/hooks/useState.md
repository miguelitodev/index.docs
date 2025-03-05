Gerenciador de estados, observa valor nas variáveis, para atualizar em tempo real, já que para cada renderização do react, ele não muda o conteúdo da pagina mais, a não ser que recarregue a pagina, ai quando um estado muda, meio que aquela parte da app e re-renderizada

```js
const [name, setName] = React.useState("");

...

return (
	<input 
		id="name"
		onChange={(event) => {
			setName(event.target.value)
		}} 
	/>
)
```


