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
---

Extensions can be used to make your Compose file more efficient and easier to maintain.

Use the prefix `x-` as a top-level element to modularize configurations that you want to reuse.
Compose ignores any fields that start with `x-`, this is the sole exception where Compose silently ignores unrecognized fields.
