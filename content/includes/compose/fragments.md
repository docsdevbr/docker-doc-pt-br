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

source_url: https://github.com/docker/docs/blob/main/content/includes/compose/fragments.md
source_revision: 7e9a8ec5ed90ef58a3999993b7204e3fe8ae0d44
translation_status: ready
---

Com o Compose, você pode usar recursos nativos do
[YAML](https://www.yaml.org/spec/1.2/spec.html#id2765878) para tornar seu
arquivo Compose mais organizado e eficiente.
Âncoras e apelidos permitem criar blocos reutilizáveis.
Isso é útil se você começar a encontrar configurações comuns que abrangem vários
serviços.
Ter blocos reutilizáveis minimiza possíveis erros.
