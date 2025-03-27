---
source_url: https://github.com/docker/docs/blob/main/content/get-started/introduction/build-and-push-first-image.md
revision: abd030c3fe2b5db526fb7a16d6d9892d46d678e5
status: ready

title: Crie e envie sua primeira imagem
keywords: conceitos, container, docker desktop
description: |
  Esta página conceitual lhe ensinará como construir e enviar sua primeira
  imagem.
summary: |
  Aprenda a construir sua primeira imagem Docker, uma etapa fundamental na
  conteinerização de sua aplicação.
  Nós te guiaremos pelo processo de criação de um repositório de imagens e
  construção e envio de sua imagem para o Docker Hub.
  Isso permitirá que você compartilhe sua imagem facilmente com seu time.
weight: 3
aliases: 
 - /guides/getting-started/build-and-push-first-image/
---

{{< youtube-embed 7ge1s5nAa34 >}}

## Explicação

Agora que você atualizou a
[aplicação de lista de tarefas](develop-with-containers.md),
já pode criar uma imagem de contêiner para a aplicação e compartilhá-la no
Docker Hub.
Para fazer isso, você precisará fazer o seguinte:

1. Entrar com sua conta do Docker
2. Criar um repositório de imagens no Docker Hub
3. Criar a imagem do contêiner
4. Enviar a imagem para o Docker Hub

Antes de mergulhar no guia prático, a seguir estão alguns conceitos básicos dos
quais você deve estar ciente.

### Imagens de contêiner

Se você é uma pessoa nova em imagens de contêiner, pense nelas como um pacote
padronizado que contém tudo o que é necessário para executar uma aplicação,
incluindo seus arquivos, configuração e dependências.
Esses pacotes podem ser distribuídos e compartilhados com outros.

### Docker Hub

Para compartilhar suas imagens do Docker, você precisa de um lugar para
armazená-las.
É aqui que os registros entram.
Embora existam muitos registros, o Docker Hub é o registro padrão e de
referência para imagens.
O Docker Hub fornece um lugar para você armazenar suas imagens e encontrar
outras imagens para executar ou usar como base para suas imagens.

Em [Desenvolva com contêineres](develop-with-containers.md), você usou as
seguintes imagens que vieram do Docker Hub, cada uma das quais são
[Imagens Oficiais do Docker](/manuals/docker-hub/image-library/trusted-content.md#docker-official-images):

* [node](https://hub.docker.com/_/node) - fornece um ambiente Node e é usada
  como base para seu trabalho de desenvolvimento.
  Esta imagem também é usada como base para a imagem final da aplicação.
* [mysql](https://hub.docker.com/_/mysql) - fornece um banco de dados MySQL para
  armazenar os itens da lista de tarefas.
* [phpmyadmin](https://hub.docker.com/_/phpmyadmin) - fornece o phpMyAdmin, uma
  interface _web_ para o banco de dados MySQL.
* [traefik](https://hub.docker.com/_/traefik) - fornece o Traefik, um moderno
  _proxy_ reverso HTTP e balanceador de carga que roteia requisições para o
  contêiner apropriado com base em regras de roteamento.

Explore o catálogo completo de
[Imagens Oficiais do Docker](https://hub.docker.com/search?image_filter=official&q=),
editores verificados pelo Docker e imagens do
[programa de código aberto patrocinado pelo Docker](https://hub.docker.com/search?q=&image_filter=open_source)
para ver mais do que há para executar e desenvolver.

## Experimente

Neste guia prático, você aprenderá como fazer o _login_ no Docker Hub e enviar
imagens para o repositório do Docker Hub.

## Entre com sua conta do Docker

Para enviar imagens para o Docker Hub, você precisará fazer o _login_ com uma
conta do Docker.

1. Abra o Painel do Docker.

2. Selecione **Sign in** no canto superior direito.

3. Se necessário, crie uma conta e conclua o fluxo de _login_.

Quando terminar, você verá o botão **Sign in** se transformar em uma foto de
perfil.

## Crie um repositório de imagens

Agora que você tem uma conta, pode criar um repositório de imagens.
Assim como um repositório Git contém código-fonte, um repositório de imagens
armazena imagens de contêiner.

1. Acesse o [Docker Hub](https://hub.docker.com).

2. Selecione **Create repository**.

3. Na página **Create repository**, insira as seguintes informações:
    * **Repository name** - `getting-started-todo-app`
    * **Short description** - sinta-se à vontade para inserir uma descrição, se
      desejar.
    * **Visibility** - selecione **Public** para permitir que outros baixem sua
      aplicação de tarefas personalizada.

4. Selecione **Create** para criar o repositório.


## Crie e envie a imagem

Agora que você tem um repositório, já pode criar e enviar sua imagem.
Uma observação importante é que a imagem que você está criando estende a imagem
do Node, o que significa que você não precisa instalar ou configurar o Node, o
Yarn, etc.
Você pode simplesmente se concentrar no que torna sua aplicação única.

> **O que é uma imagem/Dockerfile?**
>
> Sem entrar muito em detalhes ainda, pense em uma imagem de contêiner como um
> único pacote que contém tudo o que é necessário para executar um processo.
> Nesse caso, ela conterá um ambiente Node, o código de _backend_ e o código
> React compilado.
>
> Qualquer máquina que execute um contêiner usando a imagem poderá executar a
> aplicação como ela foi criada, sem precisar de mais nada pré-instalado na
> máquina.
>
> Um `Dockerfile` é um _script_ baseado em texto que fornece o conjunto de
> instruções sobre como criar a imagem.
> Para esse início rápido, o repositório já contém o `Dockerfile`.


{{< tabs group="cli-or-vs-code" persist=true >}}
{{< tab name="CLI" >}}

1. Para começar, clone ou
   [baixe o projeto como um arquivo ZIP](https://github.com/docker/getting-started-todo-app/archive/refs/heads/main.zip)
   para sua máquina local:

   ```console
   $ git clone https://github.com/docker/getting-started-todo-app
   ```

   Depois que o projeto for clonado, navegue até o novo diretório criado pelo
   comando:

   ```console
   $ cd getting-started-todo-app
   ```

2. Construa o projeto executando o seguinte comando, trocando `DOCKER_USERNAME`
   pelo seu nome de pessoa usuária:

    ```console
    $ docker build -t <DOCKER_USERNAME>/getting-started-todo-app .
    ```

   Por exemplo, se seu nome de pessoa usuária do Docker fosse `mobydock`, você
   executaria o seguinte:

    ```console
    $ docker build -t mobydock/getting-started-todo-app .
    ```

3. Para verificar se a imagem existe localmente, você pode usar o comando
   `docker image ls`:

    ```console
    $ docker image ls
    ```

   Você verá uma saída semelhante à seguinte:

    ```console
    REPOSITORY                          TAG       IMAGE ID       CREATED          SIZE
    mobydock/getting-started-todo-app   latest    1543656c9290   2 minutes ago    1.12GB
    ...
    ```

4. Para enviar a imagem, use o comando `docker push`.
   Certifique-se de substituir `DOCKER_USERNAME` pelo seu nome de pessoa
   usuária:

    ```console
    $ docker push <DOCKER_USERNAME>/getting-started-todo-app
    ```

   Dependendo da sua velocidade de _upload_, isso pode levar um tempo para ser
   concluído.

{{< /tab >}}
{{< tab name="VS Code" >}}

1. Abra o Visual Studio Code.
   No menu **File**, selecione **Open Folder**.
   Escolha **Clone Git Repository...** e cole esta URL:
   [https://github.com/docker/getting-started-todo-app](https://github.com/docker/getting-started-todo-app)
   ![Captura de tela do VS Code mostrando como clonar um repositório](images/clone-the-repo.webp?border=true)

2. Clique com o botão direito no `Dockerfile` e selecione o item de menu **Build
   Image...**.
   ![Captura de tela do VS Code mostrando o menu do botão direito e o item de menu "Build Image"](images/build-vscode-menu-item.webp?border=true)



3. Na caixa de diálogo que aparece, insira o nome
   `DOCKER_USERNAME/getting-started-todo-app`, substituindo `DOCKER_USERNAME`
   pelo seu nome de pessoa usuária do Docker.

4. Após pressionar **Enter**, você verá um terminal aparecer onde a construção
   ocorrerá.
   Quando estiver concluído, sinta-se à vontade para fechar o terminal.

5. Abra a Extensão Docker para VS Code selecionando o logotipo do Docker no menu
   de navegação esquerdo.

6. Encontre a imagem que você criou.
   Ela terá um nome de `docker.io/DOCKER_USERNAME/getting-started-todo-app`.

7. Expanda a imagem para visualizar as _tags_ (ou versões diferentes) da imagem.
   Você deve ver uma _tag_ chamada `latest`, que é a _tag_ padrão dada a uma
   imagem.

8. Clique com o botão direito no item **latest** e selecione a opção
   **Push...**.
   ![Captura de tela da extensão Docker e do menu do botão direito para enviar uma imagem](images/build-vscode-push-image.webp?border=true)

9. Pressione **Enter** para confirmar e então observe enquanto sua imagem é
   enviada para o Docker Hub.
   Dependendo da sua velocidade de _upload_, pode levar um tempo para enviar a
   imagem.

{{< /tab >}}
{{< /tabs >}}


## Recapitulando

Antes de prosseguir, reserve um momento para refletir sobre o que aconteceu
aqui.
Em alguns momentos, você conseguiu criar uma imagem de contêiner que empacota
sua aplicação e enviar a imagem para o Docker Hub.

No futuro, você vai querer lembrar que:

* O Docker Hub é o registro de referência para encontrar conteúdo confiável.
  O Docker fornece uma coleção de conteúdo confiável, composta por Imagens
  Oficiais do Docker, Editores Verificados do Docker e Software de Código Aberto
  Patrocinado pelo Docker, para usar diretamente ou como base para suas imagens.

* O Docker Hub fornece um mercado para distribuir suas aplicações.
  Qualquer pessoa pode criar uma conta e distribuir imagens.
  Enquanto você está distribuindo publicamente a imagem que criou, repositórios
  privados podem garantir que suas imagens sejam acessíveis apenas a pessoas
  usuárias autorizadas.

> **Uso de outros registros**
>
> Embora o Docker Hub seja o registro padrão, os registros são padronizados e
> se tornaram interoperáveis por meio da
> [Open Container Initiative](https://opencontainers.org/).
> Isso permite que empresas e organizações executem seus próprios registros
> privados.
> Muitas vezes, o conteúdo confiável é espelhado (ou copiado) do Docker Hub para
> esses registros privados.


## Próximos passos

Agora que você construiu uma imagem, é hora de discutir por que você, como
pessoa desenvolvedora, deve aprender mais sobre o Docker e como ele te ajudará
em suas tarefas do dia a dia.

{{< button text="What's Next" url="whats-next" >}}


