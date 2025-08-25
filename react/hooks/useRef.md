---
tags:
  - react
  - hooks
  - dom
  - reference
related:
  - "[[useState]]"
  - "[[useEffect]]"
  - "[[Manipulação do DOM]]"
creation-date: "2025-08-25"
---

# `useRef()`

> [!NOTE] Summary
> O hook `useRef` retorna um objeto ref mutável cuja propriedade `.current` é inicializada com o argumento passado (`initialValue`). O objeto retornado persistirá durante todo o ciclo de vida do componente.

## Syntax

```javascript
const myRef = useRef(initialValue);
```

- `myRef.current`: Acessa o valor atual da referência.

## Use Cases

`useRef` tem dois casos de uso principais:

1.  **Acessar elementos do DOM.**
2.  **Manter uma variável mutável que não causa re-renderização quando alterada.**

### Caso de Uso 1: Acessando o DOM

```jsx
import React, { useRef, useEffect } from 'react';

function TextInputWithFocusButton() {
  // 1. Crie a ref
  const inputEl = useRef(null);

  const onButtonClick = () => {
    // 3. Use a ref para acessar o elemento do DOM e chamar seus métodos
    inputEl.current.focus();
  };

  useEffect(() => {
    // Foca no input assim que o componente é montado
    inputEl.current.focus();
  }, []);

  return (
    <>
      {/* 2. Anexe a ref ao elemento JSX */}
      <input ref={inputEl} type="text" />
      <button onClick={onButtonClick}>Focar no input</button>
    </>
  );
}
```

### Caso de Uso 2: Variável de Instância

```jsx
import React, { useState, useRef, useEffect } from 'react';

function Timer() {
  const [seconds, setSeconds] = useState(0);
  // Use ref para armazenar o ID do intervalo
  const intervalRef = useRef(null);

  useEffect(() => {
    // Inicia o timer na montagem
    intervalRef.current = setInterval(() => {
      setSeconds(prev => prev + 1);
    }, 1000);

    // Limpa o intervalo na desmontagem
    return () => {
      clearInterval(intervalRef.current);
    };
  }, []);

  const handleStop = () => {
    clearInterval(intervalRef.current);
  };

  return (
    <div>
      <p>Timer: {seconds}s</p>
      <button onClick={handleStop}>Parar</button>
    </div>
  );
}
```

## See Also

- [[useState]]
- [[useEffect]]
- [[Manipulação do DOM]]

## References

- [React Docs: `useRef`](https://react.dev/reference/react/useRef)