
Ele da a média de tempo e espaço que meu algoritmo cresce, assim você pode classificar se tua função ou algoritmo é escalável ou não, ai tem algumas formas de representar.

## Classificações

### Constantes
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

![[Pasted image 20250815191324.png]]



### Linear

São classificadas pelo número de interações que tiverem com as entradas passadas. Então o tempo de execução vai depender diretamente da quantidade de entradas passadas.
#### Exemplo:

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

![[Pasted image 20250815192206.png]]

### Quadrática
Esse aqui pega um pouco do tipo Linear, a diferença seria que, além de, ele interagir com cada entrada, ele faz u
## Bibliografia

- [Big O Notation: O Pesadelo do Programador Iniciante - Lucas Montano](https://www.youtube.com/watch?v=GLKDo13920k)
- [O que é Big O Notation? - Matheus Kielkowski](https://medium.com/linkapi-solutions/o-que-%C3%A9-big-o-notation-32f171e4a045)