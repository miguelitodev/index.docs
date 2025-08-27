---
tags:
  - javascript
  - data-structures
  - array
related:
  - "[[javascript/array/filter]]"
  - "[[javascript/string/split]]"
creation-date: "2025-08-26"
---

# Arrays em JavaScript

> [!NOTE] Summary
> Arrays em JavaScript são objetos usados para armazenar uma coleção de múltiplos itens sob uma única variável. Eles são redimensionáveis, podem conter uma mistura de diferentes tipos de dados e vêm com um vasto conjunto de métodos para manipulação.

---

## **1. Métodos de Iteração e Transformação**

### `forEach()`

> [!NOTE] Summary
> O método `forEach()` executa uma função (um "callback") uma vez para cada elemento do array. É usado principalmente para executar "efeitos colaterais" e não retorna valor.

#### Syntax
```javascript
array.forEach(callback(element, index, array), thisArg)
```

#### Use Cases
- **Quando usar:** Para executar uma operação em cada item, como imprimir no console, atualizar um elemento de UI para cada item da lista.
- **Quando não usar:** Se você precisa criar um novo array (use `map`) ou se precisa parar o loop no meio do caminho (use um loop `for...of`).

---

### `map()`

> [!NOTE] Summary
> O método `map()` cria um **novo** array populado com os resultados da chamada de uma função de callback em cada elemento do array original.

#### Syntax
```javascript
const new_array = array.map(callback(element, index, array), thisArg)
```

#### Use Cases
- **Quando usar:** Para transformar cada elemento de um array em outra coisa, criando um novo array com os dados transformados.
- **Cuidado:** Sempre cria um novo array. Se você não precisa do array retornado, `forEach` é mais eficiente.

---

### `filter()`

> [!NOTE] Summary
> O método `filter()` cria um **novo** array com todos os elementos que passam no teste implementado pela função de callback.

#### Syntax
```javascript
const new_array = array.filter(callback(element, index, array), thisArg)
```

#### Use Cases
- **Quando usar:** Para selecionar um subconjunto de elementos que atendem a um critério.
- **Cuidado:** Se precisar apenas do primeiro item que corresponde, `find()` é mais performático.

---

### `reduce()`

> [!NOTE] Summary
> O método `reduce()` executa uma função "redutora" em cada elemento do array, resultando em um único valor de saída.

#### Syntax
```javascript
const result = array.reduce(callback(accumulator, currentValue, index, array), initialValue)
```

#### Use Cases
- **Quando usar:** Para "resumir" um array em um único valor (soma, média) ou para agrupar itens.
- **Cuidado:** Pode ser complexo de ler. Para transformações simples, `map` ou `filter` são mais claros.

---

### `some()`

> [!NOTE] Summary
> O método `some()` testa se **pelo menos um** elemento no array passa no teste implementado pela função fornecida. Retorna `true` ou `false`.

#### Syntax
```javascript
const result = array.some(callback(element, index, array), thisArg)
```

#### Use Cases
- **Quando usar:** Para verificar de forma eficiente se um item que satisfaz uma condição existe.
- **Cuidado:** Não informa *qual* ou *quantos* itens passaram no teste.

---

### `every()`

> [!NOTE] Summary
> O método `every()` testa se **todos** os elementos no array passam no teste implementado pela função fornecida.

#### Syntax
```javascript
const result = array.every(callback(element, index, array), thisArg)
```

#### Use Cases
- **Quando usar:** Para validar se todos os itens de um array seguem uma regra.
- **Exemplo:** Validar se todos os campos de um formulário foram preenchidos.

---
---

## **2. Métodos de Busca e Localização**

### `find()`

> [!NOTE] Summary
> O método `find()` retorna o **valor do primeiro elemento** no array que satisfaz a função de teste fornecida. Caso contrário, `undefined` é retornado.

#### Syntax
```javascript
const found = array.find(callback(element, index, array), thisArg)
```

#### Use Cases
- **Quando usar:** Para encontrar um objeto específico em um array, por exemplo, encontrar um usuário pelo seu ID.

---

### `findIndex()`

> [!NOTE] Summary
> O método `findIndex()` retorna o **índice do primeiro elemento** no array que satisfaz a função de teste, ou `-1` se nenhum for encontrado.

#### Syntax
```javascript
const index = array.findIndex(callback(element, index, array), thisArg)
```

#### Use Cases
- **Quando usar:** Quando você precisa da posição de um item para depois modificá-lo ou removê-lo.

---

### `indexOf()`

> [!NOTE] Summary
> O método `indexOf()` retorna o primeiro índice no qual um determinado elemento pode ser encontrado no array, ou -1 se não estiver presente.

#### Syntax
```javascript
const index = array.indexOf(searchElement, fromIndex)
```

#### Use Cases
- **Quando usar:** Para encontrar a posição de valores primitivos (string, número, booleano).
- **Cuidado:** Não funciona para objetos ou arrays, pois compara por referência. Use `findIndex()` para esses casos.

---

### `includes()`

> [!NOTE] Summary
> O método `includes()` determina se um array contém um determinado elemento, retornando `true` ou `false`.

#### Syntax
```javascript
const hasElement = array.includes(valueToFind, fromIndex)
```

#### Use Cases
- **Quando usar:** Para uma verificação simples de existência. É mais legível que `indexOf() !== -1`.
- **Cuidado:** Também compara por referência para objetos.

---

### `at()`

> [!NOTE] Summary
> O método `at()` recebe um valor inteiro e retorna o item naquele índice, permitindo índices positivos e negativos.

#### Syntax
```javascript
const item = array.at(index)
```

#### Use Cases
- **Quando usar:** Para pegar elementos do final do array de forma concisa. `arr.at(-1)` é o mesmo que `arr[arr.length - 1]`.
- **Cuidado:** É um método mais recente (ES2022), verifique a compatibilidade.

---
---

## **3. Métodos de Adição e Remoção (Mutação)**

> [!WARNING] Cuidado
> Os métodos a seguir **modificam o array original**. Isso pode causar efeitos colaterais inesperados.

### `push()`

> [!NOTE] Summary
> Adiciona um ou mais elementos no **final** do array e retorna o novo comprimento.

#### Syntax
```javascript
const newLength = array.push(element1, ..., elementN)
```

#### Use Cases
- **Quando usar:** Adicionar um item a uma lista de tarefas, registrar um novo evento em um log.
- **Cuidado:** Modifica o array original.

---

### `pop()`

> [!NOTE] Summary
> Remove o último elemento de um array e retorna aquele elemento.

#### Syntax
```javascript
const removedElement = array.pop()
```

#### Use Cases
- **Quando usar:** Implementar uma pilha (LIFO - Last-In, First-Out), desfazer a última ação.
- **Cuidado:** Modifica o array. Retorna `undefined` se o array estiver vazio.

---

### `shift()`

> [!NOTE] Summary
> Remove o primeiro elemento de um array e retorna aquele elemento.

#### Syntax
```javascript
const removedElement = array.shift()
```

#### Use Cases
- **Quando usar:** Processar itens em uma fila (FIFO - First-In, First-Out).
- **Cuidado:** Modifica o array. É uma operação lenta (O(n)) em arrays grandes pois re-indexa todos os elementos.

---

### `unshift()`

> [!NOTE] Summary
> Adiciona um ou mais elementos no **início** de um array e retorna o novo comprimento.

#### Syntax
```javascript
const newLength = array.unshift(element1, ..., elementN)
```

#### Use Cases
- **Quando usar:** Adicionar um item de alta prioridade no topo de uma lista.
- **Cuidado:** Modifica o array. É uma operação lenta (O(n)) pois re-indexa todos os elementos.

---

### `splice()`

> [!NOTE] Summary
> Altera o conteúdo de um array removendo, substituindo ou adicionando elementos.

#### Syntax
```javascript
const removedElements = array.splice(start, deleteCount, item1, ..., itemN)
```

#### Use Cases
- **Quando usar:** Remover ou adicionar itens em qualquer ponto do array sabendo sua posição.
- **Cuidado:** Modifica o array. Sua sintaxe é poderosa, mas pode ser complexa.

---

## **4. Métodos de Cópia e Imutabilidade**

> [!TIP] Boas Práticas
> Prefira métodos imutáveis sempre que possível para evitar efeitos colaterais e tornar o código mais previsível.

### `slice()`

> [!NOTE] Summary
> Retorna uma **cópia superficial (shallow copy)** de uma porção do array em um novo array.

#### Syntax
```javascript
const new_array = array.slice(start, end)
```

#### Use Cases
- **Quando usar:** Criar um sub-array ou uma cópia de um array sem modificar o original.
- **Cuidado:** Por ser uma cópia superficial, objetos dentro do array são copiados por referência.

---

### `concat()`

> [!NOTE] Summary
> Junta dois ou mais arrays, retornando um novo array que contém todos os arrays passados.

#### Syntax
```javascript
const new_array = old_array.concat(array2, array3, ..., arrayN)
```

#### Use Cases
- **Quando usar:** Combinar múltiplos arrays. O operador Spread (`...`) é geralmente mais conciso.

---

### `flat()`

> [!NOTE] Summary
> Cria um novo array com todos os elementos de sub-arrays concatenados nele recursivamente até uma profundidade especificada.

#### Syntax
```javascript
const new_array = array.flat(depth)
```

#### Use Cases
- **Quando usar:** Para "achatar" um array de arrays, como `[[1], [2, 3]]` para `[1, 2, 3]`.

---

### `with()`

> [!NOTE] Summary
> Retorna uma **cópia** do array com o valor em um índice especificado substituído pelo novo valor.

#### Syntax
```javascript
const new_array = array.with(index, value)
```

#### Use Cases
- **Quando usar:** Atualizar um item em um array de forma imutável (ótimo para React).
- **Cuidado:** Método novo (ES2023), verifique a compatibilidade.

---
---

## **5. Métodos de Ordenação e Inversão**

### `sort()`

> [!NOTE] Summary
> Ordena os elementos do próprio array e retorna o array ordenado.

#### Syntax
```javascript
array.sort(compareFunction)
```

#### Use Cases
- **Quando usar:** Ordenar uma lista de produtos por preço, ou nomes em ordem alfabética.
- **Cuidado:** **Muta o array original**. A ordenação padrão é por string Unicode. Sempre forneça uma função de comparação para números: `(a, b) => a - b`.

---

### `toSorted()`

> [!NOTE] Summary
> Versão imutável do `sort()`. Retorna uma **cópia** ordenada do array sem modificar o original.

#### Syntax
```javascript
const sorted_array = array.toSorted(compareFunction)
```

#### Use Cases
- **Quando usar:** Para ordenar um array quando a imutabilidade é importante.
- **Cuidado:** Método novo (ES2023).

---

### `reverse()`

> [!NOTE] Summary
> Inverte a ordem dos elementos de um array. O primeiro elemento se torna o último, e o último, o primeiro.

#### Syntax
```javascript
array.reverse()
```

#### Use Cases
- **Quando usar:** Inverter uma lista de comentários para mostrar os mais recentes primeiro.
- **Cuidado:** **Muta o array original**.

---

### `toReversed()`

> [!NOTE] Summary
> Versão imutável do `reverse()`. Retorna uma **cópia** invertida do array.

#### Syntax
```javascript
const reversed_array = array.toReversed()
```

#### Use Cases
- **Quando usar:** Para inverter um array sem modificar o original.
- **Cuidado:** Método novo (ES2023).

---
---

## **6. Métodos de Conversão**

### `join()`

> [!NOTE] Summary
> Junta todos os elementos de um array em uma string e retorna esta string.

#### Syntax
```javascript
const str = array.join(separator)
```

#### Use Cases
- **Quando usar:** Criar uma string a partir de um array, especificando um separador. `['a', 'b'].join('-')` -> `"a-b"`.

---

### `Array.from()`

> [!NOTE] Summary
> Cria uma nova instância de `Array` a partir de um objeto "array-like" ou iterável.

#### Syntax
```javascript
const new_array = Array.from(arrayLike, mapFn, thisArg)
```

#### Use Cases
- **Quando usar:** Converter uma `NodeList` (retornada por `querySelectorAll`) em um array para poder usar `map`, `filter`, etc.

---

### `Array.of()`

> [!NOTE] Summary
> Cria uma nova instância de `Array` com um número variável de argumentos, independentemente do número ou tipo dos argumentos.

#### Syntax
```javascript
const new_array = Array.of(element0, element1, ..., elementN)
```

#### Use Cases
- **Quando usar:** Para criar um array de forma previsível, evitando o comportamento de `new Array(N)` que cria N posições vazias.

## See Also

- [[javascript/string/split]] - Cria um array a partir de uma string.
- [[data-structures/complexity-and-memory/big-o-notation]]

## References

- [MDN Web Docs: Array](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Global_Objects/Array)
