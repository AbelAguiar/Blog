---

layout: post
title:  "Localhost com docker"
date:   2019-05-17 17:00 -0300
description: "Usando docker no seu ambiente de desenvolvmento"
categories: ferramentas
tags: [docker, docker-compose]
author: "Abel Aguiar"
authorUrl: http://abelaguiar.github.io
imageBanner: localhost-docker.png

---

## Porque docker?

Docker é uma ferramenta de virtualização que usa recursos nativos do linux (LXC), não emulando o S.O. de forma completa, mas sim alguns recursos, assim ficando mais simple e leve de funcionar nos servidores. Nos dias de hoje temos que lidar com vários tipos de aplicações que funcionam com tecnologias distintas, assim a configuração dessas máquinas fica cada vez mais complexa e ai onde o docker entra para resolver esse problema, permitindo criar scripts que automatizam esses processos, fazendo com que no seu servidor precise apenas do docker e por ele todo o trabalho é feito.

### Empacotamento

Com docker podemos empacotar todos os serviços que precisamos e criar containers, que por sua vez são isolados e tem sua própria rede, fazendo a separação dos recursos e usados de forma mais leve e de acordo com a necessidade. 

### Portátio

Dentro do desenvolvimento de software o docker se torna ainda mais prático, pela forma como novos desenvolvedores podem entrar no projeto sem se preocupar com configurações de máquina e requisitos do projeto, assim executando alguns scripts do docker a aplicação funciona sem restrições com o mesmo ambiente do servidor.

### Comparação entre virtualização comum e com docker

Na virtualização comum temos um sistema operacional sendo instalado e recursos de hardware sendo reservados para ele, tendo isolamento de rede e software. No final temos uma máquina completa, que consome recursos e espaço em disco maior do que com docker.

No docker temos uma virtualização de recursos usando LXC do linux, container é o foco, assim temos serviços como o apache2 ou ngnix, assim como seus módulos. O sistema operacional linux é o própria base usada pelo docker, assim temos compartilhamento de recursos e S.O. e isso fornece leveza em bytes e rapidez na hora de levantar o serviço, diferente de uma máquina virtual completa, que demanda mais espaço e processamento.   

### Aplicando de forma simples em seu projeto

Primeiro você deve ter uma máquina linux e nela instalar docker, tendo feito esse processo fica mais fácil, execute no seu terminal o seguinte comando para criar seu primeiro container.

```sh
docker run hello-world
```

Ele irá baixar a imagem referente ao nome fornecido no comando, existe containers e imagens dentro do docker, a imagem seria os arquivos do seu recurso instalado e o container seria a instância do sistema para executar a tarefa a partir da imagem.

### Docker compose

É uma ferramenta que automatiza a execução de todos os scripts do seu projeto, assim através de um simples comando poderá subir todos os containers sem a necessidade subir cada um, como ele é um plus do docker também precisa ser instalado, antes de continuarmos instale na sua máquina.

O projeto que vamos trabalhar nesse post é com tecnologias para a web, como na lista abaixo:

[docker]:https://docs.docker.com/install
[docker-compose]:https://docs.docker.com/compose/install/
[apache]:https://httpd.apache.org
[php]:https://www.php.net/manual/en/install.php
[mysql]:https://dev.mysql.com/downloads/installer/

* [Docker][docker]
* [Docker Compose][docker-compose]
* [Apache][apache]
* [PHP][php]
* [Mysql][mysql]

Primeiro passo é criar um arquivo chamando docker-compose.yml dentro do seu projeto e nele colocar as seguintes informações:

```
version: '2'

services:
 app:
   build:
     context: ./docker/app
   volumes:
    - .:/var/www/html
   ports:
     - 8080:80
   depends_on:
     - database

 database:
   image: mysql:5.7
   ports:
     - 3306:3306
   environment:
     - MYSQL_USER=project
     - MYSQL_PASSWORD=project
     - MYSQL_ROOT_PASSWORD=project
     - MYSQL_DATABASE=project
```

Nesse arquivo temos APP e DATABASE com suas respectiva configurações, portas, apontamentos e variáveis de ambiente, no início do arquivo temos a versão do docker-compose utilizado, temos hoje até a versão 3, cada uma tem atributos que podem ser usados para aumentar o poder de ação do docker-compose, assim temos o primeiro serviço que podemos chamar como quiser, no caso chamo de APP e nele faço algumas configurações.

Build é o primeiro atributo usado em app, nele é feito referência a imagem que vai ser usada para montar o container de APP, build irá executar um dockerfile, que terá todas a configuração da imagem, assim também poderia ser usado o atributo image, chamando ela direto do dockerhub (Dockerhub seria uma central de imagens tanto oficiais como também as suas que foram criadas). No caso da configuração que fiz acima ele vai em uma pasta chamada docker/app e lá estará nosso dockerfile com o conteúdo abaixo:

```
FROM php:7.1-apache

MAINTAINER Abel Aguiar <abelaguiarce@gmail.com>

RUN apt update \
   && apt install -y \
       curl \
       git \
       vim \
       openssl \
       libpq-dev \
       libxml2-dev \
       libicu-dev \
       libmcrypt-dev \
       locales \
       libmagickwand-dev --no-install-recommends \
       libfreetype6-dev \
       libjpeg62-turbo-dev \
       libpng-dev \
   && a2enmod rewrite

RUN docker-php-ext-configure intl \
   && pecl install imagick  \
   && docker-php-ext-enable imagick

RUN docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/

RUN docker-php-ext-install -j$(nproc)\
       ctype dom iconv intl json mbstring opcache pdo_mysql mysqli \
       session simplexml tokenizer xml gd

RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/bin --filename=composer \
   && echo 'error_reporting = E_ALL' >> /usr/local/etc/php/conf.d/php-error-reporting.conf \
   && echo 'display_errors = On' >> /usr/local/etc/php/conf.d/php-error-reporting.conf

ADD 000-default.conf /etc/apache2/sites-available/000-default.conf
```

Também precisará de um arquivo chamado 000-default.conf, nele será configurado nosso host, ou seja, para acessarmos nosso aplicação por um browser, assim quando for num servidor podemos configurar um domínio ou localmente pode configurar seu próprio IP.

```
<VirtualHost *:80>
   #ServerName www.example.com
   #ServerAdmin webmaster@localhost
   DocumentRoot /var/www/html/public
   ErrorLog ${APACHE_LOG_DIR}/error.log
   CustomLog ${APACHE_LOG_DIR}/access.log combined
   #Include conf-available/serve-cgi-bin.conf
</VirtualHost>
```

Assim temos o build da imagem pronta, seguindo para a configuração de porta de acesso, volume e dependência de outros containers, como os container são isolados da rede temos que apontar uma porta externa da máquina para um porta dentro do container como temos no docker-compose 8080:80, assim internamente no container a porta usada é a 80 e a de acesso externamente será a 8080, por exemplos poderíamos acessar a aplicação pelo link http://localhost:8080.

Volume é quando temos que pegar arquivos fora do container para utilização dentro dele, assim todo o código produzido pode ser acessado dentro do container através do volume, que no nosso docker-compose.yml faz volume da pasta atual para /var/www/html, que é uma pasta padrão de execução do apache para arquivos html e php. Por último temos depends_on que faz que a execução e construção do container dependa de outro serviço, que no nosso caso é o database e nesse mesmo atributo é feito um link dos containers referentes ao nome do serviço informado.

No database temos a chamada da imagem do mysql com sua versão, forneço qual as informações quero para acesso o banco, assim como também porta e volume dos dados salvos do banco. Tendo todos esse arquivos dentro do seu projeto e com docker e docker-compose instalados no seu linux, é só executar o comando abaixo dentro do terminal de comando:

```
docker-compose up -d
```

Up para criar os containers e -d para que eles fiquem em segundo plano, seguindo todos os passos os containers e imagens serão criadas e executando os comandos abaixo você confere se ocorreu tudo bem.

```
docker ps -a
```

Obrigado a todos que leram até aqui, quero dá uma introdução para quem quer iniciar com docker, assim como reforça um poucos meus conhecimentos sobre o assunto.
