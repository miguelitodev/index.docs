# `useState()`

O hook `useState` permite que você adicione uma variável de estado a um componente de função. Ele é o hook mais fundamental e um dos mais usados no React.

Tags: #react #hooks #state

---

## Sintaxe

```javascript
const [state, setState] = useState(initialState);
```

- **`state`**: A variável que armazena o estado atual. Na primeira renderização, ela terá o valor de `initialState`.
- **`setState`**: Uma função que você usa para atualizar o valor de `state` e acionar uma nova renderização do componente.
- **`initialState`**: O valor inicial do estado. Pode ser um valor direto ou uma função que retorna o valor inicial (útil para inicializações custosas).

---

## Exemplos

### Contador Simples

```jsx
import React, { useState } from 'react';

function Counter() {
  // Declara uma nova variável de estado chamada "count"
  const [count, setCount] = useState(0);

  return (
    <div>
      <p>Você clicou {count} vezes</p>
      {/* Ao clicar, chama setCount para atualizar o estado */}
      <button onClick={() => setCount(count + 1)}>
        Clique aqui
      </button>
    </div>
  );
}
```

### Estado com Strings

```jsx
import React, { useState } from 'react';

function NameInput() {
  const [name, setName] = useState('Visitante');

  return (
    <div>
      <input 
        type="text" 
        value={name}
        onChange={e => setName(e.target.value)}
      />
      <p>Olá, {name}!</p>
    </div>
  );
}
```

---

## Atualizações Funcionais

Se o novo estado depende do estado anterior, é mais seguro usar a forma de função do `setState`. O React garante que você receberá o estado mais recente, evitando problemas de concorrência.

**Incorreto (pode falhar em alguns casos):**

```javascript
function Counter() {
  const [count, setCount] = useState(0);

  function handleIncrementThreeTimes() {
    setCount(count + 1); // count é 0
    setCount(count + 1); // count ainda é 0
    setCount(count + 1); // count ainda é 0
    // O resultado final será 1, não 3!
  }
  // ...
}
```

**Correto (usando atualização funcional):**

```javascript
function Counter() {
  const [count, setCount] = useState(0);

  function handleIncrementThreeTimes() {
    setCount(prevCount => prevCount + 1); // prevCount é 0 -> 1
    setCount(prevCount => prevCount + 1); // prevCount é 1 -> 2
    setCount(prevCount => prevCount + 1); // prevCount é 2 -> 3
    // O resultado final será 3.
  }
  // ...
}
```

---

## Links Relacionados

- [[useReducer]] (para lógicas de estado mais complexas)
- [[useEffect]] (para executar efeitos colaterais após o estado mudar)
- [[Ciclo de Vida do Componente]]