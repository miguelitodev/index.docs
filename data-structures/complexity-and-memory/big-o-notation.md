---
tags:
  - data-structures
  - complexity
  - big-o
  - algorithms
related:
  - "[[data-structures/recursion/recursive-functions]]"
creation-date: "2025-08-25"
---

# Notação Big O

> [!NOTE] Summary
> A notação Big O descreve o **pior cenário** de complexidade de um algoritmo, analisando como o tempo de execução ou o espaço de memória exigido por ele cresce à medida que o tamanho da entrada (`n`) aumenta. Ela nos ajuda a classificar a eficiência e a escalabilidade de uma função ou algoritmo.

## Syntax

### Constante — O(1)

Um algoritmo tem complexidade constante quando o tempo de execução ou o espaço utilizado não varia com o tamanho da entrada. A resposta é sempre obtida no mesmo tempo.

```typescript
function logFirstTwoElements(array: any[]) {
  console.log(array[0]); // O(1)
  console.log(array[1]); // O(1)
}
```

### Linear — O(n)

A complexidade linear ocorre quando o tempo de execução cresce proporcionalmente ao tamanho da entrada. Se a entrada dobra de tamanho, o tempo de execução também dobra.

```typescript
function logAllElements(array: any[]) {
  for (let i = 0; i < array.length; i++) { // O(n)
    console.log(array[i]);
  }
}
```

### Quadrática — O(n²)

A complexidade quadrática geralmente está associada a laços aninhados. Para cada elemento da entrada, o algoritmo realiza uma operação para cada outro elemento.

```typescript
function logAllPairs(array: string[]) {
  for (let i = 0; i < array.length; i++) { // O(n²)
    for (let j = 0; j < array.length; j++) {
      console.log(array[i] + array[j]);
    }
  }
}
```

### Logarítmica — O(log n)

Algoritmos com complexidade logarítmica são considerados muito eficientes, especialmente para grandes volumes de dados. A cada passo, eles reduzem drasticamente o tamanho do problema a ser resolvido.

```typescript
function binarySearch(arr: number[], target: number): number {
  let left = 0;
  let right = arr.length - 1;

  while (left <= right) {
    const mid = Math.floor((left + right) / 2);

    if (arr[mid] === target) {
      return mid; // Encontrado
    }
    if (arr[mid] < target) {
      left = mid + 1; // Procura na metade direita
    } else {
      right = mid - 1; // Procura na metade esquerda
    }
  }

  return -1; // Não encontrado
}
```

## Use Cases

- **Análise de Algoritmos:** A principal utilidade da notação Big O é na análise de algoritmos, permitindo comparar a eficiência de diferentes soluções para um mesmo problema.
- **Otimização de Código:** Entender a complexidade de um algoritmo ajuda a identificar gargalos de performance e a otimizar o código.

## See Also

- "[[data-structures/complexity-and-memory/data-types]]"

## References

- [Big O Notation: O Pesadelo do Programador Iniciante - Lucas Montano](https://www.youtube.com/watch?v=GLKDo13920k)
- [O que é Big O Notation? - Matheus Kielkowski](https://medium.com/linkapi-solutions/o-que-%C3%A9-big-o-notation-32f171e4a045)
- [Big O Cheat Sheet](https://www.bigocheatsheet.com/)
- [O que é Big O (Complexidade de Algoritmos)? - Código Fonte TV](https://www.youtube.com/watch?v=QndXJL5ehS0)
- [Big O Notation fácil de entender! - Attekita Dev](https://youtu.be/FR44uWofQ7o)
- [Learn Big O notation in 6 minutes - Bro Code](https://youtu.be/XMUe3zFhM5c)
- [Big-O Notation in 100 Seconds - Fireship](https://youtu.be/2ZLl8JgPntc)
- [O que significa Big O(n)???? - Lucas Montano (Shorts)](https://www.youtube.com/shorts/aPhU-ZUYpeo?feature=share)
- [Explicando Big O - spacecoding (Shorts)](https://www.youtube.com/shorts/CyL-3ZhCwGo?feature=share)
- [Binary Search em 5 minutos - Augusto Galego](https://youtu.be/zSyV0VaTF3k)
- [Big O explained with a deck of cards - Fireship (Shorts)](https://www.youtube.com/shorts/WbF2bLbAUik?feature=share)
