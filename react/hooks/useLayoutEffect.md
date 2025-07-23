# `useLayoutEffect()`

O hook `useLayoutEffect` tem a mesma assinatura do `useEffect`, mas ele é executado **sincronamente** após todas as mutações do DOM serem concluídas, mas **antes** que o navegador pinte a tela.

Use isso para ler o layout do DOM e, de forma síncrona, re-renderizar. Atualizações agendadas dentro do `useLayoutEffect` serão processadas de forma síncrona antes que o navegador tenha a chance de pintar.

Tags: #react #hooks #lifecycle #dom

---

## `useEffect` vs `useLayoutEffect`

- **`useEffect` (Padrão):**
  - Executa **assincronamente** após a renderização e a pintura da tela.
  - Não bloqueia a pintura do navegador.
  - É a escolha certa para a maioria dos efeitos colaterais (fetching de dados, timers, etc.).

- **`useLayoutEffect` (Caso de Uso Específico):**
  - Executa **sincronamente** após a renderização, mas antes da pintura.
  - **Bloqueia a pintura do navegador**. Se o seu efeito for lento, a UI parecerá travada.
  - Útil para medições do DOM que precisam ser aplicadas antes que o usuário veja qualquer inconsistência visual.

**Regra geral:** Comece sempre com `useEffect`. Se você notar um *flicker* (piscada) na tela (o componente renderiza em um estado inicial e depois muda rapidamente para outro estado), `useLayoutEffect` pode ser a solução.

---

## Exemplo: Medindo a Posição de um Tooltip

Imagine que você precisa posicionar um tooltip com base no tamanho de um elemento. Se você usar `useEffect`, o tooltip pode aparecer no lugar errado por um instante e depois "pular" para a posição correta, causando um *flicker*.

```jsx
import React, { useState, useLayoutEffect, useRef } from 'react';

function Tooltip() {
  const buttonRef = useRef(null);
  const [tooltipHeight, setTooltipHeight] = useState(0);

  // Usamos useLayoutEffect para garantir que o cálculo seja feito
  // antes que o usuário veja a tela.
  useLayoutEffect(() => {
    if (buttonRef.current) {
      const { height } = buttonRef.current.getBoundingClientRect();
      setTooltipHeight(height);
    }
  }, []);

  return (
    <div>
      <button ref={buttonRef}>Passe o mouse sobre mim</button>
      <div style={{ marginTop: tooltipHeight + 5 }}>
        Este tooltip aparece abaixo do botão.
      </div>
    </div>
  );
}
```

Neste caso, `useLayoutEffect` garante que, no momento em que o componente é exibido na tela, o `marginTop` do tooltip já foi calculado e aplicado corretamente, evitando qualquer piscada visual.

---

## Links Relacionados

- [[useEffect]]
- [[useRef]]
- [[Renderização no Navegador]]