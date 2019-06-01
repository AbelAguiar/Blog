---

layout: post
title:  "Editores de código, qual o melhor?"
date:   2019-05-25 10:30:00 -0300
description: "Novos editores surgem no mercado de programação, qual deles tem destaque nos dias de hoje"
categories: code-editors
tags: [editores]
author: "Abel Aguiar"
authorUrl: http://abelaguiar.github.io
imageBanner: 04-editores-codigo-qual-melhor.jpg

---

Não quero refletir opinião, dizer qual o melhor editor de texto ou algo nesse sentido, apenas trazer informações e possibilidades, tendo em mente os dados dentro do mercado atual de software e as tendências dos desenvolvedores.

## Diferenças entre editor de texto e IDE

Maioria das pessoas que entram para área de tecnologia, principalmente na de software, já deparou-se com editores de texto ou IDEs para trabalhar com código, onde essa ferramenta é extremamente essencial para facilitar e organizar textos, tendo vários tipos de atalhos e recursos de busca, substituição de texto, indentação e execução o que foi produzindo.

Falando primeiro de **IDE** ([Integrated Development Environment][IDE]), é na prática um editor de texto com várias ferramentas integradas, geralmente usado em linguagens que são compiladas, também podem ser usados por qualquer linguagem, claro que algumas com foco maior em algumas linguagens, mas quando ela é compilada, a IDE facilita a programação desse software por causa das ferramentas integradas, fazendo que a execução seja vista direto no editor.

[IDE]: https://en.wikipedia.org/wiki/Integrated_development_environment

Muito além do editor é a tecnologia que vai ser trabalhada, como mobile, onde vai depender bastante do seu editor para ver o que está sendo produzido, que faça a ligação com o máquina virtual de um celular ou até mesmo um celular físico. 

**Editor de texto**, é usado mais para linguagens interpretadas, tendo maior economia de recursos da máquina, além da velocidade de execução de suas tarefas, mas para linguagens compiladas terá que usar outras ferramentas externas ao editor para execução do código.

## Um pouco da história dos editor de texto

Nesse post vamos falar especificamente de editores de texto, sendo assim vamos explicar sobre sua necessidade nesse mercado de software que foi bastante tempo, quando nem tínhamos telas e vermos o que foi desenvolvido, cartões perfurados era bola da vez, máquinas de escrever perfuravam os cartões que por sua vez era inseridos numa leitora para daí sair o resultado em na impressora de cartão perfurado de novo, bastante trabalho.

<img class="img-fluid" src="https://abelaguiar.github.io/blog/assets/img/posts/04-editor-codigo-qual-melhor/cartao-perfurado.png" alt="Cartões Perfurados usados na programação de máquinas">

Foram surgir os primeiro editores que poderiam ser visualizados em uma tela nos anos de 1967 e 1970, que eram verdadeiros terminais de comando, vindo aí o **vi** no linux, **textEdit** no OSX e outros que foram surgindo na época, assim todos eles eram editores sem muito recursos, com edição de texto simples, mas antes era os cartões perfurados, então já era de grande ajuda esses novos editores. 

## Alguns editores populares

Antes temos abaixo uma pesquisa realizada dentro do [google trends][google-trends] para os editores que irei falar nesse post:

[google-trends]: https://trends.google.com/trends

<script type="text/javascript" src="https://ssl.gstatic.com/trends_nrtr/1754_RC01/embed_loader.js"></script> <script type="text/javascript"> trends.embed.renderExploreWidget("TIMESERIES", {"comparisonItem":[{"keyword":"Sublime text 3","geo":"BR","time":"today 12-m"},{"keyword":"Atom Editor","geo":"BR","time":"today 12-m"},{"keyword":"Vim Editor","geo":"BR","time":"today 12-m"},{"keyword":"Vscode","geo":"BR","time":"today 12-m"}],"category":0,"property":""}, {"exploreQuery":"geo=BR&q=Sublime%20text%203,Atom%20Editor,Vim%20Editor,Vscode&date=today 12-m,today 12-m,today 12-m,today 12-m","guestPath":"https://trends.google.com:443/trends/embed/"}); </script>

### [Atom][atom]

[atom]: https://atom.io

<img class="img-fluid" src="https://abelaguiar.github.io/blog/assets/img/posts/04-editor-codigo-qual-melhor/atom-editor.png" alt="Atom Editor">

Editor de código gratuito e com código aberto, desenvolvido com electron, que tem como finalidade a edição e criação de código de aplicações, sejam eles em qual linguagem for, tem integração com git e ferramentas de para estilizar o editor, é uma boa opção entre os demais. Disponível para todas as plataformas, windows, macOs e linux. Permite a instalação de pacotes, configuração de fonte, tipos e cores, assim como também integração com outras ferramentas de commandline.

### Vim

<img class="img-fluid" src="https://abelaguiar.github.io/blog/assets/img/posts/04-editor-codigo-qual-melhor/vim.jpeg" alt="Vim Editor">

Editor baseado no [vi][vi], sua interação é feita inteiramente pelo terminal, assim disponível para as plataformas unix e linux, também com pouquíssimas interação com o mouse, sendo o editor mais roots dessa lista, para se trabalhar com ele vamos ter uma lista de comandos que vão servir para buscar e substituir linhas de código, como também buscar pasta, tudo pelo teclado, sendo uma adaptação demorada, mas seguindo um bom ritmo e persistindo, passa a ser o mais eficiente de todos.

[vi]: https://en.wikipedia.org/wiki/Vi

### Sublime text 3

<img class="img-fluid" src="https://abelaguiar.github.io/blog/assets/img/posts/04-editor-codigo-qual-melhor/sublime-text-3.jpg" alt="Sublime Text 3">

Sublime surgiu em 2008 voltado para edição de código, ferramenta criada na linguagem [python][python], sendo simples na organização das pastas e navegação rápida dentro de projetos ou aplicações, com vários temas e estilos de texto que facilita a leitura com cores bem distintas, pelo seu plano de fundo padrão escuro com letras claras, chamou atenção das comunidades de desenvolvimento de software, que fazia e faz a leitura de código ficar menos cansativa durante o dia a dia.

[python]: https://pt.wikipedia.org/wiki/Python

Suportado para as plataformas windows, macOs e linux. Falando um pouco sobre licença para o [sublime][sublime], no seu site informa que ele pode ser usado para teste na forma free, porém existe uma licença no valor de 80$ dólares, eu nunca precisei, sempre usei na forma free, para aqueles que tenham o dinheiro para contribuir com a ferramenta, a compra da licença é a melhor.

[sublime]: https://www.sublimetext.com

### Visual Studio Code

<img class="img-fluid" src="https://abelaguiar.github.io/blog/assets/img/posts/04-editor-codigo-qual-melhor/vscode.png" alt="Atom Editor">

Em 2015 foi lançado pela microsoft um editor de código para todas as plataformas, windows, macOs e linux, com código aberto, seguindo uma linha parecida com o sublime text em relação a interface, porém com várias ferramentas integradas, como um gerenciador de git local e uma área de apps, que podem integrar diversas funcionalidades, assim como um terminal embutido para quem usa linux e mac, o prompt de comando no windows.

Vscode é baseado no [electron][electron], sendo uma ferramenta de desenvolvimento para aplicações desktop em [node.js][nodejs] com motor de layout no [blink][blink], assim um editor com várias destaques apareceu no mercado em 2015, no seu lançamento ele era gratuito para todos e hoje é código aberto, uma bela iniciativa da microsoft e para mercado de programadores. Segui link de um post falando um pouco sobre a ascensão do vscode nesse ultimos tempos, é uma boa leitura https://www.infoq.com/br/news/2018/12/the-rise-vscode.

[electron]: https://en.wikipedia.org/wiki/Electron_(software_framework)
[nodejs]: https://pt.wikipedia.org/wiki/Node.js
[blink]: https://pt.wikipedia.org/wiki/Blink_(motor_de_layout)

## Conclusão

No final desse post fica para cada um decidir qual editor usar, falei um pouco sobre cada um dos editores, não abordei mais que esses quatro, porque senão iria se estender muito, o melhor editor é aquele mais confortável no seu dia a dia, o que lhe traz mais produtividade, várias tecnologias nascem, cabe a nós programadores fazermos com que isso aconteça, não importando a IDE ou editor de texto, use o que achar melhor para você, mostre o que há de melhor no que você usa para as pessoas e até próximo post.

