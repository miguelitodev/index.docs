---
tags:
  - react
  - performance
  - hoc
  - hooks
related:
  - "[[useCallback]]"
  - "[[useMemo]]"
  - "[[shouldComponentUpdate]]"
creation-date: "2025-08-25"
---

# `React.memo()`

> [!NOTE] Summary
> `React.memo` é um Higher-Order Component (HOC) que memoriza o resultado de um componente de função. Ele evita que o componente seja renderizado novamente se suas props não mudaram.

## Syntax

```jsx
const MyComponent = React.memo(function MyComponent(props) {
  /* render using props */
});
```

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

## Use Cases

Use `memo` para componentes funcionais que:

1.  Renderizam com frequência.
2.  Recebem as mesmas props na maior parte do tempo.
3.  São razoavelmente complexos para renderizar (ou seja, a memorização é mais barata que a renderização).

## See Also

- [[useCallback]]
- [[useMemo]]
- [[shouldComponentUpdate]]

## References

- [React Docs: `memo`](https://react.dev/reference/react/memo)