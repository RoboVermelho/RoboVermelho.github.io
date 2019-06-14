---
published: true 
layout: post
comments: true
title: Chess in a Shell - Me aventurando em Shell Script
categories: [programacao]
tags: [shell script, linux]
excerpt_separator: <!--more-->
---
A um tempo estava estudando sobre shell script. E depois de um tempo, achei
que seria interessante desenvolver algum projeto não trivial para  praticar
<!--more-->
Meu estudo começou com o livro Linux Shell Scripting Cookbook, fazendo
anotações sobre cada capítulo, porém não estava fazendo muita coisa além
dos exercícios e exemplos propostos pelo livro.
Para conciliar meu recente interesse pelo xadrez, resolvi, por que não,
desenvolver um jogo de xadrez em shell script. Já tinha interesse em criar
algo do gênero, então seria algo interessante.
Ainda estou desenvolvendo o jogo, e assim que estiver em um nível um pouco
mais completo irei postar o código no github e disponibilizar o link.
Gostaria de passar alguns detalhes que eu considero importantes e que não
foram abordados no livro, é algo que deve ser trivial para quem já trabalha
com Shell porém pode pegar usuários iniciantes desprevenidos assim como eu.

Um dos fatos que me impulsionou a fazer o jogo, foi descobrir que dentro do
Unicode existem os códigos separados para as peças de xadrez, que você pode
verificar na Wikipedia:
https://en.wikipedia.org/wiki/Chess_symbols_in_Unicode
Desta forma poderia exibir o real desenho das peças, deixando o jogo mais
interessante.
Mas sem mais demora vamos aos pontos interessantes do Shell:
* Atribuição de variáveis: na maioria das linguagens de programação, o
  senso estético comum é que ao atribuir valores à variáveis seja usada a
  forma: VARIAVEL = VALOR, dexiando espaços em branco entre o sinal de
  atribuição. No shell o valor deve ser atribuído SEM ESPAÇOS:
  VARIAVEL=VALOR caso contrário isso resulta em um erro de sintaxe.
* Não há suporte para arrays multidimensionais: esse é o ponto que mais deu
  trabalho. No Shell, podemos definir arrays comuns que são acessados pelo
  índice numérico como em:
  VALORES=(1 2 3 4) #Isso mesmo sem vírgulas.
  Ou ainda temos acesso à arrays indexados com:
  VALORES=([A]=1 [B]=2 [C]=3)
  Porém você não pode criar arrays e atribuí-los como elementos de outro
  array, até onde eu pesquisei não há suporte nativo. E já que é um recurso
  nativo da maioria das linguagens, isso pode fazer você repensar toda
  forma de desenvolver.
* Funções não definem quantidade de argumentos: o shell dá suporte para
  funções, podendo desta forma modularizar um pouco mais o código, porém,
  a assinatura da função consiste apenas no nome da função, sem argumentos.
  Para acessar os argumentos, eles são acessados por índice numérico. Ex:

  metodo_um() { #definindo método.
    echo "$1"
  }

  metodo_um $VARIAVEL #Chamado do método.

  As variáveis são numeradas como $1, $2, $3... E a variável $0 é o  nome
  do método.
  * O retorno do método é limitado a um valor entre 0 e 255. Exatamente, o
    tamanho do retorno é um byte. Não é possível retornar qualquer outro
    tipo de valor através do método. Aliado a isso, os métodos podem
    acessar e inclusive modificar variáveis globais, o que pode não ser
    considerada uma boa prática. Existem formas de contornar essa
    dificuldade, porém, como pra mim isso também não soa exatamente como
    algo correto, no meu sistema acabei por modificar as variáveis globais.
    Cada um escolha seu veneno =).
  * Não existe comentário multilinha: esta não é tão irritante,
    principalmente depois que descobri como inserir caracteres no início de
    cada linha com o Vim. No Shell comentários sempre se iniciam com '#',
    então você vai ter que aprender alguma artimanha do seu editor de texto
    favorito se quiser deixar um comentário mais volumoso.

Bem, por enquanto é isso, além do que deixei exposto, também saliento que
pra mim a sintaxe em geral é um pouco estranha: a estrutura de if/else, o
acesso à itens de um array, atribuição de valores aritméticos à uma
variável, (se você quer atribuir o resultado de uma operação matemática -
ex: 3 + 2 - você deve fazer tudo entre parênteses: $AB=$(3+2) ) é claro que
isso é minha opinião pessoal. Já programei em Python, C#, Javascript, PHP,
além de me divertir às vezes com C, e todas elas tem semelhanças entre si,
porém, são todas bem diferentes do Shell Script, talvez Perl ou Vim Script
sejam mais parecidas, porém, ainda não utilizei muito estas linguagens pra
saber. 
Este post também será interativo, e quanto mais descobrir do Shell, mais
vou modificar o post.
Se você já trabalhou com Shell e discorda ou concorda em algum ponto, deixe
um comentário.
Até a próxima.



