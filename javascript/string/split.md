---
tags:
  - javascript
  - string
  - methods
related:
  - "[[join]]"
  - "[[substring]]"
creation-date: "2025-08-25"
---

# `String.prototype.split()`

> [!NOTE] Summary
> O método `split()` divide uma `String` em uma lista ordenada de substrings, coloca essas substrings em um array e retorna o array. A divisão é feita procurando um padrão, que é fornecido como o primeiro parâmetro na chamada do método.

## Syntax

```javascript
str.split([separator[, limit]])
```

- `separator` (Opcional): Especifica o caractere (ou expressão regular) a ser usado para separar a string. Se omitido, o array retornado conterá um único elemento com a string inteira.
- `limit` (Opcional): Um número inteiro não negativo que limita o número de substrings a serem incluídas no array.

## Use Cases

### Dividindo uma string por espaços

```javascript
const sentence = 'O rato roeu a roupa do rei de Roma';

const words = sentence.split(' ');

console.log(words);
// ['O', 'rato', 'roeu', 'a', 'roupa', 'do', 'rei', 'de', 'Roma']
```

### Dividindo por um caractere específico

```javascript
const data = 'maçã,banana,laranja,morango';

const fruits = data.split(',');

console.log(fruits);
// ['maçã', 'banana', 'laranja', 'morango']
```

### Usando o parâmetro `limit`

```javascript
const sentence = 'O rato roeu a roupa do rei de Roma';

const firstThreeWords = sentence.split(' ', 3);

console.log(firstThreeWords);
// ['O', 'rato', 'roeu']
```

### Dividindo por cada caractere

Se você usar um separador vazio (`''`), a string será dividida em um array de seus caracteres.

```javascript
const word = 'hello';

const chars = word.split('');

console.log(chars); // ['h', 'e', 'l', 'l', 'o']
```

## See Also

- [[join]]
- [[substring]]

## References

- [MDN Web Docs: String.prototype.split()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/split)
