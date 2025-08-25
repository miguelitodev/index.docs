---
tags:
  - react
  - libs
  - state-management
  - performance
  - frontend
related:
  - "[[React Hooks]]"
  - "[[Gerenciamento de Estado]]"
  - "[[Performance em React]]"
creation-date: "2025-08-25"
---

# 🐻 Zustand - Gerenciamento de Estado Simples e Performático

> [!NOTE] Summary
> `Zustand` é uma biblioteca de gerenciamento de estado para React, pequena, rápida e flexível. Ela se baseia em hooks e oferece uma API mínima e intuitiva, removendo grande parte da complexidade e do _boilerplate_ associados a outras libs como o Redux.

## Syntax

### O Store (`create`)

Tudo começa com a função `create`. Ela recebe uma função que define o estado inicial e as ações que podem modificá-lo.

- **`state`**: Os dados que você quer armazenar (ex: `count`, `notes`).
- **`set`**: A função usada para atualizar o estado. Ela é imutável por baixo dos panos; você sempre descreve o _novo_ estado.
- **Ações**: Funções que vivem dentro do store e que usam o `set` para realizar as atualizações.

```typescript
// store.ts
import { create } from "zustand";

type CounterState = {
  count: number;
  increment: () => void;
  decrement: () => void;
};

// 'create' retorna um hook que usaremos nos componentes
export const useCounterStore = create<CounterState>((set) => ({
  count: 0,
  // Para atualizar, passamos uma função ao 'set' que recebe o estado atual
  increment: () => set((state) => ({ count: state.count + 1 })),
  decrement: () => set((state) => ({ count: state.count - 1 })),
}));
```

### Consumindo o Estado no Componente (O Hook)

Para usar o estado em um componente, basta chamar o hook que criamos. A "mágica" da performance do Zustand está no **seletor**.

- **Seletor**: É a função que passamos para o hook para extrair apenas os pedaços do estado que o componente precisa. **O componente só vai re-renderizar se o valor retornado pelo seletor mudar.**

```javascript
// Counter.tsx
import { useCounterStore } from './store';

function Counter() {
  // ✅ BOM: Seleciona apenas o que precisa.
  // Este componente só re-renderiza quando 'count' muda.
  const count = useCounterStore((state) => state.count);
  const increment = useCounterStore((state) => state.increment);

  return (
    <div>
      <p>{count}</p>
      <button onClick={increment}>+</button>
    </div>
  );
}
```

### Acessando o Estado Fora de Componentes (`getState`)

Como o estado do Zustand vive fora do React, você pode acessá-lo de qualquer lugar do seu código JS, sem precisar de um hook.

```typescript
import { useCounterStore } from "./store";

// Uma função utilitária qualquer
export const logCurrentCount = () => {
  // Pega o valor atual do contador de forma imperativa
  const currentCount = useCounterStore.getState().count;
  console.log(`O valor do contador agora é: ${currentCount}`);
};
```

### Middlewares: Superpoderes para seu Store

Zustand tem um ecossistema de middlewares que adicionam funcionalidades extras de forma simples.

- **`devtools`**: Integra seu store com a extensão Redux DevTools do navegador.
- **`persist`**: Salva o estado no `localStorage` (ou outro storage) e o reidrata automaticamente.

```tsx
import { create } from 'zustand';
import { devtools, persist } from 'zustand/middleware';

// ... (definição do type do seu estado)

export const useMyStore = create<MyState>()(
  // Envolvemos nosso 'create' com os middlewares
  devtools(
    persist(
      (set) => ({
        // ... seu estado e ações aqui
      }),
      {
        name: 'my-app-storage', // nome da chave no localStorage
      }
    )
  )
);
```

## Use Cases

### Exemplo Prático: Lista de Notas

```typescript
// listStore.ts
import { create } from "zustand";
import { v4 as uuidv4 } from 'uuid'; // ou crypto.randomUUID()

type Note = {
  id: string;
  text: string;
};

type ListState = {
  notes: Note[];
  addNote: (text: string) => void;
  removeNote: (id: string) => void;
};

export const useListStore = create<ListState>((set) => ({
  notes: [],
  addNote: (text) => {
    set((state) => ({
      notes: [...state.notes, { id: uuidv4(), text }],
    }));
  },
  removeNote: (id) => {
    set((state) => ({
      notes: state.notes.filter((note) => note.id !== id),
    }));
  },
}));
```

## See Also

- [[React Hooks]]
- [[Gerenciamento de Estado]]
- [[Performance em React]]

## References

- [Zustand Documentation](https://zustand-demo.pmnd.rs/)
- [Fireship - Zustand in 100 Seconds](https://www.youtube.com/watch?v=_ngCLZ5Iz-0)