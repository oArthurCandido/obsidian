# Tabelas hash

![](_page_0_Picture_1.jpeg)

### Neste capítulo

- Você conhecerá as tabelas hash, uma estrutura de dados básica muito útil.
- Você também conhecerá os detalhes sobre as tabelas hash: implementação, colisões e funções hash.

![](_page_1_Picture_0.jpeg)

Imagine que você trabalha em um mercado. Quando um cliente compra um produto, é preciso conferir <sup>o</sup> preço deste produto em um caderno. Porém, se <sup>o</sup> caderno não estiver organizado alfabeticamente, você levará muito tempo analisando cada linha até encontrar <sup>o</sup> preço da maçă, por exemplo. Procurando desta forma você realizaria uma pesquisa simples, vista no Capítulo 1, <sup>e</sup> por meio dela teria de analisar todas as linhas. Você lembra qual era <sup>o</sup> tempo de execução da pesquisa simples? O(n). No entanto, se <sup>o</sup> caderno estivesse ordenado alfabeticamente, poderia executar uma pesquisa binária para encontrar <sup>o</sup> preço da maçã com um tempo de execução O(log n).

![](_page_1_Figure_2.jpeg)

Vale lembrar que existe uma grande diferença entre um tempo de execução O(n) e O(log n)! Suponha que você conseguisse ler dez

linhas do caderno por segundo. Na figura <sup>a</sup> seguir você pode ver quanto tempo levaria usando <sup>a</sup> pesquisa binária <sup>e</sup> <sup>a</sup> pesquisa simples.

![](_page_2_Figure_1.jpeg)

Você já sabe que <sup>a</sup> pesquisa binária é muito mais rápida. Porém, como um caixa de mercado, você já sabe que procurar <sup>o</sup> preço de mercadorias em um caderno é uma tarefa chata, mesmo que este caderno esteja ordenado, pois <sup>o</sup> cliente está fica impaciente enquanto <sup>a</sup> procura pelo preço dos itens é realizada. Assim, <sup>o</sup> que você precisa é de um amigo que conheça todas as mercadorias <sup>e</sup> os seus preços, pois, dessa forma, não é necessário procurar nada: vocé pede para este seu amigo <sup>e</sup> ele informa <sup>o</sup> preço imediatamente.

![](_page_2_Figure_3.jpeg)

<sup>A</sup> sua amiga Maggie pode dizer <sup>o</sup> preço com tempo de execução O(1) para todos os itens, não importando <sup>a</sup> quantidade de itens que compõem o caderno de preços. Dessa forma, ela é ainda mais rápida

do que <sup>a</sup> pesquisa binária.

![](_page_3_Figure_1.jpeg)

Que amiga maravilhosa! Mas, então, como você arranja uma "Maggie"?

Agora, vamos voltar <sup>a</sup> falar de estruturas de dados. Você já conhece duas estruturas até agora: arrays <sup>e</sup> listas (não vou falar sobre as pilhas, pois não é possível "procurar" algo nelas). Seria possível implementar este seu caderno de preços como um array.

$$
\left(\text{OVO5, 2.49}\right)\left(\text{LEITE}, 1.49\right)\left(\text{PÊRA, 0.79}\right)
$$

Cada item neste array é, na realidade, uma dupla de itens: um é <sup>o</sup> nome <sup>e</sup> <sup>o</sup> tipo do produto <sup>e</sup> <sup>o</sup> outro é <sup>o</sup> preço. Se ordenar este array por nome, será possível executar uma pesquisa binária para procurar <sup>o</sup> preço de um item. Logo, é possível pesquisar itens com tempo de execução O(log n). Entretanto nós queremos encontrar itens com tempo de execução O(1), ou seja, queremos uma "Maggie", <sup>e</sup> <sup>é</sup> aí que entram as funções hash.

# Funções hash

Uma função hash é uma função na qual você insere uma string e, depois disso, a função retorna um número.

![](_page_4_Figure_0.jpeg)

Em uma terminologia mais técnica, diríamos que uma função hash "mapeia strings <sup>e</sup> números". Você pode pensar que não existe um padrão indicando qual número será retornado após <sup>a</sup> inserção de uma string, mas existem alguns requisitos para uma função hash:

- Ela deve ser consistente. Imagine que você insere <sup>a</sup> string "maçã" <sup>e</sup> recebe <sup>o</sup> número 4. Todas as vezes que você inserir "maçă", <sup>a</sup> função deverá retornar <sup>o</sup> número "4"; caso contrário, sua tabela hash não funcionará corretamente.
- A função deve mapear diferentes palavras para diferentes números. Desta forma, uma função hash não será útil se ela sempre retornar "1",independentemente da palavra inserida. No melhor caso, cada palavra diferente deveria ser mapeada <sup>e</sup> ligada <sup>a</sup> um número diferente.

Então, uma função hash mapeia strings <sup>e</sup> as relaciona <sup>a</sup> números. Mas qual é <sup>a</sup> utilidade disso? Bem, você pode usar esta funcionalidade para criar <sup>a</sup> sua "Maggie"!

Comece com um array vazio:

$$
\begin{array}{|c|c|c|}\n\hline\n\downarrow & & \downarrow \\
\hline\n\downarrow & 1 & 2 & 3 & 4\n\end{array}
$$

Você armazenará os preços das mercadorias neste array. Vamos

adicionar <sup>o</sup> preço de uma maçã. Insira "maçã" na função hash.

![](_page_5_Picture_1.jpeg)

Ela retornará <sup>o</sup> valor "3". Agora, vamos armazenar <sup>o</sup> preço da maçã no índice 3 do array.

![](_page_5_Figure_3.jpeg)

Vamos adicionar <sup>o</sup> leite agora. Insira "leite" na função hash.

![](_page_5_Figure_5.jpeg)

A função hash retornou "0". Agora, armazene <sup>o</sup> preço do leite no índice 0.

![](_page_5_Figure_7.jpeg)

Continue e, eventualmente, todo <sup>o</sup> array estará repleto de preços.

$$
1.49 \big| 0.79 \big| 2.49 \big| 0.67 \big| 1.49 \big|
$$

Agora, você poderá perguntar "Ei, qual é <sup>o</sup> preço de um abacate?" <sup>e</sup> não será necessário procurar <sup>o</sup> preço deste produto no array. Em vez disso, insira "abacate" na função hash.

دو <sup>フ</sup> ABACATE 4

Ela informará <sup>o</sup> preço armazenado no índice 4.

![](_page_6_Figure_2.jpeg)

A função hash informará <sup>a</sup> posição exata em que <sup>o</sup> preço está armazenado. Assim, não precisará procurá-lo! Isto funciona porque

- A função hash mapeia consistentemente um nome para <sup>o</sup> mesmo índice. Todas as vezes que você inserir "abacate", ela retornará <sup>o</sup> mesmo número. Assim, <sup>a</sup> primeira execução da função hash servirá para identificar onde é possível armazenar <sup>o</sup> preço do abacate, <sup>e</sup> depois disso ela será utilizada para encontrar este valor armazenado.
- 이 A função hash mapeia diferentes strings para diferentes índices. A string "abacate" é mapeada para <sup>o</sup> índice 4. A string "leite" é mapeada para <sup>o</sup> índice 0. Todas as diferentes strings são mapeadas para diferentes lugares do array onde você está armazenando os preços.
- A função hash tem conhecimento sobre <sup>o</sup> tamanho do seu array <sup>e</sup> retornará apenas índices válidos. Portanto, caso <sup>o</sup>seu array tenha cinco itens, <sup>a</sup> função hash não retornará 100, pois este valor não seria um índice válido do array.

Você acabou de criar uma "Maggie"! Coloque uma função hash em conjunto com um array <sup>e</sup> você terá uma estrutura de dados chamada tabela hash. Uma tabela hash é <sup>a</sup> primeira estrutura de dados que tem uma lógica adicional aliada que você aprenderá, visto que arrays <sup>e</sup> listas mapeiam diretamente para <sup>a</sup> memória, porém as tabelas hash são mais inteligentes. Elas usam uma função hash para indicar, de maneira inteligente, onde armazenar os elementos.

As tabelas hash são, provavelmente, as mais úteis <sup>e</sup> complexas estruturas de dados que você aprenderá. Elas também são conhecidas como mapas hash, mapas, dicionários <sup>e</sup> tabelas de dispersão. Além disso, as tabelas hash são muito rápidas! Você se lembra da nossa discussão sobre arrays <sup>e</sup> listas encadeadas no Capítulo 2? Você pode pegar um item de um array instantaneamente que as tabelas hash usarão arrays para armazenar os dados desse item; desta forma, elas são igualmente velozes.

![](_page_7_Picture_1.jpeg)

Você provavelmente nunca terá de implementar uma tabela hash, pois qualquer linguagem de programação já terá uma implementação dela. A linguagem Python contém tabelas hash chamadas de dicionários. Para criar uma nova tabela hash você pode utilizar <sup>a</sup> função dict:

```python
>>> caderno = dict()
```

Book (caderno) é uma nova tabela hash. Agora, vamos adicionar alguns preços <sup>a</sup> ela.

![](_page_7_Picture_5.jpeg)

UMA TABELA HASH DE PREÇOS DE PRODUTOS

```python
>>> caderno["maçã"] = 0.67
>>> caderno["leite"] = 1.49
>>> caderno["abacate"] = 1.49
>>> print caderno
```

```python
{'abacate': 1.49, 'maçă': 0.67, 'leite': 1.49}
```

• Uma maçă custa 67 centavos.

O leite custa R\$ 1,49

Fácil! Agora, vamos perguntar <sup>o</sup> preço de um abacate:

```python
>>> print caderno["abacate"]
1.490
```

O preço de um abacate.

Uma tabela hash contém chaves <sup>e</sup> valores. Na hash caderno, os nomes dos produtos são as chaves <sup>e</sup> os preços são os valores. Logo, uma tabela hash mapeia chaves <sup>e</sup> valores.

Na próxima seção você verá alguns exemplos em que as tabelas hash são muito úteis.

#### EXERCÍCIOS

![](_page_8_Figure_9.jpeg)

É importante que funções hash retornem <sup>o</sup> mesmo valor de saída quando <sup>o</sup> mesmo valor de entrada for inserido. Caso contrário, não será possível encontrar <sup>o</sup> item que você deseja na tabela hash!

Quais destas funções hash são consistentes?

5.1 f(x) <sup>=</sup> 10

5.2 f(x) <sup>=</sup> rand() 2

5.3 f(x) <sup>=</sup> proximo_espaco_vazio()

5.4 f(x) <sup>=</sup> len(x) 4

Retorna "1" para qualquer entrada.

Retorna um número aleatório a cada execução.

- Retorna <sup>o</sup> índice do próximo espaço livre da tabela hash.
- Usa <sup>o</sup> comprimento da string como índice.

# Utilização

Tabelas hash são amplamente utilizadas. Nesta seção, vamos analisar alguns casos.

## Usando tabelas hash para pesquisas

![](_page_9_Picture_5.jpeg)

O seu celular tem uma agenda telefônica integrada.

Cada nome está associado <sup>a</sup> um número telefônico.

BADE MAMA 581 66Ø 982ø ALEX MANNING- 484 234 4680 JANE MARIN 415 567 3579

Imagine que você queira construir uma lista telefônica como esta. Será necessário mapear <sup>o</sup> nome das pessoas <sup>e</sup> associá-los <sup>a</sup> números telefônicos. Dessa forma, <sup>a</sup> sua lista telefônica deverá ter estas funcionalidades:

• Adicionar <sup>o</sup> nome de uma pessoa <sup>e</sup> <sup>o</sup> número de telefone associado a este nome.

Inserir <sup>o</sup> nome de uma pessoa <sup>e</sup> receber <sup>o</sup> número telefônico associado <sup>a</sup> ela.

Este é um exemplo perfeito de situações em que tabelas hash podem ser usadas! As tabelas hash são ótimas opções quando

- Você deseja mapear algum item com relação <sup>a</sup> outro
- Você precisa pesquisar algo

Criar uma lista telefônica é uma tarefa simples. Primeiro, faça uma nova tabela hash para lista_telefonica:

```python
>>> lista_telefonica = dict()
```

<sup>A</sup> propósito, <sup>a</sup> linguagem Pyhton tem um atalho para <sup>a</sup> criação de tabelas hash utilizando duas chaves:

```python
>>> lista_telefonica = {} 0
```

Igual ao que foi feito com lista telefonica <sup>=</sup> dict().

![](_page_10_Figure_9.jpeg)

UMA LISTA TELEFÔNICA

Então vamos adicionar <sup>o</sup> número de algumas pessoas nesta lista:

```python
>>> lista_telefonica["jenny"] = 8675309
>>> lista_telefonica["emergency"] = 911
```

É isso! Agora, digamos que queira encontrar <sup>o</sup> número de telefone da Jenny. Para isso, é necessário apenas informar <sup>a</sup> chave para <sup>a</sup> hash:

```python
>>> print lista_telefonica["jenny"]
8675309 1
```

Número de telefone da Jenny.

Imagine que tivesse de fazer isto utilizando um array. Como faria? As tabelas hash tornam simples a modelagem de uma relação entre dois

itens.

As tabelas hash são usadas para pesquisas em uma escala muito maior. Por exemplo, suponha que você queira acessar um website como <sup>o</sup> http://adit.io. <sup>O</sup> seu computador deve traduzir adit.io para <sup>a</sup> forma de um endereço de IP.

#### ADIT. <sup>10</sup> 173.255.248.55

Para cada website que você acessar, <sup>o</sup> endereço deverá ser traduzido para um endereço de IP.

> GOOGLE.COM 74.125,239.133 FACEBOOK.COM 173.252.120.6 SCRIBD.COM 23.235.47.175

Nossa, mapear <sup>o</sup> endereço de um website para um endereço IP? Isso parece <sup>o</sup> caso perfeito para <sup>a</sup> utilização de tabelas hash! Este processo é chamado de resolução DNS, <sup>e</sup> as tabelas hash são uma das maneiras pelas quais esta funcionalidade pode ser implementada.

![](_page_11_Picture_6.jpeg)

### Evitando entradas duplicadas

Imagine que esteja organizando uma votação. Obviamente, cada pessoa poderá votar apenas uma vez. Como você pode verificar se uma pessoa já não votou antes? Você pode perguntar para <sup>a</sup> pessoa que veio votar qual é o seu nome completo e então conferir esse

nome em uma lista que contenha <sup>o</sup> nome das pessoas que já votaram.

![](_page_12_Picture_1.jpeg)

Se <sup>o</sup>nome dessa pessoa estiver na lista, isso significa que ela já votou, ou seja, você deve dispensá-la! Caso contrário, você deverá adicionar <sup>o</sup> nome dela na lista <sup>e</sup> permitir que ela vote. Agora, suponha que diversas pessoas chegaram para votar <sup>e</sup> que, além disso, <sup>a</sup> lista de pessoas que já votaram seja muito longa.

![](_page_12_Picture_3.jpeg)

A cada nova pessoa que chegar para votar, você deverá conferir esta lista enorme para checar se esta pessoa já votou. No entanto, temos uma solução melhor: use uma hash!

Primeiro, crie uma hash votaram para registrar as pessoas que já votaram:

```python
>>> votaram = {}
```

Quando alguém chegar para votar, confira se <sup>o</sup> nome desta pessoa já está na hash:

```python
>>> valor = votaram.get("tom")
```

<sup>A</sup> função get (pegar) retornará um valor se "Tom" já estiver na tabela hash. Caso contrário, ela retornará None (nada). Você pode usar esta funcionalidade para conferir se as pessoas já votaram!

![](_page_13_Figure_2.jpeg)

Aqui você pode conferir <sup>o</sup> código completo:

```python
voted = {}
def verifica_eleitor(nome):
 if votaram.get(nome):
   print "Mande embora!"
 else:
   voted [nome] = True
   print "Deixe votar!"
```

Vamos fazer alguns testes:

```python
>>> verifica_eleitor("tom")
Deixe votar!
>>> verifica_eleitor("mike")
Deixe votar!
>>> verifica_eleitor("mike")
Mande embora!
```

Na primeira vez que Tom for inserido, aparecerá <sup>a</sup> mensagem na tela "Deixe votar!". Depois, <sup>o</sup> nome Mike será inserido <sup>e</sup> novamente <sup>a</sup> mensagem "Deixe votar!" será mostrada na tela. Por fim, Mike será inserido mais uma vez <sup>e</sup> <sup>a</sup> mensagem "Mande embora!" surgirá na tela.

Lembre-se: se você estivesse armazenando estes nomes em uma lista de pessoas que já votaram, esta função se tornaria muito lenta eventualmente, pois uma pesquisa simples seria utilizada para pesquisar em toda <sup>a</sup> lista. Porém você está armazenando estes nomes em uma tabela hash, <sup>e</sup> <sup>a</sup> tabela hash informa instantaneamente se <sup>o</sup> nome da pessoa está ou não na lista. Logo, <sup>a</sup> checagem por duplicatas é realizada muito rapidamente com <sup>o</sup> uso de uma tabela hash.

![](_page_14_Picture_2.jpeg)

### Utilizando tabelas hash como cache

Apresentaremos um último uso para tabelas hash: utilização como cache. Se você trabalha com websites, talvez já tenha ouvido falar sobre <sup>a</sup> utilização de cache como uma boa prática. <sup>A</sup> ideia é esta: imagine que você visite facebook.com:

- 1. Você faz uma solicitação aos servidores do Facebook.
- 2. O servidor pensa por um segundo <sup>e</sup> então envia uma página web.
- 3. Você recebe uma página da web.

![](_page_15_Figure_0.jpeg)

O servidor do Facebook pode estar coletando toda <sup>a</sup> atividade dos seus amigos para então mostrar <sup>a</sup> você, por exemplo. Para coletar todos estes dados, <sup>o</sup> servidor pode levar alguns segundos. Entretanto estes poucos segundos podem parecer uma eternidade, <sup>e</sup> você pode pensar "Por que <sup>o</sup> Facebook está tão lento?". Por outro lado, <sup>o</sup> servidor do Facebook precisa responder <sup>a</sup> solicitações de milhões de pessoas, <sup>e</sup> estes poucos segundos vão se acumulando. Ou seja, <sup>o</sup> servidor do Facebook está trabalhando duro para responder <sup>a</sup> todas as solicitações. Mas será que existe alguma maneira de tornar <sup>o</sup> Facebook mais rápido <sup>e</sup> fazer com que os seus servidores trabalhem menos?

Suponha que você tenha uma sobrinha que faça muitas perguntas sobre planetas do tipo "O quão distante Marte fica da Terra?", "Qual <sup>a</sup> distância até <sup>a</sup> Lua?" <sup>e</sup> "Qual <sup>a</sup> distância até Júpiter?". A cada pergunta você precisa pesquisar no Google <sup>a</sup> resposta <sup>e</sup> só então você conseguirá responder. Logo você terá memorizado que <sup>a</sup> Lua fica <sup>a</sup> 384.400 km de distância <sup>e</sup> não precisará mais procurar esta resposta no Google. É desta forma que <sup>o</sup> cache funciona: os websites lembram dos dados em vez de recalculá-los <sup>a</sup> cada solicitação.

Caso você esteja conectado ao Facebook, saiba que todo <sup>o</sup> conteúdo que você vê foi feito sob medida. Assim, todas as vezes que você acessa <sup>a</sup> página facebook.com, os servidores precisam pensar <sup>e</sup> selecionar qual conteúdo é de seu interesse. Porém, se você não estiver logado ao Facebook, verá apenas <sup>a</sup> página de login, sendo que todas as pessoas verão <sup>a</sup> mesma página de login. Ou seja, <sup>o</sup> Facebook engloba diversas solicitações para <sup>a</sup> mesma informação: "Mostre-me a página inicial quando eu não estiver logado". Isso evita que <sup>o</sup>

servidor tenha de pensar como <sup>a</sup> página inicial é, pois ele memoriza como <sup>a</sup> página inicial deve ser apresentada <sup>e</sup> então <sup>a</sup> envia <sup>a</sup> você.

![](_page_16_Figure_1.jpeg)

Isso se chama caching, <sup>e</sup> esta prática oferece duas vantagens:

- Você recebe <sup>a</sup> página da web muito mais rapidamente, da mesma forma que você memorizou <sup>a</sup> distância entre <sup>a</sup> Terra <sup>e</sup> <sup>a</sup> Lua. Assim, da próxima vez que sua sobrinha perguntar sobre isso, não será necessário pesquisar no Google, pois você conseguirá responder instantaneamente.
- O Facebook precisa trabalhar menos.

Esta técnica é uma maneira comum de agilizar as coisas. Todos os grandes sites usam caching, <sup>e</sup> os dados destes cachings são armazenados em uma tabela hash!

O Facebook não está só aplicando <sup>o</sup> caching na página de entrada. Ele está fazendo cache das páginas Sobre, Contato, Termos <sup>e</sup> Condições <sup>e</sup> muitas outras. Assim, ele precisa mapear <sup>a</sup> URL de uma página e relacioná-la aos dados da página.

facebook.com/about DADOS DA PÁGINA SOBRE facebook.com DADOS DA PÁGINA INICIAL

Quando você visitar uma página no Facebook, este irá primeiro checar se esta página está armazenada na hash.

![](_page_17_Figure_2.jpeg)

Aqui você pode ver isso em forma de código:

```python
cache = {}
def pega_pagina(url):
  if cache.get(url):
    return cache[url]
 else:
                     Ο
   dados = pega_dados_do_servidor(url)
   cache[url] = dados
   return dados
                      2
```

Retorna os dados do cache.

2 Salva esses dados primeiro no seu cache.

Desta forma, você faz <sup>o</sup> servidor trabalhar apenas se <sup>a</sup> URL não estiver armazenada no cache. Antes de você retornar os dados, eles serão salvos no cache. Assim, <sup>a</sup> próxima vez que alguém solicitar esta URL, você poderá enviar os dados do cache em vez de fazer <sup>o</sup> servidor executar esta tarefa.

## Recapitulando

As tabelas hash são úteis para

- <sup>이</sup> Modelar relações entre dois itens
- Filtrar por duplicatas
- Caching/memorização de dados, em vez de solicitar estes dados do servidor.

# Colisões

Como eu disse antes, <sup>a</sup> maioria das linguagens de programação contém tabelas hash, por isso você não precisa escrevê-las do zero. Sendo assim, não falarei muito sobre <sup>a</sup> estrutura das tabelas hash. No entanto você precisa saber sobre <sup>o</sup> desempenho delas, <sup>e</sup> para isso precisa primeiro entender <sup>o</sup> que são colisões. As duas próximas seções falam sobre colisões <sup>e</sup> desempenho.

Primeiro, preciso dizer que estive contando uma pequena mentira. Disse que uma função hash sempre mapeia diferentes chaves para diferentes espaços em um array.

![](_page_18_Figure_9.jpeg)

Na realidade, é praticamente impossível escrever uma função hash

que faça isso. Vamos analisar este exemplo simples: suponha que você tenha um array que contenha 26 espaços.

![](_page_19_Picture_1.jpeg)

Sua função hash é bem simples: ela apenas indica um espaço do array alfabeticamente.

![](_page_19_Figure_3.jpeg)

Talvez você já consiga ver <sup>o</sup> problema. Você quer inserir <sup>o</sup> preço de uma ameixa na sua hash. Assim, <sup>o</sup> primeiro espaço do array é indicado.

![](_page_19_Figure_5.jpeg)

Depois, você quer inserir <sup>o</sup> preço das bananas. Então, <sup>o</sup> segundo espaço do array <sup>é</sup> indicado.

$$
\begin{array}{|c|c|c|}\n\hline\n0.67 & 0.39 & \cdots \\
\hline\n\end{array}
$$

Tudo está indo tão bem! Mas agora quer inserir <sup>o</sup> preço dos abacates na sua hash. Então, <sup>o</sup> primeiro espaço do array é indicado novamente.

![](_page_20_Figure_0.jpeg)

Ah, não! As ameixas já estão neste espaço! O que vamos fazer? Isso se chama colisão: duas chaves são indicadas para <sup>o</sup> mesmo espaço, <sup>e</sup> isto <sup>é</sup> um problema. Assim, se armazenar <sup>o</sup> preço dos abacates neste espaço, eles irão sobrescrever <sup>o</sup> preço das ameixas. Desta forma, da próxima vez que alguém perguntar <sup>o</sup> preço das ameixas, <sup>o</sup> preço dos abacates será informado! Colisões são um problema, <sup>e</sup> vocé precisa solucioná-lo. Para isso há várias alternativas, <sup>e</sup> <sup>a</sup> mais simples é esta: se diversas chaves mapeiam para <sup>o</sup> mesmo espaço, inicie uma lista encadeada neste espaço.

![](_page_20_Figure_2.jpeg)

Neste exemplo, tanto <sup>a</sup> "ameixa" quanto <sup>o</sup> "abacate" são mapeados para <sup>o</sup> mesmo espaço. Logo, você deve iniciar uma lista encadeada neste espaço. Caso você queira saber <sup>o</sup> preço das bananas, esta informação ainda será acessada de maneira rápida. Porém, se você quiser saber <sup>o</sup> preço das ameixas, essa informação será retornada de forma mais lenta, pois você precisará pesquisar na sua lista encadeada para encontrar "ameixas". Se <sup>a</sup> lista encadeada for pequena, não haverá nenhum problema, pois você deverá pesquisar entre três ou quatro elementos. Mas imagine que você trabalha em um mercado onde são vendidos apenas produtos que iniciam com <sup>a</sup> letra A.

![](_page_21_Figure_0.jpeg)

Ei, espere um pouco aí! Quase toda <sup>a</sup> tabela hash está vazia, exceto por um espaço, <sup>e</sup> neste espaço há uma lista gigante linkada! Ou seja, cada elemento dessa tabela hash está contido nessa lista. Isso é tão ineficiente quanto colocar todos esses elementos apenas na lista encadeada, pois essa lista diminuirá <sup>o</sup> tempo de execução da sua tabela hash.

Aprendemos duas lições aqui:

- A função hash é muito importante. Ela mapeia todas as chaves para um único espaço. Idealmente, <sup>a</sup> sua função hash mapearia chaves de maneira simétrica por toda <sup>a</sup> hash.
- <sup>이</sup> Caso as listas encadeadas se tornem muito longas, elas diminuirão demais <sup>o</sup> tempo de execução da tabela hash. Porém elas não se tornarão muito longas se você utilizar uma boa função hash!

As funções hash são importantes, pois uma boa função hash cria poucas colisões. Mas como você escolhe uma boa função hash? É isso que veremos na próxima seção!

# Desempenho

Você iniciou este capítulo em um supermercado, pois era necessário criar algo que fornecesse os preços dos produtos instantaneamente. Bem, as tabelas hash são muito rápidas.

|                             | CASO<br>MÉDIO | PIOR<br>CASO |     |
| --------------------------- | ------------- | ------------ | --- |
| PROCURA                     | 0(1)          | O(n)         |     |
| INSERÇÃO                    | OC1)          | O(n)         |     |
| REMOÇÃO                     | (1)           | O)           |     |
| DESEMPENHO DAS TABELAS HASH |               |              |     |

No caso médio, as tabelas hash têm tempo de execução O(1) para tudo. Assim, O(1) é chamado de tempo constante. Você ainda não foi apresentado <sup>a</sup> tempo constante. Tempo constante não é algo que acontece instantaneamente, mas sim um tempo que continuará sempre <sup>o</sup> mesmo, independentemente de quão grande <sup>a</sup> tabela hash possa ficar. Por exemplo, você sabe que<sup>a</sup> pesquisa simples tem tempo de execução linear.

![](_page_22_Figure_2.jpeg)

<sup>A</sup> pesquisa binária <sup>é</sup> mais rápida, pois tem tempo de execução log:

![](_page_23_Figure_0.jpeg)

Procurar algo em uma tabela hash tem tempo de execução constante.

![](_page_23_Figure_2.jpeg)

Percebe como é uma linha reta? Isso significa que não importa se <sup>a</sup> sua tabela hash tem 1 elemento ou 1 bilhão de elementos, pois <sup>o</sup> retorno da tabela hash sempre levará <sup>a</sup> mesma quantidade de tempo. Na verdade, você já viu tempo constante antes, pois retornar um item de um array leva um tempo constante. Novamente, não importa <sup>o</sup> tamanho do array, pois ele sempre levará <sup>a</sup> mesma quantidade de tempo para retornar um elemento. No caso médio, as tabelas hash são muito rápidas.

No pior caso, uma tabela hash tem tempo de execução O(n), ou seja, tempo de execução linear para tudo, <sup>o</sup> que <sup>é</sup> bem lento. Vamos comparar as tabelas hash com os arrays e com as listas.

|          | (CASO MÉDIO) (PIOR CASO) | TABELAS HASH TABELAS HASH | ARRAYS | LISTAS<br>ENCADEADAS |
| -------- | ------------------------ | ------------------------- | ------ | -------------------- |
| BUSCA    | 0(2)                     | On>                       | O(1)   | On                   |
| INSERÇÃO | 0(1)                     | O(ny                      | Ocn)   | 1)                   |
| REMOÇÃO  | 0(1)                     | On)                       | On     | OX                   |

Preste atenção ao caso médio para as tabelas hash. As tabelas hash são tão velozes quanto os arrays na busca (pegar um valor em algum índice), <sup>e</sup> elas são tão velozes quanto as listas na inserção <sup>e</sup> na remoção de itens. Ou seja, ela é <sup>o</sup> melhor dos dois mundos! Porém, no pior caso, as tabelas hash são lentas em ambos os casos. Assim, é importante que você não opere no pior caso; para isso <sup>é</sup> preciso evitar colisões. Para evitar colisões são necessários

- um baixo fator de carga;
- uma boa função hash.

#### Nota

Antes de iniciar esta seção, saiba que ela não é uma leitura obrigatória, pois falarei sobre como implementar uma tabela hash. Porém você provavelmente nunca fará isso. Não importa <sup>a</sup> linguagem na qual você programe, ela terá uma implementação de tabela hash já agregada. Assim, é possível usar esta tabela hash agregada admitir que ela terá um bom desempenho. A próxima seção pode ser considerada uma espiada dentro do capô para analisar <sup>o</sup> funcionamento do motor. e

### Fator de carga

O fator de carga de uma tabela hash é simples de calcular.

NÚMERO DE ITENS NA TABELA HASH

NÚMERO TOTAL DE ESPAÇOS

As tabelas hash utilizam um array para armazenamento, então você deve contar <sup>o</sup> número de espaços usados no array. Por exemplo, esta tabela hash tem fator de carga de 2/5, ou 0,4.

![](_page_25_Figure_1.jpeg)

Qual <sup>o</sup> fator de carga desta tabela hash?

![](_page_25_Figure_3.jpeg)

Se você disse um terço, acertou. O fator de carga mede quantos espaços continuam vazios na sua tabela hash.

Suponha que você precise armazenar <sup>o</sup> preço de cem produtos em sua tabela hash, considerando que ela tenha cem espaços. Na melhor hipótese, cada item terá seu próprio espaço.

![](_page_25_Figure_6.jpeg)

Esta tabela hash tem um fator de carga de 1. <sup>E</sup> se <sup>a</sup> tabela hash tivesse apenas cinquenta espaços? Neste caso, ela teria um fator de carga de 2, sendo impossível que cada item tenha <sup>o</sup> seu próprio espaço, pois não existem espaços suficientes! Um fator de carga maior do que 1 indica que você tem mais itens do que espaços em seu array. Se <sup>o</sup> fator de carga começar <sup>a</sup> crescer, será necessário adicionar mais espaços em sua tabela hash. Isso se chama redimensionamento. Suponha, por exemplo, que você tenha esta tabela hash que está quase cheia:

![](_page_26_Picture_0.jpeg)

É necessário redimensionar esta tabela hash. Para isso, primeiro você deve criar um array maior. Empiricamente, definiu-se que este array deve ter <sup>o</sup> dobro do tamanho do array original.

![](_page_26_Figure_2.jpeg)

Agora é necessário reinserir todos os itens nesta nova tabela hash utilizando <sup>a</sup> função hash:

![](_page_26_Figure_4.jpeg)

Esta nova tabela tem um fator de carga de % (três oitavos). Bem melhor! Com um fator de carga menor haverá menos colisões <sup>e</sup> sua tabela terá melhor desempenho. Uma boa regra geral é: redimensione quando <sup>o</sup> fator de carga for maior do que 0,7.

Você pode estar pensando "Redimensionar leva muito tempo!", <sup>e</sup> isto é verdade. O redimensionamento é caro <sup>e</sup> não deve ser feito com frequência. No entanto, em média, as tabelas hash têm tempo de execução O(1), mesmo com <sup>o</sup> redimensionamento.

## Uma boa função hash

Uma boa função hash distribui os valores no array simetricamente.

$$
\begin{array}{|c|c|c|c|c|}\n\hline\n2 & 6 & 4 & 10 & 12 \\
\hline\n\end{array}
$$

Uma função hash não ideal agrupa valores e produz diversas colisões.

![](_page_27_Picture_0.jpeg)

Mas <sup>o</sup> que é uma boa função hash? Isso é algo com que você jamais deverá se preocupar, pois homens (e mulheres) velhos <sup>e</sup> barbudos sentam em quartos escuros <sup>e</sup> se preocupam com isso. Se você é muito curioso, dê uma olhada na função SHA (há uma breve descrição sobre ela no último capítulo). Você pode usar aquilo como sua função hash.

#### EXERCÍCIOS

É importante que funções hash tenham uma boa distribuição. Dessa forma, elas ficam com <sup>o</sup> mapeamento mais amplo possível. O pior caso é uma função hash que mapeia todos os itens para <sup>o</sup> mesmo espaço da tabela hash.

Suponha que você tenha estas quatro funções hash que operam com strings:

- a. Retorne "1" para qualquer entrada.
- b. Use <sup>o</sup> comprimento da string como <sup>o</sup> índice.
- c. Use <sup>o</sup> primeiro caractere da string como índice. Assim, todas as strings que iniciam com <sup>a</sup> letra <sup>a</sup> são hasheadas juntas <sup>e</sup> assim por diante.
- d. Mapeie cada letra para um número primo: <sup>a</sup> <sup>=</sup> 2, b <sup>=</sup> 3, <sup>c</sup> <sup>=</sup> 5, d <sup>=</sup> 7, <sup>e</sup> = 11, <sup>e</sup> assim por diante. Para uma string, <sup>a</sup> função hash é <sup>a</sup>

soma de todos os caracteres-módulo² conforme <sup>o</sup> tamanho da hash. Se <sup>o</sup> tamanho de sua hash for 10, por exemplo, <sup>e</sup> <sup>a</sup> string for "bag", <sup>o</sup> índice será (3 <sup>+</sup> <sup>2</sup> <sup>+</sup> 17) % 10 <sup>=</sup> 22 % 10 <sup>=</sup> 2.

Para cada um destes exemplos, qual função hash fornecerá uma boa distribuição? Considere que <sup>o</sup> tamanho da tabela hash tenha dez espaços.

- 5.5 Uma lista telefônica em que as chaves são os nomes <sup>e</sup> os valores são os números telefônicos. Os nomes são os seguintes: Esther, Ben, Bob <sup>e</sup> Dan.
- 5.6 Um mapeamento do tamanho de baterias <sup>e</sup> sua devida potência. Os tamanhos são A, АА, ААA <sup>e</sup> AAAA.
- 5.7 Um mapeamento de títulos de livros <sup>e</sup> autores. Os títulos são Maus, Fun Home <sup>e</sup> Watchmen.

# Recapitulando

Você provavelmente nunca terá de implementar uma tabela hash, pois <sup>a</sup> linguagem de programação que você utiliza deve fornecer uma implementação desta funcionalidade. É possível usar <sup>a</sup> tabela hash do Python <sup>e</sup> acreditar que ela operará no caso médio de desempenho: tempo de execução constante.

As tabelas hash são estruturas de dados poderosas, pois elas são muito rápidas <sup>e</sup> possibilitam <sup>a</sup> modelagem de dados de uma forma diferente. Logo você estará utilizando-as <sup>o</sup> tempo todo:

- 이 Você pode fazer uma tabela hash ao combinar uma função hash com um array.
- 이 Colisões são problemas. É necessário haver uma função hash que minimize colisões.
- 이 As tabelas hash são extremamente rápidas para pesquisar, inserir <sup>e</sup> remover itens.
- Tabelas hash são boas para modelar relações entre dois itens.
- Se o seu fator de carga for maior que 0,7, será necessário

redimensionar <sup>a</sup> sua tabela hash.

- 이 As tabelas hash são utilizadas como cache de dados (como em um servidor da web, por exemplo).
- Tabelas hash são ótimas para localizar duplicatas.

![](_page_29_Picture_3.jpeg)

<sup>1</sup> String, neste caso, significa qualquer tipo de dado - uma sequência de bytes. 2 N.T.: A operação módulo encontra o resto da divisão de um número por outro
