Basicamente, ele serve para ganho de performance, quando você quer obter um valor a partir de outro, exemplo, eu tenho uma lista de usuários e quero ordená-la por ordem alfabética, quando eu atualizar essa lista, em vez de fazer todo o processo novamente, eu posso simplesmente, pegar a lista do cache, e ele só atualiza novamente, se algum dos valores mudar.

```js
const [users, setUsers] = React.useState([]);

const sortedUsers = React.useMemo(() => {
	return sortUsers(users)
}, [users]);

...
```

Nesse exemplo ai, a app, no caso onde esse users esta sendo utilizado, só vai ser atualizada novamente, quando o valor de users ser alterado.