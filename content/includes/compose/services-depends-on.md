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

source_url: https://github.com/docker/docs/blob/main/content/includes/compose/services-depends-on.md
revision: e3aa78b72c9faf56e97896681c33425cafc1c847
status: ready
---

Com o atributo `depends_on`, você pode controlar a ordem de inicialização e
encerramento dos serviços.
Isso é útil quando os serviços são altamente interdependentes e a sequência de
inicialização impacta a funcionalidade da aplicação.
