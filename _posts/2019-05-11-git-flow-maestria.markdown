---

layout: post
title:  "Git flow com maestria"
date:   2019-05-11 08:30:23 -0300
description: "Porque usar git flow e aplicando formas práticas de usar"
categories: ferramentas
tags: [git, git-flow]
author: "Abel Aguiar"
authorUrl: http://abelaguiar.github.io
imageBanner: git-flow-com-maestria.png

---

### Git como ferramenta essencial

Sendo bem simples, é uma ferramenta de versionamento de código que melhora a forma de trabalhar com projetos e aplicações, ajudando na interação entre os desenvolvedores, assim temos um repositório ou local que centraliza toda a aplicação e nele vamos ter inserções de linhas de código através do git, esse repositório é na verdade um servidor onde poderá centralizar seu trabalho, pode ser criado dentro de sua empresa, como explica a [documentação][git-configuracao-servidor], pode usar também através de serviços na internet como [bitbucket][bitbucket], [github][github] e [gitlab][gitlab].

[github]: https://github.com
[bitbucket]: https://bitbucket.org
[gitlab]: https://gitlab.com
[git-configuracao-servidor]: https://git-scm.com/book/pt-br/v1/Git-no-Servidor-Configurando-o-Servidor

Git é uma ferramenta criada e desenvolvida dentro do linux, sendo assim tem diversos tipos de comandos, em outros sistemas existe suporte só que limitado, onde é feito uma virtualização de uma base linux e nela o git será instalado e executado, linux é o sistema mais fácil para começa, mas fica a seu gosto.

O que vamos abordar nesse post são de comandos básicos ao avançado, daí vamos do git ao git flow. As ferramentas que vamos trabalhar nesse projeto serão:

* Linux (Fedora ou Ubunto).
* Git
* Git Flow

No seu linux e faça a [instalação do git][instalando-git], vá na pasta do projeto pelo terminal e daí vamos aos comandos básicos:

[instalando-git]: https://git-scm.com/book/pt-br/v1/Primeiros-passos-Instalando-Git

```sh
  git init

  git add --all

  git commit -m “init project”
```

Assim o git é iniciado no seu projeto e você cria sua primeira versão através do commit “init project”, agora vamos subir o projeto para um servidor onde virará um repositório:

```sh
  git remote add origin git@github.com:{usuario}/{nomeDoProjeto}.git

  git push -u origin master
```
Usando o github como servidor, adicionamos a origem, que é uma url, podendo ser um servidor na sua empresa ou um terceiro como é nosso caso. Para baixar o projeto em outras máquinas, use o comando abaixo:

```sh
  git clone git@github.com:{usuario}/{nomeDoProjeto}.git
```

---

### Git Flow no dia a dia

Essa ferramenta seria como um PLUS para o git, atuando em como vamos tratar as tarefas e versões do código, tendo uma separação de pequenas tarefas a grande módulos, desde uma correção de bug a manutenção de partes inteiras de seu sistema. Git flow criada por [Vincent Driessen][vincent], agradeçam esse cara.

[vincent]: https://nvie.com/about

Como tratamos no começo do post sobre o básico de git e seus comandos, aqui vou explicar como usar e em que ocasições usar, pelo menos dentro da minha esperiência.

Para entender como funciona os tipos de abordagens do git flow, como **hotfix** e **feature**, temos que entender primeiro o que é um branch. Quando criamos um projeto e iniciamos com o git, automaticamente é criado uma branch chamada **master**, podemos enteder ela como se fosse um caminho a pecorrer e dentro dele temos as pegadas que podemos chamar de commits, esse conjunto de pegadas dentro de um caminho chamos de branch, e cada uma tem um significado, master no caso é a principal.

Vamos iniciar a utilização, primeiro [instale o git flow][instalando-git-flow] no seu linux e na seguência entre no seu terminal, vá até a pasta do projeto onde o git já tenha sido iniciado e execulte o comando abaixo:

[instalando-git-flow]: https://danielkummer.github.io/git-flow-cheatsheet/index.pt_BR.html

```sh
  git flow init
```

Todas as opções que aparecem ao execultar o comando devem ser aceitas.

---

#### Hotfix

Hotfix são mudanças pequenas como correção de bugs, os commits gerados dentro do hotfix vão direto para a branch MASTER quando finalizado, passando da versão de 1.0.0 para 1.0.1 através das tags.

```sh
  git flow hotfix start <1.0.0 version>
```

Após execultar o comando, uma branch é criada do tipo hotfix com o nome informado, particulamente ao hotfix coloco o nome da versão na qual o bug vai ser corrigido. Na seguência faça as correções e no final crio um commit como o comando abaixo:

```sh
  git add --all

  git commit -m "update project"
```

Commit criado, finalizo o hotfix:

```sh
  git flow hotfix finish <1.0.0 version>
```

Finalizando o hotfix temos uma release sendo feita de forma automática, que será explicado mais a frente o que acontece nesse processo, uma nova versão é criada e envio tudo o que voi feito até mesmo a versão para o servidor do repositório.

**Observação:** sobre versões, existe um site que explica sobre [versionamento semântico][versionamento], que uma forma de organizar melhor as nomenclaturas de versões da aplicação.

[versionamento]: https://semver.org/lang/pt-BR/

```sh
  git push origin master 1.0.0
```

---

#### Feature

Usado para quando vou fazer uma grande quantidade de atividades, sendo um módulo ou desenvolvimento de uma grande funcionalidade que vai ter grandes impactos em outras funcionalidades, sendo assim uma feature trabalha apartir de uma branch diferente da master, chamamos ela de DEVELOP, quando iniciamos o git flow ela já é criada.

Então a partir da branch DEVELOP é criado uma nova branch para trabalharmos a feature e nela o nome atribuído fica a seu cargo, geralmente coloco referente ao que vou trabalhar, exemplo: **login-with-google**.

```sh
  git flow feature start <nome>
```

Faça todas as inserções de código e crie todos os commits necessários para a funcionalidade que precisa:

```sh
  git add --all

  git commit -m "update project"
```

Finalizo a feature com o comando abaixo:

```sh
  git flow feature finish <nome>
```

Próximo passo ao finalizar a feature é criar uma release.

---

#### Release

É a forma de alinhar todas as branch, nivelando todos os commits nas branch master e develop, como mostrei anteriormente ao criar um hotfix ou feature, uma branch é criada com o nome informado, ao finalizar a branch criada é destruida, só que após isso o processo é diferente para hotfix e feature.

No hotfix, ao finaliza-lo o grupo de commits são mandadas para a MASTER e na feature é mandada para a DEVELOP, assim no primeiro caso não necessitamos de uma release, porque os dados já vão para a branch principal, na feature temos que igualar MASTER e DEVELOP, e criar uma nova versão.

```sh
  git flow release start <1.0.0 version>

  git add --all

  git commit -m "Version 1.0.0"

  git flow release finish <1.0.0 version>
```

---

#### Finalizando

Ao finalizar todo o processo, vamos enviar os dados para o servidor, nas branch **master**, **develop** e com a **tag** criada de versionamento, subindo os commits para o servidor do repositório.

```sh
  git push origin master develop <1.0.0 version>
```

Obrigado a todos que leram o post até aqui, deixem suas dúvidas, sugestões de correção e comentários, estarei a disposição.