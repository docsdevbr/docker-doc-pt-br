---
# SPDX-FileCopyrightText: 2013-2026 Docker Inc.
# Docker and the Docker logo are trademarks or registered trademarks of Docker,
# Inc. in the United States and/or other countries.
# Docker, Inc. and other parties may also have trademark rights in other terms
# used herein.
#
# SPDX-License-Identifier: Apache-2.0
# Documentation licensed under the Apache License, Version 2.0.
# The original work was translated from English into Brazilian Portuguese.
# https://github.com/docsdevbr/docker-doc-pt-br/blob/-/LICENSES/Apache-2.0.txt

source_url: https://github.com/docker/docs/blob/main/content/get-started/docker-concepts/the-basics/what-is-a-container.md
revision: f97a5fa1f8dee89a79793cf1f91bae8352c562f3
status: ready

title: O que é um contêiner?
weight: 10
keywords: conceitos, construção, imagens, contêiner, docker desktop
description: >-
  O que é um contêiner?
  Esta página conceitual ensinará sobre contêineres e fornecerá uma rápida
  prática onde você executará seu primeiro contêiner.
aliases:
- /guides/walkthroughs/what-is-a-container/
- /guides/walkthroughs/run-a-container/
- /guides/walkthroughs/
- /get-started/run-your-own-container/
- /get-started/what-is-a-container/
- /guides/docker-concepts/the-basics/what-is-a-container/
---

{{< youtube-embed W1kWqFkiu7k >}}

## Explicação

Imagine que você esteja desenvolvendo uma aplicação web incrível com três
componentes principais - um front-end React, uma API em Python e um banco de
dados PostgreSQL.
Para trabalhar nesse projeto, você precisaria instalar o Node, o Python e o
PostgreSQL.

Como você garante que tem as mesmas versões que as outras pessoas
desenvolvedoras do seu time?
Ou do seu sistema de CI/CD?
Ou do que é usado em produção?

Como você garante que a versão do Python (ou do Node ou do banco de dados) que
sua aplicação precisa não seja afetada pelo que já está na sua máquina?
Como você gerencia potenciais conflitos?

É aí que entram os contêineres!

O que é um contêiner?
Simplificando, os contêineres são processos isolados para cada um dos
componentes da sua aplicação.
Cada componente - a aplicação front-end React, o motor da API em Python e o
banco de dados - é executado em seu próprio ambiente isolado, completamente
independente do resto dos componentes na sua máquina.

É isso que os torna incríveis. Os contêineres são:

- Autocontidos.
  Cada contêiner tem tudo o que precisa para funcionar sem depender de nenhuma
  dependência pré-instalada na máquina host.
- Isolados.
  Como os contêineres são executados isoladamente, eles têm influência mínima no
  host e em outros contêineres, aumentando a segurança das suas aplicações.
- Independentes.
  Cada contêiner é gerenciado de forma independente.
  Excluir um contêiner não afetará nenhum outro.
- Portáteis.
  Os contêineres podem ser executados em qualquer lugar!
  O contêiner executado na sua máquina de desenvolvimento funcionará da mesma
  forma em um data center ou em qualquer lugar na nuvem!

### Contêineres versus máquinas virtuais (VMs)

Sem entrar muito em detalhes, uma VM é um sistema operacional completo com seu
próprio kernel, drivers de hardware, programas e aplicações.
Executar uma VM apenas para isolar uma única aplicação gera muita sobrecarga.

Um contêiner é simplesmente um processo isolado com todos os arquivos
necessários para sua execução.
Se você executar vários contêineres, todos eles compartilharão o mesmo kernel,
permitindo que você execute mais aplicações usando menos infraestrutura.

> **Usando VMs e contêineres juntos**
>
> É bastante comum ver contêineres e VMs sendo usados em conjunto.
> Por exemplo, em um ambiente de nuvem, as máquinas provisionadas normalmente
> são VMs.
> No entanto, em vez de provisionar uma máquina para executar uma aplicação, uma
> VM com um tempo de execução de contêineres pode executar várias aplicações em
> contêineres, melhorando a utilização de recursos e reduzindo custos.

## Experimente

Nesta prática, você verá como executar um contêiner Docker usando a GUI do
Docker Desktop.

{{< tabs group=concept-usage persist=true >}}
{{< tab name="Usando a GUI" >}}

Siga as instruções abaixo para executar um contêiner.

1. Abra o Docker Desktop e selecione o campo **Search** na barra de navegação
   superior.

2. Especifique `welcome-to-docker` no campo de pesquisa e selecione o botão
   **Pull**.

    ![Uma captura de tela do Painel do Docker Desktop mostrando o resultado da pesquisa para a imagem Docker welcome-to-docker](images/search-the-docker-image.webp?border=true&w=1000&h=700)

3. Após o download da imagem, selecione o botão **Run**.

4. Expanda a opção **Optional settings**.

5. No campo **Container name**, especifique `welcome-to-docker`.

6. No campo **Host port**, especifique `8080`.

   ![Uma captura de tela do Painel do Docker Desktop mostrando a caixa de diálogo de execução do contêiner com welcome-to-docker digitado como o nome do contêiner e 8080 especificado como o número da porta](images/run-a-new-container.webp?border=true&w=550&h=400)

7. Selecione **Run** para iniciar seu contêiner.

Parabéns!
Você acabou de executar seu primeiro contêiner! 🎉

### Visualize seu contêiner

Você pode visualizar todos os seus contêineres acessando a visualização
**Containers** do Painel do Docker Desktop.

![Captura de tela da visualização do contêiner da GUI do Docker Desktop mostrando o contêiner welcome-to-docker em execução na porta 8080 do host](images/view-your-containers.webp?border=true&w=750&h=600)

Este contêiner executa um servidor web que exibe um site simples.
Ao trabalhar com projetos mais complexos, você executará diferentes partes em
contêineres diferentes.
Por exemplo, você pode executar um contêiner diferente para o front-end, o
back-end e o banco de dados.

### Acesse o front-end

Ao iniciar o contêiner, você expôs uma das portas do contêiner para a sua
máquina.
Pense nisso como criar uma configuração que permite a conexão através do
ambiente isolado do contêiner.

Para este contêiner, o front-end está acessível na porta `8080`.
Para abrir o site, selecione o link na coluna **Port(s)** do seu contêiner ou
acesse [http://localhost:8080](http://localhost:8080) no seu navegador.

![Captura de tela da página inicial vinda do contêiner em execução](images/access-the-frontend.webp?border)

### Explore seu contêiner

O Docker Desktop permite explorar e interagir com diferentes aspectos do seu
contêiner.
Faça um teste.

1. Acesse a visualização **Containers** no Painel do Docker Desktop.

2. Selecione seu contêiner.

3. Selecione a aba **Files** para explorar o sistema de arquivos isolado do seu
   contêiner.

   ![Captura de tela do Painel do Docker Desktop mostrando os arquivos e diretórios em um contêiner em execução](images/explore-your-container.webp?border)

### Pare seu contêiner

O contêiner `docker/welcome-to-docker` continua em execução até que você o pare.

1. Acesse a visualização **Containers** no Painel do Docker Desktop.

2. Localize o contêiner que você deseja parar.

3. Selecione a ação **Stop** na coluna **Actions**.

   ![Captura de tela do Painel do Docker Desktop com o contêiner de boas-vindas selecionado e sendo preparado para parar](images/stop-your-container.webp?border)

{{< /tab >}}
{{< tab name="Usando a CLI" >}}

Siga as instruções para executar um contêiner usando a CLI:

1. Abra o terminal da CLI e inicie um contêiner usando o comando
   [`docker run`](/reference/cli/docker/container/run/):

   ```console
   $ docker run -d -p 8080:80 docker/welcome-to-docker
   ```

   A saída deste comando é o ID completo do contêiner.

Parabéns!
Você acabou de iniciar seu primeiro contêiner! 🎉

### Visualize seus contêineres em execução

Você pode verificar se o contêiner está em execução usando o comando
[`docker ps`](/reference/cli/docker/container/ls/):

```console
docker ps
```

Você verá uma saída semelhante à seguinte:

```console
 CONTAINER ID   IMAGE                      COMMAND                  CREATED          STATUS          PORTS                      NAMES
 a1f7a4bb3a27   docker/welcome-to-docker   "/docker-entrypoint.…"   11 seconds ago   Up 11 seconds   0.0.0.0:8080->80/tcp       gracious_keldysh
```

Este contêiner executa um servidor web que exibe um site simples.
Ao trabalhar com projetos mais complexos, você executará diferentes partes em
contêineres diferentes.
Por exemplo, um contêiner diferente para `frontend`, `backend` e `database`.

> [!TIP]
>
> O comando `docker ps` mostrará _apenas_ os contêineres em execução.
> Para visualizar os contêineres parados, adicione a flag `-a` para listar todos
> os contêineres: `docker ps -a`.

### Acesse o front-end

Ao iniciar o contêiner, você expôs uma das portas do contêiner para a sua
máquina.
Pense nisso como criar uma configuração que permite a conexão através do
ambiente isolado do contêiner.

Para este contêiner, o front-end está acessível na porta `8080`.
Para abrir o site, selecione o link na coluna **Port(s)** do seu contêiner ou
acesse [http://localhost:8080](http://localhost:8080) no seu navegador.

![Captura de tela da página inicial do servidor web Nginx, vinda do contêiner em execução](images/access-the-frontend.webp?border)

### Pare seu contêiner

O contêiner `docker/welcome-to-docker` continua em execução até que você o pare.
Você pode parar um contêiner usando o comando `docker stop`.

1. Execute `docker ps` para obter o ID do contêiner.

2. Forneça o ID ou nome do contêiner para o comando
   [`docker stop`](/reference/cli/docker/container/stop/):

   ```console
   docker stop <id-do-container>
   ```

> [!TIP]
>
> Ao referenciar contêineres por ID, você não precisa fornecer o ID completo.
> Basta fornecer o suficiente do ID para torná-lo único.
> Por exemplo, o contêiner anterior pode ser parado executando o seguinte
> comando:
>
> ```console
> docker stop a1f
> ```

{{< /tab >}}
{{< /tabs >}}

## Recursos adicionais

Os links a seguir fornecem orientações adicionais sobre contêineres:

- [Executando um contêiner](/engine/containers/run/)
- [Visão geral de contêineres](https://www.docker.com/resources/what-container/)
- [Por que usar o Docker?](https://www.docker.com/why-docker/)

## Próximos passos

Agora que você aprendeu o básico sobre um contêiner Docker, é hora de aprender
sobre imagens Docker.

{{< button text="O que é uma imagem?" url="what-is-an-image" >}}
