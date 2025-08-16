
# Notação Big O

Antes de tudo, o O significa Ordem kk, e outra informação importante é que, n = é a quantidade de passos do algoritmo.

Agora podemos começar...

Ele da a média de tempo e espaço que meu algoritmo cresce, assim você pode classificar se tua função ou algoritmo é escalável ou não, ai tem algumas formas de representar. Basicamente, serve para sabermos a ordem de crescimento do algoritmo. 

A Big O notation desconsidera constantes, ou seja se tiver 2 ou mais FORs dentro da função ele vai considerar apenas 1, e na vida real devemos considerar, pois é além da parte performática e escalável, temos que pensar na complexidade do algoritmo que estamos construindo.

![[assets/data-structures/big-o-notation/big-o-notation-chart.png]]

#### Complexidades
- Espaço
	- É eficiencia do algoritmo na memória RAM, ou seja, é a quantidade de memória que o programa/algoritmo vai alocar na memória
- Tempo
	- É a eficiencia do algoritmo no processador, ou seja, é a medida de tempo que o programa/algoritmo leva para executar uma tarefa.

## Notações

### Constantes - O(1)
As constantes são quando, independente da entrada, sempre vai executar da mesma forma, em outras palavras o tempo de resposta é sempre o mesmo.

#### Exemplo:
```ts
function log(array) {
	console.log(array[0]); // Big O(1)
	console.log(array[1]); // Big O(1)
}

log([1, 2, 3, 4, 5]);
log([1, 2, 3, 4, 5, 6, 7, 8, 9, 0]);
```

Como eu estou acessando direto, acaba que a complexidade é menor, ja que eu estou especificando o valor direto na chave do elemento que eu quero pegar no array

O melhor exemplo, é as constantes que temos na programação, como no JS/TS que temos a const, ela é imutável, não se altera, ai a complexidade dele é 1

![[assets/data-structures/big-o-notation/constant-o-1.png]]



### Linear - O(n)

São classificadas pelo número de interações que tiverem com as entradas passadas. Então o tempo de execução vai depender diretamente da quantidade de entradas passadas.

A complexidade de espaço depende do tamanho do array por exemplo, conforme o array aumenta a complexidade de tempo também aumenta

E a complexidade de tempo, vai depender do tamanho do array, porque ai é o tempo que ele vai levar para percorrer todo o array.
#### Exemplo:

Além do algoritmo abaixo, também podemos usar de exemplo quando precisamos achar uma página especifica em um livro, fazendo pela busca linear, a gente passaria página a página até chegar na que queremos.

```ts
function log(array) {
	for (var i = 0; i < array.length; i++) { // Big O(n)
		console.log(array[i]);
	}
}

log([1, 2, 3, 4, 5]);
log([1, 2, 3, 4, 5, 6, 7, 8, 9, 0]);
```

Funções/Algoritmos assim são chamados de O(n), sendo n o número de vezes que ele é chamado, o que pode ser muitas vezes.

![[assets/data-structures/big-o-notation/linear-o-n.png]]

### Quadrática - O(n²)

Esse aqui pega um pouco do tipo Linear, a diferença seria que, além de, ele interagir com cada entrada, ele faz uma sub interação.

No quesito complexidade de tempo, ele vai exigir mais tempo de processamento, ja que vai ter que fazer interação de um array com o outro. 

Ai a o tempo de execução vai ser determinado pelo tamanho dos dados
#### Exemplo:
```ts
function addAndLog(array) {
	for (var i = 0; i < array.length; i++) { // Big O(n²)
		for (var j = 0; i < array.length; j++) {
			console.log(array[i] + array[j]);
		}
	}
}

addAndLog(['A', 'B', 'C']); // 9 pares
addAndLog(['A', 'B', 'C', 'D']); // 16 pares
addAndLog(['A', 'B', 'C', 'D', 'E']); // 16 pares
```

Nessa função acima, a gente gera os pares baseado em cada campo do array, então apesar de finitas possibilidades, são diversas interações, pois para cada campo que adicionarmos ao array o tempo de execução aumenta de forma Quadrática

Esse tipo de algoritmo geralmente não é interessante pois não é performático por conta do grande volume de entrada de dados.

A notação que damos para esse tipo de algoritmo seria O(n²)

![[assets/data-structures/big-o-notation/quadratic-o-n2.png]]

### Logarítmica - O(log n)

Essa família é considerada muito performática, pois, oferece opções de interação eficientes em casos de grandes números de entradas.

#### Exemplo:
```ts
function binarySearch(arr: number[], target: number): number {
  let left = 0;
  let right = arr.length - 1;

  while (left <= right) {
    const mid = Math.floor((left + right) / 2);

    if (arr[mid] === target) {
      return mid; // encontrado
    }
    if (arr[mid] < target) {
      left = mid + 1; // procura na metade direita
    } else {
      right = mid - 1; // procura na metade esquerda
    }
  }

  return -1; // não encontrado
}

// Exemplo de uso:
const numbers = [1, 3, 5, 7, 9, 11, 13];
console.log(binarySearch(numbers, 7)); // Saída: 3 (índice do número)

```

Você começa com **tudo** que pode ser a resposta, olha **bem no meio** e decide se o que quer está **antes ou depois** dessa posição. Assim, a cada passo você **descarta metade** das opções e só continua olhando na metade que ainda faz sentido.  

Repete até encontrar o que procura. Esse “descartar metade” a cada passo é o que torna a busca **O(log n)** — poucas comparações mesmo com muitos elementos.

![[assets/data-structures/big-o-notation/logarithmic-o-log-n.png]]
## Bibliografia

- [Big O Notation: O Pesadelo do Programador Iniciante - Lucas Montano](https://www.youtube.com/watch?v=GLKDo13920k)
- [O que é Big O Notation? - Matheus Kielkowski](https://medium.com/linkapi-solutions/o-que-%C3%A9-big-o-notation-32f171e4a045)
- [Site com dicas e colas de Big O](https://www.bigocheatsheet.com/)
- [O que é Big O (Complexidade de Algoritmos)? Vem aprender tudo!](https://www.youtube.com/watch?v=QndXJL5ehS0)
- [Big O Notation fácil de entender! (Complexidade de Tempo e Espaço na Programação) - Attekita Dev](https://youtu.be/FR44uWofQ7o)
- [Learn Big O notation in 6 minutes 📈 - Bro Code](https://youtu.be/XMUe3zFhM5c)
- [Big-O Notation in 100 Seconds - Fireship]
- 