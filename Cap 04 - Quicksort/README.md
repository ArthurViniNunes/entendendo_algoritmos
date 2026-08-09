# 📚 Grokking Algorithms

## Capítulo 4 — Quicksort

> **Status:**  ✅ Concluído
>
> **Data de estudo:** 08/08/2026

---

## 🎯 Objetivo do capítulo

São 3 os objetivos do capítulo:

1. Entender o algoritmo de ordenação Quicksort.
2. Compreender a técnica de divisão e conquista.
3. Analisar melhor a complexidade de algoritmos utilizando a notação Big O.

---

## 📖 Conceitos principais

Liste os conceitos abordados.

- Recursão
- Divisão e conquista
- Algoritmo de ordenação
- Quicksort

---

## 🧠 Resumo

Em suma o Quicksort é um algoritmo de ordenação eficiente que utiliza a técnica de divisão e conquista. Ele funciona escolhendo um elemento como pivô e particionando o array em dois subarrays: um com elementos menores que o pivô e outro com elementos maiores ou iguais ao pivô. Em seguida, aplica-se recursivamente o mesmo processo aos subarrays até que todos os elementos estejam ordenados.

A técnica de divisão e conquista é fundamental para a eficiência do Quicksort, permitindo que o problema seja quebrado em subproblemas menores e resolvido de forma recursiva. A complexidade média do Quicksort é O(n log n), tornando-o uma escolha popular para ordenação de grandes conjuntos de dados.

Big O é uma notação matemática utilizada para descrever o comportamento assintótico de algoritmos, permitindo comparar a eficiência de diferentes algoritmos em termos de tempo e espaço.

---

## 📚 Novos termos

| Termo | Significado |
| ------- | ------------- |
| DC (Divisão e Conquista) | Técnica de resolução de problemas que consiste em dividir um problema em subproblemas menores, resolvê-los recursivamente e combinar as soluções para obter a solução do problema original. |
| Quicksort | Algoritmo de ordenação que utiliza a técnica de divisão e conquista para ordenar elementos em um array. |
| Caso-base | Condição que determina quando a recursão deve parar, evitando chamadas infinitas. |
| Caso-recursivo | Condição que determina quando a recursão deve continuar, chamando a função novamente com novos parâmetros. |

---

## ⚙️ Algoritmos apresentados

| Algoritmo | Complexidade |             Objetivo          |
|-----------|--------------|-------------------------------|
| Quicksort | O(n log n)   | Ordenar elementos em um array |

---

## ⏱️ Complexidade

### Tempo

| Caso   | Complexidade |
|--------|--------------|
| Melhor |    O(n log n)|
| Médio  |    O(n log n)|
| Pior   |     O(n^2)   |

### Espaço

```txt
O(log n) -> Um para cada pivô, pois a cada chamada recursiva, o espaço de pilha aumenta.
```

---

## 💡 Intuição

A ideia é semelhante ao Mergesort, mas com a diferença de que o Quicksort realiza a ordenação "in-place" e geralmente é mais rápido na prática, utilizando menos memória. A técnica de divisão e conquista é fundamental para a eficiência do Quicksort, permitindo que o problema seja quebrado em subproblemas menores e resolvido de forma recursiva.

Pega-se um array de números e escolha um elemento como pivô. Em seguida, particione o array em dois subarrays: um com elementos menores que o pivô e outro com elementos maiores ou iguais ao pivô. Aplique recursivamente o mesmo processo aos subarrays até que todos os elementos estejam ordenados.

---

## 📝 Exemplo do livro

### Problema

Ordenar um array de números utilizando o algoritmo Quicksort.

### Entrada

```text
[3, 5, 2, 1, 4]
```

### Saída

```text
[1, 2, 3, 4, 5]
```

### Passo a passo

1. Escolha o primeiro elemento como pivô (3).
2. Particione o array em dois subarrays: [2, 1] (menores que 3) e [5, 4] (maiores ou iguais a 3).
3. Aplique recursivamente o Quicksort aos subarrays [2, 1] e [5, 4].
4. Para o subarray [2, 1], escolha 2 como pivô e particione em [1] e []. Aplique recursivamente o Quicksort aos subarrays [1] e [].
5. Para o subarray [5, 4], escolha 5 como pivô e particione em [4] e []. Aplique recursivamente o Quicksort aos subarrays [4] e [].
6. Combine os subarrays ordenados: [1, 2] + [3] + [4, 5] = [1, 2, 3, 4, 5].

---

## 💻 Implementação

### JavaScript / TypeScript

```ts
function quicksort(arr: number[]): number[] {
  if (arr.length <= 1) {
    return arr;
  }

  const pivot = arr[0];
  const left: number[] = [];
  const right: number[] = [];

  for (let i = 1; i < arr.length; i++) {
    if (arr[i] < pivot) {
      left.push(arr[i]);
    } else {
      right.push(arr[i]);
    }
  }

  return [...quicksort(left), pivot, ...quicksort(right)];
}

```

### Explicação

A ideia do Quicksort é escolher um elemento como pivô e particionar o array em dois subarrays: um com elementos menores que o pivô e outro com elementos maiores ou iguais ao pivô. Em seguida, aplicamos recursivamente o mesmo processo aos subarrays até que todos os elementos estejam ordenados.
Muito semelhante ao Mergesort, mas com a diferença de que o Quicksort realiza a ordenação "in-place" e geralmente é mais rápido na prática, utilizando menos memória.
Utiliza-se da técnica de divisão e conquista, quebrando o problema em subproblemas menores e resolvendo-os de forma recursiva.

---

## ✅ Exercícios do livro

### Exercício 4.1

**Enunciado:**

> Escreva o código para a função `soma`, vista anteriormente.

**Minha resposta:**

```ts
function soma(arr: number[]): number {
  if (arr.length === 0) {
    return 0;
  }
  return arr[0] + soma(arr.slice(1));
}
```

**Solução:**

```text
Para a função `soma`, a solução apresentada no livro é semelhante à minha resposta, utilizando recursão para somar os elementos do array. A função verifica se o array está vazio e retorna 0 nesse caso. Caso contrário, retorna o primeiro elemento do array somado à soma dos elementos restantes, obtida através da chamada recursiva com `arr.slice(1)`.
```

**Observações:**

Sei que poderiamos simplesmente usar um map e reduce, mas o objetivo é praticar a recursão.

### Exercício 4.2

**Enunciado:**

> Escreva uma função recursiva que conte o número de itens em uma lista.

**Minha resposta:**

```ts
function contarItens(arr:any[]): number {
  if (arr.length === 0) {
    return 0;
  }
  return 1 + contarItens(arr.slice(1));
}
```

**Solução:**

```text
A função `contarItens` verifica se o array está vazio e retorna 0 nesse caso. Caso contrário, retorna 1 (representando o primeiro item) somado à contagem dos itens restantes, obtida através da chamada recursiva com `arr.slice(1)`.
```

**Observações:**

Sei que poderiamos simplesmente usar o length do array, mas o objetivo é praticar a recursão.

---

### Exercício 4.3

**Enunciado:**

> Encontre o valor mais alto em uma lista.

**Minha resposta:**

```ts
function findHighest(arr:any[]): number {
  if (arr.length === 0) {
    return null;
  }
  const first = arr[0];
  const rest = findHighest(arr.slice(1)) ?? first;
  return first > rest ? first : rest;
}
```

**Solução:**

```text
A função `findHighest` verifica se o array está vazio e retorna null nesse caso. Caso contrário, compara o primeiro elemento com o maior elemento dos restantes, obtido através da chamada recursiva com `arr.slice(1)`.
```

**Observações:**

Sei que poderiamos simplesmente usar Math.max(...arr), mas o objetivo é praticar a recursão.

---

### Exercício 4.4

**Enunciado:**

> Você se lembra da pesquisa binária do Capítulo 1?
>Ela também é um algoritmo do tipo dividir para conquistar.
> Você consegue determinar o caso-base e o caso recursivo para a pesquisa binária?

**Minha resposta:**

```text
caso-base: array vazio ou com elemento central igual ao elemento desejado.
caso recursivo: dividir o array em duas metades e continuar a busca na metade que pode conter o elemento desejado.
```

**Solução:**

```text
Isso observa corretamente o caso-base e o caso recursivo da pesquisa binária. O caso-base ocorre quando o array está vazio ou quando o elemento central é igual ao elemento desejado. O caso recursivo envolve dividir o array em duas metades e continuar a busca na metade que pode conter o elemento desejado. A abordagem de dividir para conquistar é fundamental para a eficiência da pesquisa binária.
```

### Para os execícios seguintes

> Quanto tempo levaria, em notação Big O, para completar cada uma destas operações?

### Exercício 4.5

**Enunciado:**

> Imprimir o valor de cada elemento em um array.

**Minha resposta:**

```text
O(n)
```

**Solução:**

```text
O motivo é que precisamos percorrer cada elemento do array uma vez para imprimir seu valor, resultando em uma complexidade linear O(n).
```

### Exercício 4.6

**Enunciado:**

> Duplicar o valor de cada elemento em um array

**Minha resposta:**

```text
O(n)
```

**Solução:**

```text
Pelo mesmo motivo do exercício anterior, precisamos percorrer cada elemento do array uma vez para duplicar seu valor, resultando em uma complexidade linear O(n).
```

### Exercício 4.7

**Enunciado:**

> Duplicar o valor apenas do primeiro elemento do array.

**Minha resposta:**

```text
O(1)
```

**Solução:**

```text
O motivo é que precisamos acessar apenas o primeiro elemento do array para duplicar seu valor, resultando em uma complexidade constante O(1).
```

### Exercício 4.8

**Enunciado:**

> Criar uma tabela de multiplicação com todos os elementos do array.
> Assim, caso o seu array seja [2, 3, 7, 8, 10], você primeiro multiplicará cada elemento por 2.
> Depois, multiplicará cada elemento por 3 e então por 7, e assim por diante.

**Minha resposta:**

```text
O(n^2)
```

**Solução:**

```text
O motivo é que precisamos acessar cada elemento do array e multiplicá-lo por todos os outros elementos, resultando em uma complexidade quadrática O(n^2).
```

---

## ❓Dificuldades encontradas

- Como escolher o pivô de forma eficiente.
- Como lidar com arrays grandes e evitar estouro de pilha devido à recursão.
- Como otimizar o Quicksort para casos específicos, como arrays já ordenados ou com muitos elementos duplicados.

---

## 🚀 Aplicações práticas

Onde esse algoritmo é utilizado?

O Quicksort é amplamente utilizado em bibliotecas de ordenação padrão em várias linguagens de programação devido à sua eficiência média e desempenho rápido na prática. Ele é usado em sistemas de banco de dados, algoritmos de busca, processamento de dados e em qualquer aplicação que exija ordenação eficiente de grandes conjuntos de dados.

---

## ⚠️ Erros comuns

- Escolher o pivô de forma inadequada, o que pode levar a um desempenho ruim.
- Aplicar o Quicksort em arrays muito pequenos, onde algoritmos mais simples podem ser mais eficientes.
- Aplicar o Quicksort em arrays já ordenados ou quase ordenados, o que pode resultar em complexidade O(n^2) no pior caso.

---

## 🔄 Comparação com outros algoritmos

| Algoritmo | Quando usar | Quando evitar |
| ----------- | ------------- | --------------- |
| Quicksort | Arrays grandes e médios | Arrays muito pequenos, arrays já ordenados |
| Mergesort | Arrays grandes e médios, quando estabilidade é importante | Memória limitada |
| Bubble Sort | Arrays pequenos | Arrays grandes |

---

## 📌 Pontos importantes

- ✔ O Quicksort é um algoritmo eficiente para ordenar grandes conjuntos de dados.
- ✔ A escolha do pivô é crucial para o desempenho do Quicksort.
- ✔ O Quicksort pode ter desempenho ruim em arrays já ordenados ou quase ordenados.

---

## 🧩 O que aprendi

Aprendi sobre a técnica de divisão e conquista, como aplicá-la no Quicksort, a importância da escolha do pivô e como analisar a complexidade de algoritmos utilizando a notação Big O.

---

## 📖 Referências

- Livro: *Grokking Algorithms*
- Documentações utilizadas
- Artigos consultados

---

## ⭐ Nota pessoal

**Dificuldade:** ⭐⭐⭐☆☆

**Domínio do conteúdo:** ⭐⭐⭐⭐☆

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
