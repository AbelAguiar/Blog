---

layout: post
title:  "Git flow com maestria"
date:   2019-05-11 08:30:23 -0300
description: "Porque usar git flow e aplicando formas práticas de usar"
categories: ferramentas
tags: [git, git-flow]
author: "Abel Aguiar"
authorUrl: http://abelaguiar.github.io
imageBanner: 01-git-flow-com-maestria.png

---

### Git como ferramenta essencial

Sendo bem simples, é uma ferramenta de versionamento de código que melhora a forma de trabalhar com projetos e aplicações, ajudando na interação entre os desenvolvedores, assim temos um repositório ou local que centraliza todos os arquivos da aplicação e nele vamos ter inserções de linhas de código através do git, esse repositório pode também ser um servidor diferente da sua máquina local que facilita a centralização do desenvolvimento, pode ser criado dentro de sua empresa, como explica a [documentação][git-configuracao-servidor], pode usar também através de serviços na internet como [bitbucket][bitbucket], [github][github] e [gitlab][gitlab].

[github]: https://github.com
[bitbucket]: https://bitbucket.org
[gitlab]: https://gitlab.com
[git-configuracao-servidor]: https://git-scm.com/book/pt-br/v1/Git-no-Servidor-Configurando-o-Servidor

Git é uma ferramenta criada e desenvolvida para funcionar na plataforma linux, sendo assim tem diversos tipos de comandos, em outros sistemas existe suporte de forma limitada, onde é feito uma virtualização de uma base linux e nela o git será instalado e executado, linux como plataforma nativa é mais fácil para começa, mas fica a seu gosto.

O que vamos abordar nesse post são de comandos básicos ao avançado, daí vamos do git ao git flow. 

As ferramentas que vamos trabalhar nesse projeto serão:

* Linux (Fedora ou Ubunto).
* Git
* Git Flow

No linux faça a [instalação do git][instalando-git], vá na pasta do projeto pelo terminal e daí vamos aos comandos básicos:

[instalando-git]: https://git-scm.com/book/pt-br/v1/Primeiros-passos-Instalando-Git

```sh
  git init

  git add --all

  git commit -m “init project”
```

Assim o git é iniciado no seu projeto e você cria a primeira versão através do commit “init project”. Agora vamos subir o projeto para um servidor onde virará o repositório do projeto:

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

Essa ferramenta seria como um PLUS para o git, atuando no tratamento de tarefas e suas versões de código, tendo uma separação de pequenas correções a grande módulos, desde uma correção de bug a manutenção de partes inteiras de um sistema. 

Git flow foi criado por [Vincent Driessen][vincent], agradeçam esse cara.

[vincent]: https://nvie.com/about

Como tratamos no começo do post sobre o básico de git, aqui vou explicar como usar e em que ocasiões usar, pelo menos dentro da minha experiência.

Para entender como funciona os tipos de abordagens do git flow, como **hotfix** e **feature**, temos que entender primeiro o que é uma branch. Quando criamos um projeto e iniciamos com o git, automaticamente é criado uma branch chamada **master**, podemos enteder ela como se fosse um caminho a pecorrer e dentro dele temos as pegadas que chamamos de commits, esse conjunto de pegadas dentro de um caminho chamos de branch, e cada uma tem um significado, master no caso é a branch principal, ou nosso código final.

Vamos iniciar a utilização da ferramenta, primeiro [instale o git flow][instalando-git-flow] no linux e na seguência entre no terminal, vá até a pasta do projeto, onde o git já tenha sido iniciado e execulte o comando abaixo:

[instalando-git-flow]: https://danielkummer.github.io/git-flow-cheatsheet/index.pt_BR.html

```sh
  git flow init
```

Todas as opções que aparecem ao executar o comando de inicialização devem ser aceitas.

```sh
Which branch should be used for bringing forth production releases?
   - master
Branch name for production releases: [master] 
Branch name for "next release" development: [develop] 

How to name your supporting branch prefixes?
Feature branches? [feature/] 
Release branches? [release/] 
Hotfix branches? [hotfix/] 
Support branches? [support/] 
Version tag prefix? []
```

---

#### Hotfix

Hotfix são mudanças pequenas como correções de bugs, os commits gerados dentro do hotfix vão direto para a branch MASTER quando finalizado, passando da versão de 1.0.0 para 1.0.1 através das tags.

```sh
  git flow hotfix start <1.0.0 version>
```

Após executar o comando, uma branch é criada do tipo hotfix com o nome informado, particulamente ao hotfix coloco o nome da versão na qual o bug vai ser corrigido. Na seguência faça as correções e no final crio um commit como o comando abaixo:

```sh
  git add --all

  git commit -m "update project"
```

Depois do commit criado, finalize o hotfix:

```sh
  git flow hotfix finish <1.0.0 version>
```

Finalizando o hotfix temos uma release sendo feita de forma automática, que será explicado mais a frente o que acontece nesse processo, uma nova versão é criada e envio tudo o que voi feito até mesmo a versão para o servidor do repositório.

**Observação:** Sobre versões, existe um site que explica sobre [versionamento semântico][versionamento], que é uma forma de organizar melhor as nomenclaturas de versões para sua aplicação.

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

Finalize a feature com o comando abaixo:

```sh
  git flow feature finish <nome>
```

Próximo passo ao finalizar a feature é criar uma release.

---

#### Release

É a forma de alinhar todas as branch, nivelando todos os commits nas branch master e develop, como mostrei anteriormente ao criar um hotfix ou feature, uma branch é criada com o nome informado, ao finalizar a branch é destruida, só que após isso o processo é diferente de hotfix e feature.

Ao finalizar o hotfix, os commits criados são mandados para a MASTER e DEVELOP, criando uma TAG de versionamento com o nome do hotfix e na feature os commits vai para a DEVELOP, assim necessitando a criação de uma release para alinhar as branchs e no final a criação de uma TAG de versionamento.

```sh
  git flow release start <1.0.0 version>

  git add --all

  git commit -m "Version 1.0.0"

  git flow release finish <1.0.0 version>
```

---

#### Finalizando

Ao finalizar todo o processo, vamos enviar os dados para algum servidor, nas branch **master**, **develop** e com a **tag**  de versionamento, subindo os commits para as branchs especificadas no repositório.

```sh
  git push origin master develop <1.0.0 version>
```

Obrigado a todos que lerem o post até aqui, deixem suas dúvidas, sugestões de correção e comentários, estarei a disposição.

#### Links de referência:

https://git-scm.com/

https://rogerdudler.github.io/git-guide/index.pt_BR.html

https://danielkummer.github.io/git-flow-cheatsheet/index.pt_BR.html
