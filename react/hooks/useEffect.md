Dispara uma função somente quando quisermos, ai a gente determina quando isso vai ocorrer no segundo parâmetro, por exemplo, quando determinado valor mudar, a função que estiver no useEffect, vai mudar

```js
const [user, setUser] = React.useState("");

React.useEffect(() => {
	useFetch('http://localhost/3000/users/id') // pegar um user especifico
	.then(response => response.json())
	.then(data => {
		console.log(data);
	})
}, [user]);

...
```

