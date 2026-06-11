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

source_url: https://github.com/docker/docs/blob/main/content/reference/compose-file/configs.md
source_revision: 3415afac4033c6befb133d63ca992a72b288dd7a
translation_status: ready

linkTitle: Configs
title: Elemento de nível superior `configs`
description: >-
  Gerencie e compartilhe dados de configuração usando o elemento `configs` no
  Docker Compose.
keywords: >-
  compose, especificação do compose, configurações, referência de arquivo
  compose
aliases:
  - /compose/compose-file/08-configs/
weight: 50
---

{{% include "compose/configs.md" %}}

Os serviços só podem acessar as configurações quando explicitamente autorizados
por um atributo [`configs`](services.md#configs) dentro do elemento de nível
superior `services`.

Por padrão, a configuração:
- Pertence ao usuário que executa o comando do contêiner, mas pode ser
  substituída pela configuração do serviço.
- Possui permissões de leitura para todos (modo 0444), a menos que o serviço
  esteja configurado para substituir isso.

A declaração de nível superior `configs` define ou referencia dados de
configuração concedidos aos serviços em sua aplicação Compose.
A origem da configuração pode ser `file`, `environment`, `content` ou
`external`.

- `file`: A configuração é criada com o conteúdo do arquivo no caminho
  especificado.
- `environment`: O conteúdo da configuração é criado com o valor de uma variável
  de ambiente.
  Introduzida na versão
  [2.23.1](https://github.com/docker/compose/releases/tag/v2.23.1).
- `content`: O conteúdo é criado com o valor em linha.
  Introduzida na versão
  [2.23.1](https://github.com/docker/compose/releases/tag/v2.23.1).
- `external`: Se definido como `true`, `external` especifica que esta
  configuração já foi criada.
  O Compose não tenta criá-la e, se ela não existir, ocorre um erro.
- `name`: O nome do objeto de configuração no mecanismo de contêiner a ser
  pesquisado.
  Este campo pode ser usado para referenciar configurações que contenham
  caracteres especiais.
  O nome é usado como está e **não** será definido com o nome do projeto.

## Exemplo 1

O arquivo `<nome_do_projeto>_http_config` é criado quando a aplicação é
implantada, registrando o conteúdo do arquivo `httpd.conf` como dados de
configuração.

```yml
configs:
  http_config:
    file: ./httpd.conf
```

Alternativamente, `http_config` pode ser declarada como externa.
O Compose consulta `http_config` para expor os dados de configuração aos
serviços.

```yml
configs:
  http_config:
    external: true
```

## Exemplo 2

A busca de configurações externas também pode usar uma chave distinta
especificando um `nome`.

O exemplo a seguir modifica o anterior para buscar uma configuração usando o
parâmetro `HTTP_CONFIG_KEY`.
A chave de busca real é definida no momento da implantação pela
[interpolação](interpolation.md) de variáveis, mas exposta aos contêineres como
o ID fixo `http_config`.

```yml
configs:
  http_config:
    external: true
    name: "${HTTP_CONFIG_KEY}"
```

## Exemplo 3

`<nome_do_projeto>_app_config` é criada quando a aplicação é implantada,
registrando o conteúdo em linha como dados de configuração.
Isso significa que o Compose infere variáveis ao criar a configuração, o que
permite ajustar o conteúdo conforme a configuração do serviço:

```yml
configs:
  app_config:
    content: |
      debug=${DEBUG}
      spring.application.admin.enabled=${DEBUG}
      spring.application.name=${COMPOSE_PROJECT_NAME}
```

## Exemplo 4

`<nome_do_projeto>_simple_config` é criada quando a aplicação é implantada,
usando o valor de uma variável de ambiente como dados de configuração.
Isso é útil para valores de configuração simples que não exigem interpolação:

```yml
configs:
  simple_config:
    environment: "SIMPLE_CONFIG_VALUE"
```

Se `external` estiver definido como `true`, todos os outros atributos, exceto
`name`, serão irrelevantes.
Se o Compose detectar qualquer outro atributo, ele rejeitará o arquivo Compose
como inválido.
