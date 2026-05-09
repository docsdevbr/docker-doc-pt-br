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

source_url: https://github.com/docker/docs/blob/main/content/manuals/engine/swarm/key-concepts.md
revision: 6e4790e2912429d3e06e461d60732a7a5dba3c2a
status: ready

description: Introdução aos principais conceitos do modo swarm da Docker Engine.
keywords: docker, contêiner, cluster, modo swarm, docker engine
title: Principais conceitos do modo swarm
---

Este tópico apresenta alguns dos conceitos exclusivos dos recursos de
gerenciamento e orquestração de clusters da Docker Engine 1.12.

## O que é um swarm?

Os recursos de gerenciamento e orquestração de clusters integrados à Docker
Engine são construídos usando o [swarmkit](https://github.com/docker/swarmkit/).
O swarmkit é um projeto separado que implementa a camada de orquestração do
Docker e é usado diretamente dentro do Docker.

Um swarm consiste em vários hosts Docker executados no modo swarm que atuam como
managers (gerenciadores), para gerenciar a associação e a delegação, e workers
(trabalhadores), que executam [serviços do swarm](#serviços-e-tarefas).
Um determinado host Docker pode ser um gerenciador, um trabalhador ou
desempenhar ambas as funções.
Ao criar um serviço, você define seu estado ideal — número de réplicas, recursos
de rede e armazenamento disponíveis, portas que o serviço expõe ao mundo externo
e muito mais.
O Docker trabalha para manter esse estado desejado.
Por exemplo, se um nó trabalhador ficar indisponível, o Docker agenda as tarefas
desse nó em outros nós.
Uma tarefa é um contêiner em execução que faz parte de um serviço do swarm e é
gerenciado por um gerenciador do swarm, ao contrário de um contêiner
independente.

Uma das principais vantagens dos serviços do swarm em relação aos contêineres
independentes é que você pode modificar a configuração de um serviço, incluindo
as redes e os volumes aos quais ele está conectado, sem a necessidade de
reiniciá-lo manualmente.
O Docker irá atualizar a configuração, interromper as tarefas do serviço com
configuração desatualizada e criar novas tarefas que correspondam à configuração
desejada.

Quando o Docker está em execução no modo swarm, você ainda pode executar
contêineres independentes em qualquer um dos hosts Docker que participam do
swarm, bem como serviços do swarm.
Uma diferença fundamental entre contêineres independentes e serviços do swarm é
que apenas os gerenciadores do swarm podem gerenciar um swarm, enquanto os
contêineres independentes podem ser iniciados em qualquer daemon.
Os daemons do Docker podem participar de um swarm como gerenciadores,
trabalhadores ou ambos.

Da mesma forma que você pode usar o [Docker Compose](/manuals/compose/_index.md)
para definir e executar containers, você pode definir e executar pilhas de
[serviços do swarm](services.md).

Continue lendo para obter detalhes sobre conceitos relacionados a serviços do
swarm do Docker, incluindo nós, serviços, tarefas e balanceamento de carga.

## Nós

Um nó é uma instância da Docker Engine que participa do swarm.
Você também pode pensar nisso como um nó do Docker.
É possível executar um ou mais nós em um único computador físico ou servidor em
nuvem, mas as implantações de swarm em produção normalmente incluem nós do
Docker distribuídos em várias máquinas físicas e em nuvem.

Para implantar sua aplicação em um swarm, você envia uma definição de serviço
para um nó gerenciador.
O nó gerenciador despacha unidades de trabalho chamadas
[tarefas](#serviços-e-tarefas) para nós trabalhadores.

Os nós gerenciadores também executam as funções de orquestração e gerenciamento
de cluster necessárias para manter o estado desejado do swarm.
Os nós gerenciadores selecionam um líder único para conduzir as tarefas de
orquestração.

Os nós trabalhadores recebem e executam as tarefas despachadas pelos nós
gerenciadores.
Por padrão, os nós gerenciadores também executam serviços como nós
trabalhadores, mas você pode configurá-los para executar exclusivamente tarefas
de gerenciamento e serem nós somente gerenciadores.
Um agente é executado em cada nó trabalhador e relata as tarefas atribuídas a
ele.
O nó trabalhador notifica o nó gerenciador sobre o estado atual de suas tarefas
atribuídas para que o gerenciador possa manter o estado desejado de cada
trabalhador.

## Serviços e tarefas

Um serviço é a definição das tarefas a serem executadas nos nós gerenciadores ou
trabalhadores.
É a estrutura central do sistema do swarm e a raiz principal da interação da
pessoa usuária com o swarm.

Ao criar um serviço, você especifica qual imagem de contêiner usar e quais
comandos executar dentro dos contêineres em execução.

No modelo de serviços replicados, o gerenciador do swarm distribui um número
específico de tarefas de réplica entre os nós com base na escala definida no
estado desejado.

Para serviços globais, o swarm executa uma tarefa para o serviço em cada nó
disponível no cluster.

Uma tarefa carrega um contêiner Docker e os comandos a serem executados dentro
do contêiner.
É a unidade de agendamento atômico do swarm.
Os nós gerenciadores atribuem tarefas aos nós de trabalho conforme o número de
réplicas definido na escala do serviço.
Uma vez que uma tarefa é atribuída a um nó, ela não pode ser movida para outro
nó.
Ela só pode ser executada no nó atribuído ou falhar.

## Balanceamento de carga

O gerenciador do swarm usa balanceamento de carga de entrada para expor os
serviços que você deseja disponibilizar externamente ao swarm.
O gerenciador do swarm pode atribuir automaticamente uma porta publicada ao
serviço ou você pode configurar uma porta publicada para o serviço.
Você pode especificar qualquer porta não usada.
Se você não especificar uma porta, o gerenciador do swarm atribuirá ao serviço
uma porta no intervalo de 30000 a 32767.

Componentes externos, como balanceadores de carga na nuvem, podem acessar o
serviço na porta publicada de qualquer nó do cluster, independentemente de o nó
estar ou não executando a tarefa para o serviço.
Todos os nós do swarm roteiam as conexões de entrada para uma instância de
tarefa em execução.

O modo swarm possui um componente DNS interno que atribui automaticamente a cada
serviço no swarm uma entrada DNS.
O gerenciador do swarm usa balanceamento de carga interno para distribuir as
requisições entre os serviços dentro do cluster com base no nome DNS do serviço.

## O que vem a seguir?

- Leia a [Visão geral do modo swarm](_index.md).
- Comece com o [Tutorial do modo swarm](swarm-tutorial/_index.md).
