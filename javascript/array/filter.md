# `Array.prototype.filter()`

O método `filter()` cria um novo array com todos os elementos que passaram no teste implementado pela função fornecida.

Tags: #javascript #array #metodos

---

## Sintaxe

```javascript
const newArray = arr.filter(callback(element[, index[, array]])[, thisArg])
```

- `callback`: Função para testar cada elemento do array. Retorna `true` para manter o elemento, `false` para descartar. Ela recebe três argumentos:
  - `element`: O elemento atual sendo processado no array.
  - `index` (Opcional): O índice do elemento atual.
  - `array` (Opcional): O array no qual `filter` foi chamado.
- `thisArg` (Opcional): Valor a ser usado como `this` ao executar o `callback`.

---

## Exemplos

### Filtrando números ímpares

```javascript
const numbers = [1, 2, 3, 4, 5, 6];

const oddNumbers = numbers.filter(number => number % 2 !== 0);

console.log(oddNumbers); // [1, 3, 5]
```

### Filtrando objetos por uma propriedade

```javascript
const products = [
  { name: 'Maçã', category: 'fruta' },
  { name: 'Alface', category: 'verdura' },
  { name: 'Banana', category: 'fruta' },
  { name: 'Cenoura', category: 'legume' }
];

const fruits = products.filter(product => product.category === 'fruta');

console.log(fruits);
// [
//   { name: 'Maçã', category: 'fruta' },
//   { name: 'Banana', category: 'fruta' }
// ]
```

---

## Links Relacionados

- [[map]]
- [[reduce]]
- [[forEach]]