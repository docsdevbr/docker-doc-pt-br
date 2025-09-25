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

title: Bake
weight: 50
keywords: build, buildx, bake, buildkit, hcl, json, compose
aliases:
  - /build/customize/bake/
---
Bake is a feature of Docker Buildx that lets you define your build configuration
using a declarative file, as opposed to specifying a complex CLI expression. It
also lets you run multiple builds concurrently with a single invocation.

A Bake file can be written in HCL, JSON, or YAML formats, where the YAML format
is an extension of a Docker Compose file. Here's an example Bake file in HCL
format:

```hcl {title=docker-bake.hcl}
group "default" {
  targets = ["frontend", "backend"]
}

target "frontend" {
  context = "./frontend"
  dockerfile = "frontend.Dockerfile"
  args = {
    NODE_VERSION = "22"
  }
  tags = ["myapp/frontend:latest"]
}

target "backend" {
  context = "./backend"
  dockerfile = "backend.Dockerfile"
  args = {
    GO_VERSION = "{{% param "example_go_version" %}}"
  }
  tags = ["myapp/backend:latest"]
}
```

The `group` block defines a group of targets that can be built concurrently.
Each `target` block defines a build target with its own configuration, such as
the build context, Dockerfile, and tags.

To invoke a build using the above Bake file, you can run:

```console
$ docker buildx bake
```

This executes the `default` group, which builds the `frontend` and `backend`
targets concurrently.

## Get started

To learn how to get started with Bake, head over to the [Bake introduction](./introduction.md).
