# 📚 index.docs: Meu Caderno de Estudos e Descobertas

Bem-vindo(a) ao meu cantinho de estudos e anotações! Este repositório é o meu diário de bordo no mundo da tecnologia, um espaço onde compartilho minhas jornadas de aprendizado, descobertas e aprofundamento em diversas áreas do desenvolvimento.

Aqui, você encontrará um compilado organizado dos meus estudos sobre novas tecnologias, conceitos e tudo aquilo que me ajuda a crescer e aprimorar minhas habilidades. Todo o conteúdo é cuidadosamente documentado e estruturado utilizando o Obsidian, refletindo meu processo de aprendizado e minha paixão por explorar o universo da programação.

Prepare-se para mergulhar em tópicos que vão desde o básico até o avançado, com uma abordagem prática e detalhada. A ideia é ter de tudo um pouco, sempre com o objetivo de consolidar o conhecimento e facilitar a consulta futura. 😄

## 🚀 Conteúdo

### Data Structures

- **[Arrays](data-structures/arrays-and-linked-lists/Arrays.md)** - Índice de métodos de Array em JavaScript.
- **[Recursive Functions](data-structures/recursion/recursive-functions.md)** - Funções que chamam a si mesmas.
- #### Complexity and Memory
    - **[Big O Notation](data-structures/complexity-and-memory/big-o-notation.md)** – Entendendo a complexidade de algoritmos com Big O.
    - **[Data Types](data-structures/complexity-and-memory/data-types.md)** – Tipos de dados primitivos e de referência em JavaScript.
    - **[Stack e Heap](data-structures/complexity-and-memory/stack-heap.md)** – Gerenciamento de memória em JavaScript.

### JavaScript

- **[Closures](javascript/closures.md)** – Entendendo como as closures funcionam em JavaScript.
- #### Array
    - **[at](javascript/array/at.md)** - Acessa um elemento por índice (inclusive negativos).
    - **[concat](javascript/array/concat.md)** - Junta arrays, retornando um novo.
    - **[every](javascript/array/every.md)** - Testa se todos os elementos passam no teste.
    - **[filter](javascript/array/filter.md)** – Cria um novo array com elementos que passam em um teste.
    - **[find](javascript/array/find.md)** - Retorna o primeiro elemento que passa no teste.
    - **[findIndex](javascript/array/findIndex.md)** - Retorna o índice do primeiro elemento que passa no teste.
    - **[flat](javascript/array/flat.md)** - "Achata" um array de arrays.
    - **[forEach](javascript/array/forEach.md)** - Executa uma função para cada elemento.
    - **[from](javascript/array/Array.from.md)** - Cria um array a partir de um objeto "array-like".
    - **[includes](javascript/array/includes.md)** - Verifica se o array contém um valor.
    - **[indexOf](javascript/array/indexOf.md)** - Retorna o primeiro índice de um valor.
    - **[join](javascript/array/join.md)** - Junta os elementos de um array em uma string.
    - **[map](javascript/array/map.md)** - Cria um novo array transformando cada elemento.
    - **[of](javascript/array/Array.of.md)** - Cria um array a partir de argumentos.
    - **[pop](javascript/array/pop.md)** - Remove o elemento do final.
    - **[push](javascript/array/push.md)** - Adiciona elementos no final.
    - **[reduce](javascript/array/reduce.md)** - Reduz o array a um único valor.
    - **[reverse](javascript/array/reverse.md)** - Inverte o array (muta o original).
    - **[shift](javascript/array/shift.md)** - Remove o elemento do início.
    - **[slice](javascript/array/slice.md)** - Retorna uma cópia superficial de uma porção do array.
    - **[some](javascript/array/some.md)** - Testa se pelo menos um elemento passa no teste.
    - **[sort](javascript/array/sort.md)** - Ordena o array (muta o original).
    - **[splice](javascript/array/splice.md)** - Remove, substitui ou adiciona elementos em qualquer posição.
    - **[toReversed](javascript/array/toReversed.md)** - Retorna uma cópia invertida do array.
    - **[toSorted](javascript/array/toSorted.md)** - Retorna uma cópia ordenada do array.
    - **[unshift](javascript/array/unshift.md)** - Adiciona elementos no início.
    - **[with](javascript/array/with.md)** - Retorna uma cópia do array com um valor substituído em um índice.
- #### String
    - **[endsWith](javascript/string/endsWith.md)** – Verifica se uma string termina com os caracteres de uma string especificada.
    - **[split](javascript/string/split.md)** – Divide uma string em um array de strings, com base em um separador.

### Kubernetes

- **[Introdução](kubernetes/introducao.md)** – Visão geral e conceitos básicos do Kubernetes.
- **[Overview](kubernetes/overview.md)** – Arquitetura e componentes principais do Kubernetes.
- **[Pods](kubernetes/pods.md)** – Entendendo os Pods, a menor unidade de computação no Kubernetes.

### React

- #### Hooks
    - **[memo](react/hooks/memo.md)** – Memorize o resultado de um componente para evitar renderizações desnecessárias.
    - **[useCallback](react/hooks/useCallback.md)** – Memoriza uma função para evitar que ela seja recriada em cada renderização.
    - **[useContext](react/hooks/useContext.md)** – Permite o acesso a valores de contexto sem precisar de "prop drilling".
    - **[useEffect](react/hooks/useEffect.md)** – Efeito colateral que permite trabalhar com side effects (ex: chamadas de API).
    - **[useId](react/hooks/useId.md)** – Gera um ID único para o componente.
    - **[useLayoutEffect](react/hooks/useLayoutEffect.md)** – Efeito colateral síncrono que é executado após a alteração do layout.
    - **[useMemo](react/hooks/useMemo.md)** – Memoriza o valor de uma expressão para otimizar o desempenho.
    - **[useReducer](react/hooks/useReducer.md)** – Gerencia estados complexos em componentes.
    - **[useRef](react/hooks/useRef.md)** – Referência mutável que persiste por toda a vida do componente.
    - **[useState](react/hooks/useState.md)** – Gerencia o estado dentro de um componente funcional.
- #### Bibliotecas
    - **[React Hook Form](react/libs/react-hook-form.md)** – Biblioteca para gerenciamento de formulários.
    - **[React Icons](react/libs/react-icons.md)** – Biblioteca de ícones para React.
    - **[React Rewards](react/libs/react-rewards.md)** – Biblioteca para adicionar "recompensas" em interações.
    - **[Sonner](react/libs/sonner.md)** – Biblioteca de notificações (toasts).
    - **[Zod](react/libs/zod.md)** – Biblioteca para validação de esquemas de dados.
    - **[Zustand](react/libs/zustand.md)** – Gerenciador de estado para React.
- #### Redux
    - **[Actions](react/redux/actions.md)** – Objetos que representam a intenção de alterar o estado.
    - **[Dispatch](react/redux/dispatch.md)** – Função que dispara as actions.
    - **[Reducers](react/redux/reducers.md)** – Funções puras que especificam como o estado da aplicação muda em resposta a uma action.
    - **[Store](react/redux/store.md)** – Objeto que mantém o estado da aplicação.
    - #### Saga
        - **[Effects](react/redux/saga/effects.md)** – Funções que descrevem operações assíncronas.
        - **[Middleware](react/redux/saga/middleware.md)** – Middleware do Redux para lidar com efeitos colaterais.
        - **[Saga](react/redux/saga/saga.md)** – Gerenciador de efeitos colaterais para Redux.
    - #### Toolkit
        - **[configureStore](react/redux/toolkit/configureStore.md)** – Função para configurar a store do Redux.

### TypeScript

- **[Non-null Assertion Operator](typescript/non-null-assertion-operator.md)** – O operador de asserção não-nula (`!`) no TypeScript.

## 🔗 Redes Sociais & Site

- **Website**: [miguelito.dev](https://miguelito.dev)
- **GitHub**: [miguelitodev](https://github.com/miguelitodev)
- **LinkedIn**: [Miguel Riquelme](https://www.linkedin.com/in/miguelitodev)