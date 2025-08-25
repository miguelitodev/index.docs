---
tags:
  - react
  - libs
  - icons
  - ui
related:
  - "[[Styled Components]]"
  - "[[UI/UX Design]]"
creation-date: "2025-08-25"
---

# React Icons

> [!NOTE] Summary
> `react-icons` é uma biblioteca que permite incluir facilmente ícones populares (Font Awesome, Material Icons, Ant Design Icons, etc.) em seus projetos React.

## Syntax

### Instalação

```bash
npm install react-icons --save
# ou
yarn add react-icons
```

### Como Usar

1.  **Encontre um ícone:** Navegue pelo site da [React Icons](https://react-icons.github.io/react-icons/) para encontrar o ícone que você precisa.
2.  **Importe o ícone:** Importe o componente do pacote de ícones apropriado.
3.  **Renderize o componente:** Use o ícone como um componente React.

### Exemplo

```jsx
import React from 'react';
// Importa o ícone de "carrinho de compras" do Font Awesome
import { FaShoppingCart } from 'react-icons/fa';
// Importa o ícone de "configurações" do Material Design
import { MdSettings } from 'react-icons/md';

function MyComponent() {
  return (
    <div>
      <h2>
        <FaShoppingCart /> Meu Carrinho
      </h2>
      <button>
        <MdSettings /> Configurações
      </button>
    </div>
  );
}
```

## Use Cases

### Customização

You can use CSS to style the icons (color, size, etc.) or use `IconContext` to apply styles to all icons at once.

### Exemplo com `IconContext`

```jsx
import { IconContext } from "react-icons";
import { FaBeer } from 'react-icons/fa';

function App() {
  return (
    // Todos os ícones dentro deste Provider terão a cor verde e tamanho 2em
    <IconContext.Provider value={{ color: "green", size: "2em" }}>
      <div>
        <h3>Lets go for a <FaBeer />?</h3>
      </div>
    </IconContext.Provider>
  );
}
```

## See Also

- [[Styled Components]]
- [[UI/UX Design]]

## References

- [React Icons Documentation](https://react-icons.github.io/react-icons/)