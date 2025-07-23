# `useCallback()`

O hook `useCallback` retorna uma versão memorizada de uma função (callback). Ele só recria a função se uma de suas dependências mudar.

Isso é útil para otimização de performance, especialmente ao passar callbacks para componentes filhos otimizados que dependem da igualdade de referência para evitar renderizações desnecessárias.

Tags: #react #hooks #performance

---

## Sintaxe

```javascript
const memoizedCallback = useCallback(
  () => {
    doSomething(a, b);
  },
  [a, b], // Array de dependências
);
```

- O `useCallback` retornará a mesma instância da função entre renderizações, a menos que os valores no array de dependências (`[a, b]`) mudem.

---

## Problema Comum

Quando você passa uma função para um componente filho, uma nova função é criada a cada renderização do componente pai. Se o componente filho for otimizado com `React.memo`, ele ainda assim renderizará novamente porque a função (prop) é sempre "nova".

## Exemplo

```jsx
import React, { useState, useCallback } from 'react';
import Button from './Button'; // Suponha que Button usa React.memo

const ParentComponent = () => {
  const [count, setCount] = useState(0);
  const [theme, setTheme] = useState('light');

  // Sem useCallback, uma nova handleClick é criada a cada renderização
  // const handleClick = () => {
  //   setCount(count + 1);
  // };

  // Com useCallback, a função só é recriada se `count` mudar.
  // No entanto, para um simples `setCount`, a dependência não é necessária
  // porque o React garante que `setCount` é estável.
  const handleClick = useCallback(() => {
    setCount(prevCount => prevCount + 1);
  }, []); // Array de dependências vazio, a função nunca é recriada

  return (
    <div>
      <p>Contador: {count}</p>
      <button onClick={() => setTheme(theme === 'light' ? 'dark' : 'light')}>
        Mudar Tema
      </button>
      <Button onClick={handleClick}>Incrementar</Button>
    </div>
  );
};
```

Neste exemplo, mesmo que `ParentComponent` renderize novamente por causa da mudança de tema, o componente `Button` não renderizará novamente, pois a prop `onClick` (a função `handleClick`) é a mesma instância memorizada pelo `useCallback`.

---

## Links Relacionados

- [[useMemo]]
- [[memo]]
