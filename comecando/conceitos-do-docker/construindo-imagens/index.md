---
source_url: https://github.com/docker/docs/blob/main/content/get-started/docker-concepts/building-images/_index.md
revision: 656d1a871c6837fae1e4538b82a3a5c01b70ed1e
status: ready
license: https://github.com/docker/docs/blob/main/LICENSE

title: Construindo imagens
weight: 20
keywords: construir imagens, Dockerfile, camadas, tag, push, cache, multiestágio
description: |
  Aprenda a construir imagens Docker a partir de um Dockerfile.
  Você entenderá a estrutura de um Dockerfile, como construir uma imagem e como
  personalizar o processo de construção.
summary: |
  Construir imagens de contêiner é tanto técnico quanto uma arte.
  Você quer manter a imagem pequena e focada para aumentar sua postura de
  segurança, mas também precisa equilibrar potenciais compensações, como
  impactos no cache.
  Nesta série, você se aprofundará nos segredos das imagens, como elas são
  construídas e nas melhores práticas.
layout: series
params:
  skill: Iniciante
  time: 25 minutos
  prereq: Nenhum
---

# Construindo imagens

Construir imagens de contêiner é tanto técnico quanto uma arte.
Você quer manter a imagem pequena e focada para aumentar sua postura de
segurança, mas também precisa equilibrar potenciais compensações, como impactos
no cache.
Nesta série, você se aprofundará nos segredos das imagens, como elas são
construídas e nas melhores práticas.
{: .lead }

## Sobre esta série

Aprenda a criar imagens Docker enxutas e eficientes prontas para produção,
essenciais para minimizar a sobrecarga e aprimorar a implantação em ambientes de
produção.

## O que você aprenderá

* Entender camadas de imagem
* Escrever um Dockerfile
* Construir, adicionar _tags_ e publicar uma imagem
* Usar o _cache_ de compilação
* Contruções em vários estágios
