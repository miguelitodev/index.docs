# Funções Recursivas

Uma função recursiva é uma função que chama a si mesma em sua própria definição, de forma direta ou indireta. Pense nela como uma boneca russa, onde uma boneca contém outra menor dentro de si.

## Iterativa vs. Recursiva

Enquanto as funções **iterativas** utilizam loops (como `for` e `while`) para repetir uma tarefa, as **recursivas** resolvem um problema dividindo-o em subproblemas menores, até que um caso base seja atingido e a "pilha" de chamadas comece a ser resolvida.

- **Performance:** Geralmente, a abordagem recursiva é mais lenta, pois cada chamada de função é adicionada à pilha de chamadas (call stack), consumindo mais memória.
- **Complexidade:** A recursão pode simplificar a lógica e a leitura de algoritmos complexos, como os de `backtracking` ou `divide and conquer`, enquanto a versão iterativa pode exigir um controle de estado mais complexo.

Um ótimo exemplo para entender a diferença é o cálculo de um fatorial.

### O que é um Fatorial?

O fatorial de um número inteiro não negativo **n**, denotado por **n!**, é o produto de todos os inteiros positivos menores ou iguais a **n**.

**Exemplo:**
`5! = 5 * 4 * 3 * 2 * 1 = 120`

Por definição, o fatorial de `0` é `1`.

### Exemplo de Fatorial com Loop (Iterativo)

```javascript
function fatorialIterativo(n) {
  let resultado = 1;
  for (let i = n; i > 1; i--) {
    resultado *= i;
  }
  return resultado;
}

console.log(fatorialIterativo(5)); // 120
```

### Exemplo de Fatorial com Recursão

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

## Exemplo Avançado: Sequência de Fibonacci com Recursão

A sequência de Fibonacci é uma série de números onde cada número é a soma dos dois anteriores. A sequência começa com `0` e `1`.

`0, 1, 1, 2, 3, 5, 8, 13, 21, ...`

A implementação recursiva é uma forma elegante de representar essa sequência:

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
**Atenção:** Embora elegante, esta implementação de Fibonacci é ineficiente para valores grandes de `n` devido à repetição de cálculos. Técnicas como a **memoização** são usadas para otimizá-la.

## Bibliografia
- [A melhor explicação de Recursividade do Youtube](https://youtu.be/qUe36p4P2CI)
- [Recursion - MDN Web Docs](https://developer.mozilla.org/en-US/docs/Glossary/Recursion)