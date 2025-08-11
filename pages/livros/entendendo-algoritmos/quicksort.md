# Quicksort

![](_page_0_Picture_1.jpeg)

## Neste capítulo

- Você irá se deparar, ocasionalmente, com problemas que não podem ser resolvidos com algum algoritmo de seu conhecimento. Porém quando um bom desenvolvedor de algoritmos encontra um destes problemas, ele não desiste. Pelo contrário, ele utiliza uma ampla gama de técnicas para encontrar uma solução, sendo a técnica de dividir para conquistar a primeira que você aprenderá.
- Você conhecerá também o quicksort, um algoritmo de ordenação elegante que é utilizado com frequência. Este algoritmo utiliza a técnica de dividir para conquistar.

No último capítulo você aprendeu tudo sobre recursão. Este capítulo

focará na utilização destas suas novas habilidades aplicadas na resolução de problemas. Para isto, vamos explorar a técnica dividir para conquistar (DC), uma técnica recursiva muito conhecida para resolução de problemas.

Este capítulo trata do ponto principal dos algoritmos, pois um algoritmo que consegue resolver apenas um tipo de problema não é muito útil. Assim, a técnica DC oferece uma nova maneira de pensar sobre a resolução de problemas, tornando-se mais uma alternativa em sua caixa de ferramentas. Quando você se deparar com um problema novo, não terá motivos para ficar desnorteado. Em vez disso, poderá se perguntar "Será que posso resolver este problema usando a técnica de dividir para conquistar?".

Ao final deste capítulo você terá aprendido o seu primeiro algoritmo que utiliza a técnica DC: o quicksort. o algoritmo quicksort é um algoritmo de ordenação muito mais rápido do que o algoritmo de ordenação por seleção (que você aprendeu no Capítulo 2), e é também um bom exemplo de programação elegante.

![](_page_1_Picture_3.jpeg)

## Dividir para conquistar

a técnica DC pode levar algum tempo para ser compreendida. Por isso, veremos três exemplos. Primeiro, mostrarei um exemplo visual. Depois, mostrarei um código de exemplo simples, mas não tão elegante. Por fim, nos aprofundaremos no quicksort, um algoritmo de ordenação que utiliza DC.

Suponha que você seja um fazendeiro que tenha uma área de terra.

![](_page_2_Figure_0.jpeg)

Você quer dividir sua fazenda em porções quadradas iguais, sendo que estas porções devem ter o maior tamanho possível. Assim, nenhuma destas alternativas funcionará.

![](_page_2_Figure_2.jpeg)

Como encontrará o maior tamanho possível para estes quadrados? Usando a estratégia DC! Os algoritmos DC são recursivos. Assim, para resolver um problema utilizando DC, você deve seguir dois passos:

1. Descubra o caso-base, que deve ser o caso mais simples possível.

2. Divida ou diminua o seu problema até que ele se torne o caso-base.

Vamos usar DC para encontrar a solução deste problema. Qual é a maior largura que você pode usar?

Primeiro, descubra o caso-base. Seria mais fácil solucionar este problema se um dos lados fosse múltiplo do outro.

![](_page_3_Figure_0.jpeg)

Suponha que um dos lados tenha 25 metros (m) e o outro tenha 50. Assim, o maior quadrado que você pode ter mede <sup>25</sup> <sup>m</sup> <sup>x</sup> 25 m. Você precisa de dois destes quadrados para dividir a porção de terra.

Agora você precisa descobrir o caso recursivo, e é aqui que a estratégia DC entra em ação. Seguindo a estratégia DC, a cada recursão você deve reduzir o seu problema. Então, como reduzir este problema? Vamos começar identificando os maiores quadrados que você pode utilizar.

![](_page_3_Figure_3.jpeg)

Você pode posicionar dois quadrados de 640 <sup>×</sup> 640 na fazenda e ainda continuará com uma porção de terra para ser dividida. Este é o momento "Aha!". Você ainda tem um segmento da fazenda que deve ser dividido. Por que não aplica este mesmo algoritmo neste segmento?

![](_page_4_Figure_0.jpeg)

Você iniciou com uma porção de terra medindo 1.680 <sup>×</sup> 640 que deveria ser dividida. Porém agora você precisa dividir um segmento menor, que mede 640 <sup>x</sup> 400. Caso encontre o maior quadrado que divide este segmento, ele será o maior quadrado que dividirá toda a fazenda. Você acabou de reduzir um problema de divisão de uma fazenda medindo 1.680 <sup>×</sup> 640 para um problema de divisão de uma área medindo 640 <sup>×</sup> 4001

### Algoritmo de Euclides

"Caso você encontre o maior quadrado que divide este segmento, ele será o maior quadrado que irá dividir toda a fazenda." Se não parece óbvio o motivo de esta afirmação ser verdadeira, não se preocupe, ela realmente não é trivial. Infelizmente, a prova desta afirmação é um pouco longa para ser incluída neste livro, então você terá de confiar em mim. Caso você queira entender a prova, procure o Algoritmo de Euclides. a Khan Academy deu uma boa explicação, disponível aqui: https://www.khanacademy.org/computing/computerscience/cryptography/modarithmetic/a/the-euclidean-algorithm.

![](_page_4_Figure_4.jpeg)

Vamos aplicar o mesmo algoritmo novamente. Começando com

uma fazenda medindo 640 <sup>x</sup> 400 m, o maior quadrado que você pode ter mede 400 <sup>×</sup> 400 m.

E isso deixa você com um segmento menor do que 400 <sup>×</sup> 240 m.

![](_page_5_Figure_2.jpeg)

Você pode desenhar um quadrado neste segmento que lhe deixa com um segmento ainda menor, de <sup>240</sup> <sup>x</sup> 160 m.

![](_page_5_Figure_4.jpeg)

Então, você desenha um quadrado neste segmento para ter um segmento ainda menor.

![](_page_5_Figure_6.jpeg)

Ei, você acabou de descobrir o caso-base, pois 80 é um múltiplo de 160. Se dividir este segmento em quadrados, não haverá segmentos sobrando!

![](_page_6_Picture_0.jpeg)

Assim, para a fazenda original, o maior quadrado que você pode utilizar é 80 <sup>×</sup> 80 m.

![](_page_6_Figure_2.jpeg)

Para recapitular, estes são os passos para aplicação da estratégia DC:

- 1. Descubra o caso-base, que deve ser o caso mais simples possível.
- 2. Descubra como reduzir o seu problema para que ele se torne o caso-base.

O algoritmo DC não é um simples algoritmo que você aplica em um problema, mas sim uma maneira de pensar sobre o problema. Vamos ver mais um exemplo.

<sup>246</sup> Você tem um array de números.

Você deve somar todos os números e retornar o valor total. Isto é simples de ser feito com um loop:

```python
def soma(lista):
 total = 0
  for x in lista:
   total += x
 return total
print soma([1, 2, 3, 4])
```

Mas como isso poderia ser feito com uma função recursiva?

Passo 1: Descubra o caso-base. Qual é o array mais simples que você pode obter? Pense sobre o caso mais simples: se você tiver um array com 0 ou com 1 elemento, será muito simples calcular a soma.

CASO-BASE

$$
\begin{cases} 1 & \text{otherwise} = 50 \text{ mA} \leq \cancel{0} \\ \boxed{7} & \text{1} \text{ ELEMENTOS} = 50 \text{ mA} \leq \cancel{7} \\ \boxed{7} & \text{1} \end{cases}
$$

Logo, esse é o caso-base.

Passo 2: Você deve chegar mais perto de um array vazio a cada recursão. Como pode reduzir o tamanho do seu problema? Esta é uma alternativa:

$$
50MA(\boxed{2|4|6}) = 12
$$

A soma deste array é igual a isto:

$$
(2 + 50MA)(146) = 2 + 10 = 12
$$

Em ambos os casos o resultado é 12. Porém, na segunda versão, você está usando um array menor na função soma. Ou seja, você está diminuindo o tamanho do problemа!

A sua função soma poderia funcionar assim:

![](_page_8_Figure_0.jpeg)

Aqui está um exemplo da função na prática:

![](_page_8_Figure_2.jpeg)

Lembre-se de que a recursão tem memória dos estados anteriores.

![](_page_9_Figure_0.jpeg)

#### Dica

Quando estiver escrevendo uma função de recursão que envolva um array, caso-base será, muitas vezes, um array vazio ou um array com apenas um elemento. Se estiver com problemas, use este caso como base. 이

#### Uma espiada em programação funcional

"Por que eu faria isto recursivamente quando é mais simples fazer através de um loop?" é o que você pode estar pensando. Bem, estamos dando uma espiada em programação funcional! Linguagens de programação funcional, como Haskell, não contêm loops, e isso faz com que você tenha de usar funções como essa. Se você compreende bem o que é recursão, linguagens funcionais serão simples de entender. Por exemplo, você escreveria uma função somatória em Haskell assim:

soma [] <sup>=</sup> 01 soma (x:xs) <sup>=</sup><sup>x</sup> <sup>+</sup> (soma xs)

#### Caso-base.

#### Caso recursivo.

Perceba que parece que você tem duas definições para a função. a primeira definição é executada quando você alcança o caso-base, e a segunda é executada no caso recursivo. Você também pode escrever essa função em Haskell usando um operador condicional if (se, em português):

```python
soma arr = if arr == []
           then 0
           else (head arr) + (soma (tail arr))
```

Porém a primeira definição é mais simples de ler. Como Haskell se baseia fortemente em recursão, essa linguagem inclui vários detalhes como este para tornar a recursão mais simples. Se você gosta de recursão ou caso você esteja interessado em aprender uma nova linguagem de programação, dê uma olhada em Haskell.

### EXERCÍCIOS

![](_page_10_Picture_3.jpeg)

- 4.1 Escreva o código para a função soma, vista anteriormente.
- 4.2 Escreva uma função recursiva que conte o número de itens em uma lista.
- 4.3 Encontre o valor mais alto em uma lista.
- 4.4 Você se lembra da pesquisa binária do Capítulo 1? Ela também é um algoritmo do tipo dividir para conquistar. Você consegue determinar o caso-base e o caso recursivo para a pesquisa binária?

# Quicksort

![](_page_11_Picture_0.jpeg)

O quicksort é um algoritmo de ordenação. Este algoritmo é muito mais rápido do que a ordenação por seleção e é muito utilizado na prática. Por exemplo, a biblioteca-padrão da linguagem <sup>C</sup> tem uma função chamada qsort, que é uma implementação do quicksort. O algoritmo quicksort também utiliza a estratégia DC.

Vamos usar o quicksort para ordenar um array. Qual é o array mais simples que um algoritmo de ordenação pode ordenar (lembre-se da minha dica na seção anterior)? Bem, alguns arrays não precisam nem ser ordenados.

![](_page_11_Figure_3.jpeg)

Arrays vazios ou arrays com apenas um elemento serão o caso-base. Você pode apenas retornar esses arrays como eles estão, visto que não há nada para ordenar:

```python
def quicksort(array):
```

```python
if len(array) < 2:
  return array
```

Vamos dar uma olhada em arrays maiores. Um array com dois elementos também é muito simples de ordenar.

![](_page_12_Figure_2.jpeg)

E um array com três elementos?

![](_page_12_Figure_4.jpeg)

Lembre-se, você está usando DC. Sendo assim, quer quebrar este array até que você chegue ao caso-base. Portanto o funcionamento do quicksort segue esta lógica: primeiro, escolha um elemento do array. Esse elemento será chamado de pivô.

![](_page_12_Picture_6.jpeg)

Falaremos sobre como escolher um bom pivô mais tarde. Neste momento, vamos utilizar o primeiro item do array como pivô.

Assim, encontre os elementos que são menores do que o pivô e também os elementos que são maiores.

![](_page_13_Figure_0.jpeg)

Isso é chamado de particionamento. Desse modo, você tem:

- Um subarray contendo todos os números menores do que o pivô
- O pivô
- Um subarray contendo todos os números maiores do que o pivô

Os dois subarrays não estão ordenados, apenas particionados. Porém, se eles estivessem ordenados, a ordenação do array contendo todos os elementos seria simples.

$$
\boxed{1\phi\,15}\,\big\langle\overline{33}\big\rangle\,[\ \, ]
$$

Caso os subarrays estejam ordenados, poderá combiná-los desta forma: array esquerdo <sup>+</sup> pivô <sup>+</sup> array direito. Consequentemente, terá um array ordenado. Neste caso, temos [10, 15] <sup>+</sup> [33] <sup>+</sup> [] <sup>=</sup> [10, 15, 33], que é um array ordenado.

Como você pode ordenar os subarrays? Bem, o caso-base do quicksort consegue ordenar arrays de dois elementos (o subarray esquerdo) e também arrays vazios (o subarray direito). Assim, se utilizar o quicksort em ambos os subarrays e então combinar os resultados, terá um array ordenado!

```python
quicksort([15, 10]) + [33] + quicksort([])
> [10, 15, 33]
              0
```

Um array ordenado

Isto funcionará com qualquer pivô. Suponha que você tenha

escolhido o número 15 como pivô.

![](_page_14_Picture_1.jpeg)

Ambos os subarrays contêm apenas um elemento, e você já sabe como ordenar este tipo de array. Logo, já sabe como ordenar um array de três elementos. Estes são os passos:

- 1. Escolha um pivô.
- 2. Particione o array em dois subarrays, separando-os entre elementos menores do que o pivô e elementos maiores do que o pivô.
- 3. Execute o quicksort recursivamente em ambos os subarrays.
- E quanto a um array de quatro elementos?

$$
33 | 16 | 15 | 7
$$

Suponha que, desta vez, você escolheu o número 33 como pivô.

$$
1\phi \mid 15 \mid 7 \mid \text{33} \rangle \quad [ \quad ]
$$

O array da esquerda contém trés elementos, e você já sabe como ordenar arrays de três elementos: executando o quicksort recursivamente.

$$
\frac{\boxed{1\phi}\boxed{15}}{4}
$$

\n

$$
\boxed{7}
$$

\n

$$
\boxed{1\phi}\boxed{15}
$$

Agora pode ordenar arrays de quatro elementos. Sabendo ordenar

arrays com quatro elementos, você consegue ordenar arrays com cinco elementos. Como? Suponha que tenha um array com cinco elementos.

![](_page_15_Picture_1.jpeg)

Estas são todas as maneiras pelas quais você pode particionar este array, dependendo do pivô que escolher.

![](_page_15_Figure_3.jpeg)

Perceba que todos estes subarrays têm entre <sup>0</sup> a <sup>4</sup> elementos, e você já sabe como ordenar arrays de <sup>0</sup> a <sup>4</sup> elementos usando o quicksort! Logo, não importa o pivô que você escolher, pois você poderá executar o quicksort recursivamente em ambos os subarrays.

Por exemplo, imagine que você escolheu o número 3 como pivô. Você executa o quicksort nos subarrays.

![](_page_16_Figure_0.jpeg)

Os subarrays são ordenados e então você os combina, obtendo um array ordenado. Isto funcionará mesmo que escolha o número 5 como pivÔ.

![](_page_16_Figure_2.jpeg)

Isso funcionará, na verdade, com qualquer elemento como pivô. Agora você já consegue ordenar um array de cinco elementos. Usando a mesma lógica, conseguirá ordenar um array de seis elementos ou mais

### Provas por indução

Você acabou de observar alguns exemplos de provas por indução. Estas provas representam uma maneira de mostrar que o seu algoritmo funciona. Cada prova por indução segue dois passos: o caso-base e o caso indutivo. Isso não soa familiar? Imagine que eu queira provar que sou capaz de subir até o topo de uma escada. No caso indutivo, se minhas pernas estiverem em um degrau, poderei colocá-las no próximo degrau. Assim, se estiver no degrau 2, poderei subir para o degrau 3. Este é o caso indutivo. Já para o caso-base, falarei que minhas pernas estão no degrau <sup>1</sup> e que, portanto, sou capaz de subir a escada inteira, um degrau de cada vez.

Você usa uma lógica semelhante para o quicksort. No caso-base, mostrei que o algoritmo funciona para o caso-base: arrays de tamanho <sup>0</sup> e 1. No caso indutivo, mostrei que, da mesma forma que o quicksort funciona para um array de tamanho 1, ele também funcionará para arrays de tamanho 2. Assim como ele funciona para arrays de dois elementos, também funcionará para arrays de três elementos, e assim por diante. Dessa forma, podemos dizer que o quicksort funciona para todos os tamanhos de array. Não me aprofundarei em provas por indução, mas elas são divertidas e andam lado a lado com a estratégia DC.

![](_page_17_Picture_1.jpeg)

Aqui está o código para o quicksort:

```python
def quicksort(array):
 if len(aггay) < 2:
   return array 0
 else:
   pivo = array [0]
   menores = [i for i in array[1:] if i <= pivo] 3
   maiores = [i for i in array[1:] if i > pivo]
   return quicksort(menores) + [pivo] + quicksort(maiores)
```

print quicksort([10, 5, 2, 3])

Base: arrays com 0 ou<sup>1</sup> elemento já estão "ordenados".

Caso recursivo.

Subarray de todos os elementos menores do que o pivô.

Subarray de todos os elementos maiores do que o pivô.

# Notação Big O revisada

O algoritmo quicksort é único, pois sua velocidade depende do pivô escolhido. Antes de falarmos sobre quicksort, vamos analisar novamente os tempos de execução Big O mais comuns.

![](_page_18_Figure_1.jpeg)

Estimativas baseadas em um computador lento que realiza dez operações por segundo.

Os exemplos de tempos de execução contidos nestes gráficos são estimativas para um caso em que você executa dez operações por segundo. Estes gráficos não são precisos, mas servem apenas para fornecer um exemplo do quão diferente são os tempos de execução. Na realidade, o seu computador é capaz de executar muito mais do que dez operações por segundo.

Cada tempo de execução contém um algoritmo de exemplo anexo. Dê uma olhada no algoritmo de ordenação por seleção, que aprendeu no Capítulo 2. o seu tempo de execução é O(n²); é bastante lento.

Há outro algoritmo de ordenação chamado merge sort, que tem tempo de execução O(n log n), o que é muito mais rápido! O algoritmo quicksort é um caso complicado. Na pior situação, o quicksort tem tempo de execução O(n²).

Ele é tão lento quanto a ordenação por seleção! Porém este é o pior caso possível. No caso médio, o quicksort tem tempo de execução O(n log n). e agora você pode estar se perguntando:

- O que significa pior caso e caso médio?
- Se o quicksort tem tempo de execução médio O(n log n), <sup>е</sup> <sup>о</sup>

merge sort tem tempo de execução O(n log n) sempre, por que não utilizar o merge sort? Não seria mais rápido?

## Merge sort versus quicksort

Suponha que você tenha esta simples função que imprime na tela todos os itens de uma lista:

```python
def imprime_itens(lista):
  for item in lista:
    print item
```

Esta função analisa cada item da lista e o imprime. Como esta função passa por toda a lista uma vez, ela tem tempo de execução O(n). Agora, imagine que você modificou esta função para que ela aguarde um segundo antes de imprimir um item:

```python
from time import sleep
def imprime_itens2(lista):
  for item in lista:
   sleep(1)
   print item
```

Antes de imprimir um item, ela espera por um segundo. Suponha que você imprima uma lista contendo cinco itens utilizando ambas as funções.

```python
2468 10
     ↓
imprime_itens: 24681
imprime_itens 2: <AGUARDE 2 <AGUARDE) 4 <AGUARDE) 6 KAGUARDE) 8 <AGUARDE) 10
```

Ambas as funções passam por toda a lista uma vez, portanto elas têm tempo de execução O(n). Qual das duas você acha que será mais rápida na prática? Acho que a função imprime_itens será muito mais rápida, visto que ela não aguarda um segundo antes de imprimir cada item. Assim, mesmo que ambas as funções tenham o mesmo tempo de execução na notação Big O, a função imprime_itens acaba

sendo mais rápida na prática. Quando você escreve algo na notação Big O, como O(n), por exemplo, está querendo dizer isso.

![](_page_20_Picture_1.jpeg)

A letra <sup>c</sup> é uma quantidade determinada de tempo que o seu algoritmo leva para ser executado. Ela é chamada de constante. Pode ser, por exemplo, <sup>10</sup> milissegundos \* <sup>n</sup> para a função imprime_itens contra <sup>1</sup> segundo \*n para a função imprime_itens2.

Normalmente você ignora a constante, pois, caso dois algoritmos tenham tempos de execução Big O diferentes, a constante não importará. Vamos usar a pesquisa binária e a pesquisa simples como exemplos deste fato. Imagine que ambos os algoritmos contenham estas constantes.

$$
\frac{10^{5} \text{ms} \cdot \text{m}}{\text{PESquisa stmPLES}} \qquad \frac{1 \text{seq} \cdot \text{K log n}}{\text{PESquisa stmÁrta}}
$$

Você pode pensar "Nossa! A pesquisa simples contém uma constante de 10 milissegundos, enquanto a pesquisa binária contém uma constante de um segundo. A pesquisa simples é muito mais rápida!". Agora, suponha que esteja realizando uma busca em uma lista com 4 bilhões de elementos. A seguir, pode visualizar os tempos de execução desta busca.

PESQUISA

\n

$$
10 \text{ ms} \times 4 \text{ BILHÕES} = 463 \text{ Jias}
$$

\nPESQUISA

\n

$$
1 \text{ seg} \times 32 = 32 \text{ segundos}
$$

Como você pode ver, a pesquisa binária continua sendo muito mais

rápida. a constante não causou diferença alguma no final das contas.

Porém, às vezes, a constante pode fazer diferença. O quicksort, comparado ao merge sort, é um exemplo disso. o quicksort tem uma constante menor do que o merge sort. Assim, como ambos têm tempo de execução O(n log n), o quicksort acaba sendo mais rápido. Além disso, o quicksort é mais rápido, na prática, pois ele funciona mais vezes no caso médio do que no pior caso.

e agora você pode estar se perguntando: o que é o caso médio e o que é o pior caso?

## Caso médio versus pior caso

O desempenho do quicksort depende bastante da escolha do pivô. Imagine que você sempre escolha o primeiro elemento como pivó e que você execute o quicksort em um array que já esteja ordenado. O quicksort não faz uma checagem para conferir se o array já está ordenado. Logo, ele tentará ordenar o array mesmo assim.

![](_page_22_Figure_0.jpeg)

Perceba como você não está dividindo o array em duas metades. Em vez disso, um dos subarrays está sempre vazio, o que faz com que a pilha de chamada seja sempre muito longa. Agora, imagine que você sempre escolha o elemento central do array como pivô. Perceba como a pilha de chamada é menor.

![](_page_23_Figure_0.jpeg)

A pilha de chamada é muito menor! Isso acontece porque você divide o array na metade, o que faz com que você não precise fazer tantas execuções recursivas. Assim, você chega ao caso-base e a pilha de chamada é consideravelmente menor.

O primeiro exemplo que você viu representa o pior caso, enquanto o segundo exemplo representa o melhor caso. No pior caso, o tamanho da pilha é O(n). No melhor caso, o tamanho da pilha é O(log n).

Agora, observe o primeiro nível da pilha. Você escolhe um elemento como o pivô e os demais elementos são divididos em dois subarrays. Assim, você tem de passar por todos os elementos no array. Logo, esta primeira execução tem tempo de execução O(n). Neste nível da pilha você passa por todos os elementos do array. Porém em todos os níveis da pilha de chamada você passará por O(n) elementos.

![](_page_24_Figure_0.jpeg)

Mesmo que você particione o array de forma diferente, continuará passando por O(n) elementos a cada execução.

![](_page_25_Figure_0.jpeg)

Dessa forma, cada nível tem tempo de execução O(n).

![](_page_25_Figure_2.jpeg)

Neste exemplo, existem O(log n) níveis (a maneira mais técnica de dizer isso é "O peso da pilha de chamada [ou pilha de execução] é O(log n)). Cada nível tem tempo de execução O(n). Além disso, o algoritmo como um todo tem tempo de execução O(n) \* O(log n) O(n log n). Este é o melhor caso. =

No pior caso, existem O(n) níveis. Portanto o algoritmo tem tempo de execução O(n) \* O(n) <sup>=</sup> O(n²).

Adivinhe? O melhor caso também é o caso médio. Se você sempre escolher um elemento aleatório do array como pivô, o quicksort será completado com tempo de execução médio O(n log n). O algoritmo quicksort é um dos mais rápidos algoritmos de ordenação que

existem, sendo um ótimo exemplo de DC.

### EXERCÍCIOS

Quanto tempo levaria, em notação Big O, para completar cada uma destas operações?

- 4.5 Imprimir o valor de cada elemento em um array.
- 4.6 Duplicar o valor de cada elemento em um array.
- 4.7 Duplicar o valor apenas do primeiro elemento do array.
- 4.8 Criar uma tabela de multiplicação com todos os elementos do array. Assim, caso o seu array seja [2, 3, 7, 8, 10], você primeiro multiplicará cada elemento por 2. Depois, multiplicará cada elemento por <sup>3</sup> e então por 7, e assim por diante.

# Recapitulando

- A estratégia DC funciona por meio da divisão do problema em problemas menores. Se você estiver utilizando DC em uma lista, o caso-base provavelmente será um array vazio ou um array com apenas um elemento.
- Se você estiver implementando o quicksort, escolha um elemento aleatório como o pivô. o tempo de execução médio do quicksort é O(n log n)!
- a constante, na notação Big O, pode ser relevante em alguns casos. Esta é a razão pela qual o quicksort é mais rápido do que o merge sort.
- A constante dificilmente será relevante na comparação entre pesquisa simples e pesquisa binária, pois O(log n) é muito mais rápido do que O(n) quando sua lista é grande.

![](_page_27_Picture_0.jpeg)
