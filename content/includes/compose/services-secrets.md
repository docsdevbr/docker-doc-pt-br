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

source_url: https://github.com/docker/docs/blob/main/content/includes/compose/services-secrets.md
revision: e3aa78b72c9faf56e97896681c33425cafc1c847
status: ready
---

O atributo `secrets` concede acesso a dados sensíveis definidos pelo elemento de
nível superior `secrets` para cada serviço individualmente.
Os serviços podem ter acesso a múltiplos segredos.
