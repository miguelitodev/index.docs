Usado para disponibilizar dados em toda a aplicação, para qualquer componente onde quer que ele esteja, para não ter que passar esses dados via props.

Para explicar melhor tenho uns trechos de código aqui, então para criar o context, usamos o createContext, podemos passar um valor inicial para ele se quisermos, ele que vai encapsular o bloco da app que vamos disponibilizar os dados, e geralmente utilizamos essa nomenclatura. E então criamos um hook para disponibilizar os dados para onde quisermos utilizar.

E temos ainda, que criar esse hook, para assegurar que quem quiser utilizar, utilize apenas dentro do escopo do `DashboardContext` e ainda para caso o `user` ainda não esteja no nosso context

```js
// context.js

import { createContext, useContext } from 'react';

export const DashboardContext = createContext(undefined);

export function useUserContext() {
  const user = useContext(DashboardContext);

  if (user === undefined) {
    throw new Error('useUserContext must be used with a DashboardContext');
  }

  return user;
}
```

Nesse componente, temos um state simples, que recebe dois valores inciais, e e passado ali para o nosso `DashboardContext` pela props value, essa prop permite que todos os componentes que estiverem em volta dela, possam acessar esse valor de user. Nota-se que o .Provider esta ali, ele serve exatamente para isso, prover os dados para todos os componentes em seu escopo.

```js
// index.js

export default function Demo({}) {
	const [user] = useState({
		isSubscribed: true,
		name: 'You',
	});

	return (
		<div>
			<DashboardContext.Provider value={user}>
				<Dashboard />
			</DashboardContext.Provider>
		</div>
	);
}
```

Dando um exemplo de onde quer que utilizaremos, importamos o hook que criamos la no arquivo context, e pegamos o valor de user que já esta sendo retornado, ai basta utilizarmos ele

```js
// Components.js

import { useUserContext } from './context';

export function Sidebar({}: SidebarProps) {
  const user = useUserContext();

  return (
    <div>
      <div>{user.name}</div>
      <div>Subscription Status: {user.isSubscribed}</div>
    </div>
  );
}

export function Profile({}: ProfileProps) {
  const user = useUserContext();

  return <div>{user.name}</div>;
}

```