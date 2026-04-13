---
# Copyright (c) 2013-2026 Docker Inc.
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

> [!NOTE]
>
> Buildx v0.10 enables support for a minimal [SLSA Provenance](https://slsa.dev/provenance/)
> attestation, which requires support for [OCI-compliant](https://github.com/opencontainers/image-spec)
> multi-platform images. This may introduce issues with registry and runtime support
> (e.g. [Google Cloud Run and AWS Lambda](https://github.com/docker/buildx/issues/1533)).
> You can optionally disable the default provenance attestation functionality
> using `--provenance=false`.
