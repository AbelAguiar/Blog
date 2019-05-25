---

layout: post
title:  "Começando com laravel"
date:   2019-05-25 10:30:00 -0300
description: "Tudo que você precisa saber para começa com laravel"
categories: frameworks
tags: [laravel, php]
author: "Abel Aguiar"
authorUrl: http://abelaguiar.github.io
imageBanner: comecando-com-laravel.jpg

---

Esse post visa dá uma introdução sobre laravel, minha visão como desenvolvedor, como também minha experiência de trabalho com ele, portanto não vamos discutir se ele é melhor do que outro ou algo assim. Boa leitura. 

## O que é um framework?

É um conjunto de código pronto para auxiliar no desenvolvimento de uma aplicação, seja ela em qual linguagem for, assim esse montante tem funções e módulos prontos para trabalhar, por exemplo, envio de email, recortar imagens, inserção de dados no banco etc.

Eles são criados para facilitar e aumentar a produtividade do desenvolvedor, fazendo que crie aplicações em menor tempo e tendo um padrão de projeto, onde outros programadores vão poder trabalhar e ingressar facilmente.

## O que é Laravel?

[**Laravel**][laravel] é um framework desenvolvido em php pelo [Taylor Otwell][taylor], tendo várias ferramentas para trabalhar com código, gerenciar e produzir aplicações, ganhando bastante popularidade entre os desenvolvedores php nos últimos tempos, pela sua documentação de fácil entendimento e  rápida adaptação.

[laravel]: https://laravel.com
[taylor]: https://twitter.com/taylorotwell

Comunidade aberta e grande, faz com que a discussão de problemas e novas funcionalidades ao framework cresça rapidamente, duas versões por ano, sendo uma com 2 anos de suporte, regras que ainda estão valendo até a data de submissão deste post. Tendo como disseminador de conteúdo o [**laracast**][laracast], mostrando desde o básico ao avançado com a ferramenta, alimentando ainda mais a comunidade com conteúdo sobre laravel, php e até boas práticas de desenvolvimento. O nome ‘Laravel’ é só um nome inventado, pra tristeza de muitos.

[laracast]: https://laracasts.com

### Rapidez

Recursos de **commandline** e utilização de composer com estruturas pré prontas, fazem o framework ser bastante adaptativo e de rápido desenvolvimento. [Eloquent][eloquent] vem para transformar sua experiência com banco de dados, assim como o trabalho com rotas, middlewares e requests. Utilizando o modelo [MVC][mvc] (**model view controller**), com recursos em javascripts para compilar sass e less, assim como também um criador de componentes [**vuejs**][vuejs] (Sei que vuejs não é apenas isso, mas estou falando do uso dele dentro do framework).

[vuejs]: https://vuejs.org
[eloquent]: https://laravel.com/docs/5.8/eloquent
[mvc]: https://en.wikipedia.org/wiki/Model%E2%80%93view%E2%80%93controller

### Popularidade

Talvez o que mais tenha deixado popular seja a emoção de trabalhar os projetos com ele, ganhando produtividade, usando técnicas de **desenvolvimento** modernas, o código simplificado, limpo e que faz o trabalho bem feito, conquistando desenvolvedores, outro ponto é a **comunidade**, muitas pessoas que trabalham e gostam de compartilhar seu conhecimento, assim como eu. Vendo pelo lado das **empresas**, acredito que seja pela rapidez na entrega de produtos com um código fácil de manter, além da facilidade de programadores aprenderem a linguagem para usar em projetos, assim não tem ninguém que resista, mas nem tudo é flores.

### Por que ganhou tanto mercado?

Quando o laravel surgiu já existia vários frameworks como **zend**, **codeigniter** e **symfony**, bem populares até hoje, tomando uma fátia do mercado o laravel chegou, conquistando os corações dos desenvolvedores e também das empresas. Teve seu começo em 2011, seguindo esse caminho até chegar na 5 versão do framework em 2015, com todo sua estrutura renovada, onde foi o divisor de águas e trouxe milhares de pessoas para o framework.

Taylor Otwell também criou várias ferramentas para auxiliar os desenvolvedores e as empresas, claro que apartir do laravel. 

### Forge

<img class="img-fluid" src="https://abelaguiar.github.io/blog/assets/img/posts/comecando-com-laravel/forge.png" alt="Ferramenta Forge">

[Forge][forge] foi criado para configuração automatizada de servidores, assim você pode criar instancias na amazon, digital ocean de forma mais simples e centralizada, independente de usa laravel ou não. Não é uma ferramenta gratuita, cobrando uma mensalidade para usa-la.

[forge]: https://forge.laravel.com/

### Spark

<img class="img-fluid" src="https://abelaguiar.github.io/blog/assets/img/posts/comecando-com-laravel/spark.png" alt="Ferramenta Spark">

Ferramenta com vários módulos prontos de cobrança, gerenciamento de times, autenticação por rede social e mais, para importar no seu laravel, [spark][spark] também é pago.

[spark]: https://spark.laravel.com/

### Horizon

<img class="img-fluid" src="https://abelaguiar.github.io/blog/assets/img/posts/comecando-com-laravel/horizon.png" alt="Ferramenta Horizon">

[Horizon][horizon] pode ser importado para o laravel apartir da versão 5.5, serve para a gerencia de filas e jobs executados em background, tendo uma interface para monitoramento, sendo gratuito.

[horizon]: https://laravel.com/docs/5.5/horizon

### Envoyer

<img class="img-fluid" src="https://abelaguiar.github.io/blog/assets/img/posts/comecando-com-laravel/envoyer.png" alt="Ferramenta Envoyer">

Trabalhar com deploy automático no [Envoyer][envoyer] de suas aplicações é muito simples, assim como outros serviços ele é pago, valendo muito apena.

[envoyer]: https://envoyer.io/

### Nova

<img class="img-fluid" src="https://abelaguiar.github.io/blog/assets/img/posts/comecando-com-laravel/nova.png" alt="Ferramenta Laravel Nova">

[Nova][nova] seria um construtor de admins, bem completo, com criação de **[CRUDs][crud]** e sistema de busca, tudo pronto, projeto tem bem mais coisas, acredito que vale apena da uma olhada.

[nova]: https://nova.laravel.com/
[crud]: https://en.wikipedia.org/wiki/Create,_read,_update_and_delete

### Lumen

<img class="img-fluid" src="https://abelaguiar.github.io/blog/assets/img/posts/comecando-com-laravel/lumen.png" alt="Framework Lumen">

[Lumen][lumen] é um mini framework baseado em laravel, onde serve para pequenos projetos, e que você pode ir evoluindo ele até chegar ao laravel que conhecemos.

Ele é bom para projetos em que não vão precisar de todos os recursos nativos do laravel, como por exemplo autenticação e envio de emails, sendo mais perfomático e simples que seu irmão mais velho.

[lumen]: https://lumen.laravel.com/

## Ferramentas 

Necessário para executar o conteúdo deste post:

* [PHP 7.1.3][php]
* [Composer][composer]
* [Framework Laravel][laravel]
* [Linux][linux]

[php]: https://www.php.net/releases/7_1_0.php
[composer]: https://getcomposer.org
[laravel]: https://laravel.com
[linux]: https://www.linux.org

### Colocando para funcionar

Através do terminal crie uma pasta em algum local que preferir, assim execute o comando abaixo para baixar o framework:

```sh
composer create-project --prefer-dist laravel/laravel ‘NOME-PROJETO’
```

Onde tem NOME-PROJETO, coloque o nome que desejar, depois pelo terminal entre no projeto:

```sh
cd /’NOME-PROJETO’
```

Na seguência

```sh
php artisan serve
```

Ao fazer esses passos vá no browser e cole http://127.0.0.1:8000, se aparecer algo como na imagem abaixo foi porque ocorreu tudo bem.

<img class="img-fluid" src="https://abelaguiar.github.io/blog/assets/img/posts/comecando-com-laravel/tela-home-framework-laravel.png" alt="Tela home framework laravel">

A partir daqui você vai moldando a aplicação como você quer, seguindo a documentação.

### Conclusão

Não existe bala de prata, sou do tipo que acredita que tem tecnologias certas para ocasiões certas, assim faça uma análise a partir dos seus conhecimento use laravel ou outro framework, conhecimento de outras tecnologias é sempre bom, assim como outras linguagens, como o próprio Taylor Otwell, antes tinha um background de .NET, e assim pode ser com você ter cada vez mais conhecimentos, onde não inutiliza outros e sim soma. Bom isso é tudo, obrigado por lerem até aqui.