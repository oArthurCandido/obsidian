# Introdução <sup>a</sup> algoritmos

![](_page_0_Picture_1.jpeg)

## Neste capítulo

- Você terá acesso ao fundamental para compreender <sup>o</sup> restante do livro.
- Escreverá seu primeiro algoritmo de busca (pesquisa binária).
- Aprenderá como falar sobre <sup>o</sup> tempo de execução de um algoritmo (na notação Big O).
- Será apresentado <sup>a</sup> uma prática comum para projetar algoritmos (recursão).

# Introdução

Um algoritmo é um conjunto de instruções que realizam uma tarefa. Cada trecho de código poderia ser chamado de um algoritmo, mas este livro trata dos trechos mais interessantes. Escolhi os algoritmos apresentados neste livro porque eles são rápidos ou porque resolvem problemas interessantes, ou por ambos os motivos. <sup>A</sup> seguir estão descritos alguns pontos importantes que serão demonstrados.

- O Capítulo 1 aborda pesquisa binária <sup>e</sup> mostra como um algoritmo pode acelerar <sup>o</sup> seu código. Em um dos exemplos, <sup>o</sup> número de etapas necessárias passa de <sup>4</sup> bilhões para 32 etapas!
- 이 Um dispositivo de GPS utiliza algoritmos de grafos (que você aprenderá nos Capítulos 6, 7 <sup>e</sup> 8) para calcular <sup>a</sup> rota mais curta até <sup>o</sup> seu destino.
- Você pode usar <sup>a</sup> programação dinâmica (ver Capítulo 9) para escrever um algoritmo de IA (inteligência artificial) que joga damas.

Em cada caso, descreverei <sup>o</sup> algoritmo <sup>e</sup> apresentarei um exemplo. Em seguida, falarei sobre <sup>o</sup> tempo de execução do algoritmo em notação Big O. Por fim, serão explorados os demais tipos de problemas que poderiam ser solucionados com <sup>o</sup> mesmo algoritmo.

# O que você aprenderá sobre desempenho

Tenho uma boa notícia: uma implementação de cada algoritmo apresentado neste livro provavelmente estará disponível em sua linguagem favorita, portanto você não terá que escrever cada algoritmo! Porém essas implementações serão inúteis caso você não entenda <sup>o</sup> desempenho dos algoritmos. Neste livro, você aprenderá como comparar <sup>o</sup> desempenho de diferentes algoritmos: Você deve utilizar merge sort (ordenação por mistura) ou quicksort (ordenação rápida)? Você deve utilizar um array ou uma lista? A escolha da estrutura de dados pode fazer uma grande diferença.

## O que você aprenderá sobre <sup>a</sup> solução de problemas

Você aprenderá técnicas para resolução de problemas que poderiam estar fora da sua gama de habilidades até agora, como por exemplo:

- Se você gosta de criar jogos, poderá desenvolver um sistema de inteligência artificial (IA) que segue <sup>o</sup> usuário utilizando algoritmos gráficos.
- Você aprenderá <sup>a</sup> criar um sistema de recomendações utilizando os K-vizinhos mais próximos.
- Alguns problemas não podem ser resolvidos em um tempo hábil! A parte deste livro que trata de problemas NP-completos demonstra como identificar estes problemas <sup>e</sup> como criar um algoritmo que forneça uma resposta aproximada.

Ao terminar de ler este livro, provavelmente, você conhecerá alguns dos algoritmos de maior aplicabilidade. Assim, poderá usar os seus conhecimentos para aprender sobre algoritmos mais específicos para IA, bancos de dados etc. Além disso, poderá encarar grandes desafios em seu trabalho

#### O que você precisa saber

Você deverá conhecer álgebra básica antes de iniciar <sup>a</sup> leitura deste livro. Em particular, partindo da função f(x) <sup>=</sup> <sup>x</sup> <sup>×</sup> 2, qual será <sup>o</sup> valor de f(5)? Se respondeu 10, você está pronto.

Além de tudo, este capítulo (e este livro) será compreendido mais facilmente se você conhecer alguma linguagem de programação. Todos os exemplos deste livro foram escritos em Python, assim, caso você não conheça nenhuma linguagem de programação <sup>e</sup> queira aprender uma, escolha Python, pois ela é ótima para iniciantes. Se você conhece alguma outra linguagem, como <sup>a</sup> Ruby, se sairá bem.

# Pesquisa binária

![](_page_3_Picture_0.jpeg)

Vamos supor que você esteja procurando <sup>o</sup> nome de uma pessoa em uma agenda telefônica (que frase antiquada!). O nome começa com K. Você pode começar na primeira página da agenda <sup>e</sup> ir folheando até chegar aos Ks. Porém você provavelmente vai começar pela metade, pois sabe que os Ks estarão mais perto dali.

Ou suponha que esteja procurando uma palavra que começa com O em um dicionário. Novamente, você começa <sup>a</sup> busca pelo meio.

Agora, imagine que você entre no Facebook. Quando faz isso, <sup>o</sup> Facebook precisa verificar que você tem uma conta no site. Logo, ele procura seu nome de usuário em um banco de dados. Digamos que seu usuário seja karlmageddon. O Facebook poderia começar pelos As <sup>e</sup> procurar seu nome - mas faz mais sentido que ele comece <sup>a</sup> busca pelo meio.

![](_page_3_Picture_4.jpeg)

Isto é um problema de busca. E todos estes casos usam um algoritmo para resolvê-lo: pesquisa binária.

A pesquisa binária é um algoritmo. Sua entrada é uma lista ordenada de elementos (explicarei mais tarde por que motivo <sup>a</sup> lista precisa ser ordenada). Se <sup>o</sup> elemento que você está buscando está na lista, <sup>a</sup> pesquisa binária retorna <sup>a</sup> sua localização. Caso contrário, <sup>a</sup> pesquisa binária retorna None.

Por exemplo:

![](_page_4_Picture_2.jpeg)

Procurando empresas em uma agenda com <sup>a</sup> pesquisa binária. Eis um exemplo de como <sup>a</sup> pesquisa binária funciona. Estou pensando em um número entre 1 <sup>e</sup> 100.

$$
123 \cdots 100
$$

Você deve procurar adivinhar <sup>o</sup> meu número com <sup>o</sup> menor número de tentativas possível. A cada tentativa, digo se você chutou muito para cima, muito para baixo ou corretamente.

Digamos que começou tentando assim: 1, 2, 3, 4... Veja como ficaria.

![](_page_5_Picture_0.jpeg)

![](_page_5_Figure_1.jpeg)

Uma tentativa ruim de acertar <sup>o</sup> número.

Isso se chama pesquisa simples (talvez pesquisa estúpida seja um termo melhor). A cada tentativa, você está eliminando apenas um número. Se <sup>o</sup> meu número fosse <sup>o</sup> 99, você precisaria de 99 chances para acertá-lo!

## Uma maneira melhor de buscar

Aqui está uma técnica melhor. Comece com 50.

![](_page_5_Figure_6.jpeg)

Muito baixo, mas você eliminou metade dos números! Agora, você

sabe que os números de <sup>1</sup> <sup>a</sup> <sup>50</sup> são muito baixos. Próximo chute: 75.

![](_page_6_Picture_1.jpeg)

Muito alto, mas novamente você pode cortar metade dos números restantes! Com <sup>a</sup> pesquisa binária, você chuta um número intermediário <sup>e</sup> elimina <sup>a</sup> metade dos números restantes <sup>a</sup> cada vez. O próximo número é <sup>o</sup> 63 (entre 50 <sup>e</sup> 75).

![](_page_6_Picture_3.jpeg)

Isso <sup>é</sup> <sup>a</sup> pesquisa binária. Você acaba de aprender um algoritmo! Aqui está <sup>a</sup> quantidade de números que você pode eliminar <sup>a</sup> cada tentativa.

![](_page_6_Figure_5.jpeg)

Elimine metade dos números <sup>a</sup> cada tentativa com <sup>a</sup> pesquisa binária.

Seja qual for <sup>o</sup> número que eu estiver pensando, você pode adivinhálo em um máximo de sete tentativas - porque <sup>a</sup> pesquisa binária elimina muitas possibilidades!

Suponha que você esteja procurando uma palavra em um dicionário.

O dicionário tem 240.000 palavras. Na pior das hipóteses, de quantas etapas você acha que <sup>a</sup> pesquisa precisaria?

| PESQUISA SIMPLES: | ETAPAS |     |
| ----------------- | ------ | --- |
| PESQUISA BINÁRIA: | ETAPAS |     |

A pesquisa simples poderia levar 240.000 etapas se <sup>a</sup> palavra que você estivesse procurando fosse <sup>a</sup> última do dicionário. <sup>A</sup> cada etapa da pesquisa binária, você elimina <sup>o</sup> número de palavras pela metade até que só reste uma palavra.

![](_page_7_Figure_3.jpeg)

Logo, <sup>a</sup> pesquisa binária levaria apenas 18 etapas - uma grande diferença! De maneira geral, para uma lista de <sup>n</sup> números, <sup>a</sup> pesquisa binária precisa de log,n para retornar <sup>o</sup> valor correto, enquanto <sup>a</sup> necauica cimnles nrecica de n etanae

#### Logaritmos

Você pode não se lembrar de logaritmos, mas provavelmente lembra-se de como calcular exponenciais. A expressão log10 100 basicamente diz: "Quantos 10s conseguimos multiplicar para chegar <sup>a</sup> 100?". A resposta é 2: 10 <sup>x</sup> 10. Então, log10 100 <sup>=</sup> 2. Logaritmos são <sup>o</sup> oposto de exponenciais.

$$
\frac{10^{2} \cdot 100 \leftrightarrow \log_{10}100 = 2}{\frac{10 \cdot 1000 \leftrightarrow \log_{10}1000 = 3}{2^{2} = 8 \leftrightarrow \log_{10}1000 = 3}}
$$

\n

$$
\frac{2^{2} = 16 \leftrightarrow \log_{10}16 = 4}{2^{2} = 32 \leftrightarrow \log_{10}32 = 5}
$$

#### Logaritmos são <sup>o</sup> oposto de exponenciais.

a Neste livro, quando falamos sobre <sup>a</sup> notação Big O (explicada daqui <sup>a</sup> pouco), levamos em conta que log sempre significa log2. Quando você procura um elemento usando pesquisa simples, no pior dos casos, terá de analisar elemento por elemento, passando por todos. Se for uma lista de oito elementos, precisaria checar no máximo oito números. Na pesquisa binária, precisa verificar log <sup>n</sup> elementos para <sup>o</sup> pior dos casos. Para uma lista de oito elementos, log 8 == 3, porque <sup>23</sup> == 8. Então, para uma lista de oito números, precisaria passar por, no máximo, três tentativas. Para uma lista de 1.024 elementos, log 1.024 == 10, porque <sup>24</sup> == 1.024. Logo, para uma lista de 1.024 números, precisaria verificar no máximo dez deles.

#### Nota

Falarei muito sobre logaritmos neste livro. Portanto você deve entender <sup>o</sup> conceito. Se não entender, <sup>a</sup> Khan Academy (khanacademy.org) tem um vídeo legal que esclarece muita coisa.

#### Nota

A pesquisa binária só funciona quando <sup>a</sup> sua lista está ordenada. Por exemplo, os nomes em uma agenda telefônica estão em ordem alfabética, então você pode utilizar <sup>a</sup> pesquisa binária para procurar um nome. O que aconteceria se <sup>a</sup> lista não estivesse ordenada?

Vamos ver como escrever <sup>a</sup> pesquisa binária em Python. <sup>O</sup> exemplo de código que utilizamos aqui usa arrays. Se não sabe como eles funcionam, não se preocupe; abordaremos isso no próximo capítulo. Você só precisa saber que pode armazenar uma sequência de elementos em uma linha de buckets consecutivos que se chama array. Os buckets são numerados <sup>a</sup> partir do 0: <sup>o</sup> primeiro bucket está na posição #0; <sup>o</sup> segundo, em #1; o terceiro, em #2, <sup>e</sup> assim por diante.

A função pesquisa_binaria pega um array ordenado <sup>e</sup> um item. Se <sup>o</sup> item está no array, <sup>a</sup> função retorna <sup>a</sup> sua posição. Dessa maneira, você é capaz de saber por qual ponto do array deve continuar procurando. No começo, <sup>o</sup> código do array segue assim:

```python

baixo = 0
alto = len(lista) -1
```

![](_page_9_Figure_2.jpeg)

A cada tentativa, você testa para <sup>o</sup> elemento central.

```python
meio = (baixo + alto) / 21
chute = lista[meio]
```

meio será arredondado para baixo automaticamente pelo Python se (baixo <sup>+</sup> alto) não for um número par.

Se <sup>o</sup> chute for muito baixo, você atualizará <sup>a</sup> variável baixo proporcionalmente:

```python
if chute < item:
 baixo = meio + 1
```

![](_page_9_Figure_8.jpeg)

E se <sup>o</sup> chute for muito alto, você atualizará <sup>a</sup> variável alto. Aqui está <sup>o</sup> código completo:

```python
def pesquisa_binaria(lista, item):
```

```python
baixo = 0 1
   alto = len(lista)-10
   while baixo <= alto:
       meio = (baixo + alto) / 2
       chute = lista[meio]
       if chute == item:4
           return meio
       if chute > item: 6
           alto = meio - 1
       else: 6
           baixo = meio + 1
    return None
minha_lista = [1, 3, 5, 7,9]
```

```python
print pesquisa_binaria(minha_lista, 3) # => 1
print pesquisa_binaria(minha_lista, -1) # => None
```

baixo <sup>e</sup> alto acompanham <sup>a</sup> parte da lista que você está procurando.

Enquanto ainda não conseguiu chegar <sup>a</sup> um único elemento...

```python
... verifica o elemento central.
```

```python
Acha o item.
```

- O chute foi muito alto.
- O chute foi muito baixo.
- O item não existe.
- Vamos testá-lo!
- Lembre-se, as listas começam no 0. O próximo endereço tem índice 1.
- "None" significa nulo em Python. Ele indica que <sup>o</sup> item não foi encontrado.

## EXERCÍCIOS

- 1.1 Suponha que você tenha uma lista com 128 nomes <sup>e</sup> esteja fazendo uma pesquisa binária. Qual seria <sup>o</sup> número máximo de etapas que você levaria para encontrar <sup>o</sup> nome desejado?
- 1.2 Suponha que você duplique <sup>o</sup> tamanho da lista. Qual seria <sup>o</sup> número máximo de etapas agora?

### Tempo de execução

![](_page_11_Picture_1.jpeg)

Sempre que falo sobre um algoritmo, falo sobre <sup>o</sup> seu tempo de execução. Geralmente, você escolhe <sup>o</sup> algoritmo mais eficiente - caso esteja tentando otimizar tempo <sup>e</sup> espaço.

Voltando à pesquisa simples, quanto tempo se otimiza utilizando-a? Bem, <sup>a</sup> primeira abordagem seria verificar número por número. Se fosse uma lista de 100 números, precisaríamos de 100 tentativas. Se fosse uma lista de 4 bilhões de números, precisaríamos de 4 bilhões de tentativas. Logo, <sup>o</sup> número máximo de tentativas é igual ao tamanho da lista. Isso é chamado de tempo linear.

A pesquisa binária é diferente. Se <sup>a</sup> lista tem 100 itens, precisa-se de, no máximo, sete tentativas. Se tem 4 bilhões, precisa-se de, no máximo, <sup>32</sup> tentativas. Poderoso, não? A pesquisa binária é executada com tempo logarítmico. <sup>A</sup> tabela <sup>a</sup> seguir resume as nossas descobertas até agora.

![](_page_12_Figure_0.jpeg)

Tempo de execução para algoritmos de pesquisa.

# Notação Big O

<sup>A</sup> notação Big <sup>O</sup> é uma notação especial que diz <sup>o</sup> quão rápido <sup>é</sup> um algoritmo. Mas quem liga para isso? Bem, acontece que você frequentemente utilizará <sup>o</sup> algoritmo que outra pessoa fez - <sup>e</sup> quando faz isso, é bom entender <sup>o</sup> quão rápido ou lento <sup>o</sup> algoritmo é. Nesta seção, explicarei como <sup>a</sup> notação Big O funciona <sup>e</sup> fornecerei uma lista com os tempos de execução mais comuns para os algoritmos.

![](_page_12_Picture_4.jpeg)

### Tempo de execução dos algoritmos cresce <sup>a</sup> taxas diferentes

Bob está escrevendo um algoritmo para <sup>a</sup> NASA. <sup>O</sup> algoritmo dele entrará em ação quando <sup>o</sup> foguete estiver prestes <sup>a</sup> pousar na lua, <sup>e</sup> ele <sup>o</sup> ajudará <sup>a</sup> calcular <sup>o</sup> local de pouso.

Este é um exemplo de como <sup>o</sup> tempo de execução de dois algoritmos pode crescer <sup>a</sup> taxas diferentes. Bob está tentando decidir entre <sup>a</sup> pesquisa simples <sup>e</sup> <sup>a</sup> pesquisa binária. O algoritmo precisa ser tão rápido quanto correto. Por um lado, <sup>a</sup> pesquisa binária é mais rápida, <sup>o</sup> que é bom, pois Bob tem apenas <sup>10</sup> segundos para descobrir onde pousar, ou <sup>o</sup> foguete sairá de seu curso. Por outro lado, é mais fácil escrever <sup>a</sup> pesquisa simples, <sup>o</sup> que gera um risco menor de erros. Bob não quer mesmo erros no seu código! Para ser ainda mais cuidadoso, Bob decide cronometrar ambos os algoritmos com uma lista de 100 elementos.

Vamos presumir que leva-se <sup>1</sup> milissegundo para verificar um elemento. Com <sup>a</sup> pesquisa simples, Bob precisa verificar 100 elementos, então <sup>a</sup> busca leva 10 ms para rodar. Em contrapartida, ele precisa verificar apenas sete elementos na pesquisa binária (log2 100 <sup>é</sup> aproximadamente 7), logo, <sup>a</sup> pesquisa binária leva <sup>7</sup> ms para ser executada. Porém, realisticamente falando, <sup>a</sup> lista provavelmente terá em torno de 1 bilhão de elementos. Se <sup>a</sup> lista tiver esse número, quanto tempo <sup>a</sup> pesquisa simples levará para ser executada? <sup>E</sup> <sup>a</sup> pesquisa binária? Tenha certeza de que sabe <sup>a</sup> resposta para essa pergunta antes de continuar lendo.

![](_page_14_Picture_0.jpeg)

Tempo de execução para pesquisa simples vs. pesquisa binária para uma lista de 100 elementos.

Bob executa <sup>a</sup> pesquisa binária com 1 bilhão de elementos <sup>e</sup> leva 30 ms (log2 1.000.000.000 <sup>é</sup> aproximadamente 30). "30 ms!" - ele pensa. "A pesquisa binária <sup>é</sup> quase 15 vezes mais rápida do que <sup>a</sup> pesquisa simples, porque <sup>a</sup> pesquisa simples levou 100 ms para uma lista de 100 elementos <sup>e</sup> <sup>a</sup> pesquisa binária levou só <sup>7</sup> ms. Logo, <sup>a</sup> pesquisa simples levará 30 <sup>×</sup> <sup>15</sup> <sup>=</sup> 450 ms, certo? Bem abaixo do meu limite de <sup>10</sup> segundos." Bob decide utilizar <sup>a</sup> pesquisa simples. Ele fez <sup>a</sup> escolha certa?

Não. Bob está errado. Muito errado. O tempo de execução para <sup>a</sup> pesquisa simples para <sup>1</sup> bilhão de itens é 1 bilhão ms, ou seja, 11 dias! O problema é que <sup>o</sup> tempo de execução da pesquisa simples <sup>e</sup> da pesquisa binária cresce com taxas diferentes.

|                         |     | PESQUISA SIMPLES | PESQUISA BINÁRIA |     |
| ----------------------- | --- | ---------------- | ---------------- | --- |
| 100 ELEMENTOS           |     | 100ms            | 7ms              |     |
| 10000 ELEMENTOS         |     | 10 segundos      | 14 ms            |     |
| 1,000,000,000 ELEMENTOS |     | 11 dias          | 32ms             |     |

#### Tempos de execução crescem com velocidades diferentes! Sendo assim, conforme <sup>o</sup> número de itens cresce, <sup>a</sup> pesquisa binária aumenta só um pouco <sup>o</sup> seu tempo de execução. Já a pesquisa

simples leva muito tempo <sup>a</sup> mais. Logo, conforme <sup>a</sup> lista de números cresce, <sup>a</sup> pesquisa binária se torna muito mais rápida do que <sup>a</sup> pesquisa simples. Bob pensou que <sup>a</sup> pesquisa binária fosse <sup>15</sup> vezes mais rápida que <sup>a</sup> pesquisa simples, mas isso está incorreto. Se <sup>a</sup> lista tem 1 bilhão de itens, <sup>o</sup> tempo de execução é aproximadamente 33 milhões de vezes mais rápido. Por isso, não basta saber quanto tempo um algoritmo leva para ser executado - você precisa saber se <sup>o</sup> tempo de execução aumenta conforme <sup>a</sup> lista aumenta. É aí que <sup>a</sup> notação Big O entra.

A notação Big O informa <sup>o</sup> quão rápido é um algoritmo. Por exemplo, imagine que você tem uma lista de tamanho n. O tempo de execução na notação Big O é O(n). Onde estão os segundos? Eles não existem - <sup>a</sup> notação Big <sup>O</sup> não fornece <sup>o</sup> tempo em segundos. A notação Big O permite que você compare <sup>o</sup> número de operações. Ela informa <sup>o</sup> quão rapidamente um algoritmo cresce.

![](_page_15_Picture_2.jpeg)

Temos outro exemplo disso. <sup>A</sup> pesquisa binária precisa de log <sup>n</sup> operações para verificar uma lista de tamanho n. Qual <sup>é</sup> <sup>o</sup> tempo de execução na notação Big O? É O(log n). De maneira geral, <sup>a</sup> notação Big O é escrita da seguinte forma:

![](_page_15_Picture_4.jpeg)

#### O formato da notação Big O.

Isso fornece <sup>o</sup> número de operações que um algoritmo realiza. É chamado de notação Big O porque coloca-se um "grande O" na frente do número de operações (parece piada, mas <sup>é</sup> verdade!).

Agora, vamos ver alguns exemplos. Veja se consegue descobrir <sup>o</sup> tempo de execução para esses algoritmos.

# Vendo diferentes tempos de execução Big O

Aqui segue um exemplo prático que você pode reproduzir em casa com um pedaço de papel <sup>e</sup> um lápis. Suponha que você tenha que desenhar uma grade com 16 divisões.

![](_page_16_Picture_5.jpeg)

Qual é um bom algoritmo para desenhar essa grade?

#### Algoritmo 1

Uma forma de desenhar essa grade de 16 divisões é desenhar uma divisão de cada vez. Lembre-se, <sup>a</sup> notação Big <sup>O</sup> conta <sup>o</sup> número de operações. Nesse exemplo, desenhar uma divisão é uma operação. Você precisa desenhar 16 divisões. Quantas operações você terá de fazer se desenhar uma divisão por vez?

![](_page_17_Picture_0.jpeg)

Desenhando a grade executando uma divisão por vez. É necessário passar por 16 etapas para desenhar 16 divisões. Qual é o tempo de execução desse algoritmo?

#### **Algoritmo 2**

Tente agora este algoritmo. Dobre o papel.

![](_page_17_Picture_4.jpeg)

Neste exemplo, dobrar o papel uma vez é uma operação. Você fez duas divisões com essa operação!

Dobre o papel de novo, de novo e de novo.

![](_page_17_Picture_7.jpeg)

Desdobre depois de quatro dobras e você terá uma bela grade! A cada dobra, o número de divisões duplica. Você fez 16 divisões com

quatro operações!

![](_page_18_Figure_1.jpeg)

Desenhando uma grade com quatro dobras.

Você pode "desenhar" duas vezes mais divisões a cada dobra, logo, você pode desenhar 16 divisões em quatro etapas. Qual é o tempo de execução para esse algoritmo? Encontre o tempo de execução dos dois algoritmos antes de seguir adiante.

Respostas: O Algoritmo 1 tem tempo de execução $O(n)$ e o algoritmo 2 tem tempo de execução $O(\log n)$ .

## A notação Big O estabelece o tempo de execução para a pior hipótese

Suponha que você utiliza uma pesquisa simples para procurar o nome de uma pessoa em uma agenda telefônica. Você sabe que a pesquisa simples tem tempo de execução $O(n)$ , o que significa que na pior das hipóteses terá verificado cada nome da agenda telefônica. Nesse caso, você está procurando uma pessoa chamada Adit. Essa pessoa é a primeira de sua lista. Logo, não teve de passar por todos os nomes – você a encontrou na primeira tentativa. Esse algoritmo levou o tempo de execução $O(n)$ ? Ou levou $O(1)$ porque encontrou o que queria na primeira tentativa?

A pesquisa simples ainda assim tem tempo de execução $O(n)$ . Nesse caso, você encontrou o que queria instantaneamente. Essa é a melhor das hipóteses. A notação Big O leva em conta a pior das hipóteses. Então pode-se dizer que, para o pior caso, você analisou cada item da lista. Esse é o tempo $O(n)$ . É uma garantia – você sabe, com certeza,

que a pesquisa simples nunca terá tempo de execução mais lento do que $O(n)$ .

#### **Nota**

Além do tempo de execução para o pior dos casos, é importante analisar o tempo de execução para o "caso médio". O pior caso e o caso médio serão discutidos no Capítulo 4.

## Alguns exemplos comuns de tempo de execução **Big O**

Aqui temos cinco tempos de execução Big O que você encontrará bastante, ordenados do mais rápido para o mais lento.

- · O(log n), também conhecido como tempo logarítmico. Exemplo: pesquisa binária.
- $\bullet$ O(n), conhecido como tempo linear. Exemplo: pesquisa simples.
- $\bullet$ O( $n * log n$ ). Exemplo: um algoritmo rápido de ordenação, como a ordenação quicksort (explicada no Capítulo 4).
- $\bullet$ O( $n^2$ ). Exemplo: um algoritmo lento de ordenação, como a ordenação por seleção (explicada no Capítulo 2).
- $\bullet$ O(n!). Exemplo: um algoritmo bastante lento, como o do caixeiroviajante (explicado a seguir!).

Suponha que você esteja desenhando novamente a grade de 16 divisões e você possa escolher cinco algoritmos diferentes para fazer isso. Se escolher o primeiro algoritmo, levará um tempo de execução de O(log n) para desenhar a grade. Você pode fazer dez operações por segundo. Com o tempo de execução O(log n), você levará quatro operações para desenhar uma grade com 16 divisões (log 16 é 4). Logo, levará 0,4 segundos para desenhar a grade. E se tiver que desenhar 1.024 divisões? Levará 1.024 = 10 operações, ou um segundo para desenhar uma grade de 1.024 divisões. Estes números são para o primeiro algoritmo.

O segundo algoritmo é mais lento: ele tem tempo de execução $O(n)$ . Levará 16 operações para desenhar 16 divisões e levará 1.024

operações para desenhar 1.024 divisões. Quanto tempo isso leva em segundos?

Aqui está quanto tempo levaria para desenhar a grade com os algoritmos restantes, do mais rápido ao mais lento:

![](_page_20_Figure_2.jpeg)

Existem outros tempos de execução, mas esses são os cinco mais comuns.

Isso é uma simplificação. Na realidade, você não pode converter um tempo de execução na notação Big O para um número de operações, mas a aproximação é boa o suficiente por enquanto. Voltaremos a falar da notação Big O no Capítulo 4, depois de ter aprendido um pouco mais sobre algoritmos. Por enquanto, os principais pontos são os seguintes:

- A rapidez de um algoritmo não é medida em segundos, mas pelo crescimento do número de operações.
- · Em vez disso, discutimos sobre o quão rapidamente o tempo de execução de um algoritmo aumenta conforme o número de elementos aumenta.
- O tempo de execução em algoritmos é expresso na notação Big O.
- $O(\log n)$ é mais rápido do que $O(n)$ , e $O(\log n)$ fica ainda mais rápido conforme a lista aumenta.

## **EXERCÍCIOS**

Forneça o tempo de execução para cada um dos casos a seguir em termos da notação Big O.

- 1.3 Você tem um nome e deseja encontrar o número de telefone para esse nome em uma agenda telefônica.
- 1.4 Você tem um número de telefone e deseja encontrar o dono dele em uma agenda telefônica. (Dica: Deve procurar pela agenda inteira!)
- 1.5 Você quer ler o número de cada pessoa da agenda telefônica.
- 1.6 Você quer ler os números apenas dos nomes que começam com A. (Isso é complicado! Esse algoritmo envolve conceitos que são abordados mais profundamente no Capítulo 4. Leia a resposta você ficará surpreso!)

### O caixeiro-viajante

Você pode ter lido a última seção e pensado: "De maneira alguma vou executar um algoritmo que tem tempo de execução O(n!)." Bem, deixe-me tentar provar o contrário! Aqui está um exemplo de um algoritmo com um tempo de execução muito ruim. Ele é um problema famoso da ciência da computação, pois seu crescimento é apavorante e algumas pessoas muito inteligentes acreditam que ele possa ser melhorado. Esse algoritmo é chamado de "o problema do caixeiro-viajante".

![](_page_21_Picture_6.jpeg)

Você tem um caixeiro-viajante.

O caixeiro precisa ir a cinco cidades.

![](_page_22_Figure_0.jpeg)

O caixeiro, o qual chamarei de Opus, quer passar por todas as cidades percorrendo uma distância mínima. Podemos enxergar o problema da seguinte forma: analisar cada ordem possível de cidades para visitar.

![](_page_22_Figure_2.jpeg)

Ele soma a distância total e escolhe o caminho de menor distância. Existem 120 permutações para cinco cidades, logo, precisa-se de 120 operações para resolver o problema de cinco cidades. Para seis cidades, precisa-se de 720 operações (ou 720 permutações). Para sete cidades são necessárias 5.050 operações!

| <b>CIDADES</b> | <b>OPERAÇÕES</b>                             |
| -------------- | -------------------------------------------- |
| G              | 720                                          |
|                | 5040                                         |
| გ              | 40320                                        |
|                |                                              |
| 15             | 1307674368000                                |
| $\cdots$<br>Зø | 2,652,52,859,812,191,058,636,308,480,000,000 |

#### O número de operações aumenta drasticamente.

De maneira geral, para _n_ itens, é necessário _n_! (fatorial de _n_) operações para chegar a um resultado. Então, este é o tempo de execução $O(n!)$ ou o tempo fatorial. Esse algoritmo consome muitas operações, exceto para casos envolvendo números pequenos. No entanto, uma vez que lidamos com mais de 100 cidades, é impossível calcular a resposta em função do tempo - o sol entrará em colapso antes.

Esse é um algoritmo terrível! Opus deveria usar outro, não? Mas ele não pode. Esse é um problema sem solução. Não existe um algoritmo mais rápido para esse problema, e as pessoas mais inteligentes acreditam ser _impossível_ melhorá-lo. O melhor que se pode fazer é chegar a uma solução aproximada. Veja o Capítulo 10 para saber mais sobre isso.

Uma observação final: se você é um leitor avançado, leia sobre árvores binárias de busca. No capítulo seguinte, há uma breve descrição do assunto.

# Recapitulando

- A pesquisa binária é muito mais rápida do que a pesquisa simples.
- $\bullet$ O(log _n_) é mais rápido do que O(_n_), e O(log _n_) fica ainda mais rápido conforme os elementos da lista aumentam.

- · A rapidez de um algoritmo não é medida em segundos.
- · O tempo de execução de um algoritmo é medido por meio de seu crescimento.
- · O tempo de execução dos algoritmos é expresso na notação Big O.
