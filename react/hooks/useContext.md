---
tags:
  - react
  - hooks
  - context
  - state-management
related:
  - "[[useState]]"
  - "[[useReducer]]"
  - "[[Prop Drilling]]"
creation-date: "2025-08-25"
---

# `useContext()`

> [!NOTE] Summary
> O hook `useContext` permite que você leia e se inscreva em um contexto do React. Ele aceita um objeto de contexto (o valor retornado de `React.createContext`) e retorna o valor atual do contexto.

## Syntax

```javascript
const value = useContext(MyContext);
```

- `MyContext`: O objeto de contexto que você deseja ler. Você deve criá-lo primeiro com `React.createContext`.

## Use Cases

É uma maneira de passar dados através da árvore de componentes sem ter que passar props manualmente em todos os níveis (evitando o "prop drilling").

### Exemplo Completo

**1. Crie o Contexto**

```javascript
// ThemeContext.js
import { createContext } from 'react';

export const ThemeContext = createContext('light'); // 'light' é o valor padrão
```

**2. Forneça o Contexto (Provider)**

```jsx
// App.js
import React, { useState } from 'react';
import { ThemeContext } from './ThemeContext';
import Toolbar from './Toolbar';

function App() {
  const [theme, setTheme] = useState('dark');

  return (
    <ThemeContext.Provider value={theme}>
      <Toolbar />
      <button onClick={() => setTheme(theme === 'light' ? 'dark' : 'light')}>
        Mudar Tema
      </button>
    </ThemeContext.Provider>
  );
}
```

**3. Consuma o Contexto (useContext)**

```jsx
// Toolbar.js
import React, { useContext } from 'react';
import { ThemeContext } from './ThemeContext';

function Toolbar() {
  const theme = useContext(ThemeContext);

  const style = {
    background: theme === 'dark' ? '#333' : '#FFF',
    color: theme === 'dark' ? '#FFF' : '#333',
    padding: '1rem',
  };

  return <div style={style}>O tema atual é {theme}</div>;
}
```

## See Also

- [[useState]]
- [[useReducer]]
- [[Prop Drilling]]

## References

- [React Docs: `useContext`](https://react.dev/reference/react/useContext)