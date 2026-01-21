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

source_url: https://github.com/docker/docs/blob/main/content/includes/compose/services-volumes.md
revision: e3aa78b72c9faf56e97896681c33425cafc1c847
status: ready
---

O atributo `volumes` define caminhos de montagem de hosts ou volumes nomeados
que são acessíveis por contêineres de serviço.
Você pode usar `volumes` para definir vários tipos de montagens: `volume`,
`bind`, `tmpfs` ou `npipe`.

Se a montagem for um caminho de host e for usada apenas por um único serviço,
ela poderá ser declarada como parte da definição do serviço.
Para reutilizar um volume em vários serviços, um volume nomeado deve ser
declarado no elemento de nível superior `volumes`.
