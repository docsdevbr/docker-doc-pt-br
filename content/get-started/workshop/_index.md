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

source_url: https://github.com/docker/docs/blob/main/content/get-started/workshop/_index.md
revision: 656d1a871c6837fae1e4538b82a3a5c01b70ed1e
status: ready

title: Visão geral do workshop de Docker
linkTitle: Workshop de Docker
keywords: >-
  conceitos básicos de docker, como iniciar um contêiner docker, configurações
  de contêiner, configurar o docker, como configurar o docker, configurando o
  docker, guia de contêiner docker, como começar com o docker
description: >-
  Comece com os conceitos básicos do Docker neste workshop.
  Você aprenderá sobre contêineres, imagens e como conteinerizar sua primeira
  aplicação.
aliases:
- /guides/get-started/
- /get-started/hands-on-overview/
- /guides/workshop/
---

Este workshop de 45 minutos contém instruções passo a passo sobre como começar a
usar o Docker.
Este workshop mostra como:

- Criar e executar uma imagem como um contêiner.
- Compartilhar imagens usando o Docker Hub.
- Implantar aplicações Docker usando vários contêineres com um banco de dados.
- Executar aplicações usando o Docker Compose.

> [!NOTE]
>
> Para uma introdução rápida ao Docker e aos benefícios de conteinerizar suas
> aplicações, consulte a [Introdução](/get-started/introduction/_index.md).

## O que é um contêiner?

Um contêiner é um processo isolado executado em uma máquina host, separado de
todos os outros processos em execução nessa mesma máquina.
Esse isolamento aproveita os
[namespaces e cgroups do kernel](https://medium.com/@saschagrunert/demystifying-containers-part-i-kernel-space-2c53d6979504),
recursos presentes no Linux há muito tempo.
O Docker torna essas capacidades acessíveis e fáceis de usar.
Resumindo, um contêiner:

- É uma instância executável de uma imagem.
  Você pode criar, iniciar, parar, mover ou excluir um contêiner usando a API ou
  a CLI do Docker.
- Pode ser executado em máquinas locais, máquinas virtuais ou implantado na
  nuvem.
- É portátil (e pode ser executado em qualquer sistema operacional).
- É isolado de outros contêineres e executa seu próprio software, binários,
  configurações etc.

Se você já conhece o `chroot`, pense em um contêiner como uma versão estendida
do `chroot`.
O sistema de arquivos vem da imagem.
No entanto, um contêiner adiciona isolamento adicional não disponível ao usar o
chroot.

## O que é uma imagem?

Um contêiner em execução usa um sistema de arquivos isolado.
Esse sistema de arquivos isolado é fornecido por uma imagem, e a imagem deve
conter tudo o que é necessário para executar uma aplicação — todas as
dependências, configurações, scripts, binários, etc.
A imagem também contém outras configurações para o contêiner, como variáveis de
ambiente, um comando padrão para executar e outros metadados.

## Próximos passos

Nesta seção, você aprendeu sobre contêineres e imagens.

A seguir, você irá conteinerizar uma aplicação simples e colocará os conceitos
em prática.

{{< button text="Conteinerize uma aplicação" url="02_our_app.md" >}}
