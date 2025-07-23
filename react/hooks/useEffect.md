# `useEffect()`

O hook `useEffect` permite que você execute efeitos colaterais (side effects) em componentes de função. Efeitos colaterais são ações que interagem com o "mundo exterior", fora do fluxo de renderização normal do React.

Exemplos de efeitos colaterais:
- Buscar dados de uma API
- Manipular o DOM diretamente
- Configurar e limpar subscriptions (como `setInterval` ou `addEventListener`)

Tags: #react #hooks #side-effects #lifecycle

---

## Sintaxe

```javascript
useEffect(() => {
  // Seu código de efeito colateral aqui

  // Opcional: função de limpeza
  return () => {
    // Código de limpeza (executado antes do próximo efeito ou ao desmontar)
  };
}, [dependency1, dependency2]); // Array de dependências
```

---

## Array de Dependências

O array de dependências controla *quando* o efeito é executado:

1.  **Sem array de dependências (omitido):**
    - O efeito é executado **após cada renderização**.
    - `useEffect(() => { ... });`

2.  **Array de dependências vazio (`[]`):**
    - O efeito é executado **apenas uma vez**, após a montagem do componente (equivalente a `componentDidMount` em componentes de classe).
    - `useEffect(() => { ... }, []);`

3.  **Array com dependências (`[prop, state]`):**
    - O efeito é executado **após a montagem e sempre que qualquer valor no array de dependências mudar**.
    - `useEffect(() => { ... }, [count, userId]);`

---

## Exemplos

### Buscando Dados (componentDidMount)

```jsx
import React, { useState, useEffect } from 'react';

function UserProfile({ userId }) {
  const [user, setUser] = useState(null);

  useEffect(() => {
    console.log('Buscando dados...');
    fetch(`https://api.example.com/users/${userId}`)
      .then(response => response.json())
      .then(data => setUser(data));
  }, [userId]); // Executa novamente se o userId mudar

  if (!user) {
    return <div>Carregando...</div>;
  }

  return <div>Nome: {user.name}</div>;
}
```

### Função de Limpeza (componentWillUnmount)

A função retornada pelo `useEffect` é usada para limpeza. Ela é executada antes do componente ser removido do DOM e antes de o efeito ser executado novamente.

```jsx
import React, { useState, useEffect } from 'react';

function Timer() {
  const [seconds, setSeconds] = useState(0);

  useEffect(() => {
    const intervalId = setInterval(() => {
      setSeconds(s => s + 1);
    }, 1000);

    // Função de limpeza
    return () => {
      console.log('Limpando o intervalo');
      clearInterval(intervalId);
    };
  }, []); // Array vazio, então a limpeza ocorre ao desmontar

  return <div>Timer: {seconds}s</div>;
}
```

---

## Links Relacionados

- [[useState]]
- [[useLayoutEffect]] (para efeitos que precisam ser síncronos com a pintura do navegador)
- [[useRef]] (para manter referências a valores sem causar re-renderizações)