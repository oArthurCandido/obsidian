# Algoritmo de Dijkstra

![](_page_0_Picture_1.jpeg)

#### Neste capítulo

- Nós continuaremos <sup>a</sup> discutir sobre grafos <sup>e</sup> você conhecerá grafos ponderados, que é uma maneira de atribuir pesos em algumas arestas.
- Você aprenderá <sup>o</sup> algoritmo de Dijkstra, que determina caminho mínimo até X para grafos ponderados.
- Você aprenderá ciclos em grafos, que são situações nas quais <sup>o</sup> algoritmo de Dijkstra não funciona.

No capítulo anterior você aprendeu como chegar do ponto A ao ponto B.

![](_page_1_Figure_0.jpeg)

Não é necessariamente <sup>o</sup> caminho mais rápido, mas é <sup>o</sup> caminho mais curto porque tem <sup>o</sup> menor número de segmentos (três segmentos). No entanto suponha que você adicione um tempo de deslocamento aos segmentos. Agora é possível perceber que há um caminho mais rápido.

![](_page_1_Figure_2.jpeg)

Você usou <sup>a</sup> pesquisa em largura no capítulo anterior, então sabe que ela retornará <sup>o</sup> caminho com <sup>o</sup> menor número de segmentos (o primeiro grafo mostrado aqui). <sup>E</sup> se, em vez disso, quiser fazer <sup>o</sup> caminho mais rápido (o segundo grafo)? O caminho mais rápido pode ser encontrado com um algoritmo diferente, chamado algoritmo de Dijkstra.

#### Trabalhando com<sup>o</sup> algoritmo de Dijkstra

Vamos ver como ele funciona com esse grafo.

![](_page_2_Figure_0.jpeg)

Cada segmento tem um tempo de deslocamento em minutos. Você usará <sup>o</sup> algoritmo de Dijkstra para ir do início ao fim no menor tempo possível.

Caso <sup>a</sup> pesquisa em largura seja executada neste grafo, <sup>o</sup> algoritmo retornará <sup>o</sup> caminho mais curto.

![](_page_2_Figure_3.jpeg)

Porém este caminho tem duração de sete minutos. Vamos ver se é possível encontrar um caminho que leve menos tempo! O algoritmo de Dijkstra tem quatro etapas:

- 1. Encontre <sup>o</sup> vértice mais "barato". Este é <sup>o</sup> vértice em que você consegue chegar no menor tempo possível.
- 2. Atualize <sup>o</sup> custo dos vizinhos desse vértice. Explicarei <sup>o</sup> que quero dizer com isso em breve.
- 3. Repita até que você tenha feito isso para cada vértice do grafo.
- 4. Calcule <sup>o</sup> caminho final.

Passo 1: Encontre o vértice mais barato. Você está parado no ponto

inicial, pensando se deve ir ao vértice A ou ao vértice B. Quanto tempo leva para alcançar cada um?

![](_page_3_Figure_1.jpeg)

Você leva seis minutos para chegar ao vértice A <sup>e</sup> dois minutos para chegar ao vértice B. O tempo para chegar aos outros vértices você ainda desconhece.

![](_page_3_Figure_3.jpeg)

Como você ainda não sabe quanto tempo demora para chegar até <sup>o</sup> final, considere-o infinito (você verá <sup>o</sup> porquê disso logo). O vértice Bé <sup>o</sup> mais próximo, pois está <sup>a</sup> dois minutos de distância.

Passo 2: Calcule quanto tempo leva para chegar até todos os vértices vizinhos de B, seguindo as arestas de B.

![](_page_4_Picture_0.jpeg)

Ei, você acabou de encontrar um caminho mais curto para <sup>o</sup> vértice A! Antes, você levava seis minutos para chegar até ele.

![](_page_4_Figure_2.jpeg)

Porém, caso você vá pelo vértice B, existe um caminho que demora apenas cinco minutos!

![](_page_4_Figure_4.jpeg)

Quando encontrar um caminho mais curto para um vizinho de B, atualize seu custo. Neste caso você encontrou

- Um caminho mais curto até A (diminuiu de seis minutos para cinco minutos)
- Um caminho mais curto até <sup>o</sup> final (diminuiu de infinito para sete minutos)

Passo 3: Repita!

Passo <sup>1</sup> novamente: Encontre <sup>o</sup> vértice ao qual você consegue chegar em menos tempo. Você já fez isso para <sup>o</sup> vértice B, então <sup>o</sup> vértice A tem, agora, menor estimativa de tempo.

![](_page_5_Figure_1.jpeg)

Passo <sup>2</sup> novamente: Atualize os custos para os vizinhos do vértice А.

![](_page_5_Figure_3.jpeg)

Uau, agora leva apenas seis minutos para chegar até <sup>o</sup> final!

Você executou <sup>o</sup> algoritmo de Dijkstra para cada vértice (não é necessário rodar para <sup>o</sup> vértice final). Até esse ponto, você já sabe que:

- demora dois minutos para chegar ao vérticeе В.
- demora cinco minutos para chegar ao vértice A.
- demora seis minutos para chegar ao final.

| VERTICE | TEMPO |
| ------- | ----- |
| A       | S     |
| B       | 2     |
| FIM     | 6     |

Guardarei a última etapa, que é <sup>o</sup> cálculo do caminho final, para <sup>a</sup>

próxima seção. Por enquanto, vou apenas mostrar como é <sup>o</sup> caminho final.

![](_page_6_Figure_1.jpeg)

A pesquisa em largura não teria encontrado esse caminho como <sup>o</sup> caminho mais curto porque ele contém três segmentos, <sup>e</sup> há uma maneira de chegar do início ao fim em dois segmentos.

![](_page_6_Figure_3.jpeg)

No capítulo anterior você usou <sup>a</sup> pesquisa em largura para achar <sup>o</sup> caminho mínimo entre dois pontos. Lá, "caminho mínimo" significava <sup>o</sup> caminho com menor número de segmentos. Porém no algoritmo de Dijkstra você atribui um peso <sup>a</sup> cada segmento. Logo, <sup>o</sup> algoritmo encontra <sup>o</sup> caminho com o menor peso total.

![](_page_6_Figure_5.jpeg)

Para relembrar, <sup>o</sup> algoritmo de Dijkstra tem quatro passos:

- 1. Encontre <sup>o</sup> vértice mais "barato". Esse é <sup>o</sup> vértice em que você consegue chegar no menor tempo possível.
- 2. Verifique se há um caminho mais barato para os vizinhos desse vértice. Caso exista, atualize os custos deles.
- 3. Repita até que você tenha feito isso para cada vértice do grafo.
- 4. Calcule <sup>o</sup> caminho final (abordado na próxima seção!).

## Terminologia

Quero mostrar mais alguns exemplos do algoritmo de Dijkstra em ação, mas, primeiro, deixe-me esclarecer algumas terminologias.

Quando você trabalha com <sup>o</sup> algoritmo de Dijkstra, cada aresta do grafo tem um número associado <sup>a</sup> ela. Eles são chamados de pesos.

![](_page_7_Figure_8.jpeg)

Um grafo com pesos <sup>é</sup> chamado de grafo ponderado (também chamado de grafo valorado). Um grafo sem pesos é chamado de grafo não ponderado (também chamado de grafo não valorado).

![](_page_7_Figure_10.jpeg)

Para calcular o caminho mínimo em um grafo não ponderado, utilize

<sup>a</sup> pesquisa em largura. Já para calcular <sup>o</sup> caminho mínimo em um grafo ponderado utilize <sup>o</sup> algoritmo de Dijkstra. Além disso, grafos também podem conter ciclos que se parecem com isso.

![](_page_8_Figure_1.jpeg)

Ciclos indicam que é possível começar em um vértice, viajar ao redor dele <sup>e</sup> terminar no mesmo vértice. Por exemplo, suponha que esteja tentando achar <sup>o</sup> caminho mínimo deste grafo, <sup>o</sup> qual contém um ciclo.

![](_page_8_Figure_3.jpeg)

Faria sentido seguir <sup>o</sup> ciclo? Bem, é possível usar <sup>o</sup> caminho que <sup>o</sup> evita.

![](_page_8_Figure_5.jpeg)

Ou podemos seguir o ciclo.

![](_page_9_Picture_0.jpeg)

Você acabará no vértice A de qualquer forma, mas <sup>o</sup> ciclo terá mais peso. Podemos até mesmo seguir <sup>o</sup> ciclo duas vezes.

![](_page_9_Figure_2.jpeg)

Porém, cada vez que você <sup>o</sup> seguir, estará apenas adicionando <sup>8</sup> no peso total. Logo, seguir <sup>o</sup> ciclo jamais fornecerá <sup>o</sup> caminho mínimo.

Você se lembra da nossa conversa sobre grafos direcionados <sup>e</sup> grafos não direcionados do Capítulo 6?

![](_page_9_Figure_5.jpeg)

Um grafo não direcionado indica que dois vértices podem apontar um para o outro. Ou seja, um grafo não direcionado é um ciclo!

![](_page_9_Figure_7.jpeg)

Com um grafo não direcionado, cada vértice adiciona um novo ciclo. O algoritmo de Dijkstra só funciona com grafos acíclicos dirigidos (em inglês Directed Acyclic Graph, DAG).

![](_page_10_Picture_1.jpeg)

## Adquirindo um piano

Chega de terminologia, vamos analisar outro exemplo! Este é <sup>o</sup> Rama.

Rama está tentando trocar um livro de música por um piano.

"Eu troco este pôster pelo seu livro", diz Alex. "É um pôster da minha banda favorita, Destroyer. Ou então darei este LP raro do Rick Astley pelo seu livro <sup>e</sup> mais 5 reais." "Ooh, ouvi dizer que esse LP tem músicas muito boas", diz Amy. "Trocarei com você meu baixo ou minha bateria pelo pôster ou pelo LP."

![](_page_10_Picture_6.jpeg)

"Eu estava com vontade de aprender baixo!", exclamou Beethoven. "Ei, troco meu piano por qualquer uma das coisas da Amy."

Perfeito! Com um pouco de dinheiro, Rama consegue trocar seu livro de piano por um piano de verdade. Agora ele só precisa descobrir como gastar <sup>a</sup> menor quantia ao fazer essas trocas. Vamos fazer um grafo do que foi oferecido.

![](_page_11_Figure_0.jpeg)

Neste grafo, os vértices são todos os itens que Rama pode trocar. Analisando <sup>a</sup> imagem, é possível observar que ele pode trocar <sup>o</sup> pôster pelo baixo por R\$ 30, ou trocar <sup>o</sup> LP pelo baixo por R\$ 15. Como Rama descobrirá <sup>o</sup> caminho do livro até <sup>o</sup> piano por meio do qual ele gasta <sup>a</sup> menor quantia? Este é <sup>o</sup> papel do algoritmo de Dijkstra! Lembre-se de que <sup>o</sup> algoritmo de Dijkstra é separado em quatro passos. Assim, neste exemplo, você executará estes quatro passos e, ao fim, conseguirá calcular <sup>o</sup> caminho final.

Antes de começar, você precisa de algumas coisas. Primeiro, faça uma tabela com <sup>o</sup> custo de cada vértice, registrando <sup>o</sup> quanto você gasta para chegar até cada um dos vértices.

| VÉRTICE CUSTO |     |                             |
| ------------- | --- | --------------------------- |
| LP            | 5   |                             |
| PÔSTER        | ھ   |                             |
| BAIXO         | 8   |                             |
| BATERIA       |     | NÓS AINDA<br>NÃO ALCANÇAMOS |
| PIANO         |     | ESTES VÉRTICES              |

Você continuará atualizando esta tabela conforme <sup>o</sup> algoritmo for executado. Para calcular <sup>o</sup> caminho final, também será necessária uma coluna pai na tabela.

| VÉRTICE | PAI   |
| ------- | ----- |
| LP      | LIVRO |
| PÔSTER  | LIVRO |
| BAIXO   |       |
| BATERIA |       |
| PIANO   |       |

Mostrarei como essa coluna funciona em breve. Agora vamos iniciar <sup>o</sup> algoritmo.

Passo 1: Encontre <sup>o</sup> vértice mais barato. Neste caso, <sup>o</sup> pôster é <sup>a</sup> troca mais barata, pois tem custo de R\$ 0. Existe alguma troca em que Rama possa ficar com <sup>o</sup> pôster por menos de R\$ 0? Leia adiante quando souber <sup>a</sup> resposta. Resposta: Não. Porque <sup>o</sup> pôster é <sup>o</sup> vértice mais barato para <sup>o</sup> qual Rama consegue ir. Logo, não há outra maneira de torná-lo mais barato. Vamos analisar <sup>o</sup> problema de forma diferente agora. Para isso, suponha que você esteja indo de casa para o trabalho.

![](_page_12_Figure_4.jpeg)

Se pegar <sup>o</sup> caminho em direção à escola, você vai demorar dois minutos para chegar. Já <sup>o</sup> caminho em direção ao parque demora seis minutos. Existe alguma maneira de ir ao parque <sup>e</sup> acabar na escola em menos de dois minutos? Não, isto é impossível, pois demora mais de dois minutos apenas para chegar até <sup>o</sup> parque. Por outro lado, você consegue achar um caminho mais rápido até <sup>o</sup> parque? Sim.

![](_page_13_Figure_1.jpeg)

Esta é <sup>a</sup> ideia-chave por trás do algoritmo de Dijkstra: Olhe para <sup>o</sup> vértice mais barato do seu gráfico: não há uma maneira mais barata de chegar até ele!

De volta ao exemplo do piano. <sup>O</sup> pôster <sup>é</sup> <sup>a</sup> troca mais barata.

Passo 2: Descubra <sup>o</sup> custo para chegar aos vizinhos do pôster.

![](_page_13_Figure_5.jpeg)

Você tem preços para <sup>o</sup> baixo <sup>e</sup> para <sup>a</sup> bateria na tabela. Os valores deles foram registrados quando você passou pelo pôster. Logo, <sup>o</sup> pôster é definido como <sup>o</sup> pai desses itens, <sup>o</sup> que significa que para chegar ao baixo você segue a aresta do pôster, <sup>e</sup> <sup>o</sup> mesmo acontece

com <sup>a</sup> bateria.

|                 | PAI    | VÉRTICE | CUSTO |
| --------------- | ------ | ------- | ----- |
|                 | LIVRO  | LP      | 5     |
| NÓS PARTIMOS    | LIVRO  | PÔSTER  |       |
| DE "PÔSTER" EM  | PÔSTER | BAIXO   | 3     |
| DIREÇÃO A UM    | PÔSTER | BATERIA | 35    |
| DESTES VÉRTICES |        | PIANO   |       |

Passo <sup>1</sup> novamente: O LP é <sup>o</sup> próximo vértice mais barato, pois custa R\$ 5.

Passo <sup>2</sup> novamente: Atualize todos os valores dos vizinhos.

![](_page_14_Figure_4.jpeg)

Ei, você atualizou <sup>o</sup><sup>o</sup> preço tanto da bateria quanto do baixo! Isso significa que é mais barato chegar até <sup>a</sup> bateria <sup>e</sup> até <sup>o</sup> baixo seguindo <sup>a</sup> aresta do LP. Então, coloque <sup>o</sup> LP como <sup>o</sup> pai para ambos os instrumentos.

O baixo é <sup>o</sup> próximo item mais barato, então você atualiza os seus vizinhos.

![](_page_15_Figure_0.jpeg)

Ok, você finalmente tem um preço para <sup>o</sup> piano, caso <sup>o</sup> troque pelo baixo. Portanto, determine <sup>o</sup> baixo como pai. Por fim, <sup>o</sup> último vértice será <sup>a</sup> bateria.

![](_page_15_Figure_2.jpeg)

Rama pode conseguir <sup>o</sup> piano com um custo ainda menor caso troque-o pela bateria. Assim, <sup>a</sup> série de trocas mais barata custará R\$ 35.

Agora, você deve descobrir <sup>o</sup> caminho. Até <sup>o</sup> momento você já sabe quanto <sup>o</sup> caminho mínimo custa (R\$ 35), mas como você descobrirá <sup>o</sup> caminho? Primeiro, olhe para <sup>o</sup> pai do piano.

| PAI     | VÉRTICE |
| ------- | ------- |
| LIVRO   | LP      |
| LIVRO   | PÔSTER  |
| LP      | BAIXO   |
| LP      | BATERIA |
| BATERIA | PIANO   |

O pai do piano é a bateria. Isso nos diz que Rama trocou a bateria

pelo piano e, por isso, deve seguir esta aresta.

Vamos analisar como devemos seguir esta aresta. Sabemos que piano tem bateria como seu pai.

![](_page_16_Figure_2.jpeg)

E bateria tem <sup>o</sup> LP como pai.

![](_page_16_Figure_4.jpeg)

Então Rama trocará <sup>o</sup> LP pela bateria <sup>e</sup> obviamente trocará <sup>o</sup> livro pelo LP. Seguindo os pais, do final para <sup>o</sup> início, você terá <sup>o</sup> caminho completo.

![](_page_16_Figure_6.jpeg)

Aqui temos a série de trocas que Rama precisa fazer.

![](_page_17_Figure_0.jpeg)

Até este ponto, tenho usado <sup>o</sup> termo caminho mínimo ou caminho mais curto de forma literal: calculando <sup>a</sup> distância entre duas localizações ou duas pessoas. Este exemplo tem por objetivo mostrar que <sup>o</sup> caminho mínimo não precisa ser somente uma distância físicа, mas que ele também envolve como reduzir algo, que nesse caso consistia em reduzir <sup>a</sup> quantidade de dinheiro que Rama gastaria. Obrigado, Dijkstra!

#### Arestas com pesos negativos

![](_page_17_Picture_3.jpeg)

Nesse exemplo de troca, Alex ofereceu trocar <sup>o</sup> livro por dois itens.

Suponha que Sarah ofereça uma troca entre <sup>o</sup> LP <sup>e</sup> <sup>o</sup> pôster, sendo que ela dará <sup>a</sup> Rama R\$ 7 adicionais. Não há nenhum custo para Rama realizar a troca, pelo contrário, ele ainda receberá R\$ <sup>7</sup> de

volta. Como você mostraria isso no grafo?

![](_page_18_Figure_1.jpeg)

A aresta do LP ao pôster tem um peso negativo! Rama receberá R\$ 7 de volta se ele fizer essa troca, <sup>o</sup> que faz com que ele tenha duas maneiras de conseguir <sup>o</sup> pôster.

![](_page_18_Figure_3.jpeg)

Então faz sentido realizar <sup>a</sup> segunda troca, pois Rama receberá R\$ 2 de volta dessa maneira! Agora, se você se lembra, Rama pode trocar <sup>o</sup> pôster pela bateria. Logo, há dois caminhos que ele pode escolher.

![](_page_19_Figure_0.jpeg)

O segundo caminho custa R\$ 2 <sup>a</sup> menos, portanto ele poderá escolher esse caminho, certo? Bem, adivinhe só, se você executar <sup>o</sup> algoritmo de Dijkstra nesse grafo, Rama escolherá <sup>o</sup> caminho errado, pois ele pegará <sup>o</sup> caminho mais longo. Você não pode usar <sup>o</sup> algoritmo de Dijkstra se você tiver arestas com pesos negativos. Ou seja, os números negativos estragam <sup>o</sup> algoritmo; para provar isso, vamos ver <sup>o</sup> que acontece quando executamos <sup>o</sup> algoritmo de Dijkstra nesta situação. Primeiro, crie <sup>a</sup> tabela de preços.

![](_page_19_Figure_2.jpeg)

Em seguida, encontre <sup>o</sup> vértice com <sup>o</sup> menor preço <sup>e</sup> atualize <sup>o</sup> preço dos seus vizinhos. Nesse caso <sup>o</sup> pôster é <sup>o</sup> vértice com <sup>o</sup> menor preço. Então, de acordo com <sup>o</sup> algoritmo de Dijkstra, não há uma maneira mais barata de conseguir <sup>o</sup> pôster do que pagando R\$ 0 (mas você sabe que isso está errado). De qualquer forma, vamos atualizar <sup>o</sup> preço dos vizinhos.

![](_page_20_Figure_0.jpeg)

A bateria custa R\$ 35 agora.

Vamos pegar <sup>o</sup> próximo vértice mais barato que ainda não foi processado.

![](_page_20_Figure_3.jpeg)

Atualize os preços para os seus vizinhos.

![](_page_20_Figure_5.jpeg)

Você já processou <sup>o</sup> vértice do pôster, mas ainda não atualizou <sup>o</sup> preço dele. Isso é um grande sinal de alerta, pois, uma vez que um vértice <sup>é</sup> processado, isso significa que não há uma maneira mais barata de chegar até ele. Porém você acabou de achar um caminho mais barato para <sup>o</sup> pôster! A bateria não tem nenhum vizinho, então esse é o final do algoritmo. Aqui estão os custos finais.

| LP            | 5   |
| ------------- | --- |
| PÔSTER        | -2  |
| BATERIA       | 35  |
| CUSTOS FINAIS |     |

Assim, <sup>o</sup> custo para conseguir <sup>a</sup> bateria é de R\$ 35. Porém você sabe que existe um caminho que custa apenas R\$ 33, mas <sup>o</sup> algoritmo de Dijkstra não <sup>o</sup> encontrou. O algoritmo supôs que, por você estar processando <sup>o</sup> vértice do pôster, não havia um caminho mais rápido para chegar até esse vértice. Essa suposição só funciona caso não haja arestas com pesos negativos. Portanto você não pode usar arestas com pesos negativos com <sup>o</sup> algoritmo de Dijkstra. Se quiser encontrar <sup>o</sup> caminho mínimo em um grafo contendo arestas com pesos negativos, existe um algoritmo específico para isso! Ele <sup>é</sup> chamado de algoritmo de Bellman-Ford. Este algoritmo está fora do âmbito desse livro, mas você pode encontrar ótimas explicações sobre ele na internet.

### Implementação

Vamos aprender como implementar <sup>o</sup> algoritmo de Dijkstra em forma de código. Aqui temos <sup>o</sup> grafo que utilizarei neste exemplo.

![](_page_21_Figure_4.jpeg)

Para programar esse exemplo você precisará de três tabelas hash.

![](_page_22_Figure_0.jpeg)

As tabelas hash relativas ao custo <sup>e</sup> aos pais serão atualizadas conforme <sup>o</sup> algoritmo for executado. Porém, antes disso, é necessário implementar <sup>o</sup> grafo, <sup>e</sup> para isso será criada uma tabela hash da forma como vimos no Capítulo 6:

grafo <sup>=</sup> {}

No capítulo anterior, você armazenou todos os vizinhos do vértice em uma tabela de dispersão desta forma:

```python
grafo["voce"] = ["alice", "bob", "claire"]
```

Porém agora é necessário armazenar os vizinhos <sup>e</sup> <sup>o</sup> custo para chegar até aquele vizinho. Por exemplo, Início tem dois vizinhos: A <sup>e</sup> B.

![](_page_22_Figure_6.jpeg)

Como representar os pesos dessas arestas? Por que não utilizar apenas outra tabela hash?

grafo["inicio"] = {}

```python
grafo["inicio"][" = 6
grafo["inicio"]["b"] = 2
```

![](_page_23_Picture_1.jpeg)

Portanto, grafo["inicio"] é uma tabela hash. Você conseguirá todos os vizinhos do Início da seguinte forma:

```python
>>> print grafo["inicio"].keys()
["a", "b"]
```

Há uma aresta do Início para A <sup>e</sup> uma aresta do Início para B. E como você encontra <sup>o</sup> peso dessas arestas?

```python
>>> print grafo["inicio"]["a"]
6
>>> print grafo["inicio"]["b"]
2
```

Vamos adicionar <sup>o</sup> restante dos vértices <sup>e</sup> seus vizinhos ao grafo:

```python
grafo["a"] = {}
grafo["a"]["fim"] = 1
grafo["b"] = {}
grafo["b"]["a"] = 3
grafo["b"]["fim"] = 5
grafo["fim"] = {}
```

O vértice final não tem vizinhos.

O grafo constituído pela tabela hash é algo assim:

![](_page_24_Figure_0.jpeg)

Em seguida você precisa de uma tabela hash para armazenar os custos de cada vértice.

![](_page_24_Figure_2.jpeg)

O custo de um vértice é <sup>a</sup> quantia necessária para chegar, <sup>a</sup> partir do Início, no vértice em questão. Você sabe que são necessários dois minutos para partir do Início <sup>e</sup> chegar ao vértice B. Além disso, sabe também que são necessários seis minutos para chegar ao vértice A (embora possa existir um caminho que leve menos tempo). Entretanto você não sabe <sup>o</sup> tempo necessário para chegar até <sup>o</sup> final. Sendo assim, este tempo é considerado infinito. Mas será que é possível representar infinito em Python? Sim, é possível:

infinito <sup>=</sup> float("inf")

Aqui está <sup>o</sup> código para criar <sup>a</sup> tabela de custos:

infinito = float("inf")

```python
custos = {}
custos ["a"] = 6
custos ["b"] = 2
custos ["fim"] = infinito
```

Você também precisará de outra tabela hash para os pais:

![](_page_25_Figure_2.jpeg)

Este é <sup>o</sup> código para criação da tabela hash para os pais:

```python
pais = {}
pais["a"] = "inicio"
pais["b"] = "inicio"
pais["fim"] = None
```

Por fim é necessário um array para manter registro de todos os vértices processados, pois eles não precisam ser processados mais de uma vez:

processados <sup>=</sup> []

Esta é toda <sup>a</sup> configuração necessária. Agora vamos olhar <sup>o</sup> algoritmo.

![](_page_26_Figure_0.jpeg)

Primeiro, mostrarei <sup>o</sup> código e, depois, <sup>o</sup> comentarei. Você pode conferir <sup>o</sup> código abaixo:

```python
nodo = ache_no_custo_mais_baixo(custos)
while nodo is not None: 2
   custo = custos[nodo]
   vizinhos = grafo[nodo]
   for n in vizinhos.keys():
       novo_custo = custo + vizinhos[n]
       if custos[n] > novo_custo: 4
           custos[n] = novo_custo
           pais[n] = nodo
   processados.append(nodo) 7
                                       1
    nodo = ache_no_custo_mais_baixo(custos)
```

- Encontra <sup>o</sup> custo mais baixo que ainda não foi processado.
- Caso todos os vértices tenham sido processados, esse laço whi le será finalizado.

Percorre todos os vizinhos desse vértice.

Caso seja mais barato chegar <sup>a</sup> um vizinho <sup>a</sup> partir desse vértice...

... atualiza <sup>o</sup> custo dele.

Esse vértice se torna <sup>o</sup> novo pai para <sup>o</sup> vizinho.

Marca <sup>o</sup> vértice como processado.

Encontra <sup>o</sup> próximo vértice <sup>a</sup> ser processado <sup>e</sup> <sup>o</sup> algoritmo é repetido.

Esse é <sup>o</sup> algoritmo de Dijkstra em Python! Mostrarei <sup>o</sup> código para <sup>a</sup> função posteriormente. Agora, vamos ver <sup>o</sup> código do algoritmo ache_no_custo_mais_baixo em ação.

Encontre <sup>o</sup> vértice com <sup>o</sup> menor custo.

![](_page_27_Figure_7.jpeg)

Pegue <sup>o</sup> custo <sup>e</sup> os vizinhos desse vértice.

![](_page_27_Figure_9.jpeg)

Percorra todos os vizinhos.

![](_page_28_Figure_0.jpeg)

Cada vértice tem um custo, sendo <sup>o</sup> custo <sup>o</sup> tempo necessário para chegar até esse vértice partindo do início. Aqui, você está calculando <sup>o</sup> tempo necessário para chegar até <sup>o</sup> ponto <sup>A</sup> se você partir do Início <sup>e</sup> seguir <sup>o</sup> caminho Início <sup>&</sup>gt; vértice B <sup>&</sup>gt; vértice A, em vez de Início > vértice А.

$$
hovo_custo = custo + vizinhos [h]
$$

\n

$$
f \quad \downarrow
$$

\n

$$
custo = 2+3
$$

\n

$$
custo = 2+3
$$

\n

$$
custo = 2+3
$$

\n

$$
custo = 2+3
$$

Comparando os custos.

![](_page_28_Figure_4.jpeg)

Você achou um caminho menor para <sup>o</sup> vértice A! Agora, atualize <sup>o</sup> custo.

![](_page_29_Figure_0.jpeg)

O caminho novo vai pelo vértice B, então considere B como <sup>o</sup> novo pai.

![](_page_29_Figure_2.jpeg)

Você está de volta ao topo do loop. <sup>O</sup> próximo vizinho do for é <sup>o</sup> vértice final.

![](_page_29_Figure_4.jpeg)

Qual <sup>o</sup> tempo necessário para chegar ao final, caso você vá pelo vértice B?

$$
1000 \text{ } \text{ } \text{ } \text{ } \text{ } \text{ } \text{ } \text{ } \text{ } \text{ }
$$

O tempo necessário é sete minutos, sendo que <sup>o</sup> custo anterior era de infinitos minutos <sup>e</sup> sete minutos é menor do que infinito.

![](_page_30_Figure_2.jpeg)

Agora, considere <sup>o</sup> novo custo <sup>e</sup> <sup>o</sup> novo pai para <sup>o</sup> vértice final.

![](_page_30_Figure_4.jpeg)

Você atualizou todos os custos para todos os vizinhos do vértice B; marque-o como processado e continue.

$$
\text{processados.} \text{append}(\text{hodo}) \text{ \text{vérntces} } \\ \text{ \textit{ce}} \\ \text{ \textit{e}} \\ \textit{f'} \text{ \textit{Process} } \\ \textit{f} \text{ \textit{f}} \\ \textit{f} \text{ \textit{f}} \\ \textit{f} \text{ \textit{f}} \\ \textit{f} \text{ \textit{f}} \\ \textit{f} \text{ \textit{f}} \\ \textit{f} \text{ \textit{f}} \\ \textit{f} \text{ \textit{f}} \\ \textit{f} \text{ \textit{f}} \\ \textit{f} \text{ \textit{f}} \\ \textit{f} \text{ \textit{f}} \\ \textit{f} \text{ \textit{f}} \\ \textit{f} \text{ \textit{f}} \\ \textit{f} \text{ \textit{f}} \\ \textit{f} \text{ \textit{f}} \\ \textit{f} \text{ \textit{f}} \\ \textit{f} \text{ \textit{f}} \\ \textit{f} \text{ \textit{f}} \\ \textit{f} \text{ \textit{f}} \\ \textit{f} \text{ \textit{f}} \\ \textit{f} \text{ \textit{f}} \\ \textit{f} \text{ \textit{f}} \\ \textit{f} \text{ \textit{f}} \\ \textit{f} \text{ \textit{f}} \\ \textit{f} \text{ \textit{f}} \\ \textit{f} \text{ \textit{f}} \\ \textit{f} \text{ \textit{f}} \\ \textit{f} \text{ \textit{f}} \\ \textit{f} \text{ \textit{f}} \\ \textit{f} \text{ \textit{f}} \\ \textit{f} \text{ \textit{f}} \\ \textit{f} \text{ \textit{f}} \\ \textit{f} \text{ \textit{f}} \\ \textit{f} \text{ \textit{f}} \\ \textit{f} \text{ \textit{f}} \\ \textit{f} \text{ \textit{f}} \\ \textit{f} \text{ \textit{f}} \\ \textit{f} \text{ \textit{f}} \\ \textit{f} \text{ \textit{f}} \\ \textit{f} \text{ \textit{f}} \\ \textit{f} \text{ \textit{f}} \\ \textit{f} \text{ \textit{f}} \\ \textit{f} \text{ \textit{f}} \\ \textit{f} \text{ \textit{f}} \\ \text
$$

Encontre <sup>o</sup> próximo vértice <sup>a</sup> ser processado.

![](_page_31_Figure_2.jpeg)

Pegue os custos <sup>e</sup> os vizinhos do vértice A.

custo = custos [nodo]  
\n5  
\nvizinhos = grab [nodo]  
\n  
\n

$$
\uparrow
$$

\nFIM1

O vértice A só tem um vizinho: <sup>o</sup> vértice final.

![](_page_31_Figure_6.jpeg)

Atualmente <sup>o</sup> menor tempo necessário para alcançar <sup>o</sup> vértice final é sete minutos. Quanto tempo levaria para chegar lá se você fosse pelo vértice А?

![](_page_32_Figure_0.jpeg)

É mais rápido chegar ao vértice final pelo vértice A! Vamos atualizar custo <sup>e</sup> <sup>o</sup> pai. <sup>이</sup>

![](_page_33_Figure_0.jpeg)

Uma vez que você processou todos os vértices, <sup>o</sup> algoritmo é finalizado. Espero que <sup>o</sup> passo <sup>a</sup> passo tenha lhe ajudado <sup>a</sup> entender <sup>o</sup> algoritmo um pouco melhor. Encontrar <sup>o</sup> vértice de custo mínimo é uma tarefa simples utilizando <sup>a</sup> função ache_no_custo_mais_baixo. O código desta função pode ser visto <sup>a</sup> seguir.

```python
def ache_no_custo_mais_baixo(custos):
2
    custo_mais_baixo = float("inf")
    nodo_custo_mais_baixo = None
    for nodo in custos:
        custo = custos[nodo]
        if custo<custo_mais_baixo and nodo not in processados:
            custo_mais_baixo = custo
            nodo_custo_mais_baixo = nodo
    return nodo_custo_mais_baixo
Vá por cada vértice.
```

Se for <sup>o</sup> vértice de menor custo até <sup>o</sup> momento <sup>e</sup> ainda não tiver sido processado...

... atribua como <sup>o</sup> novo vértice de menor custo.

#### EXERCÍCIO

7.1 Em cada um desses grafos, qual <sup>o</sup> peso do caminho mínimo do início ao fim?

![](_page_34_Figure_3.jpeg)

### Recapitulando

- A pesquisa em largura é usada para calcular <sup>o</sup> caminho mínimo para um grafo não ponderado.
- O algoritmo de Dijkstra é usado para calcular <sup>o</sup> caminho mínimo para um grafo ponderado.
- O algoritmo de Dijkstra funciona quando todos os pesos são positivos.
- Se <sup>o</sup> seu grafo tiver pesos negativos, use o algoritmo de Bellman-Ford.
