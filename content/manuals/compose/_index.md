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

source_url: https://github.com/docker/docs/blob/main/content/manuals/compose/_index.md
revision: a1774fe925fa8ea1065cceb3877e67fc57967c9f
status: ready

title: Docker Compose
weight: 30
description: >-
  Aprenda a usar o Docker Compose para definir e executar aplicações
  multicontêineres com esta introdução detalhada à ferramenta.
keywords: >-
  docker compose, docker-compose, compose.yaml, comando docker compose,
  aplicações multicontêineres, orquestração de contêineres, docker cli
params:
  sidebar:
    group: Open source
grid:
  - title: Por que usar o Compose?
    description: Entenda os principais benefícios do Docker Compose
    icon: feature_search
    link: /compose/intro/features-uses/
  - title: Como o Compose funciona
    description: Entenda como o Compose funciona
    icon: category
    link: /compose/intro/compose-application-model/
  - title: Instale o Compose
    description: Siga as instruções para instalar o Docker Compose.
    icon: download
    link: /compose/install
  - title: Início rápido
    description: >-
      Aprenda os principais conceitos do Docker Compose enquanto cria uma
      aplicação web simples em Python.
    icon: explore
    link: /compose/gettingstarted
  - title: Veja as notas de lançamento
    description: >-
      Saiba mais sobre as melhorias e correções de bugs mais recentes.
    icon: note_add
    link: /compose/release-notes
  - title: Explore a referência do arquivo Compose
    description: >-
      Encontre informações sobre como definir serviços, redes e volumes para uma
      aplicação Docker.
    icon: polyline
    link: /reference/compose-file
  - title: Use o Compose Bridge
    description: >-
      Transforme seu arquivo de configuração do Compose em arquivos de
      configuração para diferentes plataformas, como o Kubernetes.
    icon: move_down
    link: /compose/bridge
  - title: Navegue pelas perguntas frequentes mais comuns
    description: >-
      Explore as perguntas frequentes gerais e descubra como enviar feedback.
    icon: help
    link: /compose/faq
  - title: Migre para o Compose v2
    description: Aprenda como migrar do Compose v1 para o v2
    icon: folder_delete
    link: /compose/releases/migrate/
aliases:
  - /compose/cli-command/
  - /compose/networking/swarm/
  - /compose/overview/
  - /compose/swarm/
  - /compose/completion/
---

O Docker Compose é uma ferramenta para definir e executar aplicações
multicontêineres.
É a chave para desbloquear uma experiência de desenvolvimento e implantação
simplificada e eficiente.

O Compose simplifica o controle de toda a sua pilha de aplicações, facilitando o
gerenciamento de serviços, redes e volumes em um único arquivo de configuração
YAML.
Em seguida, com um único comando, você cria e inicia todos os serviços a partir
do seu arquivo de configuração.

O Compose funciona em todos os ambientes - produção, homologação,
desenvolvimento, teste, bem como fluxos de trabalho de CI.
Ele também possui comandos para gerenciar todo o ciclo de vida da sua aplicação:

- Iniciar, parar e reconstruir serviços;
- Visualizar o status dos serviços em execução;
- Transmitir a saída de log dos serviços em execução;
- Executar um comando único em um serviço.

{{< grid >}}
