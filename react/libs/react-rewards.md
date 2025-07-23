# React Rewards

`react-rewards` é uma biblioteca divertida para adicionar micro-interações e efeitos de recompensa (como confetes ou emojis explodindo) aos seus componentes React.

É uma ótima maneira de adicionar um toque de delight e feedback positivo para as ações do usuário.

Tags: #react #libs #ui #animation #micro-interactions

---

## Instalação

```bash
npm install react-rewards
# ou
yarn add react-rewards
```

---

## Como Usar

A biblioteca fornece um hook `useReward` e um componente `Reward`.

1.  **`useReward`:** Hook que retorna um objeto com a função `reward` e o `isAnimating`.
2.  **`Reward`:** Componente que você posiciona no local onde a animação deve ocorrer. Ele é controlado pela função `reward`.

### Exemplo

```jsx
import React from 'react';
import { useReward } from 'react-rewards';

const LikeButton = () => {
  const { reward, isAnimating } = useReward('like-button-reward', 'balloons');

  const handleClick = () => {
    reward();
  };

  return (
    <button onClick={handleClick} disabled={isAnimating}>
      {/* O ID 'like-button-reward' conecta o hook ao componente Reward */}
      <span id="like-button-reward" />
      Like!
    </button>
  );
};
```

**Explicação:**
- `useReward('like-button-reward', 'balloons')`: 
  - O primeiro argumento é um ID único que conecta o hook ao elemento que servirá de âncora para a animação.
  - O segundo argumento é o tipo de animação (`balloons`, `confetti`, `emoji`).
- `reward()`: Função que dispara a animação.
- `<span id="like-button-reward" />`: Elemento âncora. A animação de balões sairá deste ponto.

---

## Tipos de Recompensa

- `confetti`: Lança confetes coloridos.
- `balloons`: Lança balões coloridos.
- `emoji`: Lança emojis aleatórios. Você pode customizar quais emojis usar.

### Exemplo com Emoji Customizado

```jsx
const { reward } = useReward('reward-id', 'emoji', { 
  emoji: ['❤️', '👍', '🎉'] 
});
```

---

## Links Relacionados

- [[Framer Motion]] (para animações mais complexas)
- [[UI/UX Design]]
- [[Gamification]]
