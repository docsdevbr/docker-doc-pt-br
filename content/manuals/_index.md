---
# Copyright (c) 2013-2025 Docker Inc.
# Docker and the Docker logo are trademarks or registered trademarks of Docker,
# Inc. in the United States and/or other countries.
# Docker, Inc. and other parties may also have trademark rights in other terms
# used herein.
#
# Documentation licensed under the Apache License, Version 2.0.
# The original work was translated from English into Brazilian Portuguese.
# https://github.com/docker/docs/blob/-/LICENSE

source_url: https://github.com/docker/docs/blob/main/content/manuals/_index.md
revision: 26db073d5edddbd783232ff0b722c06d2fa38544
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
      - AI
      - Products
      - Platform
      - Enterprise
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
    icon: /icons/Compose.svg
    link: /compose/
  - title: Testcontainers
    description: >-
      Execute contêineres programaticamente em sua linguagem de programação
      preferida.
    icon: /icons/Testcontainers.svg
    link: /testcontainers/
  - title: Cagent
    description: >-
      A solução multiagente de código aberto para ajudar você em suas tarefas.
    icon: /icons/cagent.svg
    link: /ai/cagent
  ai:
  - title: Ask Gordon
    description: >-
      Simplifique seu fluxo de trabalho e aproveite ao máximo o ecossistema do
      Docker com seu assistente pessoal de IA.
    icon: note_add
    link: /ai/gordon/
  - title: Docker Model Runner
    description: Visualize e gerencie seus modelos locais.
    icon: /icons/models.svg
    link: /ai/model-runner/
  - title: Catálogo e Kit de Ferramentas MCP
    description: Aumente seu fluxo de trabalho de IA com servidores MCP.
    icon: /icons/toolkit.svg
    link: /ai/mcp-catalog-and-toolkit/
  products:
  - title: Docker Desktop
    description: Seu centro de comando para desenvolvimento de contêineres.
    icon: /icons/Whale.svg
    link: /desktop/
  - title: Docker Hardened Images
    description: Imagens seguras e mínimas para entrega confiável de software.
    icon: /icons/dhi.svg
    link: /dhi/
  - title: Docker Offload
    description: Crie e execute contêineres na nuvem.
    icon: cloud
    link: /offload/
  - title: Build Cloud
    description: Crie suas imagens mais rapidamente na nuvem.
    icon: /icons/logo-build-cloud.svg
    link: /build-cloud/
  - title: Docker Hub
    description: Descubra, compartilhe e integre imagens de contêineres.
    icon: hub
    link: /docker-hub/
  - title: Docker Scout
    description: Análise de imagens e validação de políticas.
    icon: /icons/Scout.svg
    link: /scout/
  - title: Extensões do Docker
    description: Personalize seu fluxo de trabalho do Docker Desktop.
    icon: extension
    link: /extensions/
  - title: Testcontainers Cloud
    description: Execute testes de integração, com dependências reais, na nuvem.
    icon: package_2
    link: https://testcontainers.com/cloud/docs/
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
  enterprise:
  - title: Implante o Docker Desktop
    description: Implante o Docker Desktop em escala na sua empresa.
    icon: download
    link: /enterprise/enterprise-deployment/
---

Esta seção contém guias da pessoa usuária sobre como instalar, configurar,
configurar e usar produtos Docker.

## Código aberto

Tecnologias de desenvolvimento e conteinerização de código aberto.

{{< grid items=open-source >}}

## IA

Todas as ferramentas de IA do Docker em um local de fácil acesso.

{{< grid items=ai >}}

## Produtos

Soluções completas para pessoas desenvolvedoras, para times inovadores.

{{< grid items=products >}}

## Plataforma

Documentação relacionada à plataforma Docker, como administração e gerenciamento
de assinaturas para organizações.

{{< grid items=platform >}}

## Corporativo

Destinado a pessoas administradoras de TI com ajuda na implantação do Docker
Desktop em escala, com orientação de configuração sobre recursos relacionados à
segurança.

{{< grid items=enterprise >}}
