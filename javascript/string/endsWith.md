---
tags:
  - javascript
  - string
  - methods
related:
  - "[[startsWith]]"
  - "[[includes]]"
creation-date: "2025-08-25"
---

# `String.prototype.endsWith()`

> [!NOTE] Summary
> O método `endsWith()` determina se uma string termina com os caracteres de outra string, retornando `true` ou `false` conforme apropriado.

## Syntax

```javascript
str.endsWith(searchString[, length])
```

- `searchString`: Os caracteres a serem procurados no final da string.
- `length` (Opcional): Se fornecido, é usado como o comprimento da `str`. O padrão é `str.length`.

## Use Cases

### Verificação simples

```javascript
const str = 'Olá, mundo!';

console.log(str.endsWith('mundo!')); // true
console.log(str.endsWith('Olá'));    // false
```

### Usando o parâmetro `length`

O parâmetro `length` permite que você verifique o final de uma substring.

```javascript
const str = 'Isso é um teste.';

// Considera a string como se tivesse apenas os 5 primeiros caracteres ("Isso ")
console.log(str.endsWith('Isso', 4)); // true
```

## See Also

- [[startsWith]]
- [[includes]]

## References

- [MDN Web Docs: String.prototype.endsWith()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/endsWith)
