# Recursão

  

![](_page_0_Picture_1.jpeg)

  

## Neste capítulo

  

- Você aprenderá recursão. A recursão é uma técnica de programação utilizada em muitos algoritmos. É um assunto importante para <sup>a</sup> compreensão dos capítulos seguintes.

- Você aprenderá como separar um problema em caso-base <sup>e</sup> caso recursivo. A estratégia dividir para conquistar (Capítulo 4) usa este conceito simples para resolver problemas complicados.

  

Estou animado com este capítulo porque trata de recursão, uma maneira elegante de solucionar problemas. A recursão é um dos meus tópicos favoritos, mas ela é polêmica. As pessoas ou <sup>a</sup> amam ou a odeiam, ou elas a odeiam até que aprendam a amá-la alguns anos

  

depois. Eu estava nessa terceira situação. Para facilitar as coisas, tenho um conselho:

  

- Este capítulo apresenta vários exemplos de códigos. Execute-os para ver como eles funcionam.

- <sup>이</sup> Falarei sobre funções recursivas. Pelo menos uma vez, analise uma função recursiva com um papel <sup>e</sup> uma caneta, algo do tipo "vamos ver, passo <sup>o</sup> número 5 para <sup>a</sup> função fatorial, <sup>e</sup> então retorno cinco vezes passando <sup>o</sup> número <sup>4</sup> para fatorial, <sup>o</sup> que me dá...", <sup>e</sup> assim por diante. Analisar uma função dessa forma lhe ajudará <sup>a</sup> entender como funcionam as funções recursivas.

  

Este capítulo inclui muitos pseudocódigos. Pseudocódigos são uma descrição de alto nível de um problema em formato de código. É escrito como um código, mas utiliza linguagem mais próxima da humana.

  

# Recursão

  

Suponha que você esteja vasculhando <sup>o</sup> porão de sua avó <sup>e</sup> encontre uma misteriosa mala trancada.

  

![](_page_1_Picture_6.jpeg)

  

A sua avó diz que <sup>a</sup> chave para <sup>a</sup> mala provavelmente está em uma caixa.

  

![](_page_2_Figure_0.jpeg)

  

Esta caixa contém mais caixas com mais caixas dentro delas. A chave está em alguma destas caixas. Qual é o seu algoritmo para procurála? Pense nisso antes de continuar <sup>a</sup> leitura.

  

Aqui está uma abordagem.

  

![](_page_3_Figure_0.jpeg)

  

- 1.Monte uma pilha com as caixas que serão analisadas.

- 2. Pegue uma caixa <sup>e</sup> olhe <sup>o</sup> que tem dentro dela.

- 3. Se você encontrar outra caixa dentro dela, adicione-a <sup>a</sup> um novo monte para ser verificada mais tarde.

- 4. Se você encontrar uma chave, terminou!

- 5. Repita.

  

Aqui está outra abordagem.

  

![](_page_3_Figure_7.jpeg)

  

1.Olhe o que tem dentro da caixa.

  

2. Se encontrar outra caixa, volte ao passo 1.

  

3. Se encontrar <sup>a</sup> chave, terminou!

  

Qual abordagem lhe parece mais fácil? A primeira abordagem utiliza um loop while (enquanto, em português). Enquanto <sup>o</sup> monte existir, pegue uma caixa <sup>e</sup> olheo<sup>o</sup> que tem dentro dela:

  

```python

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

  

```python

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

  

## Caso-base <sup>e</sup> caso recursivo

  

![](_page_5_Picture_1.jpeg)

  

Devido ao fato de <sup>a</sup> função recursiva chamar <sup>a</sup> si mesma, é mais fácil escrevê-la erroneamente <sup>e</sup> acabar em um loop infinito. Por exemplo, suponha que você escreva uma função que imprima uma contagem regressiva, como esta:

  

> 3...2...1

  

Você pode escrever isso de maneira recursiva fazendo <sup>o</sup> seguinte:

  

```python

def regressiva(i):

print i

regressiva(i-1)

```

  

Escreva este código <sup>e</sup> execute-o. Você perceberá um problema: essa função ficará executando para sempre!

  

![](_page_5_Figure_7.jpeg)

  

Loop infinito.

  

<sup>&</sup>gt; 3...2...1...0..-1...-2...

  

(Pressione Ctrl-C para interromper <sup>o</sup> seu script.)

  

Quando você escreve uma função recursiva, deve informar quando a

  

recursão deve parar. E por isso que toda função recursiva tem duas partes: <sup>o</sup> caso-base <sup>e</sup> <sup>o</sup> caso recursivo. <sup>O</sup> caso recursivo é quando <sup>a</sup> função chama <sup>a</sup> si mesma. O caso-base é quando <sup>a</sup> função não chama <sup>a</sup> si mesma novamente, de forma que <sup>o</sup> programa não se torna um loop infinito.

  

Vamos adicionar <sup>o</sup> caso-base à função de contagem regressiva:

  

```python

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

  

![](_page_6_Figure_6.jpeg)

  

# A pilha

  

![](_page_6_Picture_8.jpeg)

  

Esta seção aborda <sup>a</sup> pilha de chamada (call stack). Isto é um conceito importante em programação <sup>e</sup> indispensável para entender <sup>a</sup> recursão.

  

Suponha que você esteja fazendo um churrasco para os seus amigos. Você tem uma lista de afazeres em forma de uma pilha de notas adesivas.

  

![](_page_7_Picture_2.jpeg)

  

Você se lembra de que, quando falamos de arrays <sup>e</sup> listas, também havia uma lista de afazeres? Podia adicionar itens em qualquer lugar da lista ou remover itens aleatórios. A pilha de notas adesivas é bem mais simples. Quando você insere um item, ele é colocado no topo da pilha. Quando você lê um item, lê apenas <sup>o</sup> item do topo da pilha <sup>e</sup> ele é retirado da lista. Logo, sua lista de afazeres contém apenas duas ações: push (inserir) <sup>e</sup> pop (remover <sup>e</sup> ler).

  

![](_page_7_Picture_4.jpeg)

  

Vamos ver como isso funciona na prática.

  

![](_page_8_Figure_0.jpeg)

  

Esta estrutura de dados é chamada de pilha. A pilha é uma estrutura de dados simples. Você <sup>a</sup> tem usado esse tempo todo sem perceber!

  

# A pilha de chamada

  

Seu computador usa uma pilha interna denominada pilha de chamada. Vamos ver isto na prática. Aqui está um exemplo simples:

  

```python

def sauda(nome):

print "Olá, " + nome + "!"

sauda2(nome)

print "preparando para dizer tchau..."

tchau()

```

  

Esta função te cumprimenta <sup>e</sup> chama outras duas funções:

  

```python

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

  

![](_page_9_Picture_1.jpeg)

  

Agora, vamos usar <sup>a</sup> memória. A variável nome é setada para "maggie". Isso precisa ser salvo.

  

![](_page_9_Figure_3.jpeg)

  

Cada vez que você faz uma chamada de função, seu computador salva na memória os valores para todas as variáveis. Depois disso, imprime olá, maggie!. Então, chama sauda2("maggie").

  

![](_page_9_Figure_5.jpeg)

  

Novamente, seu computador aloca uma caixa de memória para essa chamada de função.

  

Seu computador está usando uma pilha para estas caixas. A segunda caixa é adicionada em cima da primeira. Você imprime "como vai maggie?". Então, retorna da chamada de função. Quando isso acontece, <sup>a</sup> caixa do topo da pilha é retirada.

  

![](_page_9_Picture_8.jpeg)

  

Agora, <sup>a</sup> caixa do topo da pilha aloca os valores da função sauda, <sup>o</sup> que significa que você retornou à função sauda. Quando você

  

chamou <sup>a</sup> função sauda2, <sup>a</sup> função sauda ficou parcialmente completa. Esta é <sup>a</sup> grande ideia por trás desta seção: quando você chama uma função <sup>a</sup> partir de outra, <sup>a</sup> chamada de função fica pausada em um estado parcialmente completo. Todos os valores das variáveis para aquela função ainda estão armazenados na memória. Agora que você já utilizou <sup>a</sup> função sauda2, você está de volta na função sauda <sup>e</sup> pode continuar de onde parou. Primeiro, imprime "preparando para dizer tchau..."e então chama <sup>a</sup> função tchau.

  

![](_page_10_Picture_1.jpeg)

  

Uma caixa para esta função é adicionada ao topo da pilha. Quando você imprimir ok, tchau!, retornará da chamada de função.

  

![](_page_10_Picture_3.jpeg)

  

Agora, você está de volta à função sauda. Não há nada mais <sup>a</sup> ser feito, <sup>e</sup> você pode sair da função sauda também. Essa pilha usada para guardar as variáveis de múltiplas funções é denominada pilha de chamada.

  

### EXERCÍCIOS

  

3.1 Suponha que eu forneça uma pilha de chamada como esta:

  

![](_page_10_Picture_7.jpeg)

  

- Quais informações você pode retirar baseando-se apenas nesta pilha de chamada?

- Agora, vamos ver esta pilha de chamada sendo executada com uma função recursiva.

  

# A pilha de chamada com recursão

  

As funções recursivas também utilizam <sup>a</sup> pilha de chamada! Vamos analisar isto na prática com <sup>a</sup> função fat (fatorial). fat(5) é escrita como 5! <sup>e</sup> é definida da seguinte forma: 5! <sup>=</sup> 5\*4\*3\*2 \* 1. De forma semelhante, fat(3) é3\*2 \* 1. Aqui está uma função recursiva para calcular <sup>a</sup> fatorial de um número:

  

```python

def fat(x):

if X == 1:

return 1

else:

return x * fat(x-1)

```

  

Agora, você chama <sup>a</sup> função fat(3). Vamos analisar esta pilha de chamada linha por linha <sup>e</sup> ver como ela se altera. Lembre-se, <sup>a</sup> caixa mais próxima ao topo lhe diz em qual chamada <sup>a</sup> função fat se encontra atualmente.

  

![](_page_12_Figure_0.jpeg)

  

![](_page_13_Figure_0.jpeg)

  

Repare que cada chamada para <sup>a</sup> função fat tem seu próprio valor de x. Você não consegue acessar <sup>a</sup> mesma função com outro valor de X.

  

A pilha tem um papel importante na recursão. No primeiro exemplo, mostrei duas abordagens para encontrar <sup>a</sup> chave. Aqui está <sup>a</sup> primeira.

  

![](_page_13_Figure_3.jpeg)

  

Desta forma, você fez um monte com caixas para analisar, então sabe quais caixas você ainda precisa abrir.

  

![](_page_14_Figure_0.jpeg)

  

Mas na abordagem recursiva não existem montes.

  

![](_page_14_Figure_2.jpeg)

  

Se não existem montes, como um algoritmo reconhece quais caixas ele deve procurar? Aqui está um exemplo.

  

![](_page_15_Figure_0.jpeg)

  

Neste ponto, <sup>a</sup> pilha de chamada se parece com isto:

  

![](_page_15_Figure_2.jpeg)

  

O "monte de caixas" é salvo na pilha! Esta é uma pilha com as funções de chamada completadas até <sup>a</sup> metade, cada uma com <sup>a</sup> sua lista de caixas, também completadas até <sup>a</sup> metade, para ser analisadas. Utilizar <sup>a</sup> pilha é conveniente porque você não precisa acompanhar <sup>o</sup> monte de caixas - <sup>a</sup> pilha faz isso para você. Usar <sup>a</sup> pilha é bom, porém, existe um custo: salvar toda essa informação pode ocupar muita memória. Cada uma destas funções de chamada ocupa um pouco de memória, <sup>e</sup> quando a sua pilha está muito cheia

  

é sinal de que seu computador está salvando informação para muitas chamadas de funções. Para esta situação, você tem duas opções:

  

- Reescrever seu código utilizando loops.

- Utilizar <sup>o</sup> que chamamos de tail recursion (recursão de cauda). Isto é um tópico avançado em recursão <sup>e</sup> está fora do escopo deste livro. Esta técnica também não é suportada por todas as linguagens de programação.

  

### EXERCÍCIO

  

3.2 Suponha que você acidentalmente escreva uma função recursiva que fique executando infinitamente. Como você viu, seu computador aloca memória na pilha para cada chamada de função. O que acontece com <sup>a</sup> pilha quando <sup>a</sup> função recursiva fica executando infinitamente?

  

# Recapitulando

  

![](_page_16_Picture_6.jpeg)

  

- Recursão é quando uma função chama <sup>a</sup> si mesma.

- 이 Toda função recursiva tem dois casos: <sup>o</sup> caso-base <sup>e</sup> <sup>o</sup> caso recursivo.

- 이 Uma pilha tem duas operações: push <sup>e</sup> pop.

- Todas as chamadas de função vão para <sup>a</sup> pilha de chamada.

- <sup>A</sup> pilha de chamada pode ficar muito grande <sup>e</sup> ocupar muita memória.

  

http://stackoverflow.com/a/72694/139117.