
---
tags:
  - data-structures
  - recursion
  - javascript
related:
  - "[[data-structures/complexity-and-memory/big-o-notation]]"
creation-date: "2025-08-25"
---

# Funções Recursivas

> [!NOTE] Summary
> Uma função recursiva é uma função que chama a si mesma em sua própria definição, de forma direta ou indireta. Pense nela como uma boneca russa, onde uma boneca contém outra menor dentro de si.


## Syntax

### Fatorial com Recursão

```javascript
function fatorialRecursivo(n) {
  // Caso base: se n for 0 ou 1, o fatorial é 1.
  if (n <= 1) {
    return 1;
  }
  // Chamada recursiva: n multiplica o fatorial de (n - 1).
  return n * fatorialRecursivo(n - 1);
}

console.log(fatorialRecursivo(5)); // 120
```

### Sequência de Fibonacci com Recursão

```javascript
function fibonacci(n) {
  // Casos base
  if (n <= 1) {
    return n;
  }
  // Chamada recursiva
  return fibonacci(n - 1) + fibonacci(n - 2);
}

// Exemplo para encontrar o 7º número na sequência (índice 6)
console.log(fibonacci(6)); // 8
```

## Use Cases

### Comparação: Iterativo vs. Recursivo

Enquanto as funções **iterativas** utilizam loops (como `for` e `while`) para repetir uma tarefa, as **recursivas** resolvem um problema dividindo-o em subproblemas menores, até que um caso base seja atingido e a "pilha" de chamadas comece a ser resolvida.

> [!INFO] Performance vs. Complexidade
> - **Performance:** Geralmente, a abordagem recursiva é mais lenta, pois cada chamada de função é adicionada à pilha de chamadas (call stack), consumindo mais memória.
> - **Complexidade:** A recursão pode simplificar a lógica e a leitura de algoritmos complexos, como os de `backtracking` ou `divide and conquer`, enquanto a versão iterativa pode exigir um controle de estado mais complexo.

> [!WARNING] Atenção
> Embora elegante, esta implementação de Fibonacci é ineficiente para valores grandes de `n` devido à repetição de cálculos. Técnicas como a **memoização** são usadas para otimizá-la.

### Como a Recursão do Fatorial Funciona na Prática

Quando chamamos `fatorialRecursivo(5)`, o que acontece é:

> [!TIP] Descendo e Subindo
> **Descendo até o caso base:**
> ```
> fatorial(5) → precisa do fatorial(4)
> fatorial(4) → precisa do fatorial(3)
> fatorial(3) → precisa do fatorial(2)
> fatorial(2) → precisa do fatorial(1)
> fatorial(1) = 1   ✅ (caso base)
> ```
>
> **Subindo e resolvendo:**
> ```
> fatorial(2) = 2 * 1   = 2
> fatorial(3) = 3 * 2   = 6
> fatorial(4) = 4 * 6   = 24
> fatorial(5) = 5 * 24  = 120
> ```
> 👉 Pense nisso como **descer de galho em galho até o menor** e depois **subir carregando as respostas**.

![Ilustração da pilha de chamadas da função fatorial recursiva.](assets/data-structures/recursion/recursive-functions/recursive-factorial-call-stack.png)

## See Also

- "[[data-structures/complexity-and-memory/stack-heap]]"

## References

- [A melhor explicação de Recursividade do Youtube](https://youtu.be/qUe36p4P2CI)
- [Recursion - MDN Web Docs](https://developer.mozilla.org/en-US/docs/Glossary/Recursion)
  