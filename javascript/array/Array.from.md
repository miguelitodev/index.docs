---
tags:
  - javascript
  - array
  - conversion
  - static-method
related:
  - "[[Array.of]]"
creation-date: "2025-08-26"
---
# `Array.from()`

> [!NOTE] Summary  
> O método estático `Array.from()` cria uma nova instância de `Array` a partir de um objeto **“array-like”** (com propriedade `length` e elementos indexados) ou de um objeto **iterável** (como `Map`, `Set` ou `String`).

---

## **Syntax**

```javascript
const new_array = Array.from(arrayLike, mapFn, thisArg)
```

- `arrayLike` → Objeto que será convertido em um array.
    
- `mapFn` (opcional) → Função para transformar cada elemento do novo array.
    
- `thisArg` (opcional) → Valor para usar como `this` dentro de `mapFn`.
    

---

## **Quando usar**

- Para **converter estruturas que parecem arrays**, mas não são, em **arrays reais** para poder usar métodos como `map`, `filter`, `reduce`, etc.
    
- Exemplos de objetos que podem ser convertidos:
    
    - `NodeList` do DOM (`document.querySelectorAll`)
        
    - Strings
        
    - `Set` ou `Map`
        
    - Objetos com `length` e índices numéricos
        

---

## **Exemplos**

### 1️⃣ Converter uma **string** em array de caracteres:

```javascript
const str = "javascript";
const chars = Array.from(str);
console.log(chars);
// ["j","a","v","a","s","c","r","i","p","t"]
```

---

### 2️⃣ Converter uma **string** e aplicar transformação com `mapFn`:

```javascript
const str = "javascript";
const upperChars = Array.from(str, char => char.toUpperCase());
console.log(upperChars);
// ["J","A","V","A","S","C","R","I","P","T"]
```

---

### 3️⃣ Converter um **Set** em array:

```javascript
const mySet = new Set([1, 2, 3]);
const arr = Array.from(mySet);
console.log(arr);
// [1, 2, 3]
```

---

### 4️⃣ Converter um **NodeList** do DOM em array:

```javascript
// Suponha que existam vários <p> no HTML
const nodeList = document.querySelectorAll('p');
const pArray = Array.from(nodeList);
pArray.forEach(p => console.log(p.textContent));
```

---

### 5️⃣ Criar array a partir de um **objeto array-like**:

```javascript
const arrayLike = {0: 'a', 1: 'b', 2: 'c', length: 3};
const arr = Array.from(arrayLike);
console.log(arr);
// ["a", "b", "c"]
```

---

### 6️⃣ Criar um array de números com `Array.from` usando `length` e `mapFn`:

```javascript
const numbers = Array.from({ length: 5 }, (_, i) => i + 1);
console.log(numbers);
// [1, 2, 3, 4, 5]
```

---

## **See Also**

- [[Array.of]] → Cria um array a partir de argumentos passados, diferente de `Array.from` que pode criar a partir de qualquer objeto iterável.
    

---

## **References**

- [MDN Web Docs: Array.from()](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Global_Objects/Array/from)
    

---

Se você quiser, posso **fazer uma versão “ultra resumida + visual”** dessa nota, com **exemplos e retornos lado a lado**, que fica ótima para **consultar rápido** enquanto programa.

Quer que eu faça isso?