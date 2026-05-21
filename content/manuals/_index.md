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

source_url: https://github.com/docker/docs/blob/main/content/manuals/_index.md
source_revision: ee71c80562c0edf1177ed79a8d67ddcd83a726e4
translation_status: ready

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
  icon: document-text
  sidebar:
    groups:
      - AI and agents
      - Application development
      - Supply chain security
      - Platform
      - Enterprise
  notoc: true
  ai-and-agents:
  - title: Docker Sandboxes
    description: Execute agentes de codificação de IA em ambientes isolados.
    icon: command-line
    link: /ai/sandboxes/
  - title: Catálogo e Kit de Ferramentas MCP
    description: Aumente seu fluxo de trabalho de IA com servidores MCP.
    icon: /icons/toolkit.svg
    link: /ai/mcp-catalog-and-toolkit/
  - title: Gordon
    description: >-
      Simplifique seu fluxo de trabalho e aproveite ao máximo o ecossistema do
      Docker com seu assistente pessoal de IA.
    icon: document-plus
    link: /ai/gordon/
  - title: Docker Model Runner
    description: Visualize e gerencie seus modelos locais.
    icon: /icons/models.svg
    link: /ai/model-runner/
  application-development:
  - title: Docker Agent
    description: >-
      A solução multiagente de código aberto para ajudar você em suas tarefas.
    icon: /icons/cagent.svg
    link: /ai/docker-agent
  - title: Docker Desktop
    description: Seu centro de comando para desenvolvimento com contêineres.
    icon: /icons/Whale.svg
    link: /desktop/
  - title: Docker Offload
    description: Crie e execute contêineres na nuvem.
    icon: cloud
    link: /offload/
  - title: Docker Build Cloud
    description: Crie suas imagens mais rapidamente na nuvem.
    icon: /icons/logo-build-cloud.svg
    link: /build-cloud/
  - title: Testcontainers
    description: >-
      Execute contêineres programaticamente em sua linguagem de programação
      preferida.
    icon: /icons/Testcontainers.svg
    link: /testcontainers/
  - title: Docker Build
    description: Crie e lance qualquer aplicação em qualquer lugar.
    icon: wrench-screwdriver
    link: /build/
  - title: Docker Engine
    description: O tempo de execução de contêiner líder do setor.
    icon: cpu-chip
    link: /engine/
  - title: Docker Compose
    description: Defina e execute aplicações multicontêineres.
    icon: /icons/Compose.svg
    link: /compose/
  supply-chain-security:
  - title: Docker Hub
    description: Descubra, compartilhe e integre imagens de contêineres.
    icon: globe-alt
    link: /docker-hub/
  - title: Imagens Docker Reforçadas
    description: Imagens seguras e mínimas para entrega confiável de software.
    icon: /icons/dhi.svg
    link: /dhi/
  - title: Docker Scout
    description: Análise de imagens e validação de políticas.
    icon: /icons/Scout.svg
    link: /scout/
  platform:
  - title: Administração
    description: Observabilidade centralizada para empresas e organizações.
    icon: shield-check
    link: /admin/
  - title: Faturamento
    description: Gerencie métodos de faturamento e pagamento.
    icon: credit-card
    link: /billing/
  - title: Contas
    description: Gerencie sua conta Docker.
    icon: user-circle
    link: /accounts/
  - title: Segurança
    description: >-
      Guardrails de segurança para pessoas administradoras e desenvolvedoras.
    icon: lock-closed
    link: /security/
  - title: Assinatura
    description: Licenças de uso comercial para produtos Docker.
    icon: credit-card
    link: /subscription/
  enterprise:
  - title: Implante o Docker Desktop
    description: Implante o Docker Desktop em escala na sua empresa.
    icon: arrow-down-tray
    link: /enterprise/enterprise-deployment/
---

Esta seção contém guias da pessoa usuária sobre como instalar, configurar e usar
produtos Docker.

## IA e agentes

Todas as ferramentas de IA do Docker em um local de fácil acesso.

{{< grid items=ai-and-agents >}}

## Desenvolvimento de aplicações

Soluções completas para pessoas desenvolvedoras, para times inovadores.

{{< grid items=application-development >}}

## Segurança da cadeia de suprimentos

Guardrails de segurança e análise de imagens para sua cadeia de suprimentos de
software.

{{< grid items=supply-chain-security >}}

## Plataforma

Documentação relacionada à plataforma Docker, como administração e gerenciamento
de assinaturas.

{{< grid items=platform >}}

## Corporativo

Destinado a pessoas administradoras de TI com ajuda na implantação do Docker
Desktop em escala, com orientação de configuração sobre recursos relacionados à
segurança.

{{< grid items=enterprise >}}
