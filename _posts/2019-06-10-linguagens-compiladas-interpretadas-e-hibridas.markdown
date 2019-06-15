---

layout: post
title: "Linguagens Compliladas, Interpretadas e Híbridas"
date: 2019-06-10 08:30:23 -0300
description: ""
categories: linguagens
tags: [linguagens, programação]
author: "Abel Aguiar"
authorUrl: http://abelaguiar.github.io
imageBanner: 05-linguagens-compiladas-interpretadas-hibridas.png

---

No mundo do desenvolvimento de software temos vários tipos de linguagens, cada uma com suas características, aplicações específicas e também maneiras de funcionamento diferente, nesse post vou falar um pouco sobre elas aqui.

Para entender um pouco sobre linguagens de programação, primeiro precisamos entender como a máquina ([CPU][cpu]) vai entender nosso código. Podemos classificar em três tipo, **compilado**, **interpretado** e **híbrido**.

[cpu]: https://en.wikipedia.org/wiki/Central_processing_unit

### Linguagens Interpretadas

Nesse modelo o código gerado pelo desenvolvedor ao ser executado, ele passa primeiro por um software de interpretação que fará a leitura e na sequência execução dos comandos no sistema operacional, fazendo assim um meio de campo. Exemplos de linguagens interpretadas: PHP, Ruby e JS.

### Linguagens Compiladas

Já nesse caso, o código é passado para um compilador, que será convertido em uma linguagem nativa da máquina, para na sequência ser lido diretamente pelo processador, sem a necessidade de intermediador para a execução. Exemplos de linguagens compiladas: Assembly, C, Pascal e Fortran.

Tem a vantagem em velocidade de execução do que linguagens somente interpretadas, podendo classificar também o código compilado como linguagem de baixo nível, projetada para a leitura e processamento da máquina, sendo assembly um exemplo disso.

### Linguagens Híbridas

São aquelas que implementam as duas formas de leituras, compilado e interpretado, por exemplo o Java que tem um compilador que converte seu código para [bytecode][bytecode] e na sequência isso é lido para **JVM** ([Java Virtual Machine][jvm]) que é basicamente um interpretador, para no final ser executado pelo CPU.

[jvm]: https://en.wikipedia.org/wiki/Java_virtual_machine

[bytecode]: https://pt.wikipedia.org/wiki/Bytecode

### Falando um pouco mais…

As linguagens hoje se modernizaram bastante, criando e adotando práticas de execução e compilação de código melhores, tendo em vista essa evolução, várias linguagens surgiram implementando novas técnicas de desenvolvimento e assim melhorando o desempenho e os recursos que o programador pode usar dentro de seus software.