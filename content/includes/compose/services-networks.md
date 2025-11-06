---
# Copyright (c) 2013-2025 Docker Inc.
# Docker and the Docker logo are trademarks or registered trademarks of Docker,
# Inc. in the United States and/or other countries.
# Docker, Inc. and other parties may also have trademark rights in other terms
# used herein.
#
# Documentation licensed under the Apache License, Version 2.0.
# The original work was translated from English into Brazilian Portuguese.
# https://github.com/docker/docs/blob/-/LICENSE

source_url: https://github.com/docker/docs/blob/main/content/includes/compose/services-networks.md
revision: e3aa78b72c9faf56e97896681c33425cafc1c847
status: ready
---

O atributo `networks` define as redes às quais os contêineres de serviço estão
conectados, fazendo referência às entradas no elemento de nível superior
`networks`.
O atributo `networks` ajuda a gerenciar os aspectos de rede dos contêineres,
fornecendo controle sobre como os serviços são segmentados e interagem dentro do
ambiente Docker.
Ele é usado para especificar a quais redes os contêineres desse serviço devem se
conectar.
Isso é importante para definir como os contêineres se comunicam entre si e
externamente.
