---
tags:
  - react
  - hooks
  - lifecycle
  - side-effects
related:
  - "[[useState]]"
  - "[[useLayoutEffect]]"
creation-date: "2025-08-25"
---

# `useEffect()`

> [!NOTE] Summary
> O hook `useEffect` permite que você execute "efeitos colaterais" em componentes funcionais. Efeitos colaterais são operações que interagem com o mundo exterior, como chamadas de API, manipulação direta do DOM, subscriptions, timers, etc.

## Syntax

```javascript
useEffect(() => {
  // Código do efeito colateral
  return () => {
    // Função de limpeza (opcional)
  };
}, [dependencies]); // Array de dependências (opcional)
```

- **Função de efeito:** A função que contém a lógica do seu efeito colateral. Ela é executada após cada renderização do componente, a menos que as dependências impeçam.
- **Função de limpeza (opcional):** Se a sua função de efeito retornar uma função, essa função será executada quando o componente for desmontado ou antes que o efeito seja re-executado (se as dependências mudarem). É usada para limpar recursos (ex: cancelar subscriptions, limpar timers).
- **Array de dependências (opcional):** Um array de valores que o efeito "observa". O efeito só será re-executado se um desses valores mudar entre as renderizações.
  - Se o array estiver vazio (`[]`), o efeito será executado apenas uma vez, após a montagem inicial do componente (comportamento de `componentDidMount`).
  - Se o array for omitido, o efeito será executado após *cada* renderização do componente.

## Use Cases

- **Chamadas de API:** Buscar dados de um servidor.
- **Manipulação do DOM:** Adicionar ou remover event listeners, modificar o título da página.
- **Timers:** Configurar `setInterval` ou `setTimeout`.
- **Subscriptions:** Inscrever-se em eventos externos.
- **Sincronização com sistemas externos:** Interagir com bibliotecas de terceiros.

### Exemplo: Contador com Título da Página

```jsx
import React, { useState, useEffect } from 'react';

function Counter() {
  const [count, setCount] = useState(0);

  useEffect(() => {
    // Este efeito atualiza o título da página
    document.title = `Você clicou ${count} vezes`;

    // Função de limpeza (opcional): executada antes da próxima execução do efeito ou na desmontagem
    return () => {
      console.log('Limpando efeito anterior...');
    };
  }, [count]); // O efeito será re-executado sempre que 'count' mudar

  return (
    <div>
      <p>Você clicou {count} vezes</p>
      <button onClick={() => setCount(count + 1)}>
        Clique-me
      </button>
    </div>
  );
}
```

## See Also

- [[useState]]
- [[useLayoutEffect]]

## References

- [React Docs: `useEffect`](https://react.dev/reference/react/useEffect)
