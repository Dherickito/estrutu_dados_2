# Guia Completo: Resolução dos Desafios de Grafos

Este guia detalha os conceitos fundamentais e o passo a passo completo para a resolução do **Desafio 5 (Isomorfismo)** e do **Desafio 7 (Sequência de Graus)** na teoria dos grafos.

---

## Parte 1: Conceitos Fundamentais

Antes de resolvermos os desafios, é essencial compreender alguns conceitos básicos da teoria de grafos:

1. **Grafo ($G$):** É uma estrutura composta por um conjunto de vértices e um conjunto de arestas que os conectam.
2. **Vértices ($V$):** São os pontos, nós ou elementos fundamentais do grafo.
3. **Arestas ($E$):** São as linhas que estabelecem conexões diretas entre os vértices.
4. **Ordem de um Grafo:** Representa a quantidade total de vértices ($\vert{}V\vert{}$).
5. **Tamanho de um Grafo:** Representa a quantidade total de arestas ($\vert{}E\vert{}$).
6. **Grau de um Vértice:** É o número de arestas incidentes a esse vértice (quantas "pontas de linha" chegam nele).
7. **Grafo Simples:** Um grafo que não possui laços (arestas que ligam um vértice a ele mesmo) nem arestas paralelas (mais de uma aresta entre o mesmo par de vértices).

---

## Parte 2: Desafio 5 — Isomorfismo de Grafos

O objetivo do isomorfismo é determinar se dois grafos estruturalmente idênticos possuem a mesma disposição de conexões, mesmo que seus desenhos e rótulos pareçam diferentes.

### Dados Iniciais
* **Grafo G:** $V = \{1, 2, 3, 4\}$ e $E = \{(1,2), (2,3), (3,4), (4,1)\}$
* **Grafo H:** $V = \{a, b, c, d\}$ e $E = \{(a,c), (c,b), (b,d), (d,a)\}$

### Passo a Passo da Resolução

#### Passo 1: Determinar a ordem e o tamanho de cada grafo
* **No Grafo G:** Contamos 4 elementos em $V$, logo a ordem é 4. Contamos 4 pares em $E$, logo o tamanho é 4.
* **No Grafo H:** Contamos 4 elementos em $V$, logo a ordem é 4. Contamos 4 pares em $E$, logo o tamanho é 4.
* *Conclusão parcial:* Como ambos possuem a mesma ordem e o mesmo tamanho, eles passam no primeiro teste de compatibilidade.

#### Passo 2: Calcular o grau de cada vértice e a sequência de graus
* **No Grafo G:** Cada vértice está conectado a outros 2 vizinhos formando um ciclo. O grau de cada vértice é 2. Sequência de graus: $(2, 2, 2, 2)$.
* **No Grafo H:** Cada vértice também está conectado a outros 2 vizinhos em um ciclo. O grau de cada vértice é 2. Sequência de graus: $(2, 2, 2, 2)$.

#### Passo 3: Procurar uma correspondência entre os vértices de G e os de H
Estabelecemos uma função bijetora (mapeamento) entre os conjuntos:
* Vértice $1 \rightarrow$ Correspondente $a$
* Vértice $2 \rightarrow$ Correspondente $c$
* Vértice $3 \rightarrow$ Correspondente $b$
* Vértice $4 \rightarrow$ Correspondente $d$

#### Passo 4: Verificar, aresta por aresta, a preservação de adjacências
Validamos se as conexões de $G$ encontram correspondentes exatos em $H$:
* Aresta $(1,2)$ em $G$ mapeia para o par $(a,c)$ em $H$ (que pertence ao conjunto de arestas de $H$).
* Aresta $(2,3)$ em $G$ mapeia para o par $(c,b)$ em $H$ (que pertence ao conjunto de arestas de $H$).
* Aresta $(3,4)$ em $G$ mapeia para o par $(b,d)$ em $H$ (que pertence ao conjunto de arestas de $H$).
* Aresta $(4,1)$ em $G$ mapeia para o par $(d,a)$ em $H$ (que pertence ao conjunto de arestas de $H$).

#### Passo 5: Conclusão
Os grafos **são isomorfos**, pois a bijeção estabelecida preserva rigorosamente todas as adjacências estruturais.

* **Reflexão Importante:** Ter a mesma sequência de graus **não** é suficiente para garantir o isomorfismo. É apenas uma condição necessária, mas diferentes estruturas de grafos podem compartilhar a mesma distribuição de graus sem possuírem a mesma conectividade exata.

---

## Parte 3: Desafio 7 — Construção de Grafo a partir da Sequência de Graus

Este desafio consiste em desenhar ou estruturar um grafo simples com base em uma lista pré-determinada de graus em ordem não decrescente.

### Dados Iniciais
* **Sequência de Graus:** $(1, 1, 2, 3, 3, 4, 4, 6)$
* **Vértices:** $A, B, C, D, E, F, G, H$ (Total de 8 vértices)

### Passo a Passo da Resolução

#### Passo 1: Identificação dos vértices
Definimos o conjunto de vértices: $V = \{A, B, C, D, E, F, G, H\}$.

#### Passo 2: Início da construção pelo maior grau
* O vértice $H$ possui grau 6 (o maior da sequência). Isso significa que ele deve ser conectado diretamente a outros 6 vértices distintos do conjunto.
* Conectamos $H$ a $A, B, C, D, E$ e $F$, deixando $G$ temporariamente sem essa ligação direta.

#### Passo 3: Distribuição das demais arestas
* Ajustamos as conexões restantes entre os demais vértices para satisfazer exatamente a demanda de grau de cada um, evitando laços (arestas de um vértice para ele mesmo) e arestas paralelas.

#### Passo 4: Registro do Conjunto de Arestas ($E$)
O conjunto de arestas resultante da construção é:
$E = \{(H,A), (H,B), (H,C), (H,D), (H,E), (H,F), (C,G), (D,G), (E,G), (F,G), (F,C), (D,E)\}$

#### Passo 5: Cálculo dos Graus Obtidos
Contando o número de conexões incidentes em cada vértice no grafo construído:
* **A:** Grau 1
* **B:** Grau 1
* **C:** Grau 2
* **D:** Grau 3
* **E:** Grau 3
* **F:** Grau 4
* **G:** Grau 4
* **H:** Grau 6
* **Sequência Obtida:** $(1, 1, 2, 3, 3, 4, 4, 6)$

#### Passo 6: Verificação Matemática (O Lema do Aperto de Mãos)
O Lema do Aperto de Mãos estabelece que a soma dos graus de todos os vértices de um grafo é sempre igual ao dobro do número de arestas:
$$\sum \text{graus} = 2 \times \vert{}E\vert{}$$

* **Soma dos graus obtidos:** $1 + 1 + 2 + 3 + 3 + 4 + 4 + 6 = 24$
* **Número total de arestas ($\vert{}E\vert{}$):** $12$
* **Conferência:** $24 = 2 \times 12$

Como a igualdade é verdadeira, a construção do grafo está matematicamente correta e consistente.