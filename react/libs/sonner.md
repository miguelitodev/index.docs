# Sonner

Sonner é uma biblioteca de notificações (também conhecidas como "toasts") para React. Ela se destaca por ser opinativa, fácil de usar e esteticamente agradável, seguindo um design moderno.

Tags: #react #libs #ui #notifications #toast

---

## Instalação

```bash
npm install sonner
# ou
yarn add sonner
```

---

## Como Usar

1.  **Adicione o `Toaster`:** Coloque o componente `<Toaster />` na raiz do seu aplicativo (por exemplo, no `App.js`).
2.  **Chame a função `toast`:** Importe a função `toast` de `sonner` e chame-a de qualquer lugar do seu código para exibir uma notificação.

### Exemplo

**1. Configuração no `App.js`**

```jsx
// App.js
import React from 'react';
import { Toaster } from 'sonner';
import MyPage from './MyPage';

function App() {
  return (
    <div>
      {/* O Toaster renderiza as notificações */}
      <Toaster />
      <MyPage />
    </div>
  );
}
```

**2. Disparando um Toast em um Componente**

```jsx
// MyPage.js
import React from 'react';
import { toast } from 'sonner';

function MyPage() {
  const handleSave = () => {
    // Simula uma chamada de API
    console.log('Salvando dados...');
    toast.success('Seus dados foram salvos com sucesso!');
  };

  return (
    <button onClick={handleSave}>
      Salvar Alterações
    </button>
  );
}
```

---

## Tipos de Toast

Sonner oferece vários tipos de toasts prontos para uso:

- `toast(message)`: Toast padrão.
- `toast.success(message)`: Toast de sucesso (geralmente verde).
- `toast.error(message)`: Toast de erro (geralmente vermelho).
- `toast.warning(message)`: Toast de aviso (geralmente amarelo).
- `toast.info(message)`: Toast de informação (geralmente azul).
- `toast.loading(message)`: Toast de carregamento, que pode ser atualizado.

### Exemplo com Loading

```jsx
import { toast } from 'sonner';

function uploadFile(file) {
  const toastId = toast.loading('Enviando seu arquivo...');

  // Simula o upload
  setTimeout(() => {
    // Atualiza o toast original usando seu ID
    toast.success('Arquivo enviado com sucesso!', { id: toastId });
  }, 2000);
}
```

---

## Links Relacionados

- [[React Hot Toast]] (outra biblioteca popular de toasts)
- [[UI/UX Design]]
- [[Feedback ao Usuário]]
