---
tags:
  - react
  - hooks
  - performance
related:
  - "[[useMemo]]"
  - "[[memo]]"
creation-date: "2025-08-25"
---

# `useCallback()`

> [!NOTE] Summary
> O hook `useCallback` retorna uma versão memorizada de uma função (callback). Ele só recria a função se uma de suas dependências mudar.

## Syntax

```javascript
const memoizedCallback = useCallback(
  () => {
    doSomething(a, b);
  },
  [a, b], // Array de dependências
);
```

- O `useCallback` retornará a mesma instância da função entre renderizações, a menos que os valores no array de dependências (`[a, b]`) mudem.

## Use Cases

Isso é útil para otimização de performance, especialmente ao passar callbacks para componentes filhos otimizados que dependem da igualdade de referência para evitar renderizações desnecessárias.

```jsx
import React, { useState, useCallback } from 'react';
import Button from './Button'; // Suponha que Button usa React.memo

const ParentComponent = () => {
  const [count, setCount] = useState(0);
  const [theme, setTheme] = useState('light');

  // Com useCallback, a função só é recriada se `count` mudar.
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

## See Also

- [[useMemo]]
- [[memo]]

## References

- [React Docs: `useCallback`](https://react.dev/reference/react/useCallback)