# Algoritmo de Dijkstra

##  Introdução

O algoritmo de Dijkstra é um algoritmo de grafos utilizado para encontrar o menor caminho entre um vértice de origem e os demais vértices de um grafo ponderado.

Ele é um dos algoritmos mais importantes da computação e é amplamente utilizado em sistemas de navegação, GPS, redes de computadores e diversas aplicações que envolvem cálculo de rotas.

O algoritmo foi desenvolvido pelo cientista da computação :contentReference[oaicite:0]{index=0} em 1956.

---

# O que é um grafo?

Um grafo é uma estrutura composta por:

- **Vértices (nós)** → representam pontos
- **Arestas** → representam conexões entre os pontos

Exemplo:

```txt
A ---- B
 \    /
   C
```

Nesse exemplo:
- `A`, `B` e `C` são vértices
- As linhas representam as conexões entre eles

Quando essas conexões possuem valores numéricos, chamamos de:

# 📊 Grafo ponderado

Exemplo:

```txt
A ----4---- B
 \         /
  2       1
   \     /
      C
```

Os números representam o custo, distância ou peso do caminho.

---

# Objetivo do algoritmo

O objetivo do algoritmo de Dijkstra é:

✅ Encontrar o menor caminho entre um vértice inicial e todos os outros vértices do grafo.

---

# Limitação importante

O algoritmo de Dijkstra:

✅ Funciona com pesos positivos

❌ Não funciona corretamente com pesos negativos

Para grafos com pesos negativos, utiliza-se o algoritmo de Bellman-Ford.

---

# Como o algoritmo funciona

O Dijkstra funciona explorando sempre o caminho de menor custo conhecido até o momento.

A lógica principal é:

1. Começar pelo vértice inicial
2. Calcular os menores custos para os vizinhos
3. Escolher o próximo vértice com menor distância
4. Repetir o processo até visitar todos os vértices

---

# Relaxamento de arestas

Assim como Bellman-Ford, o Dijkstra utiliza o conceito de relaxamento.

Relaxar uma aresta significa:

> Verificar se existe um caminho menor passando por determinado vértice.

---

## Exemplo simples

Imagine:

```txt
Distância até B = 10
```

Existe uma aresta:

```txt
A → B = 3
```

E sabemos que:

```txt
Distância até A = 5
```

Então:

```txt
5 + 3 = 8
```

Como `8` é menor que `10`, atualizamos:

```txt
Distância até B = 8
```

---

# Passo a passo do algoritmo

## Inicialização

O algoritmo começa definindo:

- Distância do vértice inicial = `0`
- Distância dos demais vértices = infinito

Exemplo:

| Vértice | Distância |
|---|---|
| A | 0 |
| B | ∞ |
| C | ∞ |
| D | ∞ |

---

## Escolher o vértice mais próximo

O algoritmo seleciona o vértice não visitado com menor distância conhecida.

Exemplo:

```txt
A = 0
```

Então o primeiro vértice escolhido será `A`.

---

## Atualizar os vizinhos

O algoritmo verifica os vizinhos do vértice atual e calcula novas distâncias.

Exemplo:

```txt
A → B = 4
A → C = 2
```

Atualização:

| Vértice | Distância |
|---|---|
| A | 0 |
| B | 4 |
| C | 2 |

---

## Repetir o processo

O algoritmo continua:

- Escolhendo o vértice mais próximo
- Atualizando os vizinhos
- Marcando vértices visitados

Até que todos os vértices sejam processados.

---

# Complexidade do algoritmo

## Complexidade de Tempo

A complexidade depende da implementação.

### Implementação simples

```txt
O(V²)
```

### Utilizando fila de prioridade

```txt
O((V + E) log V)
```

Onde:

- `V` = quantidade de vértices
- `E` = quantidade de arestas

---

# Comparação com Bellman-Ford

| Algoritmo | Pesos Negativos | Detecta Ciclos Negativos | Velocidade |
|---|---|---|---|
| Dijkstra | ❌ | ❌ | Mais rápido |
| Bellman-Ford | ✅ | ✅ | Mais lento |

---

# Exemplo completo

## Grafo

```txt
A → B = 4
A → C = 2
C → B = 1
B → D = 5
C → D = 8
```

---

## Menor caminho partindo de A

```txt
A → C → B → D
```

---

## Cálculo

```txt
A → C = 2
C → B = 1
B → D = 5

Total = 8
```

---

# Exemplo básico em Python

```python
import heapq

grafo = {
    'A': [('B', 4), ('C', 2)],
    'B': [('D', 5)],
    'C': [('B', 1), ('D', 8)],
    'D': []
}

distancias = {vertice: float('inf') for vertice in grafo}
distancias['A'] = 0

fila = [(0, 'A')]

while fila:
    distancia_atual, vertice_atual = heapq.heappop(fila)

    for vizinho, peso in grafo[vertice_atual]:
        distancia = distancia_atual + peso

        if distancia < distancias[vizinho]:
            distancias[vizinho] = distancia
            heapq.heappush(fila, (distancia, vizinho))

print(distancias)
```

---

# Como executar o projeto

##  Clonar o repositório

```bash
git clone URL_DO_REPOSITORIO
```

---

## Entrar na pasta do projeto

```bash
cd nome-do-projeto
```

---

## Executar o arquivo Python

```bash
python algoritmoDijkstra.py
```

---

# Aplicações reais

O algoritmo de Dijkstra é utilizado em:

- 🛰️ GPS e aplicativos de navegação
- 🌐 Redes de computadores
- 🚚 Sistemas de logística
- 🗺️ Aplicativos de mapas
- 📡 Roteamento de redes
- 🎮 Inteligência artificial em jogos

---

# Conceitos utilizados

Durante a implementação deste algoritmo são utilizados conceitos importantes como:

- Grafos
- Estruturas de dados
- Caminho mínimo
- Fila de prioridade
- Heap
- Relaxamento de arestas
- Complexidade de algoritmos
- Laços de repetição

---

# Tecnologias utilizadas

- Python
- Algoritmos e Estruturas de Dados

---

# Objetivo acadêmico

Este projeto foi desenvolvido com fins acadêmicos para estudo de algoritmos de grafos, análise de caminhos mínimos e compreensão do funcionamento do algoritmo de Dijkstra.

---

# Autor

Desenvolvido por Daniel Pacheco.
