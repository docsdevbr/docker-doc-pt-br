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

source_url: https://github.com/docker/docs/blob/main/content/includes/compose/networks.md
source_revision: e3aa78b72c9faf56e97896681c33425cafc1c847
translation_status: ready
---

As redes permitem que os serviços se comuniquem entre si.
Por padrão, o Compose configura uma única rede para sua aplicação.
Cada contêiner de um serviço entra na rede padrão e é acessível por outros
contêineres nessa rede, além de ser detectável pelo nome do serviço.
O elemento de nível superior `networks` permite configurar redes nomeadas que
podem ser reutilizadas em vários serviços.
