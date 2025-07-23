**React rewards** permite adicionar micro-interações ao seu app, recompensando os usuários com confetes, emojis ou balões. Fácil de integrar e altamente personalizável!

- 🌲 Tree-shakeable
- 🕵️‍♀️ Feito com TypeScript
- 📦 3.6kB gzipped

Inspirado no [react-dom-confetti](https://github.com/simonwep/react-dom-confetti).

---

## 🚀 Instalação

Instale via npm ou yarn:

```bash
npm install react-rewards
# ou
yarn add react-rewards
```

---

## ⚡ Uso

### Recompensa Única

```tsx
import { useReward } from 'react-rewards';

const { reward, isAnimating } = useReward('rewardId', 'confetti');

<button disabled={isAnimating} onClick={reward}>
  <span id="rewardId" />
  🎉 Clique em mim!
</button>
```

### Múltiplas Recompensas

```tsx
import { useReward } from 'react-rewards';

const { reward: confettiReward, isAnimating: isConfettiAnimating } = useReward('confettiReward', 'confetti');
const { reward: balloonsReward, isAnimating: isBalloonsAnimating } = useReward('balloonsReward', 'balloons');

<button
  disabled={isConfettiAnimating || isBalloonsAnimating}
  onClick={() => {
    confettiReward();
    balloonsReward();
  }}
>
  <span id="confettiReward" />
  <span id="balloonsReward" />
  🎉
</button>
```

---

## 🎨 Tipos de Animação

- **confetti** 🎊
- **balloons** 🎈
- **emoji** 😍

---

## 🛠️ Opções de Configuração

### Configuração do Confetti

- **fps**: Frames por segundo. Padrão: `60`
- **lifetime**: Tempo de vida dos confetes em ms. Padrão: `200`
- **angle**: Direção inicial das partículas em graus. Padrão: `90`
- **decay**: Quanto a velocidade diminui a cada quadro. Padrão: `0.94`
- **spread**: Espalhamento das partículas em graus. Padrão: `45`
- **startVelocity**: Velocidade inicial das partículas. Padrão: `35`
- **elementCount**: Quantidade de partículas. Padrão: `50`
- **elementSize**: Tamanho das partículas em px. Padrão: `8`
- **zIndex**: Z-index das partículas. Padrão: `0`
- **position**: Posição das partículas (`absolute`, `fixed`, etc.). Padrão: `fixed`
- **colors**: Cores usadas para gerar os confetes. Padrão: `['#A45BF1', '#25C6F6', '#72F753', '#F76C88', '#F5F770']`
- **onAnimationComplete**: Função executada quando a animação termina. Padrão: `undefined`

### Configuração dos Balões

- **fps**: Frames por segundo. Padrão: `60`
- **lifetime**: Tempo de vida dos balões em ms. Padrão: `600`
- **angle**: Direção inicial dos balões em graus. Padrão: `90`
- **decay**: Quanto a velocidade diminui a cada quadro. Padrão: `0.999`
- **spread**: Espalhamento dos balões em graus. Padrão: `50`
- **startVelocity**: Velocidade inicial dos balões. Padrão: `3`
- **elementCount**: Quantidade de balões. Padrão: `10`
- **elementSize**: Tamanho dos balões em px. Padrão: `20`
- **zIndex**: Z-index dos balões. Padrão: `0`
- **position**: Posição dos balões (`absolute`, `fixed`, etc.). Padrão: `fixed`
- **colors**: Cores usadas para gerar os balões. Padrão: `['#A45BF1', '#25C6F6', '#72F753', '#F76C88', '#F5F770']`
- **onAnimationComplete**: Função executada quando a animação termina. Padrão: `undefined`

### Configuração dos Emojis

- **fps**: Frames por segundo. Padrão: `60`
- **lifetime**: Tempo de vida dos emojis em ms. Padrão: `200`
- **angle**: Direção inicial dos emojis em graus. Padrão: `90`
- **decay**: Quanto a velocidade diminui a cada quadro. Padrão: `0.94`
- **spread**: Espalhamento dos emojis em graus. Padrão: `45`
- **rotate**: Habilitar ou desabilitar rotação dos emojis. Padrão: `true`
- **startVelocity**: Velocidade inicial dos emojis. Padrão: `35`
- **elementCount**: Quantidade de emojis. Padrão: `20`
- **elementSize**: Tamanho dos emojis em px. Padrão: `25`
- **zIndex**: Z-index dos emojis. Padrão: `0`
- **position**: Posição dos emojis (`absolute`, `fixed`, etc.). Padrão: `fixed`
- **emoji**: Emojis para gerar. Padrão: `['🤓', '😊', '🥳']`
- **onAnimationComplete**: Função executada quando a animação termina. Padrão: `undefined`

---

## 🔗 Links

- **GitHub**: [react-rewards](https://github.com/catdad/react-rewards)
- **Demo**: [react-rewards.netlify.app](https://react-rewards.netlify.app/)

---

Divirta-se com as recompensas! 🎉