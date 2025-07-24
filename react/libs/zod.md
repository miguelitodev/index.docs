# Zod: Validação de Esquemas com TypeScript

Zod é uma biblioteca de declaração e validação de esquemas baseada em TypeScript. Ela é super útil para garantir que seus dados (sejam eles de formulários, APIs, etc.) estejam no formato certo. E o melhor: ela infere os tipos automaticamente, o que é uma mão na roda para quem usa TypeScript!

## O Básico do Zod

### 1. Importando o Zod

Você importa o Zod de forma bem simples:

```typescript
import { z } from "zod";
```

### 2. Criando um Schema

Um schema Zod é a "receita" de como seus dados devem ser. Você define o tipo de cada campo e as regras de validação.

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

### 3. Validando Dados com Zod

Depois de criar seu schema, você pode usá-lo para validar qualquer dado. O método `parse` vai lançar um erro se a validação falhar, e o `safeParse` retorna um objeto com `success` e `data` ou `error`.

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
  console.log("Dados válidos (safeParse):
", result.data);
} else {
  console.error("Erro de validação (safeParse):
", result.error.errors);
}
```

### 4. Inferência de Tipos

Uma das maiores vantagens do Zod é que ele pode inferir os tipos TypeScript a partir do seu schema. Isso significa menos trabalho manual para você!

```typescript
type LoginFormData = z.infer<typeof loginSchema>;
// LoginFormData agora é: { email: string; password: string; }

type User = z.infer<typeof userSchema>;
// User agora é: { id: string; name: string; age: number; isActive: boolean; roles: string[]; }
```

## Zod com React Hook Form

A integração do Zod com o React Hook Form é super fácil e recomendada para validações mais robustas e complexas.

### 1. Instalando o Resolver

Você vai precisar de um pacote extra para fazer a ponte entre os dois:

```bash
npm install @hookform/resolvers zod
# ou
yarn add @hookform/resolvers zod
```

### 2. Usando o Zod Resolver

Agora, é só passar seu schema Zod para o `resolver` do `useForm`:

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
        <input {...register("username")} />
        {errors.username && <p style={{ color: 'red' }}>{errors.username.message}</p>}
      </div>

      <div>
        <label>Email:</label>
        <input type="email" {...register("email")} />
        {errors.email && <p style={{ color: 'red' }}>{errors.email.message}</p>}
      </div>

      <div>
        <label>Idade:</label>
        <input type="number" {...register("age", { valueAsNumber: true })} />
        {errors.age && <p style={{ color: 'red' }}>{errors.age.message}</p>}
      </div>

      <button type="submit">Enviar</button>
    </form>
  );
}

export default MeuFormularioComZod;
```

### Recursos Avançados do Zod

O Zod vai muito além do básico. Aqui estão alguns recursos que podem ser muito úteis:

*   **Transformações (`transform`)**: Altera o valor de um campo após a validação. Por exemplo, converter uma string para um número.
    ```typescript
    const priceSchema = z.string().transform(val => parseFloat(val));
    ```
*   **Uniões (`union`)**: Define que um campo pode ser de um tipo OU de outro.
    ```typescript
    const idSchema = z.union([z.string().uuid(), z.number().int()]);
    ```
*   **Interseções (`intersection`)**: Combina dois schemas em um só.
    ```typescript
    const baseUser = z.object({ name: z.string() });
    const adminUser = z.object({ role: z.literal("admin") });
    const fullAdmin = z.intersection(baseUser, adminUser);
    ```
*   **Validações Personalizadas (`refine`, `superRefine`)**: Para regras de validação que dependem de múltiplos campos ou lógicas mais complexas.
    ```typescript
    const passwordConfirmSchema = z.object({
      password: z.string(),
      confirmPassword: z.string(),
    }).refine(data => data.password === data.confirmPassword, {
      message: "Senhas não conferem!",
      path: ["confirmPassword"], // Onde o erro será anexado
    });
    ```
*   **`optional()` e `nullable()`**: Para campos que podem ser opcionais ou nulos.
    ```typescript
    const optionalField = z.string().optional(); // undefined
    const nullableField = z.string().nullable(); // null
    ```

Com o Zod, você tem um poder enorme para validar seus dados de forma segura e com a ajuda do TypeScript, garantindo que seus formulários sejam robustos e livres de erros de tipo. 
