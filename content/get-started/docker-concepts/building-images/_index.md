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

source_url: https://github.com/docker/docs/blob/main/content/get-started/docker-concepts/building-images/_index.md
revision: 656d1a871c6837fae1e4538b82a3a5c01b70ed1e
status: ready

title: Construindo imagens
weight: 20
keywords: construir imagens, Dockerfile, camadas, tag, push, cache, multiestágio
description: >-
  Aprenda a construir imagens Docker a partir de um Dockerfile.
  Você entenderá a estrutura de um Dockerfile, como construir uma imagem e como
  personalizar o processo de construção.
summary: >-
  Construir imagens de contêineres é uma tarefa técnica e uma arte.
  Você deseja manter a imagem pequena e focada para aumentar sua postura de
  segurança, mas também precisa equilibrar possíveis compensações, como os
  impactos do cache.
  Nesta série, você se aprofundará nos segredos das imagens, como elas são
  construídas e nas melhores práticas.
layout: series
params:
  skill: Iniciante
  time: 25 minutos
  prereq: Nenhum
---

## Sobre esta série

Aprenda a criar imagens Docker enxutas e eficientes prontas para produção,
essenciais para minimizar a sobrecarga e aprimorar a implantação em ambientes de
produção.

## O que você aprenderá

- Entender camadas de imagem.
- Escrever um Dockerfile.
- Construir, adicionar tags e publicar uma imagem.
- Usar o cache de construção.
- Contruções em vários estágios.
