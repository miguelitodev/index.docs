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
array.forEach(function(currentValue, index, arr), thisValue)
```
- `currentValue`: O valor do elemento atual.
- `index` (opcional): O índice do elemento atual.

#### Use Cases
- **Quando usar:** Para executar uma operação em cada item, como imprimir no console, atualizar um elemento de UI para cada item da lista.
- **Quando não usar:** Se você precisa criar um novo array (use `map`) ou se precisa parar o loop no meio do caminho (use um loop `for...of`).

---

### `map()`

> [!NOTE] Summary
> O método `map()` cria um **novo** array populado com os resultados da chamada de uma função de callback em cada elemento do array original.

#### Syntax
```javascript
const new_array = array.map(function(currentValue, index, arr), thisValue)
```

#### Use Cases
- **Quando usar:** Para transformar cada elemento de um array em outra coisa, criando um novo array com os dados transformados.
- **Exemplo:** Obter uma lista de IDs de um array de objetos.
- **Cuidado:** Sempre cria um novo array. Se você não precisa do array retornado, `forEach` é mais eficiente.

---

### `filter()`

> [!NOTE] Summary
> O método `filter()` cria um **novo** array com todos os elementos que passam no teste implementado pela função de callback.

#### Syntax
```javascript
const new_array = array.filter(function(element, index, arr), thisValue)
```

#### Use Cases
- **Quando usar:** Para selecionar um subconjunto de elementos que atendem a um critério.
- **Exemplo:** Remover itens inativos de uma lista.
- **Cuidado:** Se precisar apenas do primeiro item que corresponde, `find()` é mais performático.

---

### `reduce()`

> [!NOTE] Summary
> O método `reduce()` executa uma função "redutora" em cada elemento do array, resultando em um único valor de saída.

#### Syntax
```javascript
array.reduce(function(accumulator, currentValue, currentIndex, arr), initialValue)
```
- `accumulator`: O valor acumulado retornado em cada iteração.
- `currentValue`: O elemento atual.
- `initialValue` (opcional): Um valor para ser usado como o primeiro argumento da primeira chamada do callback.

#### Use Cases
- **Quando usar:** Para "resumir" um array em um único valor (soma, média, etc.) ou para agrupar itens.
- **Exemplo:** Somar o total de um carrinho de compras.
- **Cuidado:** Pode ser complexo de ler. Para transformações simples, `map` ou `filter` são mais claros.

---

### `some()`

> [!NOTE] Summary
> O método `some()` testa se **pelo menos um** elemento no array passa no teste implementado pela função fornecida. Retorna `true` ou `false`.

#### Syntax
```javascript
array.some(function(element, index, arr), thisValue)
```

#### Use Cases
- **Quando usar:** Para verificar de forma eficiente se um item que satisfaz uma condição existe.
- **Exemplo:** Checar se há algum produto com desconto em um carrinho.
- **Cuidado:** Não informa *qual* ou *quantos* itens passaram no teste, apenas se algum passou.

---

### `every()`

> [!NOTE] Summary
> O método `every()` testa se **todos** os elementos no array passam no teste implementado pela função fornecida.

#### Syntax
```javascript
array.every(function(element, index, arr), thisValue)
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
array.find(function(element, index, arr), thisValue)
```

#### Use Cases
- **Quando usar:** Para encontrar um objeto específico em um array.
- **Exemplo:** Encontrar um usuário pelo ID.

---

### `findIndex()`

> [!NOTE] Summary
> O método `findIndex()` retorna o **índice do primeiro elemento** no array que satisfaz a função de teste, ou `-1` se nenhum for encontrado.

#### Syntax
```javascript
array.findIndex(function(element, index, arr), thisValue)
```

#### Use Cases
- **Quando usar:** Quando você precisa da posição de um item para depois modificá-lo ou removê-lo.

---

### `indexOf()`

> [!NOTE] Summary
> O método `indexOf()` retorna o primeiro índice no qual um determinado elemento pode ser encontrado no array, ou -1 se não estiver presente.

#### Syntax
```javascript
array.indexOf(searchElement, fromIndex)
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
array.includes(valueToFind, fromIndex)
```

#### Use Cases
- **Quando usar:** Para uma verificação simples de existência, sem se importar com a posição. É mais legível que `indexOf() !== -1`.
- **Cuidado:** Também compara por referência para objetos.

---

### `at()`

> [!NOTE] Summary
> O método `at()` recebe um valor inteiro e retorna o item naquele índice, permitindo índices positivos e negativos.

#### Syntax
```javascript
array.at(index)
```

#### Use Cases
- **Quando usar:** Para pegar elementos do final do array de forma concisa. `arr.at(-1)` é o mesmo que `arr[arr.length - 1]`.
- **Cuidado:** É um método mais recente (ES2022), verifique a compatibilidade.

---
---

## **3. Métodos de Adição e Remoção (Mutação)**

> [!WARNING] Cuidado
> Os métodos a seguir **modificam o array original**. Isso pode causar efeitos colaterais inesperados se não for manuseado com cuidado.

### `push()`

- **O que faz:** Adiciona um ou mais elementos no **final** do array.
- **Use para:** Adicionar um item a uma lista de tarefas.
- **Cuidado:** Modifica o array.

### `pop()`

- **O que faz:** Remove o último elemento do array.
- **Use para:** Implementar uma pilha (LIFO) ou desfazer uma ação.
- **Cuidado:** Modifica o array. Retorna `undefined` se o array estiver vazio.

### `shift()`

- **O que faz:** Remove o primeiro elemento do array.
- **Use para:** Processar itens em uma fila (FIFO).
- **Cuidado:** Modifica o array. É uma operação lenta (O(n)) em arrays grandes.

### `unshift()`

- **O que faz:** Adiciona um ou mais elementos no **início** do array.
- **Use para:** Adicionar um item de alta prioridade no topo de uma lista.
- **Cuidado:** Modifica o array. É uma operação lenta (O(n)).

### `splice()`

- **O que faz:** Altera o conteúdo de um array removendo, substituindo ou adicionando elementos.
- **Use para:** Remover ou adicionar itens em qualquer ponto do array.
- **Cuidado:** Modifica o array. Sua sintaxe (`start`, `deleteCount`, `item1`, ...) pode ser complexa.

---
---

## **4. Métodos de Cópia e Imutabilidade**

> [!TIP] Boas Práticas
> Prefira métodos imutáveis sempre que possível para evitar efeitos colaterais e tornar o código mais previsível.

### `slice()`

- **O que faz:** Retorna uma **cópia superficial (shallow copy)** de uma porção do array.
- **Use para:** Criar um sub-array ou uma cópia de um array sem modificar o original.
- **Cuidado:** Por ser uma cópia superficial, objetos dentro do array são copiados por referência.

### `concat()`

- **O que faz:** Junta dois ou mais arrays, retornando um novo array.
- **Use para:** Combinar múltiplos arrays.
- **Cuidado:** O operador Spread (`...`) é geralmente mais conciso e preferido hoje em dia.

### `flat()`

- **O que faz:** Cria um novo array com todos os elementos de sub-arrays concatenados nele.
- **Use para:** "Achat" um array de arrays, como `[[1], [2, 3]]` para `[1, 2, 3]`.

### `with()`

- **O que faz:** Retorna uma **cópia** do array com o valor em um índice substituído.
- **Use para:** Atualizar um item em um array de forma imutável (ótimo para React).
- **Cuidado:** Método novo (ES2023), verifique a compatibilidade.

---
---

## **5. Métodos de Ordenação e Inversão**

### `sort()`

- **O que faz:** Ordena os elementos do próprio array e retorna o array.
- **Cuidado:** **Muta o array original**. A ordenação padrão é por string Unicode. Sempre forneça uma função de comparação para números: `(a, b) => a - b`.

### `toSorted()`

- **O que faz:** Versão imutável do `sort()`. Retorna uma **cópia** ordenada do array.
- **Use para:** Ordenar um array sem modificar o original.
- **Cuidado:** Método novo (ES2023).

### `reverse()`

- **O que faz:** Inverte a ordem dos elementos do array.
- **Cuidado:** **Muta o array original**.

### `toReversed()`

- **O que faz:** Versão imutável do `reverse()`. Retorna uma **cópia** invertida.
- **Use para:** Inverter um array sem modificar o original.
- **Cuidado:** Método novo (ES2023).

---
---

## **6. Métodos de Conversão**

### `join()`

- **O que faz:** Junta todos os elementos de um array em uma string.
- **Use para:** Criar uma string a partir de um array, especificando um separador. `['a', 'b'].join('-')` -> `"a-b"`.

### `Array.from()`

- **O que faz:** Cria um novo array a partir de um objeto "array-like" ou iterável.
- **Use para:** Converter uma `NodeList` (de `querySelectorAll`) em um array para usar `map`, `filter`, etc.

### `Array.of()`

- **O que faz:** Cria um novo array com um número variável de argumentos.
- **Use para:** Criar um array de forma previsível, evitando o comportamento `new Array(N)` que cria N posições vazias.

## See Also

- [[javascript/string/split]] - Cria um array a partir de uma string.
- [[data-structures/complexity-and-memory/big-o-notation]]

## References

- [MDN Web Docs: Array](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Global_Objects/Array)