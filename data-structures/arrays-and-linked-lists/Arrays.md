Perfeito! Vou organizar **todos os métodos de arrays em JavaScript** que conhecemos, separados por **tipo/função**, incluindo métodos clássicos, modernos e alguns menos usados, com exemplos rápidos. 😎

---

## **1. Iteração / transformação**

|Método|O que faz|Exemplo|
|---|---|---|
|`forEach()`|Executa função para cada elemento|`[1,2,3].forEach(x => console.log(x))`|
|`map()`|Cria novo array transformando elementos|`[1,2,3].map(x => x*2)` → `[2,4,6]`|
|`filter()`|Cria novo array com elementos que passam no teste|`[1,2,3].filter(x => x>1)` → `[2,3]`|
|`reduce()`|Reduz array a um único valor|`[1,2,3].reduce((a,b)=>a+b,0)` → `6`|
|`reduceRight()`|Igual ao reduce, mas da direita para esquerda|`[1,2,3].reduceRight((a,b)=>a-b)` → `0`|
|`some()`|Retorna true se algum elemento passa no teste|`[1,2,3].some(x => x>2)` → `true`|
|`every()`|Retorna true se todos os elementos passam no teste|`[1,2,3].every(x>0)` → `true`|
|`flatMap()`|Combina map + flat|`[1,2].flatMap(x => [x, x*2])` → `[1,2,2,4]`|

---

## **2. Busca / localização**

|Método|O que faz|Exemplo|
|---|---|---|
|`find()`|Retorna o primeiro elemento que passa no teste|`[1,2,3].find(x>1)` → `2`|
|`findIndex()`|Retorna índice do primeiro que passa no teste|`[1,2,3].findIndex(x>1)` → `1`|
|`findLast()`|Igual ao find, mas do final (ES2022+)|`[1,2,3].findLast(x>1)` → `3`|
|`findLastIndex()`|Índice do último que passa no teste|`[1,2,3].findLastIndex(x>1)` → `2`|
|`indexOf()`|Índice do primeiro elemento igual|`[1,2,3].indexOf(2)` → `1`|
|`lastIndexOf()`|Índice do último elemento igual|`[1,2,2].lastIndexOf(2)` → `2`|
|`includes()`|Verifica se contém valor|`[1,2,3].includes(2)` → `true`|
|`at()`|Acessa elemento por índice positivo ou negativo|`[10,20,30].at(-1)` → `30`|

---

## **3. Adição / remoção**

|Método|O que faz|Exemplo|
|---|---|---|
|`push()`|Adiciona no final|`[1,2].push(3)` → `[1,2,3]`|
|`pop()`|Remove do final|`[1,2,3].pop()` → `[1,2]`|
|`unshift()`|Adiciona no início|`[2,3].unshift(1)` → `[1,2,3]`|
|`shift()`|Remove do início|`[1,2,3].shift()` → `[2,3]`|
|`splice()`|Remove/substitui elementos em qualquer posição|`[1,2,3,4].splice(1,2)` → `[1,4]`|
|`slice()`|Cria subarray (não altera original)|`[1,2,3].slice(1,3)` → `[2,3]`|
|`concat()`|Junta arrays (não altera original)|`[1].concat([2,3])` → `[1,2,3]`|
|`fill()`|Preenche array com valor|`[1,2,3].fill(0)` → `[0,0,0]`|
|`copyWithin()`|Copia parte do array dentro do mesmo array|`[1,2,3,4].copyWithin(0,2)` → `[3,4,3,4]`|

---

## **4. Ordenação / inversão**

|Método|O que faz|Exemplo|
|---|---|---|
|`sort()`|Ordena elementos|`[3,1,2].sort((a,b)=>a-b)` → `[1,2,3]`|
|`reverse()`|Inverte array|`[1,2,3].reverse()` → `[3,2,1]`|

---

## **5. Conversão / string**

|Método|O que faz|Exemplo|
|---|---|---|
|`join()`|Junta elementos em string|`[1,2,3].join('-')` → `"1-2-3"`|
|`toString()`|Converte array em string|`[1,2,3].toString()` → `"1,2,3"`|
|`toLocaleString()`|Converte array em string com regras de localidade|`[123456.78].toLocaleString('pt-BR')` → `"123.456,78"`|
|`Array.from()`|Cria array a partir de iteráveis|`Array.from('abc')` → `['a','b','c']`|
|`Array.of()`|Cria array a partir de argumentos|`Array.of(1,2,3)` → `[1,2,3]`|

---

## **6. Iteradores / acesso**

|Método|O que faz|Exemplo|
|---|---|---|
|`entries()`|Retorna iterator [index, valor]|`for (let [i,v] of [1,2].entries()) console.log(i,v)`|
|`keys()`|Retorna iterator de índices|`[1,2].keys()`|
|`values()`|Retorna iterator de valores|`[1,2].values()`|

---

## **7. Imutabilidade moderna**

|Método|O que faz|Exemplo|
|---|---|---|
|`with()`|Retorna cópia do array com valor substituído|`[1,2,3].with(1,99)` → `[1,99,3]`|

---

Se você quiser, posso fazer **uma versão visual tipo “mapa mental/tabela colorida”** mostrando **todos os métodos e suas relações**, que fica super fácil de memorizar.

Quer que eu faça isso?