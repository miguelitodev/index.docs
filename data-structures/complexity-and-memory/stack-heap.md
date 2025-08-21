# Stack vs. Heap: Gerenciamento de Memória em JavaScript

Entender como JavaScript gerencia a memória é crucial para escrever código eficiente e evitar problemas como vazamentos de memória (memory leaks). A memória em um ambiente de execução JavaScript é dividida principalmente em duas áreas: a **Stack** e a **Heap**.

Tags: #javascript #memory-management #fundamentals

---

### A Stack (Pilha de Execução)

A **Stack** é uma estrutura de dados estática e altamente organizada que armazena o contexto de execução do código. Ela funciona no formato **LIFO** (Last-In, First-Out), ou seja, o último item adicionado é o primeiro a ser removido.

> [!NOTE] O que a Stack armazena?
> 1.  **Valores Primitivos:** Variáveis de tipos como `number`, `string`, `boolean`, `null`, `undefined`, `symbol` e `bigint`. Por terem tamanho fixo, são armazenados diretamente aqui.
> 2.  **Referências (Ponteiros):** O "endereço" de onde objetos e funções estão localizados na Heap.
> 3.  **Contexto de Execução (Call Stack):** Cada vez que uma função é chamada, um "quadro" (_stack frame_) é empilhado. Ele contém os argumentos da função, suas variáveis locais e o ponto de retorno.

O gerenciamento da Stack é rápido e determinístico. Quando uma função conclui sua execução, seu quadro é automaticamente removido ("desempilhado"), liberando a memória de forma instantânea.

##### Exemplo de Funcionamento da Call Stack:

```javascript
function calcularQuadrado(n) {
  // 3. Quadro de 'calcularQuadrado' é empilhado.
  const resultado = n * n;
  return resultado; // 4. Quadro é desempilhado.
}

function logicaPrincipal() {
  // 1. Quadro de 'logicaPrincipal' é empilhado.
  const valor = 5;
  const quadrado = calcularQuadrado(valor); // 2. Chama outra função.
  console.log(quadrado);
}

logicaPrincipal(); // 5. Quadro é desempilhado. A Stack fica vazia.
```

---

### A Heap (Monte)

A **Heap** é uma região de memória muito maior e menos organizada, usada para armazenamento dinâmico. É aqui que os objetos residem.

> [!NOTE] O que a Heap armazena?
> - **Objetos:** Tudo que não é um tipo primitivo. Isso inclui objetos literais (`{}`), arrays (`[]`), e as próprias definições de funções.

Quando um objeto é criado (ex: `let usuario = { nome: 'Ana' }`), um espaço de memória é alocado na Heap para guardar o objeto `{ nome: 'Ana' }`. A variável `usuario`, que vive na Stack, armazena apenas a **referência** para esse objeto.

A memória na Heap não é liberada automaticamente quando uma função termina. Um objeto permanece na Heap enquanto houver pelo menos uma referência apontando para ele.

##### Exemplo de Funcionamento da Heap:

```javascript
function criarUsuario(nome) {
  // O objeto { nome } é criado na HEAP.
  const user = { nome: nome };
  // A função retorna a REFERÊNCIA para o objeto.
  return user;
}

// 'novoUsuario' (na STACK) recebe a REFERÊNCIA para o objeto na HEAP.
let novoUsuario = criarUsuario('Carlos');
```

Mesmo após a função `criarUsuario` terminar, o objeto `{ nome: 'Carlos' }` sobrevive na Heap, pois a variável `novoUsuario` ainda o referencia.

---

### O Garbage Collector (Coletor de Lixo)

Se a Heap não é limpa automaticamente, o que impede a memória de se esgotar? O **Garbage Collector (GC)**.

O GC é um processo automático do motor JavaScript (como o V8) que periodicamente identifica e libera a memória da Heap que não está mais em uso.

> [!NOTE] Como o GC sabe o que é "lixo"?
> Um objeto é considerado "lixo" quando se torna **inacessível** a partir do código. Isso acontece quando não existe mais nenhuma referência ativa que aponte para ele.

O algoritmo mais comum para isso é o **Mark-and-Sweep (Marcar e Varrer)**:

1.  **Fase de Marcação (Mark):** O GC começa das "raízes" (objetos globais, variáveis na stack) e segue todas as referências, marcando cada objeto alcançável como "em uso".
2.  **Fase de Limpeza (Sweep):** O GC varre toda a Heap e libera a memória de todos os objetos que **não foram marcados**, pois são considerados inacessíveis.

##### Exemplo Prático de Coleta de Lixo:

```javascript
// 1. O objeto { nome: 'Batman' } é criado na Heap.
let heroi = { nome: 'Batman' };

// 2. 'outroHeroi' agora também aponta para o mesmo objeto. Existem 2 referências.
let outroHeroi = heroi;

// 3. Uma referência é removida. O objeto sobrevive, pois 'outroHeroi' ainda o acessa.
heroi = null;

// 4. A última referência é removida. O objeto torna-se inacessível.
outroHeroi = null;

// Na próxima execução do GC, a memória do objeto { nome: 'Batman' } será liberada.
```

---

### Vazamentos de Memória (Memory Leaks)

Um vazamento de memória ocorre quando a memória alocada na Heap não é liberada pelo GC porque ainda existem referências desnecessárias a ela.

Causas comuns em JavaScript:

1.  **Variáveis Globais Acidentais:** Se você esquecer `let`, `const` ou `var` dentro de uma função, a variável pode se tornar global e nunca ser coletada.
    ```javascript
    function criar() {
      // 'minhaVariavel' se torna uma propriedade do objeto global (window).
      minhaVariavel = "dados secretos";
    }
    ```
2.  **Timers e Callbacks Esquecidos:** Se um `setInterval` ou `setTimeout` referencia um objeto, esse objeto não será coletado enquanto o timer não for limpo (`clearInterval`).
    ```javascript
    function configurar() {
      let dados = { /* objeto grande */ };
      setInterval(() => {
        // O callback mantém a referência a 'dados' para sempre.
        console.log(dados);
      }, 1000);
    }
    ```
3.  **Closures:** Funções aninhadas que mantêm referência a variáveis de seu escopo pai podem impedir que essas variáveis sejam coletadas.
4.  **Referências a Elementos do DOM Removidos:** Se você mantém uma referência a um elemento do DOM em seu código JavaScript, mas remove esse elemento da árvore do DOM, a memória não será liberada.

---

### Resumo

> [!SUMMARY]
> - **Stack:** Rápida, organizada (LIFO) e de curta duração. Armazena primitivos e referências. Gerenciada automaticamente.
> - **Heap:** Ampla, dinâmica e de longa duração. Armazena objetos. Gerenciada pelo Garbage Collector.
> - **Garbage Collector:** É o sistema de limpeza automático da Heap, essencial para prevenir vazamentos de memória.

### Bibliografia

- [wtf is “the stack” ?](https://www.youtube.com/watch?v=CRTR5ljBjPM)
- [Gerenciamento de memória - Stack vs Heap | Dias de Dev](https://www.youtube.com/watch?v=7kJwVQGJCbw)
- [Stack vs Heap Memory - Simple Explanation](https://www.youtube.com/watch?v=5OJRqkYbK-4)
- [O que são e onde estão a "stack" e "heap"?](https://pt.stackoverflow.com/questions/3797/o-que-s%c3%a3o-e-onde-est%c3%a3o-a-stack-e-heap)
