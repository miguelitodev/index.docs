---
tags:
  - react
  - forms
  - validation
  - library
related:
  - "[[Zod]]"
creation-date: "2025-08-25"
---

# React Hook Form: Gerenciando Formulários no React

> [!NOTE] Summary
> React Hook Form é uma biblioteca para gerenciar o estado de formulários, validações e submissões de forma eficiente no React, evitando o uso excessivo de `useState`.

## Syntax

### Importando o `useForm`

```jsx
import { useForm } from "react-hook-form";
```

### Registrando seus Campos

```jsx
function MeuFormulario() {
  const { register, handleSubmit, formState: { errors } } = useForm();

  const onSubmit = (data) => console.log(data);

  return (
    <form onSubmit={handleSubmit(onSubmit)}>
      <input {...register("nome")} placeholder="Seu nome" />
      <input {...register("email")} type="email" placeholder="Seu e-mail" />
      <button type="submit">Enviar</button>
    </form>
  );
}
```

### Lidando com a Submissão (`onSubmit`)

```jsx
const { handleSubmit } = useForm();

const onSubmit = (data) => {
  console.log("Dados do formulário:", data);
  // Aqui você enviaria os dados para uma API, por exemplo
};

return (
  <form onSubmit={handleSubmit(onSubmit)}>
    {/* ... seus campos ... */}
    <button type="submit">Enviar</button>
  </form>
);
```

### Exibindo Erros de Validação

```jsx
const { register, formState: { errors } } = useForm();

return (
  <form>
    <input {...register("nome", { required: "Nome é obrigatório!" })} />
    {errors.nome && <p>{errors.nome.message}</p>}

    <input {...register("email", {
      required: "Email é obrigatório!",
      pattern: {
        value: /^[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,4}$/,
        message: "Email inválido"
      }
    })} />
    {errors.email && <p>{errors.email.message}</p>}
  </form>
);
```

### Valores Iniciais (`defaultValues`)

```jsx
const { register, handleSubmit } = useForm({
  defaultValues: {
    nome: "João Silva",
    email: "joao.silva@example.com"
  }
});
```

### Outras Funções Úteis do `useForm`

*   **`watch()`**: Observa as mudanças em um campo específico ou em todos os campos.
*   **`getValues()`**: Pega os valores atuais do formulário sem causar uma re-renderização.
*   **`reset()`**: Reseta o formulário para os `defaultValues` ou para um novo conjunto de valores.
*   **`setError()`**: Define um erro manualmente para um campo.
*   **`trigger()`**: Aciona a validação de um ou mais campos manualmente.

## Use Cases

### Integração com Bibliotecas de UI: O Componente `<Controller>`

O `<Controller>` atua como um adaptador, uma ponte que conecta o mundo "não controlado" e performático do React Hook Form com o mundo "controlado" dos componentes de UI externos.

```jsx
import React from 'react';
import { useForm, Controller } from 'react-hook-form';
import { TextField, Button, Box } from '@mui/material';

function MeuFormularioMUI() {
  const { handleSubmit, control, formState: { errors } } = useForm({
    defaultValues: {
      nome: '',
      email: '',
    },
  });

  const onSubmit = (data) => {
    console.log("Dados enviados:", data);
    // Aqui você faria a chamada para sua API
  };

  return (
    <form onSubmit={handleSubmit(onSubmit)}>
      <Box display="flex" flexDirection="column" gap={2} width="300px">

        {/* Campo Nome com Controller */}
        <Controller
          name="nome" // Nome do campo para o estado do formulário
          control={control} // Objeto que conecta ao useForm
          rules={{ required: 'O nome é obrigatório!' }} // Regras de validação

          // A prop 'render' recebe 'field' e 'fieldState' para conectar ao componente
          render={({ field, fieldState }) => (
            <TextField
              // O spread {...field} passa as props necessárias:
              // value, onChange, onBlur, ref
              {...field}

              // Conecta o estado de erro ao visual do componente do Material-UI
              label="Nome Completo"
              variant="outlined"
              error={!!fieldState.error} // true se houver erro
              helperText={fieldState.error?.message} // Mensagem de erro
              fullWidth
            />
          )}
        />

        {/* Campo Email com Controller */}
        <Controller
          name="email"
          control={control}
          rules={{
            required: 'O email é obrigatório!',
            pattern: {
              value: /^[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,4}$/,
              message: "Por favor, insira um email válido."
            }
          }}
          render={({ field, fieldState }) => (
            <TextField
              {...field}
              label="Email"
              variant="outlined"
              type="email"
              error={!!fieldState.error}
              helperText={fieldState.error?.message}
              fullWidth
            />
          )}
        />
        
        <Button type="submit" variant="contained" color="primary">
          Enviar Formulário
        </Button>
      </Box>
    </form>
  );
}
```

## See Also

- [[Zod]]

## References

- [React Hook Form Documentation](https://react-hook-form.com/get-started)