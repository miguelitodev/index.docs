---
tags:
  - typescript
  - validation
  - schema
  - library
related:
  - "[[React Hook Form]]"
creation-date: "2025-08-25"
---

# Zod: Validação de Esquemas com TypeScript

> [!NOTE] Summary
> Zod é uma biblioteca de declaração e validação de esquemas baseada em TypeScript. Ela é super útil para garantir que seus dados (sejam eles de formulários, APIs, etc.) estejam no formato certo. E o melhor: ela infere os tipos automaticamente, o que é uma mão na roda para quem usa TypeScript!

## Syntax

### Criando um Schema

```typescript
// Exemplo de um schema para um formulário de login
const loginSchema = z.object({
  email: z.string().email("Email inválido").min(1, "Email é obrigatório"),
  password: z.string().min(6, "A senha deve ter pelo menos 6 caracteres"),
});

// Exemplo de um schema para um usuário
const userSchema = z.object({
  id: z.string().uuid(),
  name: z.string().min(3, "Nome deve ter pelo menos 3 caracteres"),
  age: z.number().int().positive("Idade deve ser um número positivo"),
  isActive: z.boolean().default(true),
  roles: z.array(z.string()),
});
```

### Validando Dados com Zod

```typescript
try {
  const validData = loginSchema.parse({ email: "teste@example.com", password: "123456" });
  console.log("Dados válidos:", validData);
} catch (error) {
  console.error("Erro de validação:", error.errors);
}

// Usando safeParse para lidar com erros de forma mais controlada
const result = loginSchema.safeParse({ email: "email-invalido", password: "123" });

if (result.success) {
  console.log("Dados válidos (safeParse):\n", result.data);
} else {
  console.error("Erro de validação (safeParse):\n", result.error.errors);
}
```

### Inferência de Tipos

```typescript
type LoginFormData = z.infer<typeof loginSchema>;
// LoginFormData agora é: { email: string; password: string; }

type User = z.infer<typeof userSchema>;
// User agora é: { id: string; name: string; age: number; isActive: boolean; roles: string[]; }
```

## Use Cases

### Zod com React Hook Form

A integração do Zod com o React Hook Form é super fácil e recomendada para validações mais robustas e complexas.

```jsx
import React from 'react';
import { useForm } from 'react-hook-form';
import { zodResolver } from '@hookform/resolvers/zod';
import { z } from 'zod';

// 1. Define o schema Zod para o seu formulário
const formSchema = z.object({
  username: z.string().min(3, "Nome de usuário deve ter pelo menos 3 caracteres"),
  email: z.string().email("Email inválido"),
  age: z.number().min(18, "Você deve ter pelo menos 18 anos"),
});

// 2. Infere o tipo do formulário a partir do schema
type FormData = z.infer<typeof formSchema>;

function MeuFormularioComZod() {
  const { register, handleSubmit, formState: { errors } } = useForm<FormData>({
    resolver: zodResolver(formSchema), // Conecta o Zod ao React Hook Form
    defaultValues: {
      username: '',
      email: '',
      age: 0,
    },
  });

  const onSubmit = (data: FormData) => {
    console.log("Dados validados pelo Zod:", data);
  };

  return (
    <form onSubmit={handleSubmit(onSubmit)}>
      <div>
        <label>Nome de Usuário:</label>
        <input {...register("username")}/>
        {errors.username && <p style={{ color: 'red' }}>{errors.username.message}</p>}
      </div>

      <div>
        <label>Email:</label>
        <input type="email" {...register("email")}/>
        {errors.email && <p style={{ color: 'red' }}>{errors.email.message}</p>}
      </div>

      <div>
        <label>Idade:</label>
        <input type="number" {...register("age", { valueAsNumber: true }) }/>
        {errors.age && <p style={{ color: 'red' }}>{errors.age.message}</p>}
      </div>

      <button type="submit">Enviar</button>
    </form>
  );
}
```

### Recursos Avançados do Zod

*   **Transformações (`transform`)**: Altera o valor de um campo após a validação.
*   **Uniões (`union`)**: Define que um campo pode ser de um tipo OU de outro.
*   **Interseções (`intersection`)**: Combina dois schemas em um só.
*   **Validações Personalizadas (`refine`, `superRefine`)**: Para regras de validação que dependem de múltiplos campos ou lógicas mais complexas.
*   **`optional()` e `nullable()`**: Para campos que podem ser opcionais ou nulos.

## See Also

- [[React Hook Form]]

## References

- [Zod Documentation](https://zod.dev/)