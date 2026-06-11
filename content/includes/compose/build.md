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

source_url: https://github.com/docker/docs/blob/main/content/includes/compose/build.md
source_revision: e3aa78b72c9faf56e97896681c33425cafc1c847
translation_status: ready
---

Build (construção) é uma parte opcional da Especificação do Compose.
Ela informa ao Compose como (re)construir uma aplicação a partir do código-fonte
e permite definir o processo de construção em um arquivo Compose de forma
portátil.
`build` pode ser especificada como uma única string definindo um caminho de
contexto ou como uma definição de construção detalhada.
