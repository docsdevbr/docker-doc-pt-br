---
# Copyright (c) 2013-2025 Docker Inc.
# Docker and the Docker logo are trademarks or registered trademarks of Docker,
# Inc. in the United States and/or other countries.
# Docker, Inc. and other parties may also have trademark rights in other terms
# used herein.
#
# Documentation licensed under the Apache License, Version 2.0.
# The original work was translated from English into Brazilian Portuguese.
# https://github.com/docker/docs/blob/main/LICENSE

source_url: https://github.com/docker/docs/blob/main/content/get-started/docker-concepts/the-basics/what-is-a-container.md
revision: 656d1a871c6837fae1e4538b82a3a5c01b70ed1e
status: ready

title: O que é um contêiner?
weight: 10
keywords: conceitos, construção, imagens, contêiner, docker desktop
description: |
  Esta página conceitual ensinará sobre contêineres e fornecerá uma rápida
  introdução onde você executará seu primeiro contêiner.
aliases:
- /guides/walkthroughs/what-is-a-container/
- /guides/walkthroughs/run-a-container/
- /guides/walkthroughs/
- /get-started/run-your-own-container/
- /guides/docker-concepts/the-basics/what-is-a-container/
---
{{< youtube-embed W1kWqFkiu7k >}}

## Explicação

Imagine que você está desenvolvendo uma aplicação _web_ matadora que tem três
componentes principais - um _frontend_ React, uma API Python e um banco de dados
PostgreSQL.
Se você quisesse trabalhar neste projeto, teria que instalar o Node, Python e
PostgreSQL.

Como você garante que tem as mesmas versões que as outras pessoas
desenvolvedoras do seu time?
Ou seu sistema de CI/CD?
Ou o que é usado em produção?

Como você garante que a versão do Python (ou Node ou o banco de dados) que sua
aplicação precisa não seja afetada pelo que já está na sua máquina?
Como você gerencia potenciais conflitos?

É aí que entram os contêineres!

O que é um contêiner?
Simplificando, os contêineres são processos isolados para cada um dos
componentes da sua aplicação.
Cada componente - a aplicação _frontend_ React, o motor da API Python e o banco
de dados - é executado em seu próprio ambiente isolado, completamente isolado de
todo o resto na sua máquina.

Aqui está o que os torna incríveis. Os contêineres são:

* Autocontidos.
  Cada contêiner tem tudo o que precisa para funcionar sem depender de nenhuma
  dependência pré-instalada na máquina hospedeira.
* Isolados.
  Como os contêineres são executados isoladamente, eles têm influência mínima na
  máquina hospedeira e em outros contêineres, aumentando a segurança das suas
  aplicações.
* Independentes.
  Cada contêiner é gerenciado de forma independente.
  Excluir um contêiner não afetará nenhum outro.
* Portáteis.
  Os contêineres podem ser executados em qualquer lugar!
  O contêiner que é executado na sua máquina de desenvolvimento funcionará da
  mesma forma em um _data center_ ou em qualquer lugar na nuvem!

### Contêineres _versus_ máquinas virtuais (VMs)

Sem entrar muito em detalhes, uma VM é um sistema operacional inteiro com seu
próprio _kernel_, _drivers_ de _hardware_, programas e aplicações.
Iniciar uma VM apenas para isolar uma única aplicação é muita sobrecarga.

Um contêiner é simplesmente um processo isolado com todos os arquivos
necessários para ser executado.
Se você executar vários contêineres, todos eles compartilharão o mesmo _kernel_,
permitindo que você execute mais aplicações usando menos infraestrutura.

> **Usando VMs e contêineres juntos**
>
> Muitas vezes, você verá contêineres e VMs usados juntos.
> Como exemplo, em um ambiente de nuvem, as máquinas provisionadas são
> normalmente VMs.
> No entanto, em vez de provisionar uma máquina para executar uma aplicação, uma
> VM com um tempo de execução de contêiner pode executar várias aplicações em
> contêineres, melhorando a utilização de recursos e reduzindo custos.


## Experimente

Nesta prática, você verá como executar um contêiner Docker usando a GUI do
Docker Desktop.

{{< tabs group=concept-usage persist=true >}}
{{< tab name="Usando a GUI" >}}

Use as seguintes instruções para executar um contêiner.

1. Abra o Docker Desktop e selecione o campo **Search** na barra de navegação
   superior.

2. Especifique `welcome-to-docker` na entrada de pesquisa e selecione o botão
   **Pull**.

    ![Uma captura de tela do Painel do Docker mostrando o resultado da pesquisa para a imagem welcome-to-docker do Docker](images/search-the-docker-image.webp?border=true&w=1000&h=700)

3. Depois que a imagem for baixada com sucesso, selecione o botão **Run**.

4. Expanda a opção **Optional settings**.

5. Em **Container name**, especifique `welcome-to-docker`.

6. Em **Host port**, especifique `8080`.

    ![Uma captura de tela do Painel do Docker mostrando a caixa de diálogo de execução do contêiner com welcome-to-docker digitado como o nome do contêiner e 8080 especificado como o número da porta](images/run-a-new-container.webp?border=true&w=550&h=400)

7. Selecione **Run** para iniciar seu contêiner.

Parabéns! Você acabou de executar seu primeiro contêiner! 🎉

### Visualize seu contêiner

Você pode visualizar todos os seus contêineres acessando a visualização
**Containers** do Painel do Docker.

![Captura de tela da visualização do contêiner da GUI do Docker Desktop mostrando o contêiner welcome-to-docker em execução na porta 8080 da máquina hospedeira](images/view-your-containers.webp?border=true&w=750&h=600)

Este contêiner executa um servidor _web_ que exibe um site simples.
Ao trabalhar com projetos mais complexos, você executará partes diferentes em
contêineres diferentes.
Por exemplo, você pode executar um contêiner diferente para o _frontend_,
_backend_ e banco de dados.

### Acesse o _frontend_

Quando você iniciou o contêiner, expôs uma das portas do contêiner na sua
máquina.
Pense nisso como criar uma configuração para permitir que você se conecte
através do ambiente isolado do contêiner.

Para este contêiner, o _frontend_ é acessível na porta `8080`.
Para abrir o site, selecione o _link_ na coluna **Port(s)** do seu contêiner ou
visite [http://localhost:8080](https://localhost:8080) no seu navegador.

![Captura de tela da página inicial vinda do contêiner em execução](images/access-the-frontend.webp?border)

### Explore seu contêiner

O Docker Desktop permite que você explore e interaja com diferentes aspectos do
seu contêiner.
Faça um teste.

1. Vá para a visualização **Containers** no Painel do Docker.

2. Selecione seu contêiner.

3. Selecione a aba **Files** para explorar o sistema de arquivos isolado do seu
   contêiner.

    ![Captura de tela do Painel do Docker mostrando os arquivos e diretórios dentro de um contêiner em execução](images/explore-your-container.webp?border)

### Pare seu contêiner

O contêiner `docker/welcome-to-docker` continua em execução até que você o pare.

1. Vá para a visualização **Containers** no Painel do Docker.

2. Localize o contêiner que você gostaria de parar.

3. Selecione a ação **Stop** na coluna **Actions**.

    ![Captura de tela do Painel do Docker com o contêiner de boas-vindas selecionado e sendo preparado para parar](images/stop-your-container.webp?border)

{{< /tab >}}
{{< tab name="Usando a CLI" >}}

Siga as instruções para executar um contêiner usando a CLI:

1. Abra o terminal da CLI e inicie um contêiner usando o comando
   [`docker run`](/reference/cli/docker/container/run/):

    ```console
    $ docker run -d -p 8080:80 docker/welcome-to-docker
    ```

    A saída deste comando é o ID completo do contêiner.

Parabéns! Você acabou de iniciar seu primeiro contêiner! 🎉

### Visualize seus contêineres em execução

Você pode verificar se o contêiner está ativo e em execução usando o comando [`docker ps`](/reference/cli/docker/container/ls/):

```console
docker ps
```

Você verá uma saída como a seguinte:

```console
 CONTAINER ID   IMAGE                      COMMAND                  CREATED          STATUS          PORTS                      NAMES
 a1f7a4bb3a27   docker/welcome-to-docker   "/docker-entrypoint.…"   11 seconds ago   Up 11 seconds   0.0.0.0:8080->80/tcp       gracious_keldysh
```

Este contêiner executa um servidor _web_ que exibe um site simples.
Ao trabalhar com projetos mais complexos, você executará partes diferentes em
contêineres diferentes.
Por exemplo, um contêiner diferente para o _frontend_, _backend_ e banco de
dados.

> [!TIP]
>
> O comando `docker ps` mostrará _apenas_ os contêineres em execução.
> Para visualizar os contêineres parados, adicione o sinalizador `-a` para
> listar todos os contêineres: `docker ps -a`.


### Acesse o _frontend_

Quando você iniciou o contêiner, expôs uma das portas do contêiner na sua
máquina.
Pense nisso como criar uma configuração para permitir que você se conecte
através do ambiente isolado do contêiner.

Para este contêiner, o _frontend_ é acessível na porta `8080`.
Para abrir o site, selecione o link na coluna **Port(s)** do seu contêiner ou
visite [http://localhost:8080](http://localhost:8080) no seu navegador.

![Captura de tela da página inicial do servidor web Nginx, vinda do contêiner em execução](images/access-the-frontend.webp?border)

### Pare seu contêiner

O contêiner `docker/welcome-to-docker` continua em execução até que você o pare.
Você pode parar um contêiner usando o comando `docker stop`.

1. Execute `docker ps` para obter o ID do contêiner.

2. Forneça o ID ou nome do contêiner para o comando
   [`docker stop`](/reference/cli/docker/container/stop/):

    ```console
    docker stop <the-container-id>
    ```

> [!TIP]
>
> Ao referenciar contêineres por ID, você não precisa fornecer o ID completo.
> Você só precisa fornecer o suficiente do ID para torná-lo único.
> Como exemplo, o contêiner anterior pode ser parado executando o seguinte
> comando:
>
> ```console
> docker stop a1f
> ```

{{< /tab >}}
{{< /tabs >}}

## Recursos adicionais

Os links a seguir fornecem orientação adicional sobre contêineres:

- [Executando um contêiner](/engine/containers/run/)
- [Visão geral do contêiner](https://www.docker.com/resources/what-container/)
- [Por que Docker?](https://www.docker.com/why-docker/)

## Próximos passos

Agora que você aprendeu o básico de um contêiner Docker, é hora de aprender
sobre imagens Docker.

{{< button text="What is an image?" url="what-is-an-image" >}}
