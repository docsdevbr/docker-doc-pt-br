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

source_url: https://github.com/docker/docs/blob/main/content/includes/compose/services.md
revision: e3aa78b72c9faf56e97896681c33425cafc1c847
status: ready
---

Um serviço é uma definição abstrata de um recurso computacional dentro de uma
aplicação que pode ser escalado ou substituído independentemente de outros
componentes.
Os serviços são suportados por um conjunto de contêineres, executados pela
plataforma de acordo com os requisitos de replicação e restrições de alocação.
Como os serviços são suportados por contêineres, eles são definidos por uma
imagem Docker e um conjunto de argumentos de tempo de execução.
Todos os contêineres dentro de um serviço são criados de forma idêntica com
esses argumentos.
