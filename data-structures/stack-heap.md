Lembre-se que todo código TypeScript (TS) é convertido (transpilado) para JavaScript (JS) antes de ser executado. Portanto, o gerenciamento de memória de ambos é idêntico, sendo controlado pelo motor JavaScript que executa o código (como o V8 no Google Chrome e Node.js, ou o SpiderMonkey no Firefox).

O modelo de memória é dividido em duas áreas principais: a **Stack** e a **Heap**.

### **Stack (Pilha)**

A Stack é uma região de memória de alta velocidade usada para o contexto de execução estático. Ela segue uma estrutura de dados "LIFO" (Last-In, First-Out), ou seja, o último item adicionado é o primeiro a ser removido.

- **O que ela armazena?**
    
    1. **Tipos Primitivos:** Variáveis com valores primitivos, como `number`, `string`, `boolean`, `null`, `undefined`, `symbol` e `bigint`.
        
    2. **Referências a Objetos:** O "endereço" de onde encontrar um objeto ou função na Heap.
        
    3. **Contexto de Execução:** Quando uma função é chamada, um "quadro de pilha" (stack frame) é criado e colocado no topo da Stack. Esse quadro contém os argumentos da função e suas variáveis locais.
        
- Como funciona?
    
    Imagine que você tem um código que chama várias funções. Cada chamada de função empilha um novo quadro. Quando uma função termina sua execução (com um return ou simplesmente chegando ao fim), seu quadro é automaticamente removido do topo da pilha, liberando a memória de forma instantânea e determinística.
    
- **Exemplo:**
    
    JavaScript
    
    ```
    function calcularQuadrado(n) {
      const resultado = n * n; // 'resultado' é criado na Stack deste quadro.
      return resultado;
    }
    
    function logicaPrincipal() {
      const valor = 5; // 'valor' é criado na Stack.
      const quadrado = calcularQuadrado(valor); // Chama 'calcularQuadrado', um novo quadro é empilhado.
      console.log(quadrado);
    }
    
    logicaPrincipal(); // Chama 'logicaPrincipal', um quadro é empilhado.
    ```
    
    Neste exemplo, `logicaPrincipal` é empilhada primeiro. Dentro dela, `calcularQuadrado` é chamada e seu quadro é empilhado no topo. Quando `calcularQuadrado` termina, seu quadro é removido. Finalmente, quando `logicaPrincipal` termina, seu quadro também é removido.
    

### **Heap**

A Heap é uma região de memória maior e menos organizada, usada para armazenar dados de forma dinâmica. É aqui que os objetos vivem.

- **O que ela armazena?**
    
    - **Objetos:** Tudo que não é um tipo primitivo. Isso inclui objetos literais (`{}`), arrays (`[]`), e até mesmo as próprias funções.
        
- Como funciona?
    
    Quando você cria um objeto (ex: let usuario = { nome: 'Ana' };), a memória para { nome: 'Ana' } é alocada na Heap. A variável usuario, que vive na Stack, não armazena o objeto em si, mas sim uma referência (um ponteiro) para a localização desse objeto na Heap.
    
    Diferente da Stack, a memória na Heap não é liberada automaticamente quando uma função termina. Um objeto na Heap continua a existir enquanto houver pelo menos uma referência apontando para ele.
    
- **Exemplo:**
    
    JavaScript
    
    ```
    function criarUsuario(nome) {
      // O objeto { nome: nome } é criado na HEAP.
      const user = { nome: nome };
      // A função retorna a REFERÊNCIA para o objeto.
      return user;
    }
    
    // 'novoUsuario' (na STACK) recebe a REFERÊNCIA para o objeto na HEAP.
    let novoUsuario = criarUsuario('Carlos');
    ```
    
    Mesmo após a função `criarUsuario` ter terminado e seu quadro ter sido removido da Stack, o objeto `{ nome: 'Carlos' }` continua a existir na Heap porque a variável `novoUsuario` ainda aponta para ele.
    

### **Garbage Collector (Coletor de Lixo)**

Se a memória da Heap não é liberada automaticamente, o que impede que ela se esgote? É aqui que entra o Garbage Collector (GC).

O GC é um processo automático do motor JavaScript que tem uma única tarefa: encontrar e liberar memória na Heap que não está mais sendo usada.

- Como ele sabe o que é "lixo"?
    
    Um objeto é considerado "lixo" quando ele se torna inacessível, ou seja, quando não há mais nenhuma referência apontando para ele a partir de qualquer parte do código em execução.
    
- O Algoritmo Mark-and-Sweep (Marcar e Varrer):
    
    Este é o algoritmo mais comum usado pelos motores JS. Ele funciona em duas fases:
    
    1. **Mark (Marcar):** O GC começa de um ponto de partida conhecido como "raiz" (geralmente o objeto global, como `window` no navegador). Ele navega por todos os objetos, seguindo cada referência, e "marca" todos os objetos que consegue alcançar como "em uso".
        
    2. **Sweep (Varrer):** Após a marcação, o GC percorre toda a Heap. Qualquer objeto que não foi marcado na fase anterior é considerado lixo. O GC então libera o espaço de memória ocupado por esses objetos não marcados.
        
- **Exemplo prático:**
    
    JavaScript
    
    ```
    let heroi = { nome: 'Batman' }; // Objeto A criado na Heap. 'heroi' (Stack) aponta para ele.
    
    let outroHeroi = heroi; // 'outroHeroi' (Stack) agora também aponta para o Objeto A.
    
    heroi = null; // A referência de 'heroi' é removida. Mas o Objeto A ainda é acessível por 'outroHeroi'.
                  // O Garbage Collector NÃO vai limpá-lo ainda.
    
    outroHeroi = null; // Agora, não há mais nenhuma referência apontando para o Objeto A.
                       // Na próxima vez que o Garbage Collector rodar, ele o verá como inacessível
                       // e liberará sua memória.
    ```
    

Em resumo, a **Stack** cuida de dados de tamanho fixo e do fluxo de execução das funções de forma rápida, enquanto a **Heap** armazena objetos de forma dinâmica. O **Garbage Collector** é o sistema de limpeza automático que garante que a Heap não fique cheia de objetos que não são mais necessários.
## Bibliografia
- [wtf is “the stack” ?](https://www.youtube.com/watch?v=CRTR5ljBjPM&pp=ugMICgJwdBABGAHKBRRtZW1vcmlhIHN0YWNrIGUgaGVhcA%3D%3D "wtf is “the stack” ?")
- [Gerenciamento de memória - Stack vs Heap | Dias de Dev](https://www.youtube.com/watch?v=7kJwVQGJCbw&pp=ygUUbWVtb3JpYSBzdGFjayBlIGhlYXA%3D "Gerenciamento de memória - Stack vs Heap | Dias de Dev")
- [Stack vs Heap Memory - Simple Explanation](https://www.youtube.com/watch?v=5OJRqkYbK-4&pp=ugMICgJwdBABGAHKBRRtZW1vcmlhIHN0YWNrIGUgaGVhcNIHCQmtCQGHKiGM7w%3D%3D "Stack vs Heap Memory - Simple Explanation")
- [O que são e onde estão a "stack" e "heap"?](https://pt.stackoverflow.com/questions/3797/o-que-s%c3%a3o-e-onde-est%c3%a3o-a-stack-e-heap)
- [Stack e Heap no Java: Entenda como a JVM usa a memória do seu programa!](https://www.youtube.com/watch?v=DAzYQCTH-JE)
- [Entendendo COLETOR DE LIXO DO JAVA (memória Heap, Stack, Garbage Collector)](https://youtu.be/cgUfurMJosE)
- Heap, Stack e Garbage Collector — Um guia prático para o gerenciamento de memória no .NET
