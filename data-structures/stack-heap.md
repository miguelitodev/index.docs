#javascript #typescript #frontend 

### A Stack (Pilha de Execução)

A **Stack** é uma região de memória rápida e organizada, usada para o contexto de execução estático. Ela opera no formato **LIFO** (Last-In, First-Out): o último item a entrar é o primeiro a sair.

> [!NOTE] O que a Stack armazena?
> 
> 1. **Valores Primitivos:** Variáveis de tipos como `number`, `string`, `boolean`, `null`, `undefined`, `symbol` e `bigint`.
>     
> 2. **Referências (Ponteiros):** O "endereço" de onde os objetos e funções estão localizados na Heap.
>     
> 3. **Contexto de Execução:** Cada vez que uma função é chamada, um "quadro" (_stack frame_) é empilhado. Ele contém os argumentos e variáveis locais daquela função.
>     

Sua principal característica é o gerenciamento automático e determinístico: quando uma função termina, seu quadro é removido do topo da pilha e a memória é liberada instantaneamente.

##### Exemplo de Funcionamento da Stack:

JavaScript

```
function calcularQuadrado(n) {
  // 'resultado' é criado no quadro desta função na Stack.
  const resultado = n * n; 
  return resultado;
}

function logicaPrincipal() {
  // 'valor' é criado no quadro desta função na Stack.
  const valor = 5; 
  // Um novo quadro para 'calcularQuadrado' é empilhado no topo.
  const quadrado = calcularQuadrado(valor); 
  console.log(quadrado);
}

// O primeiro quadro é criado para 'logicaPrincipal'.
logicaPrincipal(); 
```

Quando `logicaPrincipal` termina, seu quadro é removido, e a Stack fica vazia.

---

### A Heap (Monte)

A **Heap** é uma área de memória maior e menos estruturada, usada para armazenamento dinâmico de dados. É o lar dos objetos.

> [!NOTE] O que a Heap armazena?
> 
> - **Objetos:** Tudo que não é um tipo primitivo. Isso inclui objetos (`{}`), arrays (`[]`) e as próprias funções.
>     

Quando um objeto é criado (ex: `let usuario = { nome: 'Ana' }`), um espaço é alocado na Heap para guardar `{ nome: 'Ana' }`. A variável `usuario`, que vive na Stack, armazena apenas a **referência** (o endereço) para esse objeto.

A memória na Heap não é liberada automaticamente ao final de uma função. Um objeto permanece na Heap enquanto houver pelo menos uma referência apontando para ele.

##### Exemplo de Funcionamento da Heap:

JavaScript

```
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

Se a Heap não é limpa automaticamente, o que impede a memória de esgotar? O **Garbage Collector (GC)**.

O GC é um processo automático do motor JavaScript que periodicamente identifica e libera a memória da Heap que não está mais em uso.

> [!NOTE] Como o GC sabe o que é "lixo"?
> 
> Um objeto é considerado "lixo" quando ele se torna inacessível. Isso acontece quando não existe mais nenhuma referência ativa no código que aponte para ele.

O algoritmo mais comum para isso é o **Mark-and-Sweep (Marcar e Varrer)**:

1. **Fase de Marcação (Mark):** O GC começa das "raízes" (objetos globais) e segue todas as referências, marcando cada objeto alcançável como "em uso".
    
2. **Fase de Limpeza (Sweep):** O GC varre a Heap e libera a memória de todos os objetos que **não foram marcados**, pois são considerados inacessíveis.
    

##### Exemplo Prático de Coleta de Lixo:

JavaScript

```
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

memory leak

### Resumo

> [!SUMMARY]
> 
> - **Stack:** Rápida, organizada (LIFO) e de curta duração. Armazena primitivos e referências. Gerenciada automaticamente com as chamadas de função.
>     
> - **Heap:** Ampla, dinâmica e de longa duração. Armazena objetos.
>     
> - **Garbage Collector:** É o sistema de limpeza automático da Heap, que previne vazamentos de memória ao remover objetos inacessíveis.
>     

### Bibliografia

- [wtf is “the stack” ?](https://www.youtube.com/watch?v=CRTR5ljBjPM)
  
- [Gerenciamento de memória - Stack vs Heap | Dias de Dev](https://www.youtube.com/watch?v=7kJwVQGJCbw)
    
- [Stack vs Heap Memory - Simple Explanation](https://www.youtube.com/watch?v=5OJRqkYbK-4)
    
- [O que são e onde estão a "stack" e "heap"?](https://pt.stackoverflow.com/questions/3797/o-que-s%c3%a3o-e-onde-est%c3%a3o-a-stack-e-heap)
    
- [Stack e Heap no Java: Entenda como a JVM usa a memória do seu programa!](https://www.youtube.com/watch?v=DAzYQCTH-JE)
    
- [Entendendo COLETOR DE LIXO DO JAVA (memória Heap, Stack, Garbage Collector)](https://youtu.be/cgUfurMJosE)
    
- [Heap, Stack e Garbage Collector — Um guia prático para o gerenciamento de memória no .NET](https://andresantarosa.medium.com/heap-stack-e-garbage-collector-um-guia-pr%C3%A1tico-para-o-gerenciamento-de-mem%C3%B3ria-no-net-3faf6c4cd0ed)