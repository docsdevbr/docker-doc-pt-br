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

source_url: https://github.com/docker/docs/blob/main/content/manuals/engine/swarm/_index.md
revision: 70d0c07c698bfc18bbe08b44c85f9dc859bd7718
status: ready

description: Visão geral do modo swarm da Docker Engine
keywords: docker, contêiner, cluster, swarm, docker engine
title: Modo swarm
weight: 80
aliases:
- /api/swarm-api/
- /engine/userguide/networking/overlay-standalone-swarm/
- /network/overlay-standalone.swarm/
- /release-notes/docker-swarm/
- /swarm/
- /swarm/api/
- /swarm/configure-tls/
- /swarm/discovery/
- /swarm/get-swarm/
- /swarm/install-manual/
- /swarm/install-w-machine/
- /swarm/multi-host-networking/
- /swarm/multi-manager-setup/
- /swarm/networking/
- /swarm/overview/
- /swarm/plan-for-production/
- /swarm/provision-with-machine/
- /swarm/reference/
- /swarm/reference/create/
- /swarm/reference/help/
- /swarm/reference/join/
- /swarm/reference/list/
- /swarm/reference/manage/
- /swarm/reference/swarm/
- /swarm/release-notes/
- /swarm/scheduler/
- /swarm/scheduler/filter/
- /swarm/scheduler/rescheduling/
- /swarm/scheduler/strategy/
- /swarm/secure-swarm-tls/
- /swarm/status-code-comparison-to-docker/
- /swarm/swarm-api/
- /swarm/swarm_at_scale/
- /swarm/swarm_at_scale/02-deploy-infra/
- /swarm/swarm_at_scale/03-create-cluster/
- /swarm/swarm_at_scale/04-deploy-app/
- /swarm/swarm_at_scale/about/
- /swarm/swarm_at_scale/deploy-app/
- /swarm/swarm_at_scale/deploy-infra/
- /swarm/swarm_at_scale/troubleshoot/
---

{{% include "swarm-mode.md" %}}

As versões atuais do Docker incluem o modo swarm para gerenciar nativamente um
cluster de Docker Engines chamado swarm.
Use a CLI do Docker para criar um swarm, implantar serviços de aplicações em um
swarm e gerenciar o comportamento do swarm.

O modo swarm do Docker está integrado à Docker Engine.
Não confunda o modo swarm do Docker com o
[Docker Classic Swarm](https://github.com/docker/classicswarm), que não está
mais em desenvolvimento ativo.

## Destaques do recurso

### Gerenciamento de cluster integrado à Docker Engine

Use a CLI da Docker Engine para criar um swarm da Docker Engine onde você pode
implantar serviços de aplicações.
Você não precisa de software de orquestração adicional para criar ou gerenciar
um swarm.

### Design descentralizado

Em vez de lidar com a diferenciação entre funções de nós no momento da
implantação, a Docker Engine lida com qualquer especialização em tempo de
execução.
Você pode implantar ambos os tipos de nós, managers (gerenciadores) e workers
(trabalhadores), usando a Docker Engine.
Isso significa que você pode construir um swarm inteiro a partir de uma única
imagem de disco.

### Modelo de serviço declarativo

A Docker Engine usa uma abordagem declarativa para permitir que você defina o
estado desejado dos vários serviços em sua pilha de aplicações.
Por exemplo, você pode descrever uma aplicação composta por um serviço de
front-end web com serviços de filas de mensagens e um banco de dados como
backend.

### Escalabilidade

Para cada serviço, você pode declarar o número de tarefas que deseja executar.
Ao aumentar ou diminuir a escala, o gerenciador do swarm se adapta
automaticamente, adicionando ou removendo tarefas para manter o estado desejado.

### Reconciliação do estado desejado

O nó gerenciador do swarm monitora constantemente o estado do cluster e
reconcilia quaisquer diferenças entre o estado atual e o estado desejado
especificado.
Por exemplo, se você configurar um serviço para executar 10 réplicas de um
contêiner e uma máquina de trabalho que hospeda duas dessas réplicas falhar, o
gerenciador criará duas novas réplicas para substituir as réplicas que falharam.
O gerenciador do swarm atribui as novas réplicas aos workers que estão em
execução e disponíveis.

### Redes com múltiplos hosts

Você pode especificar uma rede overlay para seus serviços.
O gerenciador do swarm atribui automaticamente endereços aos contêineres na rede
overlay quando inicializa ou atualiza a aplicação.

### Descoberta de serviços

Os nós gerenciadores do swarm atribuem a cada serviço no swarm um nome DNS
exclusivo e balanceiam a carga dos contêineres em execução.
Você pode consultar todos os contêineres em execução no swarm por meio de um
servidor DNS integrado ao swarm.

### Balanceamento de carga

Você pode expor as portas dos serviços a um balanceador de carga externo.
Internamente, o swarm permite que você especifique como distribuir os
contêineres de serviço entre os nós.

### Seguro por padrão

Cada nó no swarm impõe autenticação mútua TLS e criptografia para proteger as
comunicações entre si e todos os outros nós.
Você tem a opção de usar certificados raiz autoassinados ou certificados de uma
CA raiz personalizada.

### Atualizações contínuas

Durante a implantação, você pode aplicar atualizações de serviço aos nós de
forma incremental.
O gerenciador do swarm permite controlar o atraso entre a implantação do serviço
em diferentes conjuntos de nós.
Se algo der errado, você pode reverter para uma versão anterior do serviço.

## O que vem a seguir?

- Aprenda os [principais conceitos](key-concepts.md) do modo swarm.
- Comece com o [tutorial do modo swarm](swarm-tutorial/_index.md).
- Explore os comandos da CLI do modo swarm:
  - [swarm init](/reference/cli/docker/swarm/init/)
  - [swarm join](/reference/cli/docker/swarm/join/)
  - [service create](/reference/cli/docker/service/create/)
  - [service inspect](/reference/cli/docker/service/inspect/)
  - [service ls](/reference/cli/docker/service/ls/)
  - [service rm](/reference/cli/docker/service/rm/)
  - [service scale](/reference/cli/docker/service/scale/)
  - [service ps](/reference/cli/docker/service/ps/)
  - [service update](/reference/cli/docker/service/update/)
