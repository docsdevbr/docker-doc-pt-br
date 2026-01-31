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

source_url: https://github.com/docker/docs/blob/main/content/manuals/engine/install/_index.md
revision: 9181177b0efd89584fb1b7c5b9e25ffc81456ae8
status: wip

title: Instale a Docker Engine
linkTitle: Instalar
weight: 10
description: >-
  Aprenda como escolher o melhor método para instalar a Docker Engine.
  Esta aplicação cliente-servidor está disponível para Linux, Mac, Windows e
  como um binário estático.
keywords:  >-
  instalar engine, instalação da docker engine, instalar docker engine, docker
  engine instalação, instalação da engine, instalação do docker ce, instalador
  engine, instalando a docker engine, instalação do servidor docker, docker
  desktop vs. docker engine
aliases:
- /cs-engine/
- /cs-engine/1.12/
- /cs-engine/1.12/upgrade/
- /cs-engine/1.13/
- /cs-engine/1.13/upgrade/
- /ee/docker-ee/oracle/
- /ee/supported-platforms/
- /en/latest/installation/
- /engine/installation/
- /engine/installation/frugalware/
- /engine/installation/linux/
- /engine/installation/linux/archlinux/
- /engine/installation/linux/cruxlinux/
- /engine/installation/linux/docker-ce/
- /engine/installation/linux/docker-ee/
- /engine/installation/linux/docker-ee/oracle/
- /engine/installation/linux/frugalware/
- /engine/installation/linux/gentoolinux/
- /engine/installation/linux/oracle/
- /engine/installation/linux/other/
- /engine/installation/oracle/
- /enterprise/supported-platforms/
- /install/linux/docker-ee/oracle/
---

Esta seção descreve como instalar a Docker Engine no Linux, também conhecida
como Docker CE.
A Docker Engine também está disponível para Windows, macOS e Linux, através do
Docker Desktop.
Para obter instruções sobre como instalar o Docker Desktop, consulte:
[Visão geral do Docker Desktop](/manuals/desktop/_index.md).

## Procedimentos de instalação para plataformas suportadas

Clique no link de uma plataforma para visualizar o procedimento de instalação
correspondente.

| Plataforma                                     | x86_64 / amd64 | arm64 / aarch64 | arm (32-bit) | ppc64le | s390x |
|:-----------------------------------------------|:--------------:|:---------------:|:------------:|:-------:|:-----:|
| [CentOS](centos.md)                            |    ✅           |        ✅        |              |    ✅    |       |
| [Debian](debian.md)                            |       ✅        |      ✅          |      ✅       |    ✅    |       |
| [Fedora](fedora.md)                            |       ✅        |        ✅        |              |    ✅    |       |
| [Raspberry Pi OS (32-bit)](raspberry-pi-os.md) |                |                 |      ⚠️      |         |       |
| [RHEL](rhel.md)                                |       ✅        |        ✅        |              |         |   ✅   |
| [SLES](sles.md)                                |                |                 |              |         |   ❌   |
| [Ubuntu](ubuntu.md)                            |       ✅        |        ✅        |      ✅       |    ✅    |   ✅   |
| [Binários](binaries.md)                        |       ✅        |        ✅        |      ✅       |         |       |

### Outras distribuições Linux

> [!NOTE]
>
> Embora as instruções a seguir possam funcionar, o Docker não testa nem
> verifica a instalação em distribuições derivadas.

- Se você usa distribuições derivadas do Debian, como "BunsenLabs Linux", "Kali
  Linux" ou "LMDE" (Mint baseado em Debian), siga as instruções de instalação
  para [Debian](debian.md), substituindo a versão da sua distribuição pela
  versão correspondente do Debian.
  Consulte a documentação da sua distribuição para encontrar qual versão do
  Debian corresponde à sua versão derivada.
- Da mesma forma, se você usa distribuições derivadas do Ubuntu, como "Kubuntu",
  "Lubuntu" ou "Xubuntu", siga as instruções de instalação para
  [Ubuntu](ubuntu.md), substituindo a versão da sua distribuição pela versão
  correspondente do Ubuntu.
  Consulte a documentação da sua distribuição para encontrar qual versão do
  Ubuntu corresponde à sua versão derivada.
- Algumas distribuições Linux fornecem um pacote da Docker Engine por meio de
  seus repositórios de pacotes.
  Esses pacotes são construídos e mantidos pelas pessoas mantenedoras de pacotes
  da distribuição Linux e podem apresentar diferenças de configuração ou serem
  construídos a partir de código-fonte modificado.
  O Docker não está envolvido na distribuição desses pacotes e você deve relatar
  quaisquer falhas ou problemas relacionados a eles no rastreador de issues da
  sua distribuição Linux.

O Docker fornece [binários](binaries.md) para instalação manual da Docker
Engine.
Esses binários são vinculados estaticamente e você pode usá-los em qualquer
distribuição Linux.

## Canais de lançamento

A Docker Engine possui dois tipos de canais de atualização: **stable** e
**test**:

- O canal **stable** fornece as versões mais recentes lançadas para
  disponibilidade geral.
- O canal **test** fornece versões de pré-lançamento prontas para testes antes
  da disponibilização geral.

Use o canal de teste com cautela.
As versões de pré-lançamento incluem recursos experimentais e de acesso
antecipado que estão sujeitos a alterações que podem causar incompatibilidade.

## Support

Docker Engine is an open source project, supported by the Moby project maintainers
and community members. Docker doesn't provide support for Docker Engine.
Docker provides support for Docker products, including Docker Desktop, which uses
Docker Engine as one of its components.

For information about the open source project, refer to the
[Moby project website](https://mobyproject.org/).

### Upgrade path

Patch releases are always backward compatible with its major and minor version.

### Licensing

Commercial use of Docker Engine obtained via Docker Desktop
within larger enterprises (exceeding 250 employees OR with annual revenue surpassing
$10 million USD), requires a [paid subscription](https://www.docker.com/pricing/).
Apache License, Version 2.0. See [LICENSE](https://github.com/moby/moby/blob/master/LICENSE) for the full license.

## Reporting security issues

If you discover a security issue, we request that you bring it to our attention immediately.

DO NOT file a public issue. Instead, submit your report privately to security@docker.com.

Security reports are greatly appreciated, and Docker will publicly thank you for it.

## Get started

After setting up Docker, you can learn the basics with
[Getting started with Docker](/get-started/introduction/_index.md).
