# Notação Big O

Antes de mais nada, é importante esclarecer que a letra "O" em Big O se refere à **Ordem de Grandeza** do crescimento de um algoritmo. Além disso, a variável `n` representa o **tamanho da entrada de dados**. Pense em `n` como "o número de elementos em um array" ou "a quantidade de itens a serem processados".

Com isso em mente, podemos começar.

## O que é a Notação Big O?

A notação Big O descreve o **pior cenário** de complexidade de um algoritmo, analisando como o tempo de execução ou o espaço de memória exigido por ele cresce à medida que o tamanho da entrada (`n`) aumenta. Ela nos ajuda a classificar a eficiência e a escalabilidade de uma função ou algoritmo.

Uma característica fundamental da notação Big O é que ela **desconsidera constantes**. Por exemplo:

- **Laços Sequenciais (um após o outro):** Se você tem um laço `for` que executa `n` vezes e, em seguida, outro laço `for` que também executa `n` vezes, a complexidade total é O(n + n), que simplifica para O(2n). Como as constantes são desconsideradas, a complexidade final é **O(n)**.
- **Laços Aninhados (um dentro do outro):** Se um laço `for` está contido dentro de outro, a complexidade é multiplicada. A complexidade total se torna O(n * n), ou **O(n²)**. Neste caso, a aninhamento é crucial e não pode ser ignorado.

![Gráfico de Notação Big O](big-o-notation-chart.png)

### Tipos de Complexidade

- **Complexidade de Espaço:** Refere-se à eficiência do algoritmo em relação ao uso de memória RAM. É a quantidade de memória que o algoritmo aloca para executar sua tarefa.
- **Complexidade de Tempo:** Mede a eficiência do algoritmo em relação ao tempo de processamento. É o tempo que o algoritmo leva para ser concluído, dependendo do tamanho da entrada.

## Principais Notações

### Constante — O(1)

Um algoritmo tem complexidade constante quando o tempo de execução ou o espaço utilizado não varia com o tamanho da entrada. A resposta é sempre obtida no mesmo tempo.

#### Exemplo:

```ts
function logFirstTwoElements(array: any[]) {
  console.log(array[0]); // O(1)
  console.log(array[1]); // O(1)
}

logFirstTwoElements([1, 2, 3, 4, 5]);
logFirstTwoElements([1, 2, 3, 4, 5, 6, 7, 8, 9, 10]);
```

Neste exemplo, acessamos os elementos diretamente pelo seu índice. Não importa o tamanho do array, a operação levará sempre o mesmo tempo, resultando em uma complexidade **O(1)**.

![Gráfico de Complexidade Constante](constant-o-1.png)

### Linear — O(n)

A complexidade linear ocorre quando o tempo de execução cresce proporcionalmente ao tamanho da entrada. Se a entrada dobra de tamanho, o tempo de execução também dobra.

A complexidade de espaço também pode ser linear se a memória alocada depender diretamente do tamanho da entrada.

#### Exemplo:

Um bom exemplo prático é procurar uma página específica em um livro de forma sequencial, virando uma página de cada vez até encontrar a desejada.

```ts
function logAllElements(array: any[]) {
  for (let i = 0; i < array.length; i++) { // O(n)
    console.log(array[i]);
  }
}

logAllElements([1, 2, 3, 4, 5]);
logAllElements([1, 2, 3, 4, 5, 6, 7, 8, 9, 10]);
```

A função acima é classificada como **O(n)**, pois o laço `for` percorre cada um dos `n` elementos do array.

![Gráfico de Complexidade Linear](linear-o-n.png)

### Quadrática — O(n²)

A complexidade quadrática geralmente está associada a laços aninhados. Para cada elemento da entrada, o algoritmo realiza uma operação para cada outro elemento.

Isso significa que o tempo de execução cresce de forma exponencial com o aumento do tamanho da entrada, tornando esses algoritmos pouco eficientes para grandes volumes de dados.

#### Exemplo:

```ts
function logAllPairs(array: string[]) {
  for (let i = 0; i < array.length; i++) { // O(n²)
    for (let j = 0; j < array.length; j++) {
      console.log(array[i] + array[j]);
    }
  }
}

addAndLog(['A', 'B', 'C']);       // 9 pares
addAndLog(['A', 'B', 'C', 'D']);    // 16 pares
addAndLog(['A', 'B', 'C', 'D', 'E']); // 25 pares
```

Na função acima, para cada elemento adicionado ao array, o tempo de execução aumenta quadraticamente. A notação para este tipo de algoritmo é **O(n²)**.

![Gráfico de Complexidade Quadrática](quadratic-o-n2.png)

### Logarítmica — O(log n)

Algoritmos com complexidade logarítmica são considerados muito eficientes, especialmente para grandes volumes de dados. A cada passo, eles reduzem drasticamente o tamanho do problema a ser resolvido.

O exemplo clássico é a **busca binária**.

#### Exemplo:

```ts
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

const numbers = [1, 3, 5, 7, 9, 11, 13];
console.log(binarySearch(numbers, 7)); // Saída: 3 (índice do elemento)
```

A busca binária funciona em arrays ordenados. A cada iteração, ela "descarta" metade dos elementos restantes, olhando para o meio e decidindo se o alvo está na metade esquerda ou direita. Esse processo de divisão pela metade a cada passo resulta em uma complexidade **O(log n)**.

![Gráfico de Complexidade Logarítmica](logarithmic-o-log-n.png)

## Bibliografia

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