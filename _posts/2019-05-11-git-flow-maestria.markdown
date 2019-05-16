---

layout: post
title:  "Git flow com maestria"
date:   2019-05-11 08:30:23 -0300
description: "É a ferramenta versionamento e ótima para todos os projetos"
categories: ferramentas
tags: [git, git-flow]
author: "Abel Aguiar"

---

### Git como ferramenta essencial

Sendo bem simples, é uma ferramenta de versionamento de código que melhora a forma de trabalha do projeto e até mesmo na interação com seus colegas de trabalho, assim temos um repositório que centraliza todo o seu projeto e nele vamos ter inserções de linhas de código através do git, esse repositório é na verdade um servidor onde poderá centralizar seu trabalho, pode ser criado dentro de sua empresa, como explica a [documentação][git-configuracao-servidor], pode usar também através de serviços na internet como  [bitbucket][bitbucket], [github][github] e [gitlab][gitlab].

[github]: https://github.com
[bitbucket]: https://bitbucket.org
[gitlab]: https://gitlab.com
[git-configuracao-servidor]: https://git-scm.com/book/pt-br/v1/Git-no-Servidor-Configurando-o-Servidor

Git é uma ferramenta criada e desenvolvida dentro do linux, sendo assim ela tem diversos tipos de comandos, outros sistemas tem suporte a ele? Sim, tem suporte, só que através de ferramentas, fica a dica, usar linux é muito divertido, nada contra quem usa windows, fique avontade para usar o que preferir, mas o que vamos abordar nesse posts é comandos básicos do git e vamos até o git flow, que seria um passo mais avançado para quem quer se aprofundar na ferramenta.

Caso estaja usando linux e ja tenha [instalado o git][instalando-git], primeiro vá na pasta do seu projeto pelo terminal e daí vamos aos comandos básicos:

[instalando-git]: https://git-scm.com/book/pt-br/v1/Primeiros-passos-Instalando-Git

```sh
  git init
  git add --all
  git commit -m “init project”
```

Assim o git é iniciado no seu projeto e você cria sua primeira versão através do commit “init project”, agora vamos subir o projeto para um servidor onde virará um repositório:

```sh
  git remote add origin https://github.com/{usuario}/{nomeDoProjeto}.git
  git push -u origin master
```
Usando o github como servidor, adicionamos a origem, que é uma url, podendo ser servidor na sua empresa ou um terceiro como é nosso caso. Para baixar o projeto em outras máquinas, use o comando abaixo:

```sh
  git clone https://github.com/{usuario}/{nomeDoProjeto}.git
```

### Git Flow no dia a dia

Essa ferramenta seria como um PLUS para o git, atuando em como vamos tratar as tarefas e versões do código, tendo uma separação de pequenas tarefas a grande módulos, desde uma correção de bug e manutenção de partes inteiras de seu sistema.

Como tratamos no começo do post sobre o básico de git e seus comandos, aqui vou explicar como usar e em que ocasioões usar, pelo menos dentro da minha esperiência.

Para entender como funciona os tipos de abordagens do git flow, como hotfix e feature, temos que entender primeiro o que é um branch. Quando criamos um projeto e iniciamos com o git, automaticamente é criado uma branch chamada master, podemos enteder ela como se fosse um caminho a pecorrer e dentro dele temos as pegadas que podemos chamar de commits, esse conjunto de pegadas dentro de um caminho chamos de branch, e cada uma tem um significado, master no caso é a principal.

Vamos iniciar a utilização do git flow, primeiro instale ele no seu linux e na seguência entre no seu terminal, vá até a pasta do projeto onde o git já tenha sido iniciado e execulte o comando abaixo:

```sh
  git flow init
```

Todas as opções que aparecem ao execultar o comando devem ser aceitas.

#### Hotfix

Hotfix são mudanças pequenas como correção de bugs, os commits gerados dentro do hotfix vão direto para a branch MASTER quando finalizado, passando da versão de 1.0.0 para 1.0.1 por exemplo.

```sh
  git flow hotfix start <1.0.0 version>
```

Após execultar o comando, uma branch é criada do tipo hotfix e com o nome que foi dado a ela, particulamente ao hotfix prefiro da o nome da versão na qual o bug vai ser corrigido. Na seguência faça suas correções, inicie um commit como no comando abaixo:

```sh
  git add --all
  git commit -m "update project"
```

Após criar o commit vou finalizo meu hotfix:

```sh
  git flow hotfix finish <1.0.0 version>
```

Finalizando o hotfix temos uma release sendo feita de forma automática, que será explicado mais a frente o que acontece nesse processo, uma nova versão é criada e envio tudo o que voi feito até mesmo a versão para o servidor do repositório.

**Observação:** sobre versões, existe um site que explica sobre [versionamento semântico][versionamento], que uma forma de organizar melhor as nomenclaturas de versões da aplicação.

[versionamento]: https://semver.org/lang/pt-BR/

```sh
 git push origin master 1.0.0
```

#### Feature

Usado para quando vou fazer uma grande quantidade de atividades, sendo um módulo ou desenvolvimento de uma grande funcionalidade que vai ter grandes impactos em outras funcionalidades, sendo assim uma feature trabalha apartir de uma branch diferente da master, chamamos ela de DEVELOP, quando iniciamos o git flow ela já é criada.

Então a partir da branch DEVELOP é criado uma nova branch para trabalharmos a feature e nela o nome atribuído fica a seu cargo, geralmente coloco referente ao que vou trabalhar, exemplo: **login-with-google**.

```sh
  git flow feature start <nome>
```

Faça todas as inserções de código e crie todos os commits necessários para a funcionalidade que precisa:

```sh
  git add --all<br><br>
  git commit -m "update project"
```

Finalizo a feature com o comando abaixo:

```sh
  git flow feature finish <nome>
```

Próximo passo ao finalizar a feature é criar uma release, pra que serve, onde vive e o que come.</p> 

#### Release

É a forma de alinhar todas as brach, nivelando todos os commits nas brach master e develop, como mostrei anteriormente ao criar um hotfix ou feature, uma brach é criada com o nome informado, ao finalizar a branch criada é destruida, só que após isso o processo é diferente para hotfix e feature.

No hotfix, ao finaliza-lo as informações são mandadas para a MASTER e na feature é mandada para a DEVELOP, assim no primeiro caso não necessitamos de uma release, porque os dados já vão para a branch principal, na feature temos que igualar MASTER e DEVELOP, e ao criar uma nova versão.

```sh
  git flow release start <1.0.0 version>

  git add --all

  git commit -m "Version 1.0.0"

  git flow release finish <1.0.0 version>
```

#### Finalizando

Ao finalizar envio os dados para o servidor, nas branch MASTER, DEVELOP e a tag criada de versionamento, subindo os commits da feature e version.

```sh
  git push origin master develop <1.0.0 version>
```
