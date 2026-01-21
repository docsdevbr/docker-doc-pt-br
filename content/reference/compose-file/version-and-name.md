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

source_url: https://github.com/docker/docs/blob/main/content/reference/compose-file/version-and-name.md
revision: 4c6f75f19facf9fcba938315035addd2949f180b
status: ready

title: Elementos de nível superior version e name
description: >-
  Entenda quando e se deve definir os elementos de nível superior version e
  name.
keywords: >-
  compose, especificação do compose, serviços, referência do arquivo compose
aliases:
  - /compose/compose-file/04-version-and-name/
weight: 10
---

## Elemento de nível superior `version` (obsoleto)

> [!IMPORTANT]
>
> A propriedade de nível superior `version` é definida pela Especificação do
> Compose para compatibilidade com versões anteriores.
> Ela é apenas informativa e você receberá uma mensagem de alerta informando que
> está obsoleta se for usada.

O Compose sempre usa o esquema mais recente para validar o arquivo Compose,
independentemente do campo `version`.

O Compose valida se consegue analisar completamente o arquivo Compose.
Se alguns campos forem desconhecidos, normalmente porque o arquivo Compose foi
escrito com campos definidos por uma versão mais recente da Especificação, você
receberá uma mensagem de alerta.

## Elemento de nível superior `name`

A propriedade de nível superior `name` é definida pela Especificação do Compose
como o nome do projeto a ser usado caso você não defina um explicitamente.

O Compose oferece uma maneira de sobrescrever esse nome e define um nome de
projeto padrão a ser usado se o elemento de nível superior `name` não estiver
definido.

Sempre que um nome de projeto é definido pelo elemento de nível superior `name`
ou por algum mecanismo personalizado, ele é exposto para
[interpolação](interpolation.md) e resolução de variáveis de ambiente como
`COMPOSE_PROJECT_NAME`.

```yml
name: minha-aplicacao

services:
  foo:
    image: busybox
    command: echo "Estou executando ${COMPOSE_PROJECT_NAME}"
```

Para obter mais informações sobre outras maneiras de nomear projetos Compose,
consulte
[Especificar um nome de projeto](/manuals/compose/how-tos/project-name.md).
