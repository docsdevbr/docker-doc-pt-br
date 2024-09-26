---
source_url: https://github.com/docker/docs/blob/main/content/get-started/introduction/whats-next.md
revision: abd030c3fe2b5db526fb7a16d6d9892d46d678e5
status: ready
license: https://github.com/docker/docs/blob/main/LICENSE

title: O que vem a seguir
keywords: conceitos, construir, imagens, contêiner, docker desktop
description: |
  Explore guias passo a passo para ajudar você a entender os principais
  conceitos do Docker, criar imagens e executar contêineres.
aliases:
  - /guides/getting-started/whats-next/
summary: |
  Agora que você configurou o Docker Desktop, desenvolveu com contêineres e
  construiu e enviou sua primeira imagem, você já pode dar o próximo passo e
  mergulhar profundamente no que é um contêiner e como ele funciona.
notoc: true
weight: 4

the-basics:
  - title: O que é um contêiner?
    description: Aprenda como executar seu primeiro contêiner.
    link: ../conceitos-do-docker/o-basico/o-que-e-um-container.md
  - title: O que é uma imagem?
    description: Aprenda o básico sobre camadas de imagem.
    link: ../conceitos-do-docker/o-basico/o-que-e-uma-imagem.md
  - title: O que é um registro?
    description: |
      Aprenda sobre registros de contêineres, explore sua interoperabilidade e
      interaja com registros.
    link: ../conceitos-do-docker/o-basico/o-que-e-um-registro.md
  - title: O que é o Docker Compose?
    description: Entenda melhor o Docker Compose.
    link: ../conceitos-do-docker/o-basico/o-que-e-docker-compose.md

building-images:
  - title: Entendendo camadas de imagem
    description: Aprenda sobre as camadas de imagens de contêiner.
    link: ../../comecando/conceitos-do-docker/construindo-imagens/entendendo-camadas-de-imagem.md
  - title: Escrevendo um Dockerfile
    description: Aprenda a criar uma imagem usando um Dockerfile.
    link: ../../get-started/docker-concepts/building-images/writing-a-dockerfile.md
  - title: Crie, adicione _tags_ e publique uma imagem
    description: |
      Aprenda a criar, adicionar _tags_ e publicar uma imagem no Docker Hub ou
      em qualquer outro registro.
    link: ../../get-started/docker-concepts/building-images/build-tag-and-publish-an-image.md
  - title: Usando o _cache_ de compilação
    description: |
      Aprenda sobre o _cache_ de compilação, quais alterações invalidam o
      _cache_ e como usar o _cache_ de compilação de forma eficaz.
    link: ../../get-started/docker-concepts/building-images/using-the-build-cache.md
  - title: Compilações de vários estágios
    description: |
      Obtenha uma melhor compreensão das compilações de vários estágios e seus
      benefícios.
    link: ../../get-started/docker-concepts/building-images/multi-stage-builds.md

running-containers:
  - title: Publicando portas
    description: Entenda a importância de publicar e expor portas no Docker.
    link: ../../get-started/docker-concepts/running-containers/publishing-ports.md
  - title: Substituindo configurações padrão de contêiner
    description: |
      Aprenda a substituir as configurações padrão de contêiner usando o comando
      `docker run`.
    link: ../../get-started/docker-concepts/running-containers/overriding-container-defaults.md
  - title: Persistindo dados de contêiner
    description: Aprenda a importância da persistência de dados no Docker.
    link: ../../get-started/docker-concepts/running-containers/persisting-container-data.md
  - title: Compartilhando arquivos locais com contêineres
    description: |
      Explore as várias opções de armazenamento disponíveis no Docker e seu uso
      comum.
    link: ../../get-started/docker-concepts/running-containers/sharing-local-files.md
  - title: Aplicações multicontêineres
    description: |
      Aprenda a importância das aplicações multicontêineres e como elas são
      diferentes das aplicações de contêiner único.
    link: ../../get-started/docker-concepts/running-containers/multi-container-applications.md
---

# O que vem a seguir

Agora que você configurou o Docker Desktop, desenvolveu com contêineres e
construiu e enviou sua primeira imagem, você já pode dar o próximo passo e
mergulhar profundamente no que é um contêiner e como ele funciona.
{: .lead }

As seções a seguir fornecem guias passo a passo para ajudar você a entender os
principais conceitos do Docker, criar imagens e executar contêineres.

## O básico

Comece aprendendo os conceitos básicos de contêineres, imagens, registros e
Docker Compose.

* [O que é um contêiner?](../conceitos-do-docker/o-basico/o-que-e-um-container.md)
    * Aprenda como executar seu primeiro contêiner.
* [O que é uma imagem?](../conceitos-do-docker/o-basico/o-que-e-uma-imagem.md)
    * Aprenda o básico sobre camadas de imagem.
* [O que é um registro?](../conceitos-do-docker/o-basico/o-que-e-um-registro.md)
    * Aprenda sobre registros de contêineres, explore sua interoperabilidade e
      interaja com registros.
* [O que é o Docker Compose?](../conceitos-do-docker/o-basico/o-que-e-docker-compose.md)
    * Entenda melhor o Docker Compose.

## Criando imagens

Crie imagens de contêiner otimizadas com Dockerfiles, _cache_ de compilação e
compilações de vários estágios.

* [Entendendo camadas de imagem](../../get-started/docker-concepts/building-images/understanding-image-layers.md)
    * Aprenda sobre as camadas de imagens de contêiner.
* [Escrevendo um Dockerfile](../../get-started/docker-concepts/building-images/writing-a-dockerfile.md)
    * Aprenda a criar uma imagem usando um Dockerfile.
* [Crie, adicione _tags_ e publique uma imagem](../../get-started/docker-concepts/building-images/build-tag-and-publish-an-image.md)
    * Aprenda a criar, adicionar _tags_ e publicar uma imagem no Docker Hub ou em
      qualquer outro registro.
* [Usando o _cache_ de compilação](../../get-started/docker-concepts/building-images/using-the-build-cache.md)
    * Aprenda sobre o _cache_ de compilação, quais alterações invalidam o _cache_
      e como usar o _cache_ de compilação de forma eficaz.
* [Compilações de vários estágios](../../get-started/docker-concepts/building-images/multi-stage-builds.md)
    * Obtenha uma melhor compreensão das compilações de vários estágios e seus
      benefícios.

## Executando contêineres

Domine técnicas essenciais para expor portas, substituir configurações padrão,
persistir dados, compartilhar arquivos e gerenciar aplicações multicontêineres.

* [Publicando portas](../../get-started/docker-concepts/running-containers/publishing-ports.md)
    * Entenda a importância de publicar e expor portas no Docker.
* [Substituindo configurações padrão de contêiner](../../get-started/docker-concepts/running-containers/overriding-container-defaults.md)
    * Aprenda a substituir as configurações padrão de contêiner usando o comando `docker run`.
* [Persistindo dados de contêiner](../../get-started/docker-concepts/running-containers/persisting-container-data.md)
    * Aprenda a importância da persistência de dados no Docker.
* [Compartilhando arquivos locais com contêineres](../../get-started/docker-concepts/running-containers/sharing-local-files.md)
    * Explore as várias opções de armazenamento disponíveis no Docker e seu uso
      comum.
* [Aplicações multicontêineres](../../get-started/docker-concepts/running-containers/multi-container-applications.md)
    * Aprenda a importância das aplicações multicontêineres e como elas são
      diferentes das aplicações de contêiner único.
