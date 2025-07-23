# `useMemo()`

O hook `useMemo` retorna um **valor memorizado**. Ele só recalcula o valor quando uma de suas dependências muda.

Isso é usado para otimizar a performance, evitando cálculos caros em cada renderização.

Tags: #react #hooks #performance

---

## Sintaxe

```javascript
const memoizedValue = useMemo(() => computeExpensiveValue(a, b), [a, b]);
```

- `computeExpensiveValue`: A função que calcula o valor. Ela será chamada apenas quando as dependências mudarem.
- `[a, b]`: O array de dependências. Se os valores de `a` ou `b` mudarem entre renderizações, a função será re-executada.

---

## `useCallback` vs `useMemo`

- `useCallback(() => fn, deps)` é equivalente a `useMemo(() => () => fn, deps)`.
- **`useCallback` memoriza a função em si.**
- **`useMemo` memoriza o resultado (o valor de retorno) da função.**

---

## Exemplo: Evitando Cálculos Pesados

Imagine uma função que filtra uma lista enorme de itens. Se você a chamar diretamente no corpo do componente, ela será executada em toda renderização, mesmo que a lista ou o filtro não tenham mudado.

```jsx
import React, { useState, useMemo } from 'react';

// Suponha que esta é uma lista muito grande
const allItems = [...];

function ItemList({ filterTerm }) {
  // useMemo garante que o filtro só seja re-executado se
  // `allItems` ou `filterTerm` mudarem.
  const visibleItems = useMemo(() => {
    console.log('Executando filtro pesado...');
    return allItems.filter(item => item.name.includes(filterTerm));
  }, [filterTerm]); // `allItems` é constante, então só depende de `filterTerm`

  return (
    <ul>
      {visibleItems.map(item => (
        <li key={item.id}>{item.name}</li>
      ))}
    </ul>
  );
}

function App() {
  const [filter, setFilter] = useState('');
  const [theme, setTheme] = useState('light'); // Apenas para causar re-renderização

  return (
    <div>
      <input value={filter} onChange={e => setFilter(e.target.value)} />
      <button onClick={() => setTheme(t => t === 'light' ? 'dark' : 'light')}>
        Mudar Tema
      </button>
      <ItemList filterTerm={filter} />
    </div>
  );
}
```

Neste exemplo, quando você clica em "Mudar Tema", o componente `App` renderiza novamente. No entanto, a mensagem "Executando filtro pesado..." não aparecerá no console, porque `filterTerm` não mudou, e `useMemo` retorna o valor memorizado para `visibleItems`.

---

## Links Relacionados

- [[useCallback]]
- [[memo]]
- [[Otimização de Performance]]
