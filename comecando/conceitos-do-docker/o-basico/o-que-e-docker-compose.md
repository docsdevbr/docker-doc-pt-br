---
source_url: https://github.com/docker/docs/blob/main/content/get-started/docker-concepts/the-basics/what-is-docker-compose.md
revision: 9d975a92a6b6076f7ddcc0c6701247d425a4cf9f
status: ready
license: https://github.com/docker/docs/blob/main/LICENSE

title: O que é Docker Compose?
weight: 40
keywords: conceitos, construção, imagens, container, docker desktop
description: O que é Docker Compose?
aliases:
  - /guides/walkthroughs/multi-container-apps/
  - /guides/docker-concepts/the-basics/what-is-docker-compose/
---

# O que é Docker Compose?

<iframe width="895" height="487" src="https://www.youtube.com/embed/xhcUIK4fGtY"
title="Conceitos do Docker: O que é Docker Compose?"
frameborder="0"
allow="accelerometer; autoplay; clipboard-write; encrypted-media;
gyroscope; picture-in-picture; web-share"
referrerpolicy="strict-origin-when-cross-origin"
allowfullscreen></iframe>

## Explicação

Se você seguiu os guias até agora, você tem trabalhado com aplicações de
contêiner único.
Mas, agora você quer fazer algo mais complicado - executar bancos de dados,
filas de mensagens, _caches_ ou uma variedade de outros serviços.
Você instala tudo em um único contêiner?
Executa vários contêineres?
Se você executa vários, como você conecta todos eles entre si?

Uma prática recomendada para contêineres é que cada contêiner deve fazer uma
coisa e fazê-la bem.
Embora haja exceções a essa regra, evite a tendência de ter um contêiner fazendo
várias coisas.

Você pode usar vários comandos `docker run` para iniciar vários contêineres.
Mas, você logo perceberá que precisará gerenciar redes, todos os sinalizadores
necessários para conectar contêineres a essas redes e muito mais.
E quando terminar, a limpeza é um pouco mais complicada.

Com o Docker Compose, você pode definir todos os seus contêineres e suas
configurações em um único arquivo YAML.
Se você incluir esse arquivo em seu repositório de código, qualquer pessoa que
clonar seu repositório poderá começar a usar os contêineres com um único
comando.

É importante entender que o Compose é uma ferramenta declarativa - você
simplesmente o define e pronto.
Você nem sempre precisa recriar tudo do zero.
Se fizer uma alteração, execute `docker compose up` novamente e o Compose
reconciliará as alterações no seu arquivo e as aplicará de forma inteligente.

> **Dockerfile _versus_ arquivo Compose**
>
> Um Dockerfile fornece instruções para construir uma imagem de contêiner
> enquanto um arquivo Compose define os contêineres que serão executados.
> Muitas vezes, um arquivo Compose faz referência a um Dockerfile para construir
> uma imagem para usar em um serviço específico.

## Experimente

Nesta prática, você aprenderá como usar o Docker Compose para executar uma
aplicação multicontêiner.
Você usará uma aplicação simples de lista de tarefas criado com Node.js e MySQL
como um servidor de banco de dados.

### Inicie a aplicação

Siga as instruções para executar a aplicação de lista de tarefas em seu sistema.

1. [Baixe e instale](https://www.docker.com/products/docker-desktop/) o Docker
   Desktop.

2. Abra um terminal e
   [clone esta aplicação de exemplo](https://github.com/dockersamples/todo-list-app):
   ```shell
   git clone https://github.com/dockersamples/todo-list-app
   ```

3. Navegue até o diretório `todo-list-app`:
   ```shell
   cd todo-list-app
   ```
   Dentro deste diretório, você encontrará um arquivo chamado `compose.yaml`.
   Este arquivo YAML é onde toda a mágica acontece!
   Ele define todos os serviços que compõem sua aplicação, juntamente com suas
   configurações.
   Cada serviço especifica sua imagem, portas, volumes, redes e quaisquer outras
   configurações necessárias para sua funcionalidade.
   Reserve um tempo para explorar o arquivo YAML e se familiarizar com sua
   estrutura.

4. Use o comando
   [`docker compose up`](../../../reference/cli/docker/compose/up.md) para
   iniciar a aplicação:
   ```shell
   docker compose up -d --build
   ```
   Ao executar este comando, você deverá ver uma saída como esta:
   ```shell
   [+] Running 4/4
   ✔ app 3 layers [⣿⣿⣿]      0B/0B            Pulled           7.1s
     ✔ e6f4e57cc59e Download complete                          0.9s
     ✔ df998480d81d Download complete                          1.0s
     ✔ 31e174fedd23 Download complete                          2.5s
   [+] Running 2/4
     ⠸ Network todo-list-app_default           Created         0.3s
     ⠸ Volume "todo-list-app_todo-mysql-data"  Created         0.3s
     ✔ Container todo-list-app-app-1           Started         0.3s
     ✔ Container todo-list-app-mysql-1         Started         0.3s
   ```
   Muita coisa aconteceu aqui! Algumas coisas para destacar:
    * Duas imagens de contêiner foram baixadas do Docker Hub - node e MySQL;
    * Uma rede foi criada para sua aplicação;
    * Um volume foi criado para persistir os arquivos de banco de dados entre
      reinicializações do contêiner;
    * Dois contêineres foram iniciados com todas as configurações necessárias.
   Se isso parece muita coisa, não se preocupe! Você chegará lá!

5. Com tudo agora instalado e funcionando, você pode abrir
   [http://localhost:3000](http://localhost:3000) em seu navegador para ver o
   site.
   Sinta-se à vontade para adicionar itens à lista, marcá-los e removê-los.
   ![Uma captura de tela de uma página web mostrando a aplicação de lista de tarefas em execução na porta 3000](images/todo-list-app.webp?border=true&w=950&h=400)

6. Se você observar a GUI do Docker Desktop, poderá ver os contêineres e se
   aprofundar em suas configurações.
   ![Uma captura de tela do painel do Docker Desktop mostrando a lista de contêineres executando a aplicação todo-list](images/todo-list-containers.webp?border=true&w=950&h=400)

### Remova tudo

Como esta aplicação foi iniciada usando o Docker Compose, é fácil remover tudo
quando terminar.

1. Na CLI, use o comando
   [`docker compose down`](../../../reference/cli/docker/compose/down.md) para
   remover tudo:
   ```shell
   docker compose down
   ```
   Você verá uma saída semelhante à seguinte:
   ```shell
   [+] Running 2/2
   ✔ Container todo-list-app-mysql-1  Removed        2.9s
   ✔ Container todo-list-app-app-1    Removed        0.1s
   ✔ Network todo-list-app_default    Removed        0.1s
   ```
   > **Persistência de volumes**
   >
   > Por padrão, os volumes _não são_ removidos automaticamente quando você
   > remove uma pilha do Compose.
   > A ideia é que você pode querer os dados de volta se iniciar a pilha
   > novamente.
   >
   > Se você quiser remover os volumes, adicione o sinalizador `--volumes` ao
   > executar o comando `docker compose down`:
   >
   > ```shell
     docker compose down --volumes
     ```

2. Como alternativa, você pode usar a GUI do Docker Desktop para remover os
   contêineres selecionando a pilha de aplicações e selecionando o botão
   **Delete**.
   ![Uma captura de tela da GUI do Docker Desktop mostrando a visualização dos contêineres com uma seta apontando para o botão "Delete"](images/todo-list-delete.webp?w=930&h=400)

   > **Usando a GUI para pilhas do Compose**
   >
   > Observe que se você remover os contêineres de uma aplicação Compose na GUI,
   > ele removerá apenas os contêineres.
   > Você terá que remover manualmente a rede e os volumes se quiser fazer isso.

Neste tutorial, você aprendeu como usar o Docker Compose para iniciar e parar
uma aplicação multicontêiner.

## Recursos adicionais

Esta página foi uma breve introdução ao Compose.
Nos recursos a seguir, você pode se aprofundar no Compose e em como escrever
arquivos do Compose.

* [Visão geral do Docker Compose](../../../manuals/compose/index.md)
* [Visão geral da CLI do Docker Compose](../../../reference/cli/docker/compose/index.md)
* [Como o Compose funciona](../../../manuals/compose/intro/compose-application-model.md)
