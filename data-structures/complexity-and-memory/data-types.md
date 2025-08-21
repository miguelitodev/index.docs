# Tipos de Dados em JavaScript

Em JavaScript, os tipos de dados definem a natureza dos valores que uma variável pode conter. Eles são fundamentalmente divididos em duas categorias: **Tipos Primitivos** e **Tipos de Referência**.

Tags: #javascript #fundamentals #data-types

---

## Tipos Primitivos (Primitive Types)

Tipos primitivos são os blocos de construção básicos e imutáveis da linguagem. Quando você atribui um valor primitivo a uma variável, a variável armazena o próprio valor diretamente. Eles são armazenados na **Stack**, uma área de memória de acesso rápido.

> [!IMPORTANT] Imutabilidade
> Ser imutável significa que o valor de um primitivo não pode ser alterado após sua criação. Operações que parecem modificar um primitivo, na verdade, criam um novo valor.

Existem sete tipos de dados primitivos em JavaScript:

1.  **`string`**: Usado para representar texto. Deve ser envolvido por aspas (simples, duplas ou crases).
    ```javascript
    let nome = "Alice";
    let mensagem = `Olá, ${nome}!`;
    ```

2.  **`number`**: Representa tanto números inteiros quanto de ponto flutuante.
    ```javascript
    let idade = 30;
    let preco = 99.99;
    ```

3.  **`boolean`**: Representa um valor lógico, `true` ou `false`.
    ```javascript
    let ativo = true;
    let desligado = false;
    ```

4.  **`null`**: Representa a ausência intencional de qualquer valor de objeto. É um valor atribuído explicitamente.
    ```javascript
    let usuario = null; // O usuário não está logado, por exemplo.
    ```

5.  **`undefined`**: Representa uma variável que foi declarada, mas ainda não teve um valor atribuído.
    ```javascript
    let endereco;
    console.log(endereco); // undefined
    ```

6.  **`symbol`**: Um valor único e anônimo, frequentemente usado como chave de propriedade em objetos para evitar colisões de nomes.
    ```javascript
    const id = Symbol('id');
    const obj = { [id]: 123 };
    ```

7.  **`bigint`**: Usado para representar números inteiros arbitrariamente grandes, que excedem o limite do tipo `number`.
    ```javascript
    const numeroGigante = 9007199254740991n;
    ```

### Comportamento na Memória (Stack)

Como os primitivos têm um tamanho fixo, eles são armazenados diretamente na Stack. Cada variável tem seu próprio espaço e seu próprio valor.

```javascript
let a = 10;
let b = a; // 'b' recebe uma CÓPIA do valor de 'a'.

b = 20; // Alterar 'b' não afeta 'a'.

console.log(a); // 10
console.log(b); // 20
```

![Stack](stack.png)

---

## Tipos de Referência (Reference Types)

Tipos de referência são valores mais complexos, como objetos e arrays. Diferente dos primitivos, o valor armazenado em uma variável não é o objeto em si, mas uma **referência** (ou "ponteiro") para o local onde o objeto está armazenado na memória **Heap**.

> [!NOTE] A Heap
> A Heap é uma região de memória maior e menos organizada, usada para armazenar dados de tamanho dinâmico, como objetos e funções.

Os principais tipos de referência são:

1.  **`object`**: A estrutura de dados mais fundamental, usada para agrupar dados e funcionalidades. Inclui objetos literais, arrays, funções, etc.
    ```javascript
    let pessoa = { nome: "Beto", idade: 42 };
    let numeros = [1, 2, 3];
    ```

2.  **`function`**: Um tipo especial de objeto que pode ser invocado para executar código.
    ```javascript
    function somar(a, b) {
      return a + b;
    }
    ```

### Comportamento na Memória (Stack + Heap)

Quando você cria um objeto, ele é alocado na Heap. A variável correspondente, que vive na Stack, armazena apenas o endereço de memória (a referência) para esse objeto.

![Stack e Heap para Tipos de Referência](stack-heap-reference-types.png)

Se você atribuir uma variável de referência a outra, você está apenas copiando a referência, não o objeto em si. Ambas as variáveis apontarão para o **mesmo objeto** na Heap.

```javascript
let carro1 = { marca: "Fiat", modelo: "Uno" };

// 'carro2' agora aponta para o MESMO objeto que 'carro1'.
let carro2 = carro1;

// Modificar o objeto através de 'carro2'
carro2.modelo = "Mobi";

// A mudança é refletida em 'carro1', pois é o mesmo objeto.
console.log(carro1.modelo); // "Mobi"
```

Isso acontece porque `carro1` e `carro2` são apenas "controles remotos" que apontam para o mesmo "aparelho de TV" (o objeto na Heap).

---

## Resumo da Comparação

| Característica      | Tipos Primitivos                               | Tipos de Referência                            |
| ------------------- | ---------------------------------------------- | ---------------------------------------------- |
| **Armazenamento**   | O valor é armazenado diretamente na variável.  | A variável armazena uma referência ao valor.   |
| **Local na Memória**| **Stack**                                      | O objeto fica na **Heap**, a referência na Stack. |
| **Tamanho**         | Fixo e conhecido em tempo de compilação.       | Dinâmico, pode mudar durante a execução.       |
| **Atribuição**      | Copia o valor (`Pass-by-Value`).               | Copia a referência (`Pass-by-Reference`).      |
| **Imutabilidade**   | Imutáveis.                                     | Mutáveis (seu conteúdo pode ser alterado).     |
| **Exemplos**        | `string`, `number`, `boolean`, `null`, etc.    | `object`, `array`, `function`.                 |

---

## Bibliografia
- [Primitive vs Reference Data Types in JavaScript](https://www.freecodecamp.org/news/primitive-vs-reference-data-types-in-javascript/)