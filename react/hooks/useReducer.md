
---

Assim como o `useState`, o `useReducer` também gerencia estados dentro da aplicação. No entanto, ele segue um padrão semelhante ao Redux, onde as atualizações de estado são feitas por meio de ações enviadas a um reducer. Isso pode torná-lo mais complexo, pois exige mais código, mas quando há muitos estados interdependentes, ele pode ser uma ótima opção. Vamos entender melhor com um exemplo prático.

Vamos usar TypeScript para criar um contador simples. Precisamos definir o `State` e a `Action`, que representa as mudanças possíveis no estado. O contador pode aumentar ou diminuir, então teremos duas ações disponíveis.

```ts
interface State {
  count: number;
  error: string | null;
}

interface Action {
  type: 'increment' | 'decrement';
}
```

Agora, a parte mais importante do Hook: sua declaração no código. A sintaxe é semelhante ao `useState`, pois desestruturamos o `state` e o `dispatch`. O `useReducer` recebe dois parâmetros obrigatórios: uma função reducer, que gerencia as atualizações do estado, e o estado inicial.

```ts
const [state, dispatch] = useReducer(reducer, {
  count: 0,
  error: null,
});
```

Aqui está o código JSX. Ele exibe a contagem, um campo de erro (caso exista) e dois botões para incrementar e decrementar o contador. Nos botões, utilizamos `dispatch`, passando o tipo da ação explicitamente.

```tsx
return (
  <div>
    <div>Count: {state.count}</div>
    {state.error && <div>{state.error}</div>}
    <button className="mb-2" onClick={() => dispatch({ type: 'increment' })}>
      Increment
    </button>
    <button onClick={() => dispatch({ type: 'decrement' })}>
      Decrement
    </button>
  </div>
);
```

Por fim, a função chave do Hook: o reducer. Ele recebe o `state` e a `action`. O `state` é o estado atual e a `action` representa a mudança a ser feita.

```ts
function reducer(state: State, action: Action) {
  const { type } = action;
  ...
}
```

Dentro do reducer, usamos um `switch case` para definir as regras de atualização do estado.

- No caso de `increment`, o contador aumenta em 1, mas há um limite de 5. Se o limite for atingido, um erro é exibido.
- No caso de `decrement`, o contador diminui em 1, mas o valor mínimo é 0. Se atingir esse limite, um erro é mostrado.

```ts
switch (type) {
  case 'increment': {
    const newCount = state.count + 1;
    const hasError = newCount > 5;
    return {
      ...state,
      count: hasError ? state.count : newCount,
      error: hasError ? 'Maximum reached' : null,
    };
  }

  case 'decrement': {
    const newCount = state.count - 1;
    const hasError = newCount < 0;
    return {
      ...state,
      count: hasError ? state.count : newCount,
      error: hasError ? 'Minimum reached' : null,
    };
  }

  default:
    return state;
}
```

### **Quando usar `useReducer`?**

Nem sempre o `useReducer` é necessário. Ele é útil em componentes mais complexos, com múltiplas transições de estado e regras de negócio mais elaboradas. Um bom exemplo é um componente de input que pode assumir diferentes estados e tipos. Além disso, pode ser útil ao refatorar componentes mais antigos ou organizar melhor a lógica de estado.

Fora esses casos, o `useState` geralmente é suficiente.

---
