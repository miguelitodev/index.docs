# Closure em JavaScript 

## 1️⃣ Definição

Uma **closure** é uma função que **lembra do escopo léxico onde foi criada**, mesmo depois que a função externa terminou sua execução. Em outras palavras, a função interna **mantém acesso às variáveis do seu escopo pai**.

> Importante: nem toda função é closure. Para ser closure, a função precisa **acessar variáveis externas ao seu escopo**.

---

---
tags:
  - javascript
  - closures
  - scope
creation-date: "2025-08-25"
---

# Closure em JavaScript

> [!NOTE] Summary
> Uma **closure** é uma função que **lembra do escopo léxico onde foi criada**, mesmo depois que a função externa terminou sua execução. Em outras palavras, a função interna **mantém acesso às variáveis do seu escopo pai**.
> > Importante: nem toda função é closure. Para ser closure, a função precisa **acessar variáveis externas ao seu escopo**.

## Syntax

### Exemplo clássico – Contador

```javascript
function criarContador() {
  let contador = 0;          // variável do escopo pai
  return function() {        // função interna → closure
    contador++;              // lembra do 'contador'
    return contador;
  }
}

const contar = criarContador();
console.log(contar()); // 1
console.log(contar()); // 2
```

- `contar` **é uma função interna** que lembra da variável `contador` do escopo pai.
- Cada vez que você chama `contar()`, o valor de `contador` **é preservado e incrementado**.
- Isso acontece porque a **closure mantém o estado do escopo pai**.

### Transformando em closure

```javascript
function criarDataGuardada() {
  const dataAgora = new Date();
  return function() {       // função interna → closure
    return dataAgora;       // lembra do escopo do pai
  }
}

const pegarData = criarDataGuardada();
console.log(pegarData());  // sempre retorna a mesma data
```

- Agora sim: a função interna **lembra do valor `dataAgora` do escopo externo** → é closure.

## Use Cases

- **Estado privado:** Closures são fundamentais para criar estado privado, contadores, caches, e funções que precisam lembrar de valores do escopo externo.
- **Programação funcional:** É uma das bases para entender JavaScript moderno e programação funcional.

## See Also

- [[javascript/scope]]

## References

- [MDN Web Docs: Closures](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Closures)
    

### 🔹 Analogia macaco-banana

- Macaco pai cria **uma cesta de bananas** (`contador = 0`).
    
- Macaco filho (closure) **segura a cesta** e pega uma banana por vez.
    
- Cada vez que você pede uma banana (`contar()`), o macaco lembra quantas já pegou.
    

---

## 3️⃣ Função que retorna valor – não é closure

```js
function pegarDataAgora() {
  const dataAgora = new Date(); // variável local
  return dataAgora;             // retorna valor
}

const resultado = pegarDataAgora();
console.log(resultado);
```

- Aqui `pegarDataAgora` **não é closure**, porque:
    
    1. Ela só retorna o valor da variável do escopo interno
        
    2. Nenhuma função interna mantém referência a `dataAgora`
        

### 🔹 Analogia macaco-banana

- Macaco pega a cesta de bananas **uma vez** e entrega
    
- Depois que você olha, **não há memória da cesta**. Cada chamada é independente.
    

---

## 4️⃣ Transformando em closure

```js
function criarDataGuardada() {
  const dataAgora = new Date();
  return function() {       // função interna → closure
    return dataAgora;       // lembra do escopo do pai
  }
}

const pegarData = criarDataGuardada();
console.log(pegarData());  // sempre retorna a mesma data
```

- Agora sim: a função interna **lembra do valor `dataAgora` do escopo externo** → é closure.
    

### 🔹 Analogia macaco-banana

- Macaco pai cria a cesta de bananas (`dataAgora`).
    
- Macaco filho (closure) **continua segurando a cesta**, você pode acessar as bananas várias vezes, **o valor não muda**.
    

---

## 5️⃣ Resumo do entendimento

|Conceito|Função normal|Closure|
|---|---|---|
|Mantém variáveis do escopo pai|❌ não mantém|✅ mantém|
|Retorna valor fixo|✅ valor da execução|✅ ou valor + estado preservado|
|Estado entre chamadas|❌ não preserva|✅ preserva|
|Exemplo macaco-banana|macaco pega e entrega|macaco continua segurando cesta|

---

## 6️⃣ Observações

- **Closures** são fundamentais para criar **estado privado**, contadores, caches, e funções que precisam lembrar de valores do escopo externo.
    
- É uma das bases para entender **JavaScript moderno e programação funcional**.
    

---

## 7️⃣ Dica prática

- Sempre que criar uma função que retorna outra função e você quiser que ela **lembre valores do escopo externo**, você está criando uma **closure**.
    
- Caso só precise do valor atual e não precisa preservar estado, **não é closure**, apenas função normal.
    

---

🐒🍌 **Analogia final:**

- Função normal = macaco pega cesta, entrega e esquece.
    
- Closure = macaco pega cesta e continua segurando, lembrando de quantas bananas já pegou.