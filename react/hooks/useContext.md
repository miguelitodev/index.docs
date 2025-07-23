# `useContext()`

O hook `useContext` permite que você leia e se inscreva em um contexto do React. Ele aceita um objeto de contexto (o valor retornado de `React.createContext`) e retorna o valor atual do contexto.

É uma maneira de passar dados através da árvore de componentes sem ter que passar props manualmente em todos os níveis (evitando o "prop drilling").

Tags: #react #hooks #context #state-management

---

## Sintaxe

```javascript
const value = useContext(MyContext);
```

- `MyContext`: O objeto de contexto que você deseja ler. Você deve criá-lo primeiro com `React.createContext`.

---

## Exemplo Completo

**1. Crie o Contexto**

Primeiro, crie um arquivo para o seu contexto. Isso permite que você o importe em qualquer componente que precise dele.

```javascript
// ThemeContext.js
import { createContext } from 'react';

export const ThemeContext = createContext('light'); // 'light' é o valor padrão
```

**2. Forneça o Contexto (Provider)**

No componente de nível superior, use o `Provider` para envolver os componentes que precisam de acesso ao contexto. Você pode passar um valor dinâmico para a prop `value`.

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

Agora, qualquer componente filho (não importa quão profundo) pode usar o hook `useContext` para ler o valor do contexto.

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

Quando o botão em `App.js` é clicado, o `value` do `Provider` muda, e o componente `Toolbar` renderiza novamente com o novo valor do tema.

---

## Links Relacionados

- [[useState]]
- [[useReducer]] (frequentemente usado em conjunto para gerenciar estados mais complexos)
- [[Prop Drilling]] (o problema que o `useContext` resolve)
