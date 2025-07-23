# `React.memo()`

`React.memo` é um Higher-Order Component (HOC) que memoriza o resultado de um componente de função. Ele evita que o componente seja renderizado novamente se suas props não mudaram.

É uma otimização de performance.

Tags: #react #performance #hoc #hooks

---

## Quando Usar

Use `memo` para componentes funcionais que:

1.  Renderizam com frequência.
2.  Recebem as mesmas props na maior parte do tempo.
3.  São razoavelmente complexos para renderizar (ou seja, a memorização é mais barata que a renderização).

Não use `memo` em todos os lugares. A comparação de props tem um custo, e pode ser mais caro que a própria renderização para componentes simples.

---

## Exemplo

Imagine um componente `UserProfile` que recebe `name` e `avatar`.

```jsx
import React from 'react';

const UserProfile = ({ name, avatar }) => {
  console.log(`Renderizando UserProfile para ${name}`);
  return (
    <div>
      <img src={avatar} alt={name} />
      <p>{name}</p>
    </div>
  );
};

export default React.memo(UserProfile);
```

Agora, se um componente pai renderizar novamente, mas as props `name` e `avatar` para `UserProfile` permanecerem as mesmas, `UserProfile` não será renderizado novamente, e a mensagem no console não aparecerá.

### Controlando a Comparação

Você pode passar uma segunda função para `memo` para uma lógica de comparação personalizada.

```jsx
const areEqual = (prevProps, nextProps) => {
  // Retorna true se as props forem iguais, evitando a re-renderização
  // Retorna false se as props forem diferentes, permitindo a re-renderização
  return prevProps.user.id === nextProps.user.id;
};

export default React.memo(UserProfile, areEqual);
```

---

## Links Relacionados

- [[useCallback]]
- [[useMemo]]
- [[shouldComponentUpdate]] (para componentes de classe)
