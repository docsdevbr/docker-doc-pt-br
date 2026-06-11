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

source_url: https://github.com/docker/docs/blob/main/content/includes/compose/volumes.md
source_revision: e3aa78b72c9faf56e97896681c33425cafc1c847
translation_status: ready
---

Volumes são armazenamentos de dados persistentes implementados pela engine de
contêineres.
O Compose oferece uma maneira neutra para os serviços montarem volumes e
parâmetros de configuração para alocá-los à infraestrutura.
A declaração de nível superior `volumes` permite configurar volumes nomeados que
podem ser reutilizados por vários serviços.
