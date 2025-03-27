---
source_url: https://github.com/docker/docs/blob/main/content/get-started/introduction/whats-next.md
revision: abd030c3fe2b5db526fb7a16d6d9892d46d678e5
status: ready

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
  link: /get-started/docker-concepts/the-basics/what-is-a-container/
- title: O que é uma imagem?
  description: Aprenda o básico sobre camadas de imagem.
  link: /get-started/docker-concepts/the-basics/what-is-an-image/
- title: O que é um registro?
  description: |
      Aprenda sobre registros de contêineres, explore sua interoperabilidade e
      interaja com registros.
  link: /get-started/docker-concepts/the-basics/what-is-a-registry/
- title: O que é o Docker Compose?
  description: Entenda melhor o Docker Compose.
  link: /get-started/docker-concepts/the-basics/what-is-docker-compose/

building-images:
  - title: Entendendo camadas de imagem
    description: Aprenda sobre as camadas de imagens de contêiner.
  link: /get-started/docker-concepts/building-images/understanding-image-layers/
- title: Escrevendo um Dockerfile
  description: Aprenda a criar uma imagem usando um Dockerfile.
  link: /get-started/docker-concepts/building-images/writing-a-dockerfile/
- title: Crie, adicione _tags_ e publique uma imagem
  description: |
      Aprenda a criar, adicionar _tags_ e publicar uma imagem no Docker Hub ou
      em qualquer outro registro.
  link: /get-started/docker-concepts/building-images/build-tag-and-publish-an-image/
- title: Usando o _cache_ de construção
  description: |
      Aprenda sobre o _cache_ de construção, quais alterações invalidam o
      _cache_ e como usar o _cache_ de construção de forma eficaz.
  link: /get-started/docker-concepts/building-images/using-the-build-cache/
- title: Construções em vários estágios
  description: |
      Obtenha uma melhor compreensão das construções em vários estágios e seus
      benefícios.
  link: /get-started/docker-concepts/building-images/multi-stage-builds/

running-containers:
- title: Publicando portas
  description: Entenda a importância de publicar e expor portas no Docker.
  link: /get-started/docker-concepts/running-containers/publishing-ports/
- title: Substituindo configurações padrão de contêiner
  description: |
      Aprenda a substituir as configurações padrão de contêiner usando o comando
      `docker run`.
  link: /get-started/docker-concepts/running-containers/overriding-container-defaults/
- title: Persistindo dados de contêiner
  description: Aprenda a importância da persistência de dados no Docker.
  link: /get-started/docker-concepts/running-containers/persisting-container-data/
- title: Compartilhando arquivos locais com contêineres
  description: |
      Explore as várias opções de armazenamento disponíveis no Docker e seu uso
      comum.
  link: /get-started/docker-concepts/running-containers/sharing-local-files/
- title: Aplicações multicontêineres
  description: |
      Aprenda a importância das aplicações multicontêineres e como elas são
      diferentes das aplicações de contêiner único.
  link: /get-started/docker-concepts/running-containers/multi-container-applications/
---

As seções a seguir fornecem guias passo a passo para ajudar você a entender os
principais conceitos do Docker, criar imagens e executar contêineres.

## O básico

Comece aprendendo os conceitos básicos de contêineres, imagens, registros e
Docker Compose.

{{< grid items="the-basics" >}}

## Criando imagens

Crie imagens de contêiner otimizadas com Dockerfiles, _cache_ de construção e
construções em vários estágios.

{{< grid items="building-images" >}}

## Executando contêineres

Domine técnicas essenciais para expor portas, substituir configurações padrão,
persistir dados, compartilhar arquivos e gerenciar aplicações multicontêineres.

{{< grid items="running-containers" >}}
