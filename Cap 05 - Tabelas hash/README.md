# 📚 Grokking Algorithms

## Capítulo 5 — Tabelas hash

> **Status:** ✅ Concluído
>
> **Data de estudo:** 09/09/2026

---

## 🎯 Objetivo do capítulo

O objetivo central é introduzir a estrutura de dados hash e suas nuances.

---

## 📖 Conceitos principais

- Hash
- Colisões
- Consistência
- Fator de carga

---

## 🧠 Resumo

Hash é uma estrutura de dados utilizada em diversos cenários, a ideia é utilizar uma função auxiliar para encontrar rápidamente um dado armazenado.
A principal dificuldade encontrada na implementação de um hashing é a definição de sua função,
uma vez que a mesma deve evitar as colisões enquanto mantêm sua consistência.

---

## 📚 Novos termos

| Termo | Significado |
| :--- | :--- |
| **Colisão | Ocorre quando dois elementos diferentes geram exatamente o mesmo índice através da função hash. Como duas chaves não podem ocupar o mesmo espaço diretamente, a tabela precisa de uma estratégia (como encadeamento ou endereçamento aberto) para resolver o conflito. |
| Função Hash | O algoritmo responsável por transformar uma chave de entrada (como um texto ou número) em um índice numérico dentro dos limites do array da tabela. Uma boa função distribui os elementos de forma uniforme para evitar colisões. |
| Fator de carga | A razão entre o número de elementos armazenados e o tamanho total da tabela ($\alpha = \frac{n}{k}$). Ele indica o quão cheia a tabela está e é usado para decidir o momento exato de redimensioná-la (fazer o *rehash*) para manter as buscas rápidas. |

---

## ⏱️ Complexidade de busca em hash

### Tempo

| Caso   | Complexidade                  |
|--------|-------------------------------|
| Melhor |         O(1)                  |
| Médio  |         O(1)                  |
| Pior   |    O(n) (excesso de colisões) |

### Espaço

```txt
O(n)
```

---

## 💡 Intuição

A ideia é, ao invés de conferir toda uma lista de informações para encontrar em que local está o dado objetivo,
basta buscar diretamente no resultado de uma função de hashing.

---

## 📝 Exemplo do livro

### Problema

Sistema de votação em que cada pessoa só pode votar uma vez. Se já voltou, recusa; Se não, registra o voto.

### Entrada

```text
nome
```

### Saída

```text
Voto registrado ou recusado
```

### Passo a passo

1. Receber nome
2. Conferir se  o dono desse nome já votou
3. Se já votou, recusa o voto
4. Se não, registra o voto e marca o nome como "já votante"

---

## 💻 Implementação

### JavaScript / TypeScript

```ts

const alreadyVoted: Record<string, boolean | undefined> = {};

function can_vote(name: string): boolean {
  const voted = alreadyVoted[name];

  if (voted) {
    return false; // Não permito voto
  }

  alreadyVoted[name] = true; // Registra que já votou
  return true; // Permite voto
}

```

### Explicação

A ideia é simples, crio um dicionário e adiciono o nome da pessoa mais o fato dela já ter votado nele.
Caso o nome da pessoa não esteja no dicionário ou seu valor seja diferente de `true`, recuso o voto.
Caso contrário registro o nome da pessoa, marcando como já votante (valor `true`) e permito o voto.

---

## ✅ Exercícios do livro

### Exercícios 5.1 a 5.4

**Enunciado:**

> Quais destas funções hash são consistentes?

> 5.1 f(x) = 1
> *retorna 1 independentemente da entrada*

> 5.2 f(x) = rand()
> *retorna um número aleatório a cada execução*

> 5.3 f(x) = proximo_espaco_vazio()
> *retorna o índice do próximo espaço livre da tabela hash*

> 5.4 f(x) = len(x)
> *usa o comprimento da string como índice*

**Minha resposta:**

```text
5.1 e 5.4
```

**Solução:**

```text
A consistência de uma função hash é dada pela sua capacidade de, dada a mesma entrada, teremos a mesma saída.
Isso ocorre somente nas funções 5.1 e 5.4.
```

**Observações:**

Reforço, porém para atenção. Para ser uma "boa" função de hash, não basta apenas ser consistente.
É necessário um estudo para diminuir ao máximo o número de colisões para que a estrutura de dados permaneça eficiente.

Exemplo:

f(x) = 1 realmente é consistente, mas é uma PÉSSIMA função de hashing, por causar colisões em todas as entradas,
o que diminui a eficácia da estrutura de dados drásticamente.

---

### Exercícios 5.5 a 5.7

**Enunciado:**

> Suponha que você tenha estas quatro funções hash que operam com
strings:
> a.Retorne “1” para qualquer entrada.
>
> b. Use o comprimento da string como o índice.
>
> c. Use o primeiro caractere da string como índice. Assim, todas as strings
que iniciam com a letra a são hasheadas juntas e assim por diante.
>
>d. Mapeie cada letra para um número primo: a = 2, b = 3, c = 5, d = 7, e =
11, e assim por diante. Para uma string, a função hash é a soma de todos
os caracteres-módulo² conforme o tamanho da hash. Se o tamanho de
sua hash for 10, por exemplo, e a string for “bag”, o índice será (3 + 2 + 1) % 10 = 22 % 10 = 2.
>
>Para cada um destes exemplos, qual função hash fornecerá uma boa
distribuição? Considere que o tamanho da tabela hash tenha dez espaços.
>
>5.5 Uma lista telefônica em que as chaves são os nomes e os valores são os
números telefônicos. Os nomes são os seguintes: Esther, Ben, Bob e
Dan.
>
>5.6 Um mapeamento do tamanho de baterias e sua devida potência. Os
tamanhos são A, AA, AAA e AAAA.
>
>5.7 Um mapeamento de títulos de livros e autores. Os títulos são Maus,
Fun Home e Watchmen.

**Minha resposta:**

```text
- 5.5 d
- 5.6 b
- 5.7 c
```

**Solução:**

```text
Inicialmente podemos ignorar a existência da função a, uma vez que SEMPRE causa colisões.
Já os demais analisamos a depender do cenário, aplicando a devida complexidade que ocasiona em colisões no cenário.
```

---

## ❓Dificuldades encontradas

- Encontrar funções hash cabíveis para cada cenário
- Como implementar um hash do zero
- Diferenciação entre consistência e adequabilidade da função de hash

---

## 🚀 Aplicações práticas

Onde esse algoritmo é utilizado?

- Caching
- Cenários com muitos dados e necessidades de buscas
- Duplas de dados com ideia de "chave e valor"

---

## ⚠️ Erros comuns

- Usar funções de hash inconsistente
- Escolher funções de hash com alta taxa de colisões
- Não realizar *resize* após fator de carga ficar alto

---

## 🧩 O que aprendi

Hash é uma estrutura de dados interessantíssima e de alta otimização para dados que necessitam ser consultados com rapidez, combina a ideia de uso de um array para indexação com lista encadeada.

---

## 📖 Referências

- Livro: *Grokking Algorithms*

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
