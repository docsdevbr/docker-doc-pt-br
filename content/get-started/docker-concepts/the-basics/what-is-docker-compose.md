---
# Copyright (c) 2013-2026 Docker Inc.
# Docker and the Docker logo are trademarks or registered trademarks of Docker,
# Inc. in the United States and/or other countries.
# Docker, Inc. and other parties may also have trademark rights in other terms
# used herein.
#
# Documentation licensed under the Apache License, Version 2.0.
# The original work was translated from English into Brazilian Portuguese.
# https://github.com/docker/docs/blob/-/LICENSE

source_url: https://github.com/docker/docs/blob/main/content/get-started/docker-concepts/the-basics/what-is-docker-compose.md
revision: c5b3cb60ad63dca4d6fc7cf19c001ba893b0c6b2
status: ready

title: O que é o Docker Compose?
weight: 40
keywords: conceitos, construção, imagens, contêiner, docker desktop
description: O que é o Docker Compose?
aliases:
 - /guides/walkthroughs/multi-container-apps/
 - /guides/docker-concepts/the-basics/what-is-docker-compose/
---

{{< youtube-embed xhcUIK4fGtY >}}

## Explicação

Se você seguiu os guias até agora, trabalhou provavelmente com aplicações de um
único contêiner.
Mas, agora você quer fazer algo mais complexo: executar bancos de dados, filas
de mensagens, caches ou uma variedade de outros serviços.
Você instala tudo em um único contêiner?
Executa vários contêineres?
Se executar vários, como conectá-los?

Uma prática recomendada para contêineres é que cada contêiner faça uma coisa e a
faça bem.
Embora haja exceções a essa regra, evite a tendência de ter um contêiner fazendo
várias coisas ao mesmo tempo.

Você pode usar vários comandos `docker run` para iniciar vários contêineres.
Mas logo perceberá que precisará gerenciar redes, todas as flags necessárias
para conectar contêineres a essas redes e muito mais.
E quando terminar, a limpeza será um pouco mais complicada.

Com o Docker Compose, você pode definir todos os seus contêineres e suas
configurações em um único arquivo YAML.
Se você incluir esse arquivo no seu repositório de código, qualquer pessoa que
clonar seu repositório poderá começar a usá-lo com um único comando.

É importante entender que o Compose é uma ferramenta declarativa - basta
defini-lo e pronto.
Nem sempre é necessário recriar tudo do zero.
Se fizer alguma alteração, execute `docker compose up` novamente e o Compose
reconciliará as alterações no seu arquivo e as aplicará de forma inteligente.

> **Dockerfile versus arquivo Compose**
>
> Um Dockerfile fornece instruções para construir uma imagem de contêiner
> enquanto um arquivo Compose define os contêineres que serão executados.
> Frequentemente, um arquivo Compose faz referência a um Dockerfile para
> construir uma imagem a ser usada em um serviço específico.

## Experimente

Nesta prática, você aprenderá a usar o Docker Compose para executar uma
aplicação multicontêiner.
Você usará uma aplicação simples de lista de tarefas desenvolvida com Node.js e
MySQL como um servidor de banco de dados.

### Inicie a aplicação

Siga as instruções para executar a aplicação de lista de tarefas no seu sistema.

1. [Baixe e instale](https://www.docker.com/products/docker-desktop/) o Docker
   Desktop.
2. Abra um terminal e
   [clone esta aplicação de exemplo](https://github.com/dockersamples/todo-list-app).

   ```console
   git clone https://github.com/dockersamples/todo-list-app
   ```

3. Navegue até o diretório `todo-list-app`:

   ```console
   cd todo-list-app
   ```

   Dentro deste diretório, você encontrará um arquivo chamado `compose.yaml`.
   É neste arquivo YAML que toda a mágica acontece!
   Ele define todos os serviços que compõem sua aplicação, juntamente com suas
   configurações.
   Cada serviço especifica sua imagem, portas, volumes, redes e quaisquer outras
   configurações necessárias para sua funcionalidade.
   Reserve um tempo para explorar o arquivo YAML e se familiarizar com sua
   estrutura.

4. Use o comando
   [`docker compose up`](/reference/cli/docker/compose/up/) para
   iniciar a aplicação:

   ```console
   docker compose up -d --build
   ```

   Ao executar este comando, você deverá ver uma saída como esta:

   ```console
   [+] Running 5/5
   ✔ app 3 layers [⣿⣿⣿]      0B/0B            Pulled          7.1s
     ✔ e6f4e57cc59e Download complete                          0.9s
     ✔ df998480d81d Download complete                          1.0s
     ✔ 31e174fedd23 Download complete                          2.5s
     ✔ 43c47a581c29 Download complete                          2.0s
   [+] Running 4/4
     ⠸ Network todo-list-app_default           Created         0.3s
     ⠸ Volume "todo-list-app_todo-mysql-data"  Created         0.3s
     ✔ Container todo-list-app-app-1           Started         0.3s
     ✔ Container todo-list-app-mysql-1         Started         0.3s
   ```

   Muita coisa aconteceu aqui!
   Algumas coisas para destacar:

   - Duas imagens de contêiner foram baixadas do Docker Hub - node e MySQL.
   - Uma rede foi criada para sua aplicação.
   - Um volume foi criado para persistir os arquivos do banco de dados entre
     reinicializações do contêiner.
   - Dois contêineres foram iniciados com todas as configurações necessárias.

   Se isso parece assustador, não se preocupe!
   Você vai chegar lá!

5. Com tudo instalado e funcionando, você pode abrir
   [http://localhost:3000](http://localhost:3000) no seu navegador para ver o
   site.
   Observe que a aplicação pode levar de 10 a 15 segundos para iniciar
   completamente.
   Se a página não carregar imediatamente, aguarde um momento e atualize a
   página.
   Fique à vontade para adicionar itens à lista, marcá-los como concluídos e removê-los.

   ![Uma captura de tela de uma página web mostrando a aplicação de lista de tarefas em execução na porta 3000](images/todo-list-app.webp?border=true&w=950&h=400)

6. Se você observar a GUI do Docker Desktop, poderá ver os contêineres e se
   aprofundar em suas configurações.

   ![Uma captura de tela do Painel do Docker Desktop mostrando a lista de contêineres executando a aplicação todo-list](images/todo-list-containers.webp?border=true&w=950&h=400)

### Remova tudo

Como esta aplicação foi iniciada usando o Docker Compose, é fácil remover tudo
quando terminar.

1. Na CLI, use o comando
   [`docker compose down`](/reference/cli/docker/compose/down/) para remover
   tudo:

   ```console
   docker compose down
   ```

   Você verá uma saída semelhante à seguinte:

   ```console
   [+] Running 3/3
   ✔ Container todo-list-app-mysql-1  Removed        2.9s
   ✔ Container todo-list-app-app-1    Removed        0.1s
   ✔ Network todo-list-app_default    Removed        0.1s
   ```

   > **Persistência de volumes**
   >
   > Por padrão, os volumes _não são_ removidos automaticamente quando você
   > remove uma pilha do Compose.
   > A ideia é que você possa querer os dados de volta se reiniciar a pilha.
   >
   > Se você quiser remover os volumes, adicione a flag `--volumes` ao executar
   > o comando `docker compose down`:
   >
   > ```console
   > docker compose down --volumes
   > [+] Running 1/0
   > ✔ Volume todo-list-app_todo-mysql-data  Removed
   > ```

2. Como alternativa, você pode usar a GUI do Docker Desktop para remover os
   contêineres selecionando a pilha de aplicações e selecionando o botão
   **Delete**.

   ![Uma captura de tela da GUI do Docker Desktop mostrando a visualização dos contêineres com uma seta apontando para o botão "Delete"](images/todo-list-delete.webp?w=930&h=400)

   > **Usando a GUI para pilhas do Compose**
   >
   > Observe que, se você remover os contêineres de uma aplicação Compose na
   > GUI, removerá apenas os contêineres.
   > Você terá que remover manualmente a rede e os volumes, se desejar.

Neste passo a passo, você aprendeu a usar o Docker Compose para iniciar e parar
uma aplicação multicontêiner.

## Recursos adicionais

Esta página foi uma breve introdução ao Compose.
Nos recursos a seguir, você pode se aprofundar no Compose e aprender a escrever
arquivos Compose.

* [Visão geral do Docker Compose](/compose/)
* [Visão geral da CLI do Docker Compose](/reference/cli/docker/compose/)
* [Como o Compose funciona](/compose/intro/compose-application-model/)
