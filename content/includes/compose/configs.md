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

source_url: https://github.com/docker/docs/blob/main/content/includes/compose/configs.md
source_revision: 39d3def5a5cdff3a5286a994b06d9921d1e4e65a
translation_status: ready
---

Configs (configurações) permitem que os serviços adaptem seu comportamento sem a
necessidade de reconstruir uma imagem Docker.
Assim como os volumes, as configurações são montadas como arquivos no sistema de
arquivos de um contêiner.
O local do ponto de montagem dentro do contêiner é, por padrão,
`/<nome-da-configuração>` em contêineres Linux e `C:\<nome-da-configuração>` em
contêineres Windows.
