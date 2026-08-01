# 📚 Grokking Algorithms

## Capítulo 1 — Introdução a Algoritmos

> **Status:**  ✅ Concluído
>
> **Data de estudo:** 31/07/2026

---

## 🎯 Objetivo do capítulo

O objetivo deste capítulo é apresentar o conceito de algorítmos, introduzir a busca binária como um exemplo de algoritmo eficiente e discutir a importância da complexidade de tempo na análise de algoritmos.

---

## 📖 Conceitos principais

Liste os conceitos abordados.

- Busca binária
- Complexidade de tempo
- Tempo de execução
- Big O Notation
- Logaritmo

---

## 🧠 Resumo

Big O Notation é uma notação matemática usada para descrever o comportamento assintótico de funções, especialmente em relação à complexidade de tempo e espaço de algoritmos.

Busca binária é um algoritmo eficiente para encontrar um elemento em uma lista ordenada. Ele funciona dividindo a lista ao meio repetidamente até encontrar o elemento desejado ou determinar que ele não está presente. A complexidade de tempo da busca binária é O(log n), o que significa que o tempo de execução cresce lentamente à medida que o tamanho da lista aumenta.

Tempo de execução é uma medida de quanto tempo um algoritmo leva para completar sua tarefa, e a complexidade de tempo é uma forma de expressar isso em termos do tamanho da entrada.

A busca por algorítmos eficientes é crucial em ciência da computação, pois algoritmos mais rápidos podem lidar com conjuntos de dados maiores e melhorar o desempenho geral dos sistemas.

---

## 📚 Novos termos

| Termo | Significado                                                                 |
|-------|-----------------------------------------------------------------------------|
| Big O | Notação usada para descrever a complexidade de tempo e espaço de algoritmos |

---

## ⚙️ Algoritmos apresentados

| Algoritmo        | Complexidade | Objetivo                                                         |
|------------------|--------------|------------------------------------------------------------------|
| Busca Binária    | O(log n)     | Encontrar um elemento em uma lista ordenada                      |
| Busca sequencial | O(n)         | Encontrar um elemento em uma lista independente de sua ordenação |

---

## ⏱️ Complexidade da busca binária

### Tempo

| Caso   | Complexidade                                      |
|--------|---------------------------------------------------|
| Melhor | O(1) - Elemento encontrado na primeira tentativa  |
| Médio  | O(log n) - Elemento encontrado na média de etapas |
| Pior   | O(log n) - Elemento encontrado nas pontas         |

### Espaço

```txt
O(1) - A busca binária não requer espaço adicional significativo, pois é realizada em uma lista existente.
```

---

## 💡 Intuição

Esse algoritmo só pode ser implementado em listas ordenadas, ele funciona ao pegarmos um termo do meio da lista e compararmos com o termo que estamos procurando. Se o termo do meio for o que estamos procurando, então encontramos o termo. Caso contrário, existirão agoras 2 listas, uma a esquerda do termo do meio e outra a direita. Se tratando de valores numéricos, se o termo do meio for maior que o termo que estamos procurando, então o termo que estamos procurando estará na lista a esquerda do termo do meio. Caso contrário, ele estará na lista a direita do termo do meio. A cada iteração, a lista é dividida ao meio, até que o termo seja encontrado ou que não haja mais termos para serem comparados.

---

## 📝 Exemplo do livro

### Problema

Diga se o número K está presente em uma lista de N números ordenados.

### Entrada

```text
K = 5
N = 9
lista = [1, 3, 5, 6, 7, 9, 11, 13, 15]
```

### Saída

```text
True - O número K está presente na lista.
```

### Passo a passo

1. pegue o termo do meio da lista, que é 7, e compare com o termo que estamos procurando, que é 5.
2. Como 7 > 5, o termo que estamos procurando está à esquerda do termo do meio.
3. Repita o processo com a sublista à esquerda.
4. Encontre o termo 5.

---

## 💻 Implementação

### JavaScript / TypeScript

```ts
function buscaBinaria(lista: number[], termo: number): boolean {
    let esquerda = 0;
    let direita = lista.length - 1;
    let meio: number;

    while (esquerda <= direita) {
        meio = Math.floor((esquerda + direita)/2);
        
        if (lista[meio] == termo) {
            return true; // Termo encontrado com sucesso no index meio
        }

        if (lista[meio] > termo) {
            direita = meio - 1;
        } else {
            esquerda = meio + 1;
        }
    }
    return false; // Termo não encontrado
}
```

### Explicação

O algoritmo começa definindo os limites da lista, que são as variáveis `esquerda` e `direita`. Em seguida, ele entra em um loop que continua enquanto `esquerda` for menor ou igual a `direita`. Dentro do loop, ele calcula o índice do meio da lista e compara o valor nesse índice com o termo que estamos procurando. Se o valor do meio for igual ao termo, ele retorna `true`, indicando que o termo foi encontrado. Se o valor do meio for maior que o termo, ele ajusta o limite direito para `meio - 1`, descartando a metade direita da lista. Caso contrário, ele ajusta o limite esquerdo para `meio + 1`, descartando a metade esquerda da lista. Se o loop terminar sem encontrar o termo, ele retorna `false`, indicando que o termo não está presente na lista.

---

## ✅ Exercícios do livro

### Exercício 1.1

**Enunciado:**

> Suponha que você tenha uma lista com 128 nomes e esteja fazendo uma pesquisa binária.
> Qual seria o número máximo de etapas que vocêlevaria para encontrar o nome desejado?

**Minha resposta:**

```text
7
```

**Solução:**

```text
Para resolver isso, basta utilizarmos a ideia de logaritmo, que é a base da pesquisa binária.
Portanto, o número máximo de etapas seria log2(128) = 7.
```

**Observações:**

Isso pode ser confirmado com a seguinte sequência de divisões:

```txt
128 / 2 = 64
64 / 2 = 32
32 / 2 = 16
16 / 2 = 8
8 / 2 = 4
4 / 2 = 2
2 / 2 = 1 -> que é o nome que estamos procurando.
```

---

### Exercício 1.2

**Enunciado:**

> Suponha que você duplique o tamanho da lista.
> Qual seria o número máximo de etapas agora?

**Minha resposta:**

```text
8
```

**Solução:**

```text
Bom, como o tamanho da lista foi duplicado, agora temos 256 nomes.
Aplicando a mesma lógica do logarítmo, e reaproveitando o resultado do exercício anterior, sabemos que como para 128 nomes foram necessárias 7 etapas, para 256 nomes será necessária uma etapa a mais, ou seja, 8 etapas.
```

**Observações:**

Lembre-se das propriedades dos logaritmos:

```txt
log2(2 * 128) = log2(2) + log2(128) = 1 + 7 = 8
```

### Exercício 1.3

**Enunciado:**

> Forneça o tempo de execução do caso seguir em termos da notação Big O.
> Você tem um nome e deseja encontrar o número de telefone para esse nome em uma agenda telefônica.

**Minha resposta:**

```text
O(log n)
```

**Solução:**

```text
Consigo encontrar o número de telefone em log n etapas, pois a agenda telefônica é uma lista ordenada e posso utilizar a busca binária para encontrar o número de telefone.
```

**Observações:**

A ideia de busca binária não se restringe apenas a listas de números, ela pode ser aplicada em qualquer lista ordenada, como uma agenda telefônica, basta saber o que seria um "termo do meio" e como dividir a lista em duas partes (esquerda e direita, nesse caso alfabeticamente).

### Exercício 1.4

**Enunciado:**

> Forneça o tempo de execução do caso seguir em termos da notação Big O.
> Você tem um número de telefone e deseja encontrar o dono dele em uma agenda telefônica.

**Minha resposta:**

```text
O(n)
```

**Solução:**

```text
Nesse caso, não é possível utilizar a busca binária, pois a agenda telefônica não é ordenada por número de telefone, e sim por nome. Portanto, a única forma de encontrar o dono do número de telefone é percorrendo toda a lista, o que leva O(n) etapas.
```

**Observações:**

O pior caso seria se o número de telefone que estamos procurando não estiver na lista, pois teríamos que percorrer toda a lista para ter certeza de que ele não está presente ou, em caso de certeza de que ele está presente, ele estar no final da lista, o que também nos obrigaria a percorrer toda a lista.

### Exercício 1.5

**Enunciado:**

> Forneça o tempo de execução do caso seguir em termos da notação Big O.
> Você quer ler o número de cada pessoa da agenda telefônica.

**Minha resposta:**

```text
O(n)
```

**Solução:**

```text
Precisaríamos percorrer toda a lista para ler o número de cada pessoa, o que leva n passos, ou seja, O(n).
```

**Observações:**

Esse é um caso em que conseguimos dizer com certeza que o tempo de execução é O(n), pois precisamos percorrer toda a lista para ler o número de cada pessoa, não há como otimizar esse processo. Sendo assim, ele recebe também os valores teta(n) e omega(n), pois independentemente do tamanho da lista, precisaremos percorrer toda a lista para ler o número de cada pessoa.
Para ler mais sobre a notação teta e omega, consulte o capítulo 2 do livro, consulte:
[Entendendo as notações Big O, Big Theta e Big Omega em análise de algoritmos](https://medium.com/@adnan.mehrat/understanding-big-o-big-theta-%CE%B8-and-big-omega-%CF%89-notations-in-algorithm-analysis-7f876aa922b4)

### Exercício 1.6

**Enunciado:**

> Forneça o tempo de execução do caso seguir em termos da notação Big O.
> Você quer ler os números apenas dos nomes que começam com A.

**Minha resposta:**

```text
O(n)
```

**Solução:**

```text
Vamos supor que a agenda telefônica esteja ordenada alfabeticamente, então os nomes que começam com A estarão no início da lista. Nesse caso, o tempo de execução seria O(k), onde k é o número de nomes que começam com A. No entanto, como não sabemos quantos nomes começam com A, podemos considerar o pior caso, que seria percorrer toda a lista para encontrar todos os nomes que começam com A, o que nos leva a O(n). Ou podemos, ainda, considerar que cada letra do alfabeto tem uma quantidade similar de nomes, então o tempo de execução seria O(n/26), que é O(n) também.
```

**Observações:**

Como recomendado pelo livro, isso será melhor abordado no capítulo 4, em que entenderemos melhor como funciona a notação Big O e como ela se aplica a diferentes casos.

---

## ❓Dificuldades encontradas

- Constantes não são levadas em consideração na notação Big O, o que pode ser confuso no início.
- A notação Big O não leva em consideração o tempo de execução real do algoritmo, apenas a ordem de crescimento.

---

## 🚀 Aplicações práticas

Onde esse algoritmo é utilizado?

- Busca em cenários em que os dados estão ordenados, como em listas de contatos, dicionários, bancos de dados indexados, etc.
- Conhecer sobre a complexidade de tempo de um algoritmo é importante para escolher o algoritmo mais eficiente para um determinado problema, especialmente quando lidamos com grandes volumes de dados.

---

## ⚠️ Erros comuns

- Nem todo cenário de busca pode ser resolvido com busca binária, é necessário que os dados estejam ordenados.
- No calculo de Big O, não se deve considerar constantes, apenas a ordem de crescimento da função.

---

## 🔄 Comparação com outros algoritmos

| Algoritmo        | Quando usar         | Quando evitar       |
|------------------|---------------------|---------------------|
| Busca Binária    | Dados ordenados     | Dados não ordenados |
| Busca Sequencial | Dados não ordenados | Dados ordenados     |

---

## 📌 Pontos importantes

- ✔ A busca binária é mais eficiente que a busca sequencial para listas ordenadas.
- ✔ A notação Big O nos ajuda a entender a complexidade de tempo de um algoritmo.
- ✔ É importante considerar o pior caso ao analisar a complexidade de um algoritmo.

---

## 🧩 O que aprendi

A busca binária é um algoritmo eficiente para encontrar elementos em listas ordenadas, com complexidade de tempo O(log n). A notação Big O é uma ferramenta útil para analisar a eficiência dos algoritmos, permitindo-nos comparar diferentes abordagens e escolher a mais adequada para um problema específico. Além disso, é essencial entender as limitações e os casos de uso apropriados para cada algoritmo.

---

## 📖 Referências

- Livro: *Grokking Algorithms*
- Artigos consultados: [Entendendo as notações Big O, Big Theta e Big Omega em análise de algoritmos](https://medium.com/@adnan.mehrat/understanding-big-o-big-theta-%CE%B8-and-big-omega-%CF%89-notations-in-algorithm-analysis-7f876aa922b4)

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
