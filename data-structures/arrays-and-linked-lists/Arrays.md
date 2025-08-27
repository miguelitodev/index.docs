## **1. Iteração e Transformação**

Estes métodos ajudam a percorrer, modificar e criar novos arrays a partir de um array existente.

| Método | O que faz | Caso de Uso Comum | Vantagens (Quando usar) | Desvantagens (Quando não usar / Cuidado) |
| :--- | :--- | :--- | :--- | :--- |
| `forEach()` | Executa uma função para cada elemento. | Aplicar uma operação a cada item, como imprimir no console, atualizar um elemento de UI para cada item da lista. | Simples e direto para executar um "efeito colateral" por item. Não cria um novo array, economizando memória. | Não retorna um novo array. Se precisar de um novo array com os resultados, use `map()`. Não é possível "quebrar" (break) o loop; ele sempre percorre todos os elementos. |
| `map()` | Cria um novo array transformando cada elemento do array original. | Obter uma lista de IDs de um array de objetos. Formatar uma lista de dados para exibição. | Perfeito para transformações. Mantém o array original imutável, o que é bom para a previsibilidade do código. | Cria um novo array, o que pode consumir memória se o array for muito grande. Se você não precisa do array retornado, `forEach()` é mais eficiente. |
| `filter()` | Cria um novo array com os elementos que passam em um teste (retornam `true`). | Remover itens indesejados de uma lista, como usuários inativos ou produtos fora de estoque. | Excelente para seleção de dados de forma imutável. O código fica muito legível e declarativo. | Assim como `map()`, cria um novo array. Se você só precisa encontrar o *primeiro* item que corresponde, `find()` é mais eficiente. |
| `reduce()` | Reduz o array a um único valor (pode ser um número, string, objeto, etc.). | Somar todos os valores de um carrinho de compras. Agrupar uma lista de itens por uma categoria. | Extremamente poderoso e versátil. Pode recriar a lógica de `map`, `filter` e outros métodos. | A sintaxe pode ser confusa para iniciantes. É fácil escrever código complexo e difícil de ler se a lógica do redutor for complicada. |
| `some()` | Retorna `true` se **pelo menos um** elemento passar no teste. | Verificar se um carrinho de compras contém um item específico. Checar se há algum erro em uma lista de resultados. | Eficiente. Para de percorrer o array assim que encontra uma correspondência, economizando processamento. | Apenas informa *se* existe, não *qual* ou *quantos*. Se precisar do item em si, use `find()`. |
| `every()` | Retorna `true` se **todos** os elementos passarem no teste. | Validar se todos os campos de um formulário foram preenchidos. Garantir que todos os itens atendem a um critério de qualidade. | Também é eficiente, parando assim que um elemento falha no teste. Ótimo para validações completas. | Similar ao `some()`, não informa qual item falhou no teste. |

---

## **2. Busca e Localização**

Esses métodos são usados para encontrar elementos ou informações sobre sua posição no array.

| Método | O que faz | Caso de Uso Comum | Vantagens (Quando usar) | Desvantagens (Quando não usar / Cuidado) |
| :--- | :--- | :--- | :--- | :--- |
| `find()` | Retorna o **primeiro elemento** que passa no teste. | Encontrar um usuário específico pelo seu ID em um array de usuários. | Retorna o objeto real, o que é muito útil. Para de buscar assim que encontra, sendo eficiente. | Retorna `undefined` se nada for encontrado, o que pode causar erros se não for tratado. Se múltiplos itens podem corresponder e você precisa de todos, use `filter()`. |
| `findIndex()` | Retorna o **índice do primeiro elemento** que passa no teste. | Saber a posição de um item para poder modificá-lo ou removê-lo posteriormente com `splice()`. | Útil quando você precisa da posição, não do valor. Também para de buscar ao encontrar. | Retorna `-1` se não encontrar, o que é um valor padrão conhecido, mas precisa ser verificado. |
| `indexOf()` | Retorna o primeiro índice de um elemento com um valor específico. | Checar a posição de um valor primitivo (string, número) em um array. | Simples e rápido para valores primitivos. | Não funciona para objetos ou arrays aninhados, pois compara por referência, não por valor. Use `findIndex()` para esses casos. |
| `includes()` | Verifica se o array contém um determinado valor, retornando `true` ou `false`. | Verificar rapidamente se um item existe, sem se importar com sua posição. | Código mais legível que `indexOf() !== -1`. Funciona com `NaN`, ao contrário de `indexOf()`. | Assim como `indexOf()`, não funciona bem para encontrar objetos, a menos que seja a mesma referência. |
| `at()` | Acessa um elemento por índice, permitindo índices negativos. | Pegar o último elemento de um array (`arr.at(-1)`) de forma mais curta e legível que `arr[arr.length - 1]`. | Sintaxe muito conveniente para acessar elementos a partir do final do array. | É um método mais recente (ES2022), pode não estar disponível em ambientes JavaScript muito antigos. |

---

## **3. Adição e Remoção (Mutação)**

Estes métodos **modificam o array original**.

| Método | O que faz | Caso de Uso Comum | Vantagens (Quando usar) | Desvantagens (Quando não usar / Cuidado) |
| :--- | :--- | :--- | :--- | :--- |
| `push()` | Adiciona um ou mais elementos no **final** do array. | Adicionar um novo item a uma lista de tarefas. | Operação muito rápida (O(1)). Retorna o novo comprimento do array. | **Muta o array original.** Isso pode ser indesejado em aplicações que dependem de imutabilidade (como em React). |
| `pop()` | Remove o último elemento do array. | Implementar uma pilha (LIFO - Last-In, First-Out). Desfazer a última ação. | Também é uma operação muito rápida (O(1)). Retorna o elemento que foi removido. | **Muta o array original.** Pode causar erros se o array estiver vazio (retorna `undefined`). |
| `shift()` | Remove o primeiro elemento do array. | Processar itens de uma fila (FIFO - First-In, First-Out). | Retorna o elemento removido. | **Muta o array original.** É uma operação lenta (O(n)) porque todos os outros elementos precisam ser movidos para uma nova posição. |
| `unshift()` | Adiciona um ou mais elementos no **início** do array. | Adicionar um item com alta prioridade no topo de uma lista. | Permite adicionar no início. | **Muta o array original.** Assim como `shift()`, é lento (O(n)) pois precisa re-indexar todo o array. |
| `splice()` | Remove, substitui ou adiciona elementos em qualquer posição. | Remover um item específico de uma lista sabendo seu índice. Inserir um item no meio do array. | Extremamente versátil para manipulação em qualquer ponto do array. | **Muta o array original.** A sintaxe (`startIndex`, `deleteCount`, `...items`) pode ser complexa e levar a erros se não usada com cuidado. |

---

## **4. Cópia e Concatenação (Imutabilidade)**

Estes métodos criam um novo array ou uma cópia, preservando o original.

| Método | O que faz | Caso de Uso Comum | Vantagens (Quando usar) | Desvantagens (Quando não usar / Cuidado) |
| :--- | :--- | :--- | :--- | :--- |
| `slice()` | Cria um novo array (uma cópia superficial) de uma porção do array original. | Obter um subconjunto de um array sem modificar o original. Criar uma cópia de um array. | Não altera o array original, promovendo a imutabilidade. Ótimo para criar cópias ou partes de um array. | A cópia é "superficial" (shallow copy). Se o array contém objetos, a cópia conterá referências aos mesmos objetos, não cópias deles. |
| `concat()` | Junta dois ou mais arrays, criando um novo. | Combinar resultados de diferentes chamadas de API. | Imutável. Fácil de usar para mesclar múltiplos arrays de uma só vez. | Cria um novo array, o que pode ser ineficiente em termos de memória para arrays muito grandes. O operador Spread (`...`) é muitas vezes preferido hoje por ser mais conciso. |
| `flat()` | Cria um novo array com todos os elementos de sub-arrays concatenados nele recursivamente até uma profundidade especificada. | "Achatando" um array de arrays, como `[[1, 2], [3, 4]]` para `[1, 2, 3, 4]`. | Muito útil para simplificar estruturas de dados aninhadas. | Se a profundidade do aninhamento for desconhecida, você pode usar `Infinity`, mas isso pode ser computacionalmente caro para estruturas muito profundas. |
| `with()` | Retorna uma **cópia** do array com um valor substituído em um determinado índice. | Atualizar um valor em um array de forma imutável, comum em frameworks como React. | Promove a imutabilidade, retornando uma nova cópia em vez de modificar o original. Sintaxe clara. | Método novo (ES2023). Pode não ser suportado em todos os ambientes. |

---

## **5. Ordenação e Inversão**

| Método | O que faz | Caso de Uso Comum | Vantagens (Quando usar) | Desvantagens (Quando não usar / Cuidado) |
| :--- | :--- | :--- | :--- | :--- |
| `sort()` | Ordena os elementos do array. | Ordenar uma lista de produtos por preço, ou uma lista de nomes em ordem alfabética. | Permite fornecer uma função de comparação customizada para ordenar qualquer tipo de dado. | **Muta o array original.** A ordenação padrão é baseada em strings Unicode, o que pode levar a resultados inesperados para números (ex: `[1, 10, 2]` vira `[1, 10, 2]`). Sempre forneça uma função de comparação para números. |
| `toSorted()` | Retorna uma **cópia** ordenada do array. | O mesmo que `sort()`, mas quando a imutabilidade é necessária. | Versão imutável do `sort()`, mais segura de usar em muitos contextos. | Método novo (ES2023). Verifique a compatibilidade do ambiente. |
| `reverse()` | Inverte a ordem dos elementos. | Inverter uma lista de comentários para mostrar os mais recentes primeiro. | Simples e eficaz para inverter a ordem. | **Muta o array original.** Se precisar manter o original, crie uma cópia primeiro (`[...arr].reverse()`). |
| `toReversed()` | Retorna uma **cópia** invertida do array. | O mesmo que `reverse()`, mas de forma imutável. | Versão imutável e mais segura do `reverse()`. | Método novo (ES2023). Verifique a compatibilidade. |

---

## **6. Conversão e Criação**

| Método | O que faz | Caso de Uso Comum | Vantagens (Quando usar) | Desvantagens (Quando não usar / Cuidado) |
| :--- | :--- | :--- | :--- | :--- |
| `join()` | Junta todos os elementos de um array em uma string. | Criar uma string a partir de um array, como uma lista de tags (`['react', 'js'].join(', ')`). | Muito útil para formatação de saída. Permite especificar um separador customizado. | Se o array contiver `null` ou `undefined`, eles serão convertidos para strings vazias. |
| `Array.from()` | Cria um novo array a partir de um objeto semelhante a um array (array-like) ou iterável. | Converter uma `NodeList` (retornada por `querySelectorAll`) em um array para poder usar `map`, `filter`, etc. | Ferramenta poderosa para converter várias estruturas de dados em arrays de verdade. | Requer um objeto que seja "iterável" ou tenha uma propriedade `length`. |
| `Array.of()` | Cria uma nova instância de Array com um número variável de argumentos, independentemente do número ou tipo. | Criar um array com valores específicos, especialmente útil para evitar o comportamento estranho de `new Array(10)` (que cria um array vazio de 10 posições). | Previsível e consistente na criação de arrays. | Menos comum no dia a dia, mas útil para garantir a criação correta de arrays com um único argumento numérico. |