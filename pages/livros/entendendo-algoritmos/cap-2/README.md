# Ordenação por seleção

![](_page_0_Picture_1.jpeg)

#### Neste capítulo

- Você conhecerá arrays <sup>e</sup> listas encadeadas dois tipos de estrutura básica. Eles estão por todo lugar. Você já teve acesso aos arrays no capítulo 1 <sup>e</sup> continuará se utilizando deles por praticamente todos os capítulos. Arrays são fundamentais, então preste atenção! Porém algumas vezes é melhor usar <sup>a</sup> lista encadeada em vez do array. Este capítulo explana os prós <sup>e</sup> os contras de ambas as estruturas para que possa decidir qual é <sup>a</sup> ideal para <sup>o</sup> seu algoritmo.
- Você aprenderá <sup>a</sup> fazer <sup>o</sup> seu primeiro algoritmo de ordenação. Muitos algoritmos só funcionam se os dados estiverem ordenados. Lembra-se da pesquisa binária? Você

só pode executá-la se os elementos de sua lista estiverem ordenados. Este capítulo lhe apresentará <sup>a</sup> ordenação por seleção. A maioria das linguagens de programação contém nativamente os algoritmos de seleção, então raramente terá de escrever <sup>a</sup> sua própria versão <sup>a</sup> partir do zero. No entanto <sup>a</sup> ordenação por seleção <sup>é</sup> um trampolim para<sup>o</sup> quicksort, que abordarei no próximo capítulo. O quicksort é um algoritmo importante <sup>e</sup> será compreendido mais facilmente se você já conhecer algum tipo de algoritmo de ordenação.

#### O que você precisa saber

Para entender <sup>a</sup> análise de desempenho deste capítulo, você precisa conhecer <sup>a</sup> notação Big O <sup>e</sup> logaritmos. Se não conhece, sugiro que leia <sup>o</sup> Capítulo 1. A notação Big O é utilizada em todo este livro.

## Como funciona <sup>a</sup> memória

Imagine que você vai <sup>a</sup> um show <sup>e</sup> precisa guardar as suas coisas na chapelaria. Algumas gavetas estão disponíveis.

![](_page_1_Figure_5.jpeg)

Cada gaveta pode guardar um elemento. Você deseja guardar duas

coisas, então pede duas gavetas.

![](_page_2_Picture_1.jpeg)

Você guardou as suas duas coisas aqui.

![](_page_2_Picture_3.jpeg)

Você está pronto para<sup>o</sup> show! E mais ou menos assim que <sup>a</sup> memória do seu computador funciona. O computador se parece com um grande conjunto de gavetas, e cada gaveta tem seu endereço.

![](_page_3_Picture_0.jpeg)

feØffeeb é <sup>o</sup> endereço de um slot na memória.

Cada vez que quer armazenar um item na memória, você pede ao computador um pouco de espaço <sup>e</sup> ele te dá um endereço no qual você pode armazenar <sup>o</sup> seu item. Se quiser armazenar múltiplos itens, existem duas maneiras para fazer isso: arrays <sup>e</sup> listas. Falarei sobre arrays <sup>e</sup> listas depois, bem como sobre os prós <sup>e</sup> contras de cada um. Não existe apenas uma maneira correta para armazenar itens em cada um dos casos, então é importante saber as diferenças.

### Arrays <sup>e</sup> listas encadeadas

![](_page_3_Picture_4.jpeg)

Algumas vezes, você precisa armazenar uma lista de elementos na memória. Suponha que você esteja escrevendo um aplicativo para gerenciar os seus afazeres. É necessário armazenar os seus afazeres como uma lista na memória.

Você deve usar um array ou uma lista encadeada? Vamos armazenar

os afazeres primeiro em um array, pois assim <sup>a</sup> compreensão fica mais fácil. Usar um array significa que todas as suas tarefas estão armazenadas contiguamente (uma ao lado da outra) na memória.

![](_page_4_Figure_1.jpeg)

Agora, suponha que você queira adicionar mais uma tarefa. No entanto <sup>a</sup> próxima gaveta está ocupada por coisas de outra pessoa!

![](_page_4_Figure_3.jpeg)

É como se você estivesse indo ao cinema com os seus amigos <sup>e</sup> encontrasse um lugar para sentar, mas outro amigo se juntasse <sup>a</sup> vocês <sup>e</sup> não houvesse lugar para ele. Vocês todos precisariam se mover <sup>e</sup> encontrar um lugar onde todos coubessem. Neste caso, você precisaria solicitar ao computador uma área de memória em que coubessem todas as suas tarefas. Então você as moveria para lá.

Se outro amigo aparecesse, vocês ficariam sem lugar novamente - <sup>e</sup> todos precisariam se mover uma segunda vez! Que incômodo. Da mesma forma, adicionar novos itens <sup>a</sup> um array será muito lento. Uma maneira fácil de resolver isso <sup>é</sup> "reservando lugares": mesmo

que você tenha três itens na sua lista de tarefas, você pode solicitar ao computador dez espaços, só por via das dúvidas. Então, você pode adicionar dez itens <sup>a</sup> sua lista sem precisar mover nada. Isto é uma boa maneira de contornar o problema, mas você precisa ficar atento às desvantagens:

- Você pode não precisar dos espaços extras que reservou; então <sup>a</sup> memória será desperdiçada. Você não está utilizando <sup>a</sup> memória, mas ninguém mais pode usá-la também.
- Você pode precisar adicionar mais de dez itens <sup>a</sup> sua lista de tarefas, então você terá de mover seus itens de qualquer maneira.

Embora seja uma boa forma de contornar <sup>o</sup> problema, não é uma solução perfeita. Listas encadeadas resolvem este problema de adição de itens.

### Listas encadeadas

Com as listas encadeadas, seus itens podem estar em qualquer lugar da memória.

![](_page_5_Figure_6.jpeg)

Cada item armazena <sup>o</sup> endereço do próximo item da lista. Um monte de endereços aleatórios de memória estão ligados.

![](_page_6_Figure_0.jpeg)

Endereços de memória ligados.

ao É como uma caça ao tesouro. Você vai ao primeiro endereço <sup>e</sup> ele diz "o próximo item pode ser encontrado no endereço 123". Então vai endereço 123 <sup>e</sup> ele diz "O próximo item pode ser encontrado no endereço 847", <sup>e</sup> assim por diante. Adicionar um item <sup>a</sup> uma lista encadeada é fácil: você <sup>o</sup> coloca em qualquer lugar da memória <sup>e</sup> armazena <sup>o</sup> endereço do item anterior.

Com as listas encadeadas você nunca precisa mover os seus itens; também evita outro problema. Digamos que você vá <sup>a</sup> um cinema famoso com os seus amigos. Vocês seis estão tentando procurar um lugar para sentar, mas <sup>o</sup> cinema está cheio. Não há seis lugares juntos. Bem, algumas vezes isso acontece com arrays. Imagine que está tentando encontrar 10.000 slots para um array. Sua memória tem 10.000 slots, mas eles não estão juntos. Você não consegue arrumar um lugar para <sup>o</sup> seu array! Usar uma lista encadeada seria como dizer "vamos nos dividir <sup>e</sup> assistir ao filme". Se existir espaço na memória, você terá espaço para <sup>a</sup> sua lista encadeada.

Se as listas encadeadas são muito melhores para inserções, para que servem os arrays?

### Arrays

![](_page_7_Picture_0.jpeg)

Os websites que apresentam listas "top 10" usam uma tática trapaceira para conseguir mais visualizações. Em vez de mostrarem <sup>a</sup> lista em uma única página, eles colocam um item em cada página <sup>e</sup> fazem você clicar em "próximo" para ler <sup>o</sup> item seguinte. Por exemplo, "Os 10 melhores vilões da TV" não estarão listados em uma única página, em vez disso, você começará pelo #10 (Newman) <sup>e</sup> seguirá clicando em "próximo" até chegar em #1 (Gustavo Fring). Esta técnica fornece aos sites dez páginas inteiras para incluir anúncios, mas fica chato ficar clicando em "próximo" nove vezes até chegar ao número 1. Seria muito melhor se <sup>a</sup> lista estivesse em uma única página <sup>e</sup> você pudesse clicar no nome de cada vilão para saber mais.

Listas encadeadas têm um problema similar. Suponha que você queira ler <sup>o</sup> último item de uma lista encadeada. Você não pode fazer isso porque não sabe <sup>o</sup> endereço dele. Em vez disso, precisa ir ao item #1 para pegar <sup>o</sup> endereço do item #2. Então, é necessário ir ao item #2 para encontrar <sup>o</sup> endereço do item #3, <sup>e</sup> assim por diante, até conseguir <sup>o</sup> endereço do último item. Listas encadeadas são ótimas se você quiser ler todos os itens, um de cada vez: você pode ler um item, seguir para <sup>o</sup> endereço do próximo item <sup>e</sup> fazer isso até <sup>o</sup> fim da lista. Mas se você quiser pular de um item para outro, as listas encadeadas são terríveis.

Com arrays é diferente. Você sabe <sup>o</sup> endereço de cada item. Por exemplo, suponha que seu array tenha cinco itens <sup>e</sup> que você saiba que o primeiro está no endereço 00. Qual <sup>é</sup> o endereço do item #5?

![](_page_8_Figure_0.jpeg)

A matemática lhe dá <sup>a</sup> resposta: está no endereço 04. Arrays são ótimos se você deseja ler elementos aleatórios, pois pode encontrar qualquer elemento instantaneamente em um array. Na lista encadeada, os elementos não estão próximos uns dos outros, então você não pode calcular instantaneamente <sup>a</sup>posição de um elemento na memória - precisa ir ao primeiro elemento para encontrar <sup>o</sup> endereço do segundo, então ir ao segundo elemento para encontrar <sup>o</sup> endereço do terceiro <sup>e</sup> seguir fazendo isso até chegar ao elemento que deseja.

### Terminologia

Os elementos em um array são numerados. Essa numeração começа no 0, não no 1. Neste array, por exemplo, <sup>o</sup> número 20 está na posição 1.

| 10 | 20 | 30 40 |   |
|----|----|-------|---|
|    | 1  | 2     | 3 |

O número 10 está na posição 0. Isso geralmente confunde novos programadores. Começar no 0 simplifica todos os tipos de array na programação, logo, os programadores não podem fugir disso. Quase todas as linguagens de programação começarão os arrays numerando <sup>o</sup> primeiro elemento como 0. Logo você se acostuma!

A posição de um elemento é chamada de índice. Portanto, em vez de dizer "o número 20 está na posição 1", <sup>a</sup> terminologia correta seria dizer "o número 20 está no índice 1". Usarei índice para falar de posição neste livro.

Aqui está <sup>o</sup> tempo de execução para operações comuns de arrays <sup>e</sup> listas.

|          | ARRAYS                                                                | LISTAS |  |
|----------|-----------------------------------------------------------------------|--------|--|
| LEITURA  | (DO                                                                   | O (n)  |  |
| INSERÇÃO | O                                                                     | 0α)    |  |
|          | O(N) = TEMPO DE EXECUÇÃO LINEAR<br>0(1) = TEMPO DE EXECUÇÃO CONSTANTE |        |  |

Pergunta: Por que é necessário tempo de execução O(n) para inserir um elemento em um array? Suponha que você queira inserir um elemento no começo de um array. Como faria isso? Quanto tempo levaria? Encontre as respostas no final desta seção!

#### EXERCÍCIOS

2.1 Suponha que você esteja criando um aplicativo para acompanhar as suas finanças.

![](_page_9_Figure_4.jpeg)

Todos os dias você anotará tudo <sup>o</sup> que gastou <sup>e</sup> onde gastou. No final do mês, você deverá revisar os seus gastos <sup>e</sup> resumir <sup>o</sup> quanto gastou. Logo, você terá um monte de inserções <sup>e</sup> poucas leituras. Você deverá usar um array ou uma lista para implementar este aplicativo?

### Inserindo algo no meio da lista

Imagine que você queira que <sup>a</sup> sua lista de tarefas se pareça mais com um calendário. Antes, você adicionava os itens ao final da lista. Agora, quer adicionar suas tarefas na ordem em que elas devem ser realizadas.

![](_page_10_Picture_0.jpeg)

#### Lista desordenada.

O que seria melhor se você quisesse inserir elementos no meio de uma lista: arrays ou listas encadeadas? Usando listas encadeadas, basta mudar <sup>o</sup> endereço para <sup>o</sup> qual <sup>o</sup> elemento anterior está apontando.

![](_page_10_Figure_3.jpeg)

Já para arrays, você deve mover todos os itens que estão abaixo do endereço de inserção.

![](_page_10_Figure_5.jpeg)

Se não houver espaço, pode ser necessário mover tudo para um novo local! Por isso, listas encadeadas são melhores caso você queira inserir um elemento no meio de uma lista.

## Deleções

<sup>E</sup> se você quiser deletar um elemento? Novamente, <sup>é</sup> mais fácil fazer isso usando listas encadeadas, pois é necessário mudar apenas <sup>o</sup> endereço para <sup>o</sup> qual <sup>o</sup> elemento anterior está apontando. Com arrays, tudo precisa ser movido quando um elemento é eliminado.

Ao contrário do que ocorre com as inserções, <sup>a</sup> eliminação de elementos sempre funcionará. A inserção poderá falhar quando não houver espaço suficiente na memória.

Aqui estão os tempos de execução para as operações mais comuns em arrays <sup>e</sup> listas encadeadas.

|            | ARRAYS | LISTAS |
|------------|--------|--------|
| LEITURA    | O(1)   | (n)    |
| INSERÇÃO   | Oh     | 4)     |
| ELIMINAÇÃO | (      | O(1)   |

Vale <sup>a</sup> pena mencionar que inserções <sup>e</sup> eliminações terão tempo de execução O(1) somente se você puder acessar instantaneamente<sup>о</sup> elemento <sup>a</sup> ser deletado. É uma prática comum acompanhar <sup>o</sup> primeiro <sup>e</sup> <sup>o</sup> último item de uma lista encadeada para que <sup>o</sup> tempo de execução para deletá-los seja O(1).

O que é mais usado: arrays ou listas? Obviamente, isso depende do caso em que se aplicam. Entretanto os arrays são mais comuns porque permitem acesso aleatório. Existem dois tipos de acesso: <sup>o</sup> aleatório <sup>e</sup> <sup>o</sup> sequencial. O sequencial significa ler os elementos, um por um, começando pelo primeiro. Listas encadeadas só podem lidar com acesso sequencial. Se você quiser ler <sup>o</sup> décimo elemento de uma lista encadeada, primeiro precisará ler os nove elementos anteriores

para chegar ao endereço do décimo elemento. O aleatório permite que você pule direto para <sup>o</sup> décimo elemento. Muitos casos requerem <sup>o</sup> acesso aleatório, <sup>o</sup> que faz os arrays serem mais utilizados. Arrays <sup>e</sup> listas são usados para implementar outras estruturas de dados (isso será explicado mais adiante).

#### EXERCÍCIOS

2.2 Suponha que você esteja criando um aplicativo para anotar os pedidos dos clientes em um restaurante. Seu aplicativo precisa de uma lista de pedidos. Os garçons adicionam os pedidos <sup>a</sup> essa lista <sup>e</sup> os chefes retiram os pedidos da lista. Funciona como uma fila. Os garçons colocam os pedidos no final da fila <sup>e</sup> os chefes retiram os pedidos do começo dela para cozinhá-los.

![](_page_12_Picture_3.jpeg)

- Você usaria um array ou uma lista encadeada para implementar essa lista? (Dica: listas encadeadas são boas para inserções/eliminações <sup>e</sup> arrays são bons para acesso aleatório. O que fazer neste caso?)
- 2.3 Vamos analisar um experimento. Imagine que <sup>o</sup> Facebook guarda uma lista de usuários. Quando alguém tenta acessar <sup>o</sup> Facebook, uma busca <sup>é</sup> feita pelo nome de usuário. Se <sup>o</sup> nome da pessoa está na lista, ela pode continuar <sup>o</sup> acesso. As pessoas acessam<sup>o</sup> Facebook com muita frequência, então existem muitas buscas nessa lista. Presuma que <sup>o</sup> Facebook usa <sup>a</sup> pesquisa binária para procurar um nome na lista. A pesquisa binária requer acesso aleatório - você precisa ser capaz de acessar <sup>o</sup> meio da lista de

nomes instantaneamente. Sabendo disso, você implementaria essa lista como um array ou uma lista encadeada?

- 2.4 As pessoas se inscrevem no Facebook com muita frequência também. Suponha que você decida usar um array para armazenar <sup>a</sup> lista de usuários. Quais as desvantagens de um array em relação às inserções? Em particular, imagine que você está usando <sup>a</sup> pesquisa binária para buscar os logins. <sup>O</sup> que acontece quando você adiciona novos usuários em um array?
- 2.5 Na verdade, <sup>o</sup> Facebook não usa nem arrays nem listas encadeadas para armazenar informações. Vamos considerar uma estrutura de dados híbrida: um array de listas encadeadas. Você tem um array com 26 slots. Cada slot aponta para uma lista encadeada. Por exemplo, <sup>o</sup> primeiro slot do array aponta para uma lista encadeada que contém os usuários que começam com <sup>a</sup> letra A. O segundo slot aponta para <sup>a</sup> lista encadeada que contém os usuários que começam com <sup>a</sup> letra B, <sup>e</sup> assim por diante.

![](_page_13_Figure_3.jpeg)

- Suponha que <sup>o</sup> Adit B se inscreva no Facebook <sup>e</sup> você queira adicioná-lo à lista. Você vai ao slot <sup>1</sup> do array, <sup>a</sup> seguir para <sup>a</sup> lista encadeada do slot 1, <sup>e</sup> adiciona Adit <sup>B</sup> no final. Agora, suponha que você queira procurar <sup>o</sup> Zakhir H. Você vai ao slot 26, que aponta para <sup>a</sup> lista encadeada de todos os nomes começados em Z. Então, procura pela lista até encontrar <sup>o</sup> Zakhir H.
- Compare esta estrutura híbrida com arrays <sup>e</sup> listas encadeadas. É mais lento ou mais rápido fazer inserções <sup>e</sup> eliminações nesse caso? Você não precisa responder dando o tempo de execução

Big(O), apenas diga se <sup>a</sup> nova estrutura de dados é mais rápida ou mais lenta do que os arrays <sup>e</sup> as listas encadeadas.

### Ordenação por seleção

![](_page_14_Picture_2.jpeg)

Vamos juntar tudo aprendido até aqui para você conhecer <sup>o</sup> seu segundo algoritmo: <sup>a</sup> ordenação por seleção. Para seguir nesta seção, você precisa ter compreendido arrays <sup>e</sup> listas, bem com <sup>a</sup> notação Big Ο.

Suponha que você tenha um monte de músicas no seu computador. Para cada artista, você tem um contador de plays.

|                    | CONTADOR<br>DE PLAYS |
|--------------------|----------------------|
| RADIOHEAD          | 156                  |
| KISHORE KUMAR      | 141                  |
| THE BLACK KEYS     | 35                   |
| NEUTRAL MILK HOTEL | 94                   |
| BECK               | 88                   |
| THE STROKES        | 61                   |
| WILCO              | 111                  |

Você quer ordenar uma lista de artistas, do artista mais tocado para <sup>o</sup> menos tocado, para que possa categorizar os seus artistas favoritos. Como pode fazer isso? Uma maneira seria pegar <sup>o</sup> artista mais tocado da lista de músicas e adicioná-lo a uma nova lista.

|                                         | CONTADOR<br>DE PLAYS | SORTED                             | CONTADOR<br>DE PLAYS |  |
|-----------------------------------------|----------------------|------------------------------------|----------------------|--|
| RADIOHEAD                               | 156                  | RADIOHEAD                          | 156                  |  |
| KISHORE KUMAR                           | 141                  |                                    |                      |  |
| THE BLACK KEYS                          | 35                   |                                    |                      |  |
| NEUTRAL MILK HOTEL                      | 94                   |                                    |                      |  |
| BECK                                    | 88                   |                                    |                      |  |
| THE STROKES                             | 61                   |                                    |                      |  |
| WILCO                                   | 111                  |                                    |                      |  |
| 1. RADIOHEAD É O<br>ARTISTA MAIS TOCADO |                      | 2. ADICIONE-O EM<br>UMA NOVA LISTA |                      |  |

Faça isso de novo para encontrar <sup>o</sup> próximo artista mais tocado.

| nes<br>n                                            | CONTADOR<br>DE PLAYS | SORTED                                                          | CONTADOR<br>DE PLAYS |
|-----------------------------------------------------|----------------------|-----------------------------------------------------------------|----------------------|
|                                                     |                      | RADIOHEAD                                                       | 156                  |
| KISHORE KUMAR                                       | 141                  | KISHORE KUMAR                                                   | 141                  |
| THE BLACK KEYS                                      | 35                   |                                                                 |                      |
| NEUTRAL MILK HOTEL                                  | 94                   |                                                                 |                      |
| BECK                                                | 88                   |                                                                 |                      |
| THE STROKES                                         | 61                   |                                                                 |                      |
| WILCO                                               | 111                  |                                                                 |                      |
| 1. KISHORE KUMAR É O PRÓXIMO<br>ARTISTA MAIS TOCADO |                      | 2. PORTANTO, ELE É O PRÓXIMO<br>ARTISTA ADICIONADO À NOVA LISTA |                      |

Continue fazendo isso <sup>e</sup> então você terminará com uma lista ordenada.

| ибаи               | CONTADOR<br>DE PLAYS |
|--------------------|----------------------|
| RADIOHEAD          | 156                  |
| KISHORE KUMAR      | 141                  |
| WILCO              | 111                  |
| NEUTRAL MILK HOTEL | 94                   |
| BECK               | 88                   |
| THE STROKES        | 61                   |
| THE BLACK KEYS     | 35                   |

Vamos pensar como engenheiros da computação <sup>e</sup> avaliar quanto tempo isso demoraria <sup>a</sup> ser executado. Lembre-se de que <sup>o</sup> tempo de execução O(n) significa que você precisa passar por todos os elementos da lista uma vez. Por exemplo, executar uma pesquisa simples na lista de artistas significa olhar para cada artista uma vez.

![](_page_16_Picture_2.jpeg)

Para encontrar <sup>o</sup> artista com <sup>o</sup> maior número de plays você precisa verificar cada item da lista. Isso tem tempo de execução O(n), como você acabou de ver. Então você tem uma operação com tempo de execução O(n) <sup>e</sup> precisa repetir essa operação n vezes:

![](_page_17_Figure_0.jpeg)

Isso tem tempo de execução O(n <sup>x</sup> n) ou O(n²).

Algoritmos de ordenação são muito úteis. Agora você pode ordenar:

- nomes em uma agenda telefônica
- datas de viagem
- emaile (do maie novo an maie antioo)

#### Verificando menos elementos <sup>a</sup> cada vez

Talvez você esteja pensando: conforme passa pelas operações, <sup>o</sup> número de elementos que precisa analisar diminui. Eventualmente, você acaba tendo de checar apenas um elemento. Então como <sup>o</sup> tempo de execução permanece sendo O(n²)? Isto é uma boa pergunta, e a resposta tem <sup>a</sup> ver com <sup>a</sup> notação Big O. Falarei mais sobre isso no capítulo 4, mas aqui vai <sup>o</sup> ponto principal.

Você estava certo sobre não precisar verificar <sup>n</sup> elementos <sup>a</sup> cada vez.

Você verifica <sup>n</sup> elementos, então <sup>n</sup> - 1, <sup>n</sup> - 2 ... 2, 1. Na média, você verifica uma lista que tem <sup>½</sup> <sup>x</sup> <sup>n</sup> elementos. <sup>O</sup> tempo de execução <sup>é</sup> O(n <sup>x</sup> <sup>½</sup> <sup>x</sup> n). Mas constantes como <sup>½</sup> são ignoradas na notação Big O (novamente, leia <sup>o</sup> Capítulo 4 para ter acesso à discussão completa), então você escreve apenas O(n <sup>x</sup> n) ou O(n²).

A ordenação por seleção é um algoritmo bom, mas não é muito rápido. O Quicksort é um algoritmo de ordenação mais rápido, que tem tempo de execução de apenas O(n log n). Falarei dele no capítulo 4!

#### EXEMPLO DE CÓDIGO

Nós não lhe mostramos <sup>o</sup> código para ordenar <sup>a</sup> lista de músicas, mas <sup>a</sup> seguir estão alguns códigos que farão algo bem similar: ordenar um array do menor para <sup>o</sup> maior. Vamos escrever uma função para encontrar <sup>o</sup> menor elemento em um array:

```
def buscaMenor (arг):
   menor = arr[0] 0
   menor_indice = 0
   for i in range(1, len(arr)):
       if arr[i] < menor:
           menor = arr[i]
           menor_indice = i
   return menor_indice
```

Armazena <sup>o</sup> menor valor.

Armazena <sup>o</sup> índice do menor valor.

Agora, você pode usar esta função para escrever <sup>a</sup> ordenação por seleção:

```
def ordenacaoporSelecao(arг): 1
   novoArr = [ ]
   for i in range(len(arr)):
       menor = buscaMenor(arr)
       novoArr.append(arr.pop(menor))
   return novoArr
```

```
print ordenacaoporSelecao([5, 3, 6, 2, 10])
```

Ordenações em um array.

Encontra o menor elemento do array e adiciona ao novo array.

![](_page_19_Picture_0.jpeg)

### Recapitulando

- <sup>A</sup> memória do seu computador <sup>é</sup> como um conjunto gigante de gavetas.
- 이 Quando se quer armazenar múltiplos elementos, usa-se um array ou uma lista.
- No array, todos os elementos são armazenados um ao lado do outro.
- Na lista, os elementos estão espalhados <sup>e</sup> um elemento armazena endereço do próximo elemento. Ο
- Arrays permitem leituras rápidas.
- Listas encadeadas permitem rápidas inserções <sup>e</sup> eliminações.
- Todos os elementos de um array devem ser do mesmo tipo (todos ints, todos doubles, <sup>e</sup> assim por diante).

# Recursão

![](_page_20_Picture_1.jpeg)

### Neste capítulo

- Você aprenderá recursão. A recursão é uma técnica de programação utilizada em muitos algoritmos. É um assunto importante para <sup>a</sup> compreensão dos capítulos seguintes.
- Você aprenderá como separar um problema em caso-base <sup>e</sup> caso recursivo. A estratégia dividir para conquistar (Capítulo 4) usa este conceito simples para resolver problemas complicados.

Estou animado com este capítulo porque trata de recursão, uma maneira elegante de solucionar problemas. A recursão é um dos meus tópicos favoritos, mas ela é polêmica. As pessoas ou <sup>a</sup> amam ou a odeiam, ou elas a odeiam até que aprendam a amá-la alguns anos

depois. Eu estava nessa terceira situação. Para facilitar as coisas, tenho um conselho:

- Este capítulo apresenta vários exemplos de códigos. Execute-os para ver como eles funcionam.
- <sup>이</sup> Falarei sobre funções recursivas. Pelo menos uma vez, analise uma função recursiva com um papel <sup>e</sup> uma caneta, algo do tipo "vamos ver, passo <sup>o</sup> número 5 para <sup>a</sup> função fatorial, <sup>e</sup> então retorno cinco vezes passando <sup>o</sup> número <sup>4</sup> para fatorial, <sup>o</sup> que me dá...", <sup>e</sup> assim por diante. Analisar uma função dessa forma lhe ajudará <sup>a</sup> entender como funcionam as funções recursivas.

Este capítulo inclui muitos pseudocódigos. Pseudocódigos são uma descrição de alto nível de um problema em formato de código. É escrito como um código, mas utiliza linguagem mais próxima da humana.

## Recursão

Suponha que você esteja vasculhando <sup>o</sup> porão de sua avó <sup>e</sup> encontre uma misteriosa mala trancada.

![](_page_21_Picture_6.jpeg)

A sua avó diz que <sup>a</sup> chave para <sup>a</sup> mala provavelmente está em uma caixa.

![](_page_22_Figure_0.jpeg)

Esta caixa contém mais caixas com mais caixas dentro delas. A chave está em alguma destas caixas. Qual é o seu algoritmo para procurála? Pense nisso antes de continuar <sup>a</sup> leitura.

Aqui está uma abordagem.

![](_page_23_Figure_0.jpeg)

- 1.Monte uma pilha com as caixas que serão analisadas.
- 2. Pegue uma caixa <sup>e</sup> olhe <sup>o</sup> que tem dentro dela.
- 3. Se você encontrar outra caixa dentro dela, adicione-a <sup>a</sup> um novo monte para ser verificada mais tarde.
- 4. Se você encontrar uma chave, terminou!
- 5. Repita.

Aqui está outra abordagem.

![](_page_23_Figure_7.jpeg)

1.Olhe o que tem dentro da caixa.

2. Se encontrar outra caixa, volte ao passo 1.

3. Se encontrar <sup>a</sup> chave, terminou!

Qual abordagem lhe parece mais fácil? A primeira abordagem utiliza um loop while (enquanto, em português). Enquanto <sup>o</sup> monte existir, pegue uma caixa <sup>e</sup> olheo<sup>o</sup> que tem dentro dela:

```
def procure_pela_chave(caixa_principal):
   pilha = main_box.crie_uma_pilha_para_busca()
   while pilha is not vazia:
       caixa = pilha.pegue_caixa()
       for item in caixa:
           if item.e_uma_caixa():
               pilha.append(item)
           elif item.e_uma_chave():
               print "achei a chave!"
```

A segunda maneira utiliza <sup>a</sup> recursão. Recursão é quando uma função chama <sup>a</sup> si mesma. Veja <sup>o</sup> pseudocódigo de como isso funciona.

```
def procure_pela_chave(caixa):
    for
       item in caixa:
       if item.e_uma_caixa():
           procure_pela_chave(item)
       elif item.e_uma_chave():
           print "achei a chave!"
```

Recursão!

Ambas as abordagens cumprem com <sup>a</sup> mesma proposta, mas <sup>a</sup> segunda me parece mais objetiva. A recursão é usada para tornar <sup>a</sup> resposta mais clara. Não há nenhum benefício quanto <sup>a</sup> desempenho ao utilizar <sup>a</sup> recursão. Na verdade, os loops algumas vezes são melhor para <sup>o</sup> desempenho de um programa. Gosto desta frase de Leigh Caldwell, do Stack Overflow: "Os loops podem melhorar <sup>o</sup> desempenho do seu programa. A recursão melhora <sup>o</sup> desempenho do seu programador. Escolha <sup>o</sup> que for mais importante para <sup>a</sup> sua situação."¹

Muitos algoritmos importantes usam <sup>a</sup> recursão, então é fundamental entender este conceito.

#### Caso-base <sup>e</sup> caso recursivo

![](_page_25_Picture_1.jpeg)

Devido ao fato de <sup>a</sup> função recursiva chamar <sup>a</sup> si mesma, é mais fácil escrevê-la erroneamente <sup>e</sup> acabar em um loop infinito. Por exemplo, suponha que você escreva uma função que imprima uma contagem regressiva, como esta:

> 3...2...1

Você pode escrever isso de maneira recursiva fazendo <sup>o</sup> seguinte:

```
def regressiva(i):
   print i
   regressiva(i-1)
```

Escreva este código <sup>e</sup> execute-o. Você perceberá um problema: essa função ficará executando para sempre!

![](_page_25_Figure_7.jpeg)

Loop infinito.

<sup>&</sup>gt; 3...2...1...0..-1...-2...

(Pressione Ctrl-C para interromper <sup>o</sup> seu script.)

Quando você escreve uma função recursiva, deve informar quando a

recursão deve parar. E por isso que toda função recursiva tem duas partes: <sup>o</sup> caso-base <sup>e</sup> <sup>o</sup> caso recursivo. <sup>O</sup> caso recursivo é quando <sup>a</sup> função chama <sup>a</sup> si mesma. O caso-base é quando <sup>a</sup> função não chama <sup>a</sup> si mesma novamente, de forma que <sup>o</sup> programa não se torna um loop infinito.

Vamos adicionar <sup>o</sup> caso-base à função de contagem regressiva:

```
def regressiva(i):
 print i
 if i <= 1:0
   return
 else:
   regressiva(i-1)
```

Caso-base.

Caso recursivo.

Agora, <sup>a</sup> função funciona como esperado. Ela fica mais ou menos assim:

![](_page_26_Figure_6.jpeg)

## A pilha

![](_page_26_Picture_8.jpeg)

Esta seção aborda <sup>a</sup> pilha de chamada (call stack). Isto é um conceito importante em programação <sup>e</sup> indispensável para entender <sup>a</sup> recursão.

Suponha que você esteja fazendo um churrasco para os seus amigos. Você tem uma lista de afazeres em forma de uma pilha de notas adesivas.

![](_page_27_Picture_2.jpeg)

Você se lembra de que, quando falamos de arrays <sup>e</sup> listas, também havia uma lista de afazeres? Podia adicionar itens em qualquer lugar da lista ou remover itens aleatórios. A pilha de notas adesivas é bem mais simples. Quando você insere um item, ele é colocado no topo da pilha. Quando você lê um item, lê apenas <sup>o</sup> item do topo da pilha <sup>e</sup> ele é retirado da lista. Logo, sua lista de afazeres contém apenas duas ações: push (inserir) <sup>e</sup> pop (remover <sup>e</sup> ler).

![](_page_27_Picture_4.jpeg)

Vamos ver como isso funciona na prática.

![](_page_28_Figure_0.jpeg)

Esta estrutura de dados é chamada de pilha. A pilha é uma estrutura de dados simples. Você <sup>a</sup> tem usado esse tempo todo sem perceber!

### A pilha de chamada

Seu computador usa uma pilha interna denominada pilha de chamada. Vamos ver isto na prática. Aqui está um exemplo simples:

```
def sauda(nome):
    print "Olá, " + nome + "!"
    sauda2(nome)
    print "preparando para dizer tchau..."
    tchau()
```

Esta função te cumprimenta <sup>e</sup> chama outras duas funções:

```
def sauda2(nome):
    print "Como vai " + nome + "?"
def tchau():
    print "ok, tchau!"
```

Vamos analisar <sup>o</sup> que acontece quando você chama uma função.

#### Nota

print é uma função em Python, mas, para facilitar as coisas, vamos fingir que não é. Entre na brincadeira.

N.R.T.: tecnicamente print não é uma função em Python 2, mas uma instrução ou statement.

Suponha que você chame sauda("maggie"). Primeiro, seu computador aloca uma caixa de memória para essa chamada.

![](_page_29_Picture_1.jpeg)

Agora, vamos usar <sup>a</sup> memória. A variável nome é setada para "maggie". Isso precisa ser salvo.

![](_page_29_Figure_3.jpeg)

Cada vez que você faz uma chamada de função, seu computador salva na memória os valores para todas as variáveis. Depois disso, imprime olá, maggie!. Então, chama sauda2("maggie").

![](_page_29_Figure_5.jpeg)

Novamente, seu computador aloca uma caixa de memória para essa chamada de função.

Seu computador está usando uma pilha para estas caixas. A segunda caixa é adicionada em cima da primeira. Você imprime "como vai maggie?". Então, retorna da chamada de função. Quando isso acontece, <sup>a</sup> caixa do topo da pilha é retirada.

![](_page_29_Picture_8.jpeg)

Agora, <sup>a</sup> caixa do topo da pilha aloca os valores da função sauda, <sup>o</sup> que significa que você retornou à função sauda. Quando você

chamou <sup>a</sup> função sauda2, <sup>a</sup> função sauda ficou parcialmente completa. Esta é <sup>a</sup> grande ideia por trás desta seção: quando você chama uma função <sup>a</sup> partir de outra, <sup>a</sup> chamada de função fica pausada em um estado parcialmente completo. Todos os valores das variáveis para aquela função ainda estão armazenados na memória. Agora que você já utilizou <sup>a</sup> função sauda2, você está de volta na função sauda <sup>e</sup> pode continuar de onde parou. Primeiro, imprime "preparando para dizer tchau..."e então chama <sup>a</sup> função tchau.

![](_page_30_Picture_1.jpeg)

Uma caixa para esta função é adicionada ao topo da pilha. Quando você imprimir ok, tchau!, retornará da chamada de função.

![](_page_30_Picture_3.jpeg)

Agora, você está de volta à função sauda. Não há nada mais <sup>a</sup> ser feito, <sup>e</sup> você pode sair da função sauda também. Essa pilha usada para guardar as variáveis de múltiplas funções é denominada pilha de chamada.

#### EXERCÍCIOS

3.1 Suponha que eu forneça uma pilha de chamada como esta:

![](_page_30_Picture_7.jpeg)

- Quais informações você pode retirar baseando-se apenas nesta pilha de chamada?
- Agora, vamos ver esta pilha de chamada sendo executada com uma função recursiva.

### A pilha de chamada com recursão

As funções recursivas também utilizam <sup>a</sup> pilha de chamada! Vamos analisar isto na prática com <sup>a</sup> função fat (fatorial). fat(5) é escrita como 5! <sup>e</sup> é definida da seguinte forma: 5! <sup>=</sup> 5\*4\*3\*2 \* 1. De forma semelhante, fat(3) é3\*2 \* 1. Aqui está uma função recursiva para calcular <sup>a</sup> fatorial de um número:

```
def fat(x):
 if X == 1:
   return 1
 else:
   return x * fat(x-1)
```

Agora, você chama <sup>a</sup> função fat(3). Vamos analisar esta pilha de chamada linha por linha <sup>e</sup> ver como ela se altera. Lembre-se, <sup>a</sup> caixa mais próxima ao topo lhe diz em qual chamada <sup>a</sup> função fat se encontra atualmente.

![](_page_32_Figure_0.jpeg)

![](_page_33_Figure_0.jpeg)

Repare que cada chamada para <sup>a</sup> função fat tem seu próprio valor de x. Você não consegue acessar <sup>a</sup> mesma função com outro valor de X.

A pilha tem um papel importante na recursão. No primeiro exemplo, mostrei duas abordagens para encontrar <sup>a</sup> chave. Aqui está <sup>a</sup> primeira.

![](_page_33_Figure_3.jpeg)

Desta forma, você fez um monte com caixas para analisar, então sabe quais caixas você ainda precisa abrir.

![](_page_34_Figure_0.jpeg)

Mas na abordagem recursiva não existem montes.

![](_page_34_Figure_2.jpeg)

Se não existem montes, como um algoritmo reconhece quais caixas ele deve procurar? Aqui está um exemplo.

![](_page_35_Figure_0.jpeg)

Neste ponto, <sup>a</sup> pilha de chamada se parece com isto:

![](_page_35_Figure_2.jpeg)

O "monte de caixas" é salvo na pilha! Esta é uma pilha com as funções de chamada completadas até <sup>a</sup> metade, cada uma com <sup>a</sup> sua lista de caixas, também completadas até <sup>a</sup> metade, para ser analisadas. Utilizar <sup>a</sup> pilha é conveniente porque você não precisa acompanhar <sup>o</sup> monte de caixas - <sup>a</sup> pilha faz isso para você. Usar <sup>a</sup> pilha é bom, porém, existe um custo: salvar toda essa informação pode ocupar muita memória. Cada uma destas funções de chamada ocupa um pouco de memória, <sup>e</sup> quando a sua pilha está muito cheia

é sinal de que seu computador está salvando informação para muitas chamadas de funções. Para esta situação, você tem duas opções:

- Reescrever seu código utilizando loops.
- Utilizar <sup>o</sup> que chamamos de tail recursion (recursão de cauda). Isto é um tópico avançado em recursão <sup>e</sup> está fora do escopo deste livro. Esta técnica também não é suportada por todas as linguagens de programação.

#### EXERCÍCIO

3.2 Suponha que você acidentalmente escreva uma função recursiva que fique executando infinitamente. Como você viu, seu computador aloca memória na pilha para cada chamada de função. O que acontece com <sup>a</sup> pilha quando <sup>a</sup> função recursiva fica executando infinitamente?

### Recapitulando

![](_page_36_Picture_6.jpeg)

- Recursão é quando uma função chama <sup>a</sup> si mesma.
- 이 Toda função recursiva tem dois casos: <sup>o</sup> caso-base <sup>e</sup> <sup>o</sup> caso recursivo.
- 이 Uma pilha tem duas operações: push <sup>e</sup> pop.
- Todas as chamadas de função vão para <sup>a</sup> pilha de chamada.
- <sup>A</sup> pilha de chamada pode ficar muito grande <sup>e</sup> ocupar muita memória.