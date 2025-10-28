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

source_url: https://github.com/docker/docs/blob/main/content/reference/_index.md
revision: c69c0b53dd46ec56dc63e43e9fe6bd279f910431
status: ready

title: Documentação de referência
linkTitle: Referência
layout: wide
description: >-
  Encontre documentação de referência para as diversas APIs, CLIs e formatos de
  arquivo da plataforma Docker.
params:
  icon: terminal
  notoc: true
  grid_files:
  - title: Dockerfile
    description: >-
      Define o conteúdo e o comportamento de inicialização de um único
      contêiner.
    icon: edit_document
    link: /reference/dockerfile/
  - title: Arquivo Compose
    description: Define uma aplicação multicontêiner.
    icon: polyline
    link: /reference/compose-file/
  grid_clis:
  - title: CLI do Docker
    description: A CLI principal do Docker, inclui todos os comandos `docker`.
    icon: terminal
    link: /reference/cli/docker/
  - title: CLI do Compose
    description: >-
      A CLI do Docker Compose, para criar e executar aplicações
      multicontêineres.
    icon: subtitles
    link: /reference/cli/docker/compose/
  - title: CLI do daemon (dockerd)
    description: Processo persistente que gerencia contêineres.
    icon: developer_board
    link: /reference/cli/dockerd/
  grid_apis:
  - title: API da engine
    description: >-
      A API principal do Docker, fornece acesso programático a um daemon.
    icon: api
    link: /reference/api/engine/
  - title: API do Docker Hub
    description: API para interagir com o Docker Hub.
    icon: communities
    link: /reference/api/hub/latest/
  - title: API de dados do DVP
    description: >-
      API para Editores Verificados do Docker para buscar dados analíticos.
    icon: area_chart
    link: /reference/api/dvp/latest/
  - title: API do Docker Registry
    description: API do Docker Registry.
    icon: database
    link: /reference/api/registry/latest/
---

Esta seção inclui a documentação de referência para as diversas APIs, CLIs,
drivers e especificações da plataforma Docker, além de formatos de arquivo.

## Formatos de arquivo

{{< grid items="grid_files" >}}

## Interfaces de linha de comando (CLIs)

{{< grid items="grid_clis" >}}

## Interfaces de programação de aplicações (APIs)

{{< grid items="grid_apis" >}}
