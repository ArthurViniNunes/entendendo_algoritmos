# 📚 Grokking Algorithms

## Capítulo 2 — Ordenação por Seleção

> **Status:**  ✅ Concluído
>
> **Data de estudo:** 01/08/2026

---

## 🎯 Objetivo do capítulo

Entender qual a melhor estrutura de dados para armazenar informações, considerando o tipo de operação que será realizada com mais frequência, bem como introduzir o conceito de estrutura híbrida, que combina arrays e listas encadeadas para otimizar operações de inserção e remoção.
Ademais, vale acrescentar que o capítulo aborda a importância de escolher a estrutura de dados correta para cada situação, considerando fatores como eficiência, complexidade e frequência das operações.
Por fim apresenta ordenação por seleção, um algoritmo de ordenação simples, mas eficiente para listas pequenas, e como ele pode ser implementado.

---

## 📖 Conceitos principais

Liste os conceitos abordados.

- Array
- Lista encadeada
- Estrutura híbrida (array de listas encadeadas)
- Ordenação por seleção

---

## 🧠 Resumo

O capítulo aborda a importância de escolher a estrutura de dados correta para cada situação, considerando fatores como eficiência, complexidade e frequência das operações. Ele também explica que a memória do computador funciona como um conjunto de gavetas: para armazenar informações, precisamos pedir espaço e organizar esses dados de forma adequada. O texto apresenta arrays e listas encadeadas, destacando suas vantagens e desvantagens em diferentes cenários. Além disso, introduz a ideia de uma estrutura híbrida, que combina arrays e listas encadeadas para otimizar operações de inserção e remoção.
Ao fazer isso, o capítulo enfatiza a necessidade de analisar o contexto e as necessidades específicas do sistema antes de decidir qual estrutura de dados utilizar. Por fim, o capítulo apresenta o algoritmo de ordenação por seleção, explicando seu funcionamento e como implementá-lo.
Ao final, o capítulo reforça a importância de entender as características de cada estrutura de dados e algoritmo para tomar decisões informadas ao projetar sistemas eficientes, e introduz a ideia de ordenação por seleção, um algoritmo simples, mas eficiente para listas pequenas, apresentando seu funcionamento e implementação.

---

## 📚 Novos termos

| Termo | Significado |
| ------- | ------------- |
| índice | Posição de um elemento em um array |
| array | Estrutura de dados que armazena elementos em posições contíguas |
| lista encadeada | Estrutura de dados que armazena elementos em posições não contíguas |
| estrutura híbrida | Combinação de array e lista encadeada para otimizar operações de inserção e remoção |
| ordenação por seleção | Algoritmo de ordenação que seleciona o menor elemento e o coloca na posição correta |

---

## ⚙️ Operações nas estruturas de dados apresentados

|   Operação   |Lista  |Array |
|------------- |------ |------|
|Leitura       | O(n)  | O(1) |
|Inserção      | O(1)  | O(n) |
|Remoção       | O(1)  | O(n) |

---

## ⏱️ Complexidade do algoritmo de ordenação por seleção

### Tempo

| Caso   | Complexidade |
|--------|--------------|
| Melhor | O(n²)        |
| Médio  | O(n²)        |
| Pior   | O(n²)        |

### Espaço

```txt
O(n) -> Espaço necessário para armazenar a lista de elementos a serem ordenados.
```

---

## 💡 Intuição do algoritmo de ordenação por seleção

O algoritmo de ordenação por seleção funciona selecionando o menor elemento da lista e colocando-o na posição correta.
Em seguida, ele seleciona o próximo menor elemento e o coloca na próxima posição correta, e assim por diante, até que todos os elementos estejam ordenados.
A ideia é parecida com a de "ordenar um baralho de cartas", onde você pega a carta mais baixa e a coloca na posição correta, depois pega a próxima carta mais baixa e a coloca na próxima posição correta, e assim por diante.

---

## 📝 Exemplo do livro

### Problema

> Suponha que você tenha um monte de músicas no seu computador.
> Para cada artista, você tem um contador de plays.
> Você quer ordenar uma lista de artistas, do artista mais tocado para o menos tocado, para que possa categorizar os seus artistas favoritos.
> Como pode fazer isso?

### Entrada

```text
[Artista 1: 100 plays, Artista 2: 200 plays, Artista 3: 50 plays]
```

### Saída

```text
[Artista 2: 200 plays, Artista 1: 100 plays, Artista 3: 50 plays]
```

### Passo a passo

1. Dos artistas ainda não ordenados, encontre o artista com o maior número de plays.
2. Coloque esse artista na primeira posição da lista ordenada (a mais proxima do início, ainda não ocupada).
3. Repita o processo para os artistas restantes, encontrando o próximo artista com o maior número de plays e colocando-o na próxima posição da lista ordenada.
4. Retorne a lista ordenada de artistas, do mais tocado para o menos tocado, caso acabem os artistas.

---

## 💻 Implementação

### JavaScript / TypeScript

```ts
function findIndexOfLargest(arr: number[]): number {
    if (arr.length === 0) {
        throw new Error("Array cannot be empty");
    }

    let largest = arr[0];
    let index = 0;

    for (let i = 1; i < arr.length; i++) {
        if (arr[i] > largest) {
            largest = arr[i];
            index = i;
        }
    }

    return index;
}

function selectionSort(arr: number[]): number[] {
    const items = [...arr];
    const sorted: number[] = [];

    while (items.length > 0) {
        const largestIndex = findIndexOfLargest(items);
        sorted.push(items[largestIndex]);
        items.splice(largestIndex, 1);
    }

    return sorted;
}

```

### Explicação

Inicialmente, a função `findIndexOfLargest` percorre o array para encontrar o índice do maior elemento. Em seguida, a função `selectionSort` cria uma cópia do array original e, enquanto houver elementos na cópia, encontra o índice do maior elemento, adiciona esse elemento ao array `sorted` e remove-o da cópia. O processo se repete até que todos os elementos sejam ordenados.

---

## ✅ Exercícios do livro

### Exercício 2.1

**Enunciado:**

> Suponha que você esteja criando um aplicativo para acompanhar as suas finanças.
> Todos os dias você anotará tudo o que gastou e onde gastou.
> No final do mês, você deverá revisar os seus gastos e resumir o quanto gastou.
> Logo, você terá um monte de inserções e poucas leituras.
> Você deverá usar um array ou uma lista para implementar este aplicativo?

**Minha resposta:**

```text
Lista
```

**Solução:**

```text
O motivo da preferência por utilizar uma lista vem do fato de que suas operações de inserção e remoção são mais eficientes do que em um array.
Nesse caso, como o aplicativo terá muitas inserções e poucas leituras, a lista é a melhor escolha.
Além do fato de que as despesas podem não ser previsíveis em suas quantidades, o que torna a lista mais flexível.
```

**Observações:**

Lembre-se:

| Operação|Lista |Array|
|-------- |----- |-----|
|Leitura  | O(n) |O(1) |
|Inserção |O(1)  |O(n) |
|Remoção  |O(1)  |O(n) |

---

### Exercício 2.2

**Enunciado:**

> Suponha que você esteja criando um aplicativo para anotar os pedidos dos clientes em um restaurante.
> Seu aplicativo precisa de uma lista de pedidos.
> Os garçons adicionam os pedidos a essa lista e os chefes
> retiram os pedidos da lista. Funciona como uma fila.
> Os garçons colocam os pedidos no final da fila e os chefes retiram os pedidos do começo dela para cozinhá-los.
> Você usaria um array ou uma lista encadeada para implementar essa lista?

**Minha resposta:**

```text
Lista encadeada
```

**Solução:**

```text
Como foi bem dito durante o texto, é uma lista, nesse caso a lista seria duplamente encadeada, pois os garçons adicionam os pedidos no final da lista e os chefes retiram do começo da lista. O motivo da escolha é a facilidade de realizar operações de inserção e remoção no início e no final da lista.
```

---

### Exercício 2.3

**Enunciado:**

> Vamos analisar um experimento.
> Imagine que o Facebook guarda uma lista de usuários.
> Quando alguém tenta acessar o Facebook, uma busca é feita pelo nome de usuário. Se o nome da pessoa está na lista, ela pode continuar o acesso.
> As pessoas acessam o Facebook com muita frequência, então existem muitas buscas nessa lista.
> Presuma que o Facebook usa a pesquisa binária para procurar um nome na lista.
> A pesquisa binária requer acesso aleatório – você precisa ser capaz de acessar o meio da lista de nomes instantaneamente.
> Sabendo disso, você implementaria essa lista como um array ou uma lista encadeada?

**Minha resposta:**

```text
Array
```

**Solução:**

```text
Neste caso, a escolha do array é imprescindível, pois a pesquisa binária requer acesso aleatório, o que é possível em arrays, mas não em listas encadeadas. Além disso, como existem muitas buscas nessa lista, o array é mais eficiente para esse tipo de operação.
```

**Observações:**

Lembre-se da busca binária do [capítulo 1](../Cap%2001%20-%20Busca%20bin%C3%A1ria/README.md), que é um algoritmo de busca eficiente, mas que requer acesso aleatório aos elementos da lista.

---

### Exercício 2.4

**Enunciado:**

> As pessoas se inscrevem no Facebook com muita frequência também.
> Suponha que você decida usar um array para armazenar a lista de usuários.
> Quais as desvantagens de um array em relação às inserções?
> Em particular, imagine que você está usando a pesquisa binária para buscar os logins.
> O que acontece quando você adiciona novos usuários em um array?

**Minha resposta:**

```text
Necessidade de realocar o array.
Necessidade de manter o array ordenado.
```

**Solução:**

```text
Os principais problemas de se usar um array para armazenar a lista de usuários são:
1. Necessidade de realocar o array: Quando o array atinge sua capacidade máxima, é necessário criar um novo array maior e copiar todos os elementos do array antigo para o novo. Isso pode ser uma operação custosa em termos de tempo, especialmente se ocorrer com frequência.
2. Necessidade de manter o array ordenado: Para que a pesquisa binária funcione corretamente, o array precisa estar sempre ordenado. Isso significa que, ao adicionar novos usuários, é necessário inserir os elementos na posição correta para manter a ordem, o que pode ser uma operação custosa em termos de tempo.
Sendo assim, a escolha de um array para armazenar a lista de usuários pode levar a problemas de desempenho e complexidade adicional na manutenção da estrutura de dados.
Porém, se a frequência de inserções for baixa e a frequência de buscas for alta, o array ainda pode ser uma escolha viável devido à eficiência da pesquisa binária.
```

---

### Exercício 2.5

**Enunciado:**

> Na verdade, o Facebook não usa nem arrays nem listas encadeadas para armazenar informações.
> Vamos considerar uma estrutura de dados híbrida: um array de listas encadeadas.
> Você tem um array com 26 slots. Cada slot aponta para uma lista encadeada.
> Por exemplo, o primeiro slot do array aponta para uma lista encadeada que contém os usuários que começam com a letra A.
> O segundo slot aponta para a lista encadeada que contém os usuários que começam com a letra B, e assim por diante.
>
> Suponha que o Adit B se inscreva no Facebook e você queira adicioná-lo à lista.
> Você vai ao slot 1 do array, a seguir para a lista encadeada do slot 1, e adiciona Adit B no final.
> Agora, suponha que você queira procurar oZakhir H.
> Você vai ao slot 26, que aponta para a lista encadeada de todos os nomes começados em Z.
> Então, procura pela lista até encontrar o Zakhir H.
>
> Compare esta estrutura híbrida com arrays e listas encadeadas.
> É mais lento ou mais rápido fazer inserções e eliminações nesse caso?
> Você não precisa responder dando o tempo de execução Big(O), apenas diga se a nova estrutura de dados é mais rápida ou mais lenta do que os arrays e as listas encadeadas.

**Minha resposta:**

```text
É mais rápido fazer inserções e eliminações nessa estrutura híbrida do que em arrays e listas encadeadas.
```

**Solução:**

```text
A estrutura híbrida de um array de listas encadeadas oferece vantagens em termos de eficiência para inserções e eliminações em comparação com arrays e listas encadeadas puras.
1. Inserções: Ao adicionar um novo usuário, você pode acessar diretamente o slot correspondente à primeira letra do nome do usuário, o que reduz significativamente o tempo de busca para encontrar a posição correta na lista encadeada. Isso torna as inserções mais rápidas do que em um array, onde seria necessário realocar e manter a ordem, ou em uma lista encadeada pura, onde seria necessário percorrer toda a lista para encontrar a posição correta.
2. Eliminações: Da mesma forma, ao remover um usuário, você pode acessar diretamente o slot correspondente à primeira letra do nome do usuário e percorrer apenas a lista encadeada associada a esse slot. Isso reduz o tempo de busca para encontrar o usuário a ser removido, tornando as eliminações mais rápidas do que em um array ou em uma lista encadeada pura.
Portanto, a estrutura híbrida de um array de listas encadeadas é mais eficiente para operações de inserção e eliminação em comparação com arrays e listas encadeadas puras, especialmente quando há uma grande quantidade de dados a serem gerenciados.

```

**Observações:**

É muito importante entender que a escolha da estrutura de dados depende do contexto e das operações que serão realizadas com mais frequência. A estrutura híbrida é uma solução eficiente para cenários onde há muitas inserções e eliminações, mas pode não ser a melhor escolha para outros casos, como buscas frequentes em uma lista ordenada.
Sendo assim, é fundamental analisar o contexto e as necessidades específicas do sistema antes de decidir qual estrutura de dados utilizar.

---

## ❓Dificuldades encontradas

- Entender em que momento utilizar uma estrutura de dados híbrida, considerando o balanceamento entre desempenho e complexidade de implementação.
- Entender como a escolha da estrutura de dados pode impactar o desempenho geral do sistema.

---

## 🚀 Aplicações práticas

Onde essas estruturas de dados são utilizadas?

- Array: Armazenamento de dados em memória, implementação de vetores e matrizes, manipulação de imagens e gráficos, entre outros.
- Lista encadeada: Implementação de filas e pilhas, gerenciamento de memória dinâmica, sistemas de arquivos, entre outros.
- Estrutura híbrida (array de listas encadeadas): Sistemas de gerenciamento de usuários, bancos de dados, tabelas de dispersão (hash tables), entre outros.

---

## ⚠️ Erros comuns

- Confundir arrays com listas encadeadas, não entendendo as diferenças entre elas.
- Não considerar a complexidade de inserção e remoção ao escolher uma estrutura de dados.
- Não analisar o contexto e as necessidades específicas do sistema antes de decidir qual estrutura de dados utilizar.
- Não entender que a escolha da estrutura de dados pode impactar o desempenho geral do sistema.
- Não entender que a escolha da estrutura de dados pode impactar a complexidade de implementação do sistema.

---

## 📌 Pontos importantes

- ✔ É fundamental entender as diferenças entre arrays e listas encadeadas, bem como suas vantagens e desvantagens em diferentes cenários.
- ✔ A escolha da estrutura de dados correta depende do contexto e das operações que serão realizadas com mais frequência.
- ✔ A estrutura híbrida (array de listas encadeadas) é uma solução eficiente para cenários onde há muitas inserções e eliminações, mas pode não ser a melhor escolha para outros casos, como buscas frequentes em uma lista ordenada.
- ✔ A escolha da estrutura de dados pode impactar o desempenho geral do sistema, bem como a complexidade de implementação do mesmo.

---

## 🧩 O que aprendi

O motivo da escolha de uma estrutura de dados depende do contexto e das operações que serão realizadas com mais frequência. A estrutura híbrida é uma solução eficiente para cenários onde há muitas inserções e eliminações, mas pode não ser a melhor escolha para outros casos, como buscas frequentes em uma lista ordenada. É fundamental analisar o contexto e as necessidades específicas do sistema antes de decidir qual estrutura de dados utilizar.

---

## 📖 Referências

- Livro: *Grokking Algorithms*

---

## ⭐ Nota pessoal

**Dificuldade:** ⭐☆☆☆☆

**Domínio do conteúdo:** ⭐⭐⭐⭐⭐

**Preciso revisar?**

- [ ] Sim
- [x] Não

---

## 📋 Checklist

- [x] Li o capítulo
- [x] Fiz todos os exercícios
- [x] Implementei os exemplos
- [x] Entendi a complexidade
- [x] Consigo explicar sem consultar o livro
