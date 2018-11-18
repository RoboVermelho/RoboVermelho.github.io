---
published: true
layout: post
comments: true
title: Dumb Watches
categories: [segurança, pentest]
tags: [seguranca,smart watch, infantil]
excerpt_separator: <!--more-->
---
Cuidado com os rastreadores infantis.
<!--more-->
A empresa de pen test inglesa, Pen Test Partners, publicou artigo em seu
site, uma pesquisa preocupante ao analisar o relógio inteligente para
crianças Misafes 'Kids Watcher', que é um relógio inteligênte que se
conecta ao gps do celular para transmitir em tempo real dados da criança e
sua localização atualizada para os pais, além de permitir gravar o audio ao
redor do celular, como forma de espionagem, fazer uma chamada à criança,
retornar dados da criança através da API do site, como foto, idade, peso,
altura, sexo, etc.
Os pais poderiam ter acesso aos dados através de um aplicativo ou através
do site da empresa.
A falha de segurança encontrada, foi de que a comunicação do device com a
API não é criptografada, dessa forma, através de um aplicativo como o BURP
Suit, pode-se modificar o ID do relógio que será monitorado, podendo criar
um banco de dados de crianças, com seus trajetos sendo atualizados à cada
cinco minutos, pode-se ter um rastreamento em tempo real, e um possível
banco de dados para sequestradores e pedófilos.
A conclusão do analista é que por se tratar de um produto muito barato (ele
informa que um dos relógios foi comprado por 9 libras, aproximadamente
R$43,00) não é feita uma análise muito apurada da questão de segurança.
O artigo pode ser encontrado no link:
https://www.pentestpartners.com/security-blog/tracking-and-snooping-on-a-million-kids/
