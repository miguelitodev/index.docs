Ha um problema no react, assim dizer, que toda função, mesmo que ela seja sempre igual e use valores estáticos, ela sempre vai fazer uma re-renderização na app, então se você usar essa função em outro componente, ele provavelmente vai ser renderizado novamente, e ai foi criado o useCallback, para memorizar a função que e passada, assim, não haverá renderizares desnecessárias na app.

```js
React.useCallback((text) => {
	console.log(users[0]);
	const filteredUsers = allUsers.filter((user) => user.includes(text));
	setUsers(filteredUsers);
}, []);
```

Nesse exemplo ele congela a função, então no primeiro render, ele tem a lista de usuários estática, e faz um filtro dela e salva no state de usuários, porem, temos o console.log ali, e o que vai acontecer e que como esta congelada a função, ele vai mostrar o mesmo valor nesse log em toda execução, como arrumar isso?

```js
...
}, [users]);
```

Apenas adicionando o state users ao array de dependência do useCallback, sempre que o valor de users se alterar, ele vai fazer essa função renderizar novamente, o que obviamente, vai fazer os componentes que dependem desse valor, renderizar também, mas isso já era o esperado. 

Ainda assim, mesmo que o componente que usa o `users` renderize novamente, os demais componentes que usam outro estado ou algo do tipo, não serão renderizados novamente, o que para nos já esta ótimo.