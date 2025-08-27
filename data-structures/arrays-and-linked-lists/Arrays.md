---
tags:
  - javascript
  - data-structures
  - array
related:
  - "[[javascript/array/filter]]"
creation-date: "2025-08-26"
---

# Arrays em JavaScript

> [!NOTE] Summary
> Arrays em JavaScript são objetos usados para armazenar uma coleção de múltiplos itens sob uma única variável. Eles são redimensionáveis e podem conter uma mistura de diferentes tipos de dados.

---

## Métodos de Iteração e Transformação

### `forEach()`

> [!NOTE] Summary
> O método `forEach()` executa uma função (um "callback") uma vez para cada elemento do array. Ele não retorna um valor, sendo usado para causar "efeitos colaterais".

#### Syntax

```javascript
array.forEach(function(currentValue, index, arr), thisValue)
```

-   `currentValue`: O valor do elemento atual.
-   `index` (opcional): O índice do elemento atual.
-   `arr` (opcional): O array ao qual o elemento pertence.

#### Use Cases

-   **Quando usar:** Para executar uma operação em cada item de um array, como imprimir no console, atualizar um elemento de UI para cada item, etc.
-   **Exemplo:**

```javascript
const fruits = ['apple', 'banana', 'cherry'];
fruits.forEach(fruit => console.log(fruit));
```

-   **Quando não usar:** Não use `forEach` se você precisa criar um novo array a partir do original (use `map`). Ele não pode ser interrompido (com `break` ou `return`).

---

### `map()`

> [!NOTE] Summary
> O método `map()` cria um **novo** array populado com os resultados da chamada de uma função de callback em cada elemento do array original. Ele mantém o array original imutável.

#### Syntax

```javascript
const new_array = array.map(function(currentValue, index, arr), thisValue)
```

#### Use Cases

-   **Quando usar:** Quando você precisa transformar cada elemento de um array em outra coisa, criando um novo array com os dados transformados.
-   **Exemplo:** Obter um array com o dobro dos valores de um array de números.

```javascript
const numbers = [1, 4, 9];
const doubles = numbers.map(num => num * 2); // [2, 8, 18]
```

-   **Cuidado:** `map` sempre cria um novo array. Se você não precisa do array retornado e quer apenas iterar, `forEach` é mais eficiente em termos de memória.

---

### `filter()`

> [!NOTE] Summary
> O método `filter()` cria um **novo** array com todos os elementos que passam no teste implementado pela função de callback fornecida.

#### Syntax

```javascript
const new_array = array.filter(function(currentValue, index, arr), thisValue)
```

#### Use Cases

-   **Quando usar:** Para selecionar um subconjunto de elementos de um array que atendem a um critério específico.
-   **Exemplo:** Filtrar palavras com mais de 6 letras.

```javascript
const words = ['spray', 'limit', 'elite', 'exuberant', 'destruction', 'present'];
const longWords = words.filter(word => word.length > 6); // ['exuberant', 'destruction', 'present']
```

-   **Cuidado:** Se você precisa apenas encontrar o *primeiro* elemento que corresponde à condição, `find()` é mais performático, pois não continua percorrendo o resto do array.

> [!TIP]
> O restante dos métodos de array será formatado seguindo este mesmo padrão. Avise-me se este formato lhe agrada para eu continuar.
