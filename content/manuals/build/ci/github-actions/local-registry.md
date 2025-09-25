---
# Copyright (c) 2013-2025 Docker Inc.
# Docker and the Docker logo are trademarks or registered trademarks of Docker,
# Inc. in the United States and/or other countries.
# Docker, Inc. and other parties may also have trademark rights in other terms
# used herein.
#
# Documentation licensed under the Apache License, Version 2.0.
# The original work was translated from English into Brazilian Portuguese.
# https://github.com/docker/docs/blob/main/LICENSE

title: Local registry with GitHub Actions
linkTitle: Local registry
description: Create and use a local OCI registry with GitHub Actions
keywords: ci, github actions, gha, buildkit, buildx, registry
---
For testing purposes you may need to create a [local registry](https://hub.docker.com/_/registry)
to push images into:

```yaml
name: ci

on:
  push:

jobs:
  docker:
    runs-on: ubuntu-latest
    services:
      registry:
        image: registry:2
        ports:
          - 5000:5000
    steps:
      - name: Set up QEMU
        uses: docker/setup-qemu-action@v3

      - name: Set up Docker Buildx
        uses: docker/setup-buildx-action@v3
        with:
          driver-opts: network=host

      - name: Build and push to local registry
        uses: docker/build-push-action@v6
        with:
          push: true
          tags: localhost:5000/name/app:latest

      - name: Inspect
        run: |
          docker buildx imagetools inspect localhost:5000/name/app:latest
```
