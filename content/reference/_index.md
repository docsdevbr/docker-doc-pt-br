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

source_url: https://github.com/docker/docs/blob/main/content/reference/_index.md
source_revision: ee71c80562c0edf1177ed79a8d67ddcd83a726e4
translation_status: ready

title: Documentação de referência
linkTitle: Referência
layout: wide
description: >-
  Encontre documentação de referência para as diversas APIs, CLIs e formatos de
  arquivo da plataforma Docker.
params:
  icon: command-line
  notoc: true
  grid_files:
  - title: Dockerfile
    description: >-
      Defina o conteúdo e o comportamento de inicialização de um único
      contêiner.
    icon: pencil-square
    link: /reference/dockerfile/
  - title: Arquivo Compose
    description: Defina uma aplicação multicontêiner.
    icon: rectangle-stack
    link: /reference/compose-file/
  grid_clis:
  - title: CLI do Docker
    description: A CLI principal do Docker, inclui todos os comandos `docker`.
    icon: command-line
    link: /reference/cli/docker/
  - title: CLI do Compose
    description: >-
      A CLI do Docker Compose, para criar e executar aplicações
      multicontêineres.
    icon: server-stack
    link: /reference/cli/docker/compose/
  - title: CLI do daemon (dockerd)
    description: Processo persistente que gerencia contêineres.
    icon: cpu-chip
    link: /reference/cli/dockerd/
  grid_apis:
  - title: API da Engine
    description: >-
      A API principal do Docker, fornece acesso programático a um daemon.
    icon: code-bracket
    link: /reference/api/engine/
  - title: API do Docker Hub
    description: API para interagir com o Docker Hub.
    icon: cloud
    link: /reference/api/hub/latest/
  - title: API de dados do DVP
    description: >-
      API para Editores Verificados do Docker para buscar dados analíticos.
    icon: chart-bar
    link: /reference/api/dvp/latest/
  - title: API do Registry
    description: API do Docker Registry.
    icon: circle-stack
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
