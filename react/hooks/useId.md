# `useId()`

O hook `useId` gera IDs únicos e estáveis que podem ser usados tanto no lado do servidor (SSR - Server-Side Rendering) quanto no cliente. Isso é útil para evitar "mismatches" de hidratação em componentes que precisam de IDs, como `label` e `input`.

Tags: #react #hooks #accessibility #ssr

---

## Problema que Resolve

Ao criar componentes reutilizáveis, você frequentemente precisa conectar um `<label>` a um `<input>`. Isso é feito com os atributos `htmlFor` e `id`.

```html
<label htmlFor="my-input">Meu Input</label>
<input id="my-input" type="text" />
```

Se você renderizar este componente várias vezes na mesma página, terá IDs duplicados, o que é inválido em HTML e quebra a acessibilidade. `useId` resolve isso gerando um ID garantido como único.

---

## Sintaxe

```javascript
const uniqueId = useId();
```

- O hook não recebe argumentos.
- O ID gerado é estável entre renderizações.

---

## Exemplo

```jsx
import React, { useId } from 'react';

function FormField() {
  // Gera um ID único, por exemplo: ":r0:"
  const id = useId();

  return (
    <div>
      {/* O `htmlFor` agora corresponde ao `id` do input */}
      <label htmlFor={id}>Seu nome:</label>
      <input id={id} type="text" />
    </div>
  );
}

function App() {
  return (
    <form>
      {/* Cada FormField terá um ID único, evitando conflitos */}
      <FormField />
      <hr />
      <FormField />
    </form>
  );
}
```

### Múltiplos IDs no Mesmo Componente

Se você precisar de vários IDs no mesmo componente, chame `useId` e adicione sufixos.

```jsx
function AdvancedForm() {
  const id = useId();

  return (
    <div>
      <label htmlFor={`${id}-firstName`}>Nome:</label>
      <input id={`${id}-firstName`} type="text" />

      <label htmlFor={`${id}-lastName`}>Sobrenome:</label>
      <input id={`${id}-lastName`} type="text" />
    </div>
  );
}
```

---

## Links Relacionados

- [[Server-Side Rendering (SSR)]]
- [[Acessibilidade (a11y)]]