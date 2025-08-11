# Pesquisa em largura

![](_page_0_Picture_1.jpeg)

### Neste capítulo

- Você aprenderá como modelar uma rede usando uma estrutura de dados nova <sup>e</sup> abstrata: grafos.
- Você conhecerá <sup>a</sup> pesquisa em largura, um algoritmo que pode ser executado utilizando grafos para responder <sup>a</sup> perguntas como "Qual <sup>o</sup> menor caminho até X?".
- Você aprenderá <sup>a</sup> diferença entre grafos direcionados <sup>e</sup> não direcionados.
- Você conhecerá <sup>a</sup> ordenação topológica, um algoritmo de ordenação diferente que expõe dependências entre vértices.

Este capítulo introduzirá <sup>o</sup> conceito de grafos. Primeiro, falarei sobre <sup>o</sup> que são grafos (eles não envolvem um eixo X ou Y). Então, apresentarei seu primeiro algoritmo usando grafos, chamado pesquisa em largura (do inglês breadth-first search, BFS).

<sup>A</sup> pesquisa em largura permite encontrar <sup>o</sup> menor caminho entre dois objetos. Porém <sup>o</sup> menor caminho pode significar tantas coisas! Para exemplificar, é possível usar pesquisa em largura para:

- Escrever um algoritmo de inteligência artificial que calcula <sup>o</sup> menor número de movimentos necessários para <sup>a</sup> vitória em uma partida de damas.
- Criar um corretor ortográfico (o qual calcula <sup>o</sup> menor número de edições para transformar <sup>a</sup> palavra digitada incorretamente em uma palavra real; por exemplo, para modificar LEITOT -> LEITOR é necessária apenas uma edição).
- 이 Encontrar <sup>o</sup> médico conveniado ao seu plano de saúde que está mais próximo de você.

O algoritmo de grafos <sup>é</sup> um dos algoritmos mais úteis que conheço. Por isso leia os próximos capítulos com cuidado, pois esses algoritmos são aplicáveis <sup>a</sup> diversas situacões.

![](_page_1_Picture_6.jpeg)

### Introdução <sup>a</sup> grafos

Suponha que você esteja em San Francisco <sup>e</sup> queira ir das Twin Peaks (duas montanhas localizadas no centro da cidade) até <sup>a</sup> ponte Golden Gate. Você pretende chegar lá de ônibus, porém quer fazer

transferência de um ônibus para outro <sup>o</sup> menor número de vezes possível. Suas opções são:

![](_page_2_Figure_1.jpeg)

Qual algoritmo você propõe para encontrar <sup>o</sup> caminho com <sup>o</sup> menor número de etapas?

Bem, você consegue chegar ao seu destino com uma etapa? Aqui estão todos os lugares para os quais é possível chegar com uma etapa:

![](_page_2_Figure_4.jpeg)

A ponte não está destacada, logo não é possível chegar lá com uma etapa. E com duas etapas?

![](_page_3_Figure_0.jpeg)

Mais uma vez, <sup>a</sup> ponte não está destacada, logo você não pode chegar lá com duas etapas. E com três etapas?

![](_page_3_Figure_2.jpeg)

Ahá! Agora <sup>a</sup> ponte Golden Gate está destacada. Então, são necessárias três etapas para ir da Twin Peaks até <sup>a</sup> ponte por meio dessa rota.

![](_page_3_Figure_4.jpeg)

Existem outras rotas que levam você até a ponte, mas elas são mais

longas (quatro etapas). O algoritmo descobriu que <sup>o</sup> caminho mais curto até <sup>a</sup> ponte demanda três etapas. Esse tipo de problema é chamado de problema do caminho mínimo. Neste problema, você sempre tentará achar <sup>o</sup> caminho mínimo para algo, como por exemplo <sup>a</sup> rota mais curta até <sup>a</sup> casa de seu amigo, ou também <sup>o</sup> número mínimo de movimentos para dar xeque-mate em um jogo de xadrez. O algoritmo que resolve problemas de caminho mínimo é <sup>a</sup> pesquisa em largura.

Para descobrir como ir da Twin Peaks até <sup>a</sup> ponte Golden Bridge existem duas etapas:

1. Modele <sup>o</sup> problema utilizando grafos.

2. Resolva <sup>o</sup> problema utilizando <sup>a</sup> pesquisa em largura.

Em seguida, falarei sobre <sup>o</sup> que são grafos. Depois, abordarei <sup>a</sup> pesquisa em largura em mais detalhes.

## O que é um grafo?

![](_page_4_Picture_6.jpeg)

Um modelo de grafo <sup>é</sup> um conjunto de conexões. Por exemplo, suponha que você <sup>e</sup> seus amigos estejam jogando pôquer <sup>e</sup> que você queira descrever quem deve dinheiro <sup>a</sup> quem. Você poderia dizer "Alex deve dinheiro à Rama".

![](_page_5_Figure_0.jpeg)

O grafo completo poderia ser algo do tipo:

![](_page_5_Figure_2.jpeg)

Grafo de pessoas que devem dinheiro <sup>a</sup> outras pessoas em uma partida de pôquer.

Alex deve dinheiro <sup>à</sup> Rama, Tom deve dinheiro à Adit, <sup>e</sup> assim por diante. Cada grafo é constituído de vértices <sup>e</sup> arestas.

![](_page_5_Figure_5.jpeg)

E isso é tudo! Grafos são formados por vértices <sup>e</sup> arestas, <sup>e</sup> um vértice pode ser diretamente conectado <sup>a</sup> muitos outros vértices, por isso os chamamos de vizinhos. Neste grafo, Rama é vizinha de Alex. Já Adit não é vizinho de Alex, pois eles não estão diretamente conectados, mas Adit é vizinho de Rama <sup>e</sup> de Tom.

Os grafos são uma maneira de modelar como eventos diferentes estão conectados entre si. Agora vamos ver <sup>a</sup> pesquisa em largura na prática.

# Pesquisa em largura

Nós conhecemos um algoritmo de pesquisa no Capítulo 1: <sup>a</sup> pesquisa binária. <sup>A</sup> pesquisa em largura é um tipo diferente de algoritmo, pois utiliza grafos. Este algoritmo ajuda <sup>a</sup> responder <sup>a</sup> dois tipos de pergunta:

- 1: Existe algum caminho do vértice A até <sup>o</sup> vértice B?
- 2: Qual <sup>o</sup> caminho mínimo do vértice A até <sup>o</sup> vértice B?

Você já viu <sup>a</sup> pesquisa em largura em ação uma vez quando calculou <sup>a</sup> rota mais curta do Twin Peaks até <sup>a</sup> ponte Golden Gate. Essa pergunta foi do tipo 2: "Qual é <sup>o</sup> caminho mínimo?". Agora vamos analisar <sup>o</sup> algoritmo em mais detalhes, <sup>e</sup> você fará uma pergunta do tipo 1: "Existe um caminho?".

![](_page_6_Picture_5.jpeg)

Vamos supor que você seja <sup>o</sup> dono de uma fazenda de mangas <sup>e</sup> esteja procurando um vendedor de mangas que possa vender <sup>a</sup> sua colheita. Você conhece algum vendedor de mangas no Facebook? Bem, você pode procurar entre seus amigos.

![](_page_7_Figure_0.jpeg)

Essa pesquisa é bem direta. Primeiro, faça uma lista de amigos para pesquisar.

![](_page_7_Figure_2.jpeg)

Agora vá até cada pessoa da lista <sup>e</sup> verifique se esta pessoa vende mangas.

![](_page_8_Figure_0.jpeg)

Imagine que nenhum de seus amigos é um vendedor de mangas. Então, será necessário pesquisar entre os amigos dos seus amigos.

![](_page_9_Figure_0.jpeg)

Cada vez que você pesquisar uma pessoa da lista, todos os amigos dela serão adicionados à lista.

![](_page_9_Figure_2.jpeg)

Dessa maneira você não pesquisa apenas entre os seus amigos, mas também entre os amigos deles. Lembre-se de que <sup>o</sup> objetivo é encontrar um vendedor de mangas em sua rede. Então, se Alice não é uma vendedora de mangas, você adicionará também os amigos dela à lista. Isso significa que, eventualmente, pesquisará entre os amigos dela <sup>e</sup> entre os amigos dos amigos, <sup>e</sup> assim por diante. Com esse algoritmo você pesquisará toda <sup>a</sup> sua rede até que encontre um vendedor de mangas. Isto é o algoritmo da pesquisa em largura em

ação.

### Encontrando <sup>o</sup> caminho mínimo

Relembrando, existem dois tipos de pergunta que <sup>a</sup> pesquisa em largura responde:

- 1: Existe um caminho do vértice A até <sup>o</sup> vértice B? (Existe um vendedor de manga na minha rede?)
- 2: Qual <sup>o</sup> caminho mínimo do vértice A até <sup>o</sup> vértice B? (Quem é <sup>o</sup> vendedor de manga mais próximo?)

Você já sabe <sup>a</sup> resposta para <sup>a</sup> pergunta 1. Agora, vamos tentar responder <sup>a</sup> pergunta 2. Você consegue encontrar <sup>o</sup> vendedor de mangas mais próximo? Por exemplo, seus amigos são conexões de primeiro grau e os amigos deles são conexões de segundo grau.

![](_page_10_Figure_6.jpeg)

10 BOB CLAIRE GRAU ALICE ANUJ 2° GRAU PEGGY THOM JONNY

Você preferiria uma conexão de primeiro grau em vez de uma conexão de segundo grau, <sup>e</sup> uma conexão de segundo grau <sup>a</sup> uma de terceiro grau, <sup>e</sup> assim por diante. Portanto não se deve pesquisar nenhuma conexão de segundo grau antes de você ter certeza de que não existe uma conexão de primeiro grau com um vendedor de mangas. Bem, <sup>a</sup> pesquisa em largura já faz isso! <sup>O</sup> funcionamento da pesquisa em largura faz com que <sup>a</sup> pesquisa irradie <sup>a</sup> partir do ponto inicial. Dessa forma, você verificará as conexões de primeiro grau antes das conexões de segundo grau. Pergunta rápida: Quem será verificado primeiro, Claire ou Anuj? Resposta: Claire é uma conexão de primeiro grau <sup>e</sup> Anuj é uma conexão de segundo grau, logo Claire será verificada antes de Anuj.

Outra maneira de ver isso é sabendo que conexões de primeiro grau são adicionadas à pesquisa antes de conexões de segundo grau.

Você apenas segue <sup>a</sup> lista <sup>e</sup> verifica se <sup>a</sup> pessoa é uma vendedora de mangas. As conexões de primeiro grau serão procuradas antes das de segundo grau, e, dessa forma, você encontrará <sup>o</sup> vendedor de mangas mais próximo. Assim, <sup>a</sup> pesquisa em largura não encontra apenas um caminho entre A <sup>e</sup> B, ela encontra <sup>o</sup> caminho mais curto.

Repare que isso só funciona se você procurar as pessoas na mesma ordem em que elas foram adicionadas. Ou seja, se Claire foi adicionada <sup>à</sup> lista antes de Anuj, deve-se pesquisar Claire antes de Anuj. O que acontece se você pesquisar Anuj antes de Claire, sendo que ambos são vendedores de mangas? Bem, Anuj <sup>é</sup> um contato de

segundo grau enquanto Claire é um contato de primeiro grau, <sup>o</sup> que fará com que <sup>o</sup> vendedor de mangas encontrado não seja <sup>o</sup> mais próximo. Portanto é necessário pesquisar as pessoas na ordem em que elas foram adicionadas; para isso existe uma estrutura de dados específica: <sup>a</sup> fila.

#### Filas

![](_page_12_Picture_2.jpeg)

Uma fila em estrutura de dados funciona exatamente como uma fila da vida real. Suponha que você <sup>e</sup> um amigo estejam em uma fila em uma parada de ônibus. Se você está antes dele na fila, entrará primeiro no ônibus. As filas funcionam da mesma maneira, tendo funcionamento similar ao das pilhas. Por isso não é possível acessar elementos aleatórios em uma fila. Em vez disso, apenas duas operações são possíveis: enqueue (enfileirar) <sup>e</sup> dequeue (desenfileirar).

![](_page_12_Picture_4.jpeg)

Se você enfileirar dois itens na lista, <sup>o</sup> primeiro item adicionado será desenfileirado antes do segundo item. Isso pode ser utilizado em sua

lista de pesquisas! Dessa forma, pessoas que foram adicionadas primeiro na lista serão desenfileiradas <sup>e</sup> verificadas primeiro.

A fila é uma estrutura de dados FIFO (acrônimo para First In, First Out, que em português significa Primeiro <sup>a</sup> Entrar, Primeiro <sup>a</sup> Sair). Já <sup>a</sup> pilha é uma estrutura de dados LIFO (Last In, First Out, que em português significa Último <sup>a</sup> Entrar, Primeiro <sup>a</sup> Sair).

![](_page_13_Figure_2.jpeg)

Agora que você sabe como uma fila funciona, vamos implementar <sup>a</sup> pesquisa em largura!

#### EXERCÍCIOS

Execute <sup>o</sup> algoritmo de pesquisa em largura em cada um desses grafos para encontrar <sup>a</sup> solução.

6.1 Encontre <sup>o</sup> menor caminho do início ao fim.

![](_page_13_Figure_7.jpeg)

6.2 Encontre o menor caminho de "jato" até "gato".

![](_page_14_Figure_0.jpeg)

### Implementando <sup>o</sup> grafo

Primeiro, você deve implementar <sup>o</sup> grafo em código. Um grafo consiste de diversos vértices.

Cada vértice é conectado aos vértices vizinhos. Como expressar uma relação do tipo"você -> bob"? Felizmente, você conhece uma estrutura de dados que lhe permite expressar relações: uma tabela hash!

![](_page_15_Figure_0.jpeg)

Lembre-se de que uma tabela hash lhe permite mapear uma chave <sup>a</sup> um valor. Nesse caso você deseja mapear um vértice <sup>a</sup> todos os seus vizinhos.

![](_page_15_Figure_2.jpeg)

Em Python, isso ficaria assim:

```python
grafo = }}
grafo["voce"] = ["alice", "bob", "claire"]
```

Note que "você" é mapeado para um vetor. Logo grafo[ "voce"] lhe dará um vetor de todos os vizinhos de "voce".

Um grafo é apenas um monte de vértices <sup>e</sup> arestas, portanto isso é tudo que você precisa para ter um grafo em Python. <sup>E</sup> se tivermos um grafo maior?

![](_page_16_Figure_0.jpeg)

Em Python, ficaria assim:

```python
grafo = {}
grafo["voce"] = ["alice", "bob", "claire"]
grafo["bob"] = ["anuj", "peggy"]
grafo["alice"] = ["peggy"]
grafo["claire"] = ["thom", "jonny"]
grafo["anuj"] = []
grafo["peggy"] = []
grafo["thom"] = []
grafo["jonny"] = [][
```

Pergunta rápida: A ordem que adiciona os pares chave/valor faz diferença?

Existe diferença ao escrever

```python
grafo["claire"] = ["thom", "jonny"]
  grafo["anuj"] = []
em vez de
  grafo["anuj"] = []
 grafo["claire"] = ["thom", "jonny"]
```

Lembre-se dos capítulos anteriores! Resposta: Não faz diferença, pois as tabelas hash não são ordenadas. Portanto não importa em que

ordem você adiciona os pares chave/valor.

Anuj, Peggy, Thom <sup>e</sup> Jonny não têm vizinhos. Eles têm setas apontadas para eles, mas nenhuma seta partindo deles para outros. Isso se chama dígrafo (ou grafo direcionado), onde <sup>a</sup> relação acontece apenas em um sentido. Logo, Anuj é vizinho de Bob, mas Bob não é vizinho de Anuj. Um grafo não direcionado (ou simplesmente grafo) não contém setas, <sup>e</sup> ambos os vértices são vizinhos um do outro. Como exemplo, podemos dizer que ambos os grafos mostrados <sup>a</sup> seguir são iguais.

![](_page_17_Figure_2.jpeg)

### Implementando <sup>o</sup> algoritmo

Relembrando, a implementação funcionará da seguinte forma:

![](_page_18_Figure_0.jpeg)

#### Nota

Usei os termos enqueue <sup>e</sup> dequeue ao me referir à atualização de filas. Porém você também encontrará os termos push <sup>e</sup> pop; push é quase sempre <sup>a</sup> mesma coisa que enqueue <sup>e</sup> pop é quase sempre <sup>a</sup> mesma coisa que dequeuе.

Comece criando uma lista. Em Python, usa-se <sup>a</sup> função deque (double-ended queue, que em português significa fila com dois finais) para isso:

from collections import deque fila_de_pesquisa = deque()

fila_de_pesquisa += grafo["voce"]

Cria uma nova lista.

Adiciona todos os seus vizinhos para <sup>a</sup> lista de pesquisa.

![](_page_19_Figure_3.jpeg)

Lembre-se, grafo["voce"] fornecerá uma lista de todos os seus vizinhos, como ["alice", "bob", "claire"].

Todos eles são adicionados à fila de pesquisa.

Vamos ver <sup>o</sup> resto:

```python
while fila_de_pesquisa:
    pessoa = fila_de_pesquisa.popleft()
    if pessoa_e_vendedor (pessoa):
        print pessoa + "é um vendedor de manga!"
        return True
    else:
        fila_de_pesquisa += grafo[pessoa]
return False 6
                                         5
```

Enquanto <sup>a</sup> fila não estiver vazia...

... pega <sup>a</sup> primeira pessoa da fila.

Verifica se essa pessoa é uma vendedora de mangas.

Sim, ela é uma vendedora de mangas.

Não, ela não é uma vendedora de mangas. Adiciona todos os amigos dessa pessoa <sup>à</sup> lista.

Se você chegou até aqui, é sinal de que nenhuma pessoa da fila era uma vendedora de mangas.

Uma última observação: você precisará de uma função pessoa_e_vendedor, que lhe diz se essa pessoa <sup>é</sup> vendedora de mangas. Aqui temos um exemplo:

```python
def pessoa_e_vendedor(nome):
   return nome[-1] == 'm'
```

Essa função verifica se <sup>o</sup> nome da pessoa termina com <sup>a</sup> letra m. Caso termine, ela é uma vendedora de mangas. Esta é uma maneira um pouco boba de procurar vendedores, mas é <sup>o</sup> suficiente para este exemplo. Agora, vamos ver a pesquisa em largura em ação.

![](_page_21_Figure_0.jpeg)

<sup>E</sup> assim por diante, <sup>o</sup> algoritmo continuará até que

- um vendedor de mangas seja encontrado, ou
- <sup>a</sup> lista fique vazia (nesse caso, não há vendedores de mangas).

Alice <sup>e</sup> Bob têm uma amiga em comum: Peggy. Logo, Peggy será adicionada <sup>à</sup> lista duas vezes: uma quando você adicionar os amigos de Alice e novamente quando os amigos de Bob forem adicionados.

Desta forma existirão duas Peggys na sua lista de pesquisa.

![](_page_22_Picture_1.jpeg)

Mas você só precisar verificar Peggy uma vez para saber se ela é uma vendedora de mangas ou não. Verificá-la duas vezes será perda de tempo. Dessa forma, ao verificar uma pessoa, você deve marcá-la como verificada para que ela não seja pesquisada novamente.

Caso isso não seja feito, sua pesquisa poderá entrar em um loop infinito. Suponha que <sup>o</sup> grafo de vendedores de mangas seja algo assim:

![](_page_22_Figure_4.jpeg)

No início, <sup>a</sup> lista de pesquisa contém todos os seus vizinhos.

![](_page_22_Picture_6.jpeg)

Agora você verifica Peggy <sup>e</sup> descobre que ela não é uma vendedora de mangas, então você adiciona todos os vizinhos dela <sup>à</sup> lista de pesquisa.

![](_page_22_Picture_8.jpeg)

Agora verifique você mesmo. Você não é um vendedor de mangas,

então adicione todos os seus vizinhos à lista de pesquisa.

![](_page_23_Picture_1.jpeg)

<sup>E</sup> assim por diante. Isso será um loop infinito porque <sup>a</sup> lista de pesquisa continuará indo de você para <sup>a</sup> Peggy.

![](_page_23_Figure_3.jpeg)

Antes de verificar uma pessoa, é importante conferir se ela ainda não foi verificada. Para fazer isso, você criará uma lista de pessoas que já foram verificadas.

![](_page_23_Figure_5.jpeg)

O código final para <sup>a</sup> pesquisa em largura, considerando isso, fica da seguinte forma:

```python
def pesquisa(nome):
   fila_de_pesquisa = deque()
   fila_de_pesquisa += grafo[nome]
   verificadas = [] 0
   while fila_de_pesquisa:
       pessoa = fila_de_pesquisa.popleft()
```

```python
if not pessoa in verificadas:
       if pessoa_e_vendedor(pessoa):
           print pessoa + " é um vendedor de manga!"
           return True
       else:
return False
           fila_de_pesquisa += grafo[pessoa]
           verificadas.append(pessoa)
```

```python
pesquisa("voce")
```

Esse vetor é <sup>a</sup> forma pela qual você mantém <sup>o</sup> registro das pessoas que já foram verificadas.

Verifica essa pessoa somente se ela já não tiver sido verificada.

Marca essa pessoa como verificada.

Tente executar este código <sup>e</sup> experimente modificar <sup>a</sup> função pessoa_e_vendedor para algo com uma finalidade melhor <sup>e</sup> então veja sese ela representa <sup>o</sup> que você esperava.

### Tempo de execução

Se você procurar um vendedor de mangas em toda <sup>a</sup> sua rede, cada aresta (lembre-se de que aresta é <sup>a</sup> seta ou <sup>a</sup> conexão entre uma pessoa <sup>e</sup> outra) será analisada. Portanto <sup>o</sup> tempo de execução é, no mínimo, O(número de arestas).

Além disso, também será mantida uma lista com as pessoas já verificadas. Adicionar uma pessoa à lista leva um tempo constante: O(1). Fazer isso para cada pessoa terá tempo de execução O(número de pessoas) no total. Assim, <sup>a</sup> pesquisa em largura tem tempo de execução O(número de pessoas <sup>+</sup> número de arestas), que é frequentemente escrito como O(V+A) (V para número de vértices, А para número de arestas).

#### EXERCÍCIOS

Este <sup>é</sup> um pequeno grafo da minha rotina matinal.

![](_page_25_Figure_0.jpeg)

Ele mostra que não posso tomar café da manhã antes de escovar meus dentes. Então "tomar café da manhã" depende de "escovar os dentes".

Por outro lado, tomar banho não depende de escovar os dentes, pois posso tomar banho antes de escovar os dentes. <sup>A</sup> partir desse grafo você pode fazer uma lista relacionando <sup>a</sup> ordem das atividades da minha rotina matinal.

- 1. Acordar.
- 2. Tomar banho.
- 3. Escovar os dentes.
- 4. Tomar café da manhã.

Note que "tomar banho" pode ser movido, logo essa lista também é válida:

- 1. Acordar.
- 2. Escovar os dentes.
- 3. Tomar banho.
- 4. Tomar café da manhã.

  6.3 Quanto a estas três listas, marque se elas são válidas ou inválidas.

![](_page_26_Figure_0.jpeg)

6.4 Aqui temos um grafo maior. Faça uma lista válida para ele.

![](_page_26_Figure_2.jpeg)

Você poderia dizer que essa lista é, de certa forma, ordenada. Se <sup>a</sup> tarefa A depende da tarefa B, <sup>a</sup> tarefa <sup>A</sup> aparece depois na lista. Isso é chamado de ordenação topológica, <sup>e</sup> é uma maneira de criar uma lista ordenada <sup>a</sup> partir de um grafo. Imagine que você esteja planejando um casamento <sup>e</sup> tenha um grafo enorme de tarefas <sup>a</sup> serem realizadas. Porém você não sabe nem por onde começar. Assim, uma ordenação topológica do grafo poderia ser feita e, dessa forma, uma lista de tarefas já em ordem seria elaborada.

Suponha que você tenha uma árvore genealógica.

![](_page_27_Picture_0.jpeg)

Esta árvore <sup>é</sup> um grafo, pois existem vértices (as pessoas) <sup>e</sup> arestas, <sup>e</sup> as arestas apontam para os pais dos vértices. Porém todas as arestas apontam para baixo, pois não faria sentido uma árvore genealógica ter arestas apontando para cima! Seu pai não pode ser <sup>o</sup> pai do seu avô!

![](_page_27_Picture_2.jpeg)

Isso é chamado de árvore. Uma árvore é um tipo especial de grafo em que nenhuma aresta jamais aponta de volta.

6.5 Quais desses grafos também são árvores?

![](_page_28_Figure_0.jpeg)

### Recapitulando

- A pesquisa em largura lhe diz se há um caminho de A para B.
- Se esse caminho existir, <sup>a</sup> pesquisa em largura lhe dará <sup>o</sup> caminho mínimo.
- Se você tem um problema do tipo "encontre <sup>o</sup> menor X", tente modelar <sup>o</sup> seu problema utilizado grafos <sup>e</sup> use <sup>a</sup> pesquisa em largura para resolvê-lo.
- Um dígrafo contém setas <sup>e</sup> as relações seguem <sup>a</sup> direção das setas (Rama -> Adit significa "Rama deve dinheiro <sup>a</sup> Adit").
- Grafos não direcionados não contêm setas, <sup>e</sup> <sup>a</sup> relação acontece nos dois sentidos (Ross - Rachel significa "Ross namorou Rachel <sup>e</sup> Rachel namorou Ross").
- Filas são FIFO (primeiro <sup>a</sup> entrar, primeiro <sup>a</sup> sair).
- <sup>이</sup> Pilhas são LIFO (último <sup>a</sup> entrar, primeiro <sup>a</sup> sair).
- Você precisa verificar as pessoas na ordem em que elas foram adicionadas <sup>à</sup> lista de pesquisa. Portanto <sup>a</sup> lista de pesquisa deve ser uma fila; caso contrário, você não obterá <sup>o</sup> caminho mínimo.
- Cada vez que você precisar verificar alguém, procure não verificálo novamente. Caso contrário, poderá acabar em um loop infinito.

![](_page_29_Picture_0.jpeg)
