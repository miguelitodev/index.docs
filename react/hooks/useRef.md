# `useRef()`

O hook `useRef` retorna um objeto ref mutável cuja propriedade `.current` é inicializada com o argumento passado (`initialValue`). O objeto retornado persistirá durante todo o ciclo de vida do componente.

`useRef` tem dois casos de uso principais:

1.  **Acessar elementos do DOM.**
2.  **Manter uma variável mutável que não causa re-renderização quando alterada.**

Tags: #react #hooks #dom #reference

---

## Sintaxe

```javascript
const myRef = useRef(initialValue);
```

- `myRef.current`: Acessa o valor atual da referência.

---

## Caso de Uso 1: Acessando o DOM

Este é o uso mais comum. Você pode anexar uma ref a um elemento JSX para obter acesso direto a ele.

### Exemplo: Focar em um Input

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

---

## Caso de Uso 2: Variável de Instância

Às vezes, você precisa de um valor que persista entre renderizações, mas que **não** acione uma nova renderização quando muda. `useState` não serve, pois ele causa re-renderização.

`useRef` é perfeito para isso.

### Exemplo: Armazenando o ID de um Intervalo

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

Neste caso, mudar `intervalRef.current` não causa uma nova renderização do componente `Timer`. Ele apenas armazena o valor para que possamos acessá-lo mais tarde na função `handleStop` ou na limpeza do `useEffect`.

---

## Links Relacionados

- [[useState]]
- [[useEffect]]
- [[Manipulação do DOM]]
