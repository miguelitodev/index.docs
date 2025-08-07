
---

# 🐻 Zustand - Gerenciamento de Estado Simples e Performático

`Zustand` é uma biblioteca de gerenciamento de estado para React, pequena, rápida e flexível. O nome significa "estado" em alemão. Ela se baseia em hooks e oferece uma API mínima e intuitiva, removendo grande parte da complexidade e do _boilerplate_ associados a outras libs como o Redux.

A filosofia do Zustand é que o estado é desacoplado do componente. Ele vive fora da árvore do React, permitindo o acesso de qualquer lugar da aplicação de forma performática.

**Recursos:**

- **Site Oficial / Demo:** [zustand-demo.pmnd.rs](https://zustand-demo.pmnd.rs/)
    
- **Vídeo de Referência:** [Fireship - Zustand in 100 Seconds](https://www.youtube.com/watch?v=_ngCLZ5Iz-0)
    

**Tags:** #react #libs #state-management #performance #frontend

---

## 💡 Conceitos Fundamentais

### 1. O Store (`create`)

Tudo começa com a função `create`. Ela recebe uma função que define o estado inicial e as ações que podem modificá-lo.

- **`state`**: Os dados que você quer armazenar (ex: `count`, `notes`).
    
- **`set`**: A função usada para atualizar o estado. Ela é imutável por baixo dos panos; você sempre descreve o _novo_ estado.
    
- **Ações**: Funções que vivem dentro do store e que usam o `set` para realizar as atualizações.
    

TypeScript

```
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

### 2. Consumindo o Estado no Componente (O Hook)

Para usar o estado em um componente, basta chamar o hook que criamos. A "mágica" da performance do Zustand está no **seletor**.

- **Seletor**: É a função que passamos para o hook para extrair apenas os pedaços do estado que o componente precisa. **O componente só vai re-renderizar se o valor retornado pelo seletor mudar.**
    

JavaScript

```
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

### ⚠️ Otimização de Performance: O Anti-Padrão a Evitar

Se você selecionar o estado inteiro, seu componente vai re-renderizar a **qualquer** mudança no store, mesmo que não use aquele pedaço do estado.

JavaScript

```
// ❌ RUIM: Evite isso!
// Este componente re-renderiza sempre que QUALQUER coisa no store mudar.
const state = useCounterStore(); // ou useCounterStore(state => state)

return <div>{state.count}</div>;
```

---

## 🚀 Padrões Avançados e Boas Práticas

### Acessando o Estado Fora de Componentes (`getState`)

Como o estado do Zustand vive fora do React, você pode acessá-lo de qualquer lugar do seu código JS, sem precisar de um hook. Isso é útil para lógicas em callbacks, funções utilitárias ou integrações.

- `useStore.getState()`: Retorna uma "foto" do estado naquele exato momento. **Não é reativo**, ou seja, não dispara re-renderizações.
    

JavaScript

```ts
import { useCounterStore } from "./store";

// Uma função utilitária qualquer
export const logCurrentCount = () => {
  // Pega o valor atual do contador de forma imperativa
  const currentCount = useCounterStore.getState().count;
  console.log(`O valor do contador agora é: ${currentCount}`);
};
```

### Exemplo Prático: Lista de Notas

Este é um ótimo exemplo de como lidar com um array de objetos.

TypeScript

```ts
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

### Middlewares: Superpoderes para seu Store

Zustand tem um ecossistema de middlewares que adicionam funcionalidades extras de forma simples.

- **`devtools`**: Integra seu store com a extensão Redux DevTools do navegador. **Indispensável para debugar!**
    
- **`persist`**: Salva o estado no `localStorage` (ou outro storage) e o reidrata automaticamente. Perfeito para manter a sessão do usuário ou o conteúdo de um carrinho.
    

**Como usar:**

TypeScript

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

---

## 🆚 Zustand vs. Outras Ferramentas

- **vs. Context API**: O Context API causa a re-renderização de **todos** os componentes consumidores quando o valor do contexto muda, mesmo que o componente não use aquele pedaço específico do valor. Zustand resolve isso com seu sistema de seletores, sendo muito mais performático.
    
- **vs. Redux**: Redux exige muito mais código de configuração (_boilerplate_): actions, reducers, dispatchers, etc. Zustand oferece uma API muito mais simples e direta para a maioria dos casos de uso.
    

## Links Relacionados

- [[React Hooks]]
    
- [[Gerenciamento de Estado]]
    
- [[Performance em React]]