---
published: true
layout: post
comments: true
title: O chip espião
categories: [segurança, internacional]
tags: [china, chip espiao, espionagem]
excerpt_separator: <!--more-->
---
Spies! Spies everywhere!
<!--more-->
<p>Em uma matéria publicada pela agência de notícias Bloomberg, a empresa alega que pequenos chips espiões estariam sendo utilizados nas placas mãe da empresa Super Micro que são vendidas para grandes empresas americanas, incluindo Amazon e Apple. </p>
<p>A descoberta dos chips teve início quando a Amazon comprou a empresa Elementary que projeta servidores de grande porte específicos para processamento de vídeo em alta velocidade. A elementary por sua vez é uma entre várias empresas que é cliente da desenvolvedora de hardware Supermicro. A Supermicro realiza os projetos de hardware em sua sede no Oregon, porém, a montagem é realizada em fábricas na China. </p>
Depois de começar a observar comportamento de rede estranho e falhas de hardware, a Amazon submete o hardware para análise de segurança, e nesta análise foi descoberto um pequeno chip (aproximadamente do tamanho da ponta de um lápis) e que se parecem com um componente para condicionamento de sinal. A descoberta teria sido feita em 2015 e foi comunicada aos órgãos de segurança dos EUA. E pela análise do governo Americano, esta operação teria sido resultado de uma falha de segurança na cadeia de produção feita pelo exército Chinês o People’s Liberation Army em uma unidade especializada em ataques de hardware.
O chip em questão apesar de seu pequeno tamanho, tem uma grande liberdade de acesso pois ele está conectado ao baseboard management controller, um chip que permite o acesso à placa remotamente mesmo que a placa esteja desligada ou apresente mal funcionamento como uma forma de manutenção remota para os administradores. O chip em questão pode manipular areas do sistema operacional, modificando seu comportamento, por exemplo desabilitando a verificação de senhas e abrindo backdoors.
Mkis informações podem ser vistas no artigo da Bloomberg que serviu de parte para este texto:
- [1] https://www.bloomberg.com/news/features/2018-10-04/the-big-hack-how-china-used-a-tiny-chip-to-infiltrate-america-s-top-companies
