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

source_url: https://github.com/docker/docs/blob/main/content/manuals/_index.md
revision: b6a1061fe80c0246455465e1f13ccc3e6b658e4d
status: ready

title: Manuais
description: >-
  Aprenda a instalar, configurar e usar produtos Docker com esta coleção de
  guias da pessoa usuária.
keywords: >-
  docker, docs, documentação, manuais, produtos, guias da pessoa usuária,
  instruções
# hard-code the URL of this page
url: /manuals/
layout: wide
params:
  icon: description
  sidebar:
    groups:
      - Open source
      - Products
      - Platform
  notoc: true
  open-source:
  - title: Docker Build
    description: Crie e lance qualquer aplicação em qualquer lugar.
    icon: build
    link: /build/
  - title: Docker Engine
    description: O runtime de contêiner líder do setor.
    icon: developer_board
    link: /engine/
  - title: Docker Compose
    description: Defina e execute aplicações multicontêineres.
    icon: /assets/icons/Compose.svg
    link: /compose/
  - title: Testcontainers
    description: >-
      Execute contêineres programaticamente em sua linguagem de programação
      preferida.
    icon: /assets/icons/Testcontainers.svg
    link: /testcontainers/
  products:
  - title: Docker Desktop
    description: Seu centro de comando para desenvolvimento de contêineres.
    icon: /assets/icons/Whale.svg
    link: /desktop/
  - title: Build Cloud
    description: Crie suas imagens mais rapidamente na nuvem.
    icon: /assets/images/logo-build-cloud.svg
    link: /build-cloud/
  - title: Docker Hub
    description: Descubra, compartilhe e integre imagens de contêineres.
    icon: hub
    link: /docker-hub/
  - title: Docker Scout
    description: Análise de imagens e validação de políticas.
    icon: /assets/icons/Scout.svg
    link: /scout/
  - title: Docker para GitHub Copilot
    description: Integre os recursos do Docker com o GitHub Copilot.
    icon: chat
    link: /copilot/
  - title: Extensões do Docker
    description: Personalize seu fluxo de trabalho do Docker Desktop.
    icon: extension
    link: /extensions/
  - title: Testcontainers Cloud
    description: Execute testes de integração, com dependências reais, na nuvem.
    icon: package_2
    link: https://testcontainers.com/cloud/docs/
  - title: Projetos Docker
    description: >-
      Use um fluxo de trabalho unificado e baseado em projetos para executar
      seus projetos em contêineres.
    icon: folder
    link: /projects/
  platform:
  - title: Administração
    description: Observabilidade centralizada para empresas e organizações.
    icon: admin_panel_settings
    link: /admin/
  - title: Faturamento
    description: Gerencie métodos de faturamento e pagamento.
    icon: payments
    link: /billing/
  - title: Contas
    description: Gerencie sua conta Docker.
    icon: account_circle
    link: /accounts/
  - title: Segurança
    description: >-
      Trilhos de segurança para pessoas administradoras e desenvolvedoras.
    icon: lock
    link: /security/
  - title: Assinatura
    description: Licenças de uso comercial para produtos Docker.
    icon: card_membership
    link: /subscription/
---

Esta seção contém guias da pessoa usuária sobre como instalar, configurar,
configurar e usar produtos Docker.

## Código aberto

Tecnologias de desenvolvimento e conteinerização de código aberto.

{{< grid items=open-source >}}

## Produtos

Soluções completas para pessoas desenvolvedoras, para times inovadores.

{{< grid items=products >}}

## Plataforma

Documentação relacionada à plataforma Docker, como administração e gerenciamento
de assinaturas para organizações.

{{< grid items=platform >}}
