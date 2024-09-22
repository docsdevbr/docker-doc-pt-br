---
source_url: https://github.com/docker/docs/blob/main/content/get-started/docker-concepts/the-basics/what-is-an-image.md
revision: 656d1a871c6837fae1e4538b82a3a5c01b70ed1e
status: ready
license: https://github.com/docker/docs/blob/main/LICENSE

title: O que é uma imagem?
weight: 20
keywords: conceitos, construção, imagens, contêiner, docker desktop
description: |
  Aprenda o básico sobre camadas de imagem.
aliases:
  - /guides/docker-concepts/the-basics/what-is-an-image/
---

# O que é uma imagem?

Aprenda o básico sobre camadas de imagem.
{: .lead }

<iframe width="895" height="487" src="https://www.youtube.com/embed/NyvT9REqLe4"
        title="Conceitos do Docker: O que é uma imagem?"
        frameborder="0"
        allow="accelerometer; autoplay; clipboard-write; encrypted-media;
        gyroscope; picture-in-picture; web-share"
        referrerpolicy="strict-origin-when-cross-origin"
        allowfullscreen></iframe>

## Explicação

Vendo que um [contêiner](o-que-e-um-container.md) é um processo isolado, de onde
ele obtém seus arquivos e configurações?
Como você compartilha esses ambientes?

É aí que entram as imagens de contêiner!

Uma imagem de contêiner é um pacote padronizado que inclui todos os arquivos,
binários, bibliotecas e configurações para executar um contêiner.

Para uma imagem [PostgreSQL](https://hub.docker.com/_/postgres), essa imagem
empacotará os binários do banco de dados, arquivos de configuração e outras
dependências.
Para uma aplicação _web_ Python, ela incluirá o tempo de execução do Python, o
código da sua aplicação e todas as suas dependências.

Há dois princípios importantes de imagens:

1. As imagens são imutáveis.
   Depois que uma imagem é criada, ela não pode ser modificada.
   Você só pode fazer uma nova imagem ou adicionar alterações sobre ela.

2. As imagens de contêiner são compostas de camadas.
   Cada camada representa um conjunto de alterações no sistema de arquivos que
   adicionam, removem ou modificam arquivos.

Esses dois princípios permitem que você estenda ou adicione imagens existentes.
Por exemplo, se você estiver criando uma aplicação Python, pode começar pela
[imagem do Python](https://hub.docker.com/_/python) e adicionar camadas
adicionais para instalar as dependências da sua aplicação e adicionar seu
código.
Isso permite que você se concentre na sua aplicação, em vez do Python em si.

### Encontrando imagens

[Docker Hub](https://hub.docker.com) é o mercado global padrão para armazenar e
distribuir imagens.
Ele tem mais de 100.000 imagens criadas por pessoas desenvolvedoras que você
pode executar localmente.
Você pode pesquisar imagens do Docker Hub e executá-las diretamente do Docker
Desktop.

O Docker Hub fornece uma variedade de imagens suportadas e endossadas pelo
Docker, conhecidas como Conteúdo Confiável do Docker.
Elas fornecem serviços totalmente gerenciados ou ótimos pontos de partida para
suas imagens.
Isso inclui:

- [Imagens Oficiais do Docker](https://hub.docker.com/search?q=&type=image&image_filter=official) -
  um conjunto selecionado de repositórios do Docker, servem como ponto de
  partida para a maioria das pessoas usuárias e são algumas das mais seguras no
  Docker Hub.
- [Editores Verificados pelo Docker](https://hub.docker.com/search?q=&image_filter=store) -
  imagens de alta qualidade de editores comerciais verificados pelo Docker.
- [Programa de Código Aberto Patrocinado pelo Docker](https://hub.docker.com/search?q=&image_filter=open_source) -
  imagens publicadas e mantidas por projetos de código aberto patrocinados pelo
  Docker por meio do programa de código aberto do Docker.

Por exemplo, [Redis](https://hub.docker.com/_/redis) e
[Memcached](https://hub.docker.com/_/memcached) são algumas imagens oficiais do
Docker populares e prontas para uso.
Você pode baixar essas imagens e ter esses serviços funcionando em questão de
segundos.
Há também imagens base, como a imagem Docker do
[Node.js](https://hub.docker.com/_/node), que você pode usar como ponto de
partida e adicionar seus arquivos e configurações.

## Experimente

### Usando a GUI

Nesta prática, você aprenderá como pesquisar e extrair uma imagem de contêiner
usando a GUI do Docker Desktop.

#### Pesquise e baixe uma imagem

1. Abra o Docker Dashboard e selecione a visualização **Images** no menu de
   navegação à esquerda.
   ![Uma captura de tela do Painel do Docker mostrando a visualização da imagem na barra lateral esquerda](images/click-image.webp?border=true&w=1050&h=400)

2. Selecione o botão **Search images to run**.
   Se não o vir, selecione a _barra de pesquisa global_ na parte superior da
   tela.
   ![Uma captura de tela do Painel do Docker mostrando a guia de pesquisa](images/search-image.webp?border)

3. No campo **Search**, digite "welcome-to-docker".
   Após a conclusão da pesquisa, selecione a imagem `docker/welcome-to-docker`.
   ![Uma captura de tela do Painel do Docker mostrando os resultados da pesquisa para a imagem docker/welcome-to-docker](images/select-image.webp?border=true&w=1050&h=400)

4. Selecione **Pull** para baixar a imagem.

#### Aprenda sobre a imagem

Depois de baixar uma imagem, você pode aprender alguns detalhes sobre ela por
meio da GUI ou da CLI.

1. No Painel do Docker, selecione a visualização **Images**.

2. Selecione a imagem **docker/welcome-to-docker** para abrir detalhes sobre a
   imagem.
   ![Uma captura de tela do Docker Dashboard mostrando a visualização de imagens com uma seta apontando para a imagem docker/welcome-to-docker](images/pulled-image.webp?border=true&w=1050&h=400)

3. A página de detalhes da imagem apresenta informações sobre as camadas da
   imagem, os pacotes e bibliotecas instalados na imagem e quaisquer
   vulnerabilidades descobertas.
   ![Uma captura de tela da visualização de detalhes da imagem para a imagem docker/welcome-to-docker](images/image-layers.webp?border=true&w=1050&h=400)

### Usando a CLI

Siga as instruções para pesquisar e puxar uma imagem Docker usando a CLI para
visualizar suas camadas.

#### Pesquise e baixe uma imagem

1. Abra um terminal e pesquise imagens usando o comando
   [`docker search`](../../../reference/cli/docker/search.md):
   ```shell
   docker search docker/welcome-to-docker
   ```
   Você verá uma saída como a seguinte:
   ```shell
   NAME                       DESCRIPTION                                     STARS     OFFICIAL
   docker/welcome-to-docker   Docker image for new users getting started w…   20
   ```
   Esta saída mostra informações sobre imagens relevantes disponíveis no Docker
   Hub.

2. Baixe a imagem usando o comando
   [`docker pull`](../../../reference/cli/docker/image/pull.md).
   ```shell
   docker pull docker/welcome-to-docker
   ```
   Você verá uma saída como a seguinte:
   ```shell
   Using default tag: latest
   latest: Pulling from docker/welcome-to-docker
   579b34f0a95b: Download complete
   d11a451e6399: Download complete
   1c2214f9937c: Download complete
   b42a2f288f4d: Download complete
   54b19e12c655: Download complete
   1fb28e078240: Download complete
   94be7e780731: Download complete
   89578ce72c35: Download complete
   Digest: sha256:eedaff45e3c78538087bdd9dc7afafac7e110061bbdd836af4104b10f10ab693
   Status: Downloaded newer image for docker/welcome-to-docker:latest
   docker.io/docker/welcome-to-docker:latest
   ```
   Cada linha representa uma camada diferente baixada da imagem.
   Lembre-se de que cada camada é um conjunto de alterações do sistema de
   arquivos e fornece funcionalidade da imagem.

#### Aprenda sobre a imagem

1. Liste suas imagens baixadas usando o comando
   [`docker image ls`](../../../reference/cli/docker/image/ls.md):
   ```shell
   docker image ls
   ```
   Você verá uma saída como a seguinte:
   ```shell
   REPOSITORY                 TAG       IMAGE ID       CREATED        SIZE
   docker/welcome-to-docker   latest    eedaff45e3c7   4 months ago   29.7MB
   ```
   O comando mostra uma lista de imagens do Docker atualmente disponíveis no seu
   sistema.
   A imagem `docker/welcome-to-docker` tem um tamanho total de aproximadamente
   29,7 MB.
   > **Tamanho da imagem**
   >
   > O tamanho da imagem representado aqui reflete o tamanho descompactado da
   > imagem, não o tamanho do download das camadas.

2. Liste as camadas da imagem usando o comando
   [`docker image history`](../../../reference/cli/docker/image/history.md):
   ```shell
   docker image history docker/welcome-to-docker
   ```
   Você verá uma saída como a seguinte:
   ```shell
   IMAGE          CREATED        CREATED BY                                      SIZE      COMMENT
   648f93a1ba7d   4 months ago   COPY /app/build /usr/share/nginx/html # buil…   1.6MB     buildkit.dockerfile.v0
   <missing>      5 months ago   /bin/sh -c #(nop)  CMD ["nginx" "-g" "daemon…   0B
   <missing>      5 months ago   /bin/sh -c #(nop)  STOPSIGNAL SIGQUIT           0B
   <missing>      5 months ago   /bin/sh -c #(nop)  EXPOSE 80                    0B
   <missing>      5 months ago   /bin/sh -c #(nop)  ENTRYPOINT ["/docker-entr…   0B
   <missing>      5 months ago   /bin/sh -c #(nop) COPY file:9e3b2b63db9f8fc7…   4.62kB
   <missing>      5 months ago   /bin/sh -c #(nop) COPY file:57846632accc8975…   3.02kB
   <missing>      5 months ago   /bin/sh -c #(nop) COPY file:3b1b9915b7dd898a…   298B
   <missing>      5 months ago   /bin/sh -c #(nop) COPY file:caec368f5a54f70a…   2.12kB
   <missing>      5 months ago   /bin/sh -c #(nop) COPY file:01e75c6dd0ce317d…   1.62kB
   <missing>      5 months ago   /bin/sh -c set -x     && addgroup -g 101 -S …   9.7MB
   <missing>      5 months ago   /bin/sh -c #(nop)  ENV PKG_RELEASE=1            0B
   <missing>      5 months ago   /bin/sh -c #(nop)  ENV NGINX_VERSION=1.25.3     0B
   <missing>      5 months ago   /bin/sh -c #(nop)  LABEL maintainer=NGINX Do…   0B
   <missing>      5 months ago   /bin/sh -c #(nop)  CMD ["/bin/sh"]              0B
   <missing>      5 months ago   /bin/sh -c #(nop) ADD file:ff3112828967e8004…   7.66MB
   ```
   Esta saída mostra todas as camadas, seus tamanhos e o comando usado para
   criar a camada.
   > **Visualizando o comando completo**
   >
   > Se você adicionar o sinalizador `--no-trunc` ao comando, verá o comando
   > completo.
   > Observe que, como a saída está em um formato semelhante a uma tabela,
   > comandos mais longos farão com que a saída seja muito difícil de navegar.

Neste tutorial, você pesquisou e extraiu uma imagem do Docker.
Além de extrair uma imagem do Docker, você também aprendeu sobre as camadas de
uma imagem do Docker.

## Recursos adicionais

Os seguintes recursos ajudarão você a aprender mais sobre como explorar,
encontrar e construir imagens:

- [Conteúdo Confiável do Docker](../../../manuals/trusted-content/index.md)
  - [Documentação das Imagens Oficiais do Docker](../../../manuals/trusted-content/official-images/index.md)
  - [Documentação dos Editores Verificados do Docker](../../../manuals/trusted-content/dvp-program.md)
  - [Documentação do Programa de Código Aberto Patrocinado pelo Docker](../../../manuals/trusted-content/dsos-program.md)
- [Explore a visualização de imagens no Docker Desktop](../../../manuals/desktop/use-desktop/images.md)
- [Empacotando seu programa](../../../manuals/build/concepts/dockerfile.md)
- [Docker Hub](https://hub.docker.com)

## Próximos passos

Agora que você aprendeu o básico sobre imagens, é hora de aprender sobre como
distribuir imagens por meio de registros.
