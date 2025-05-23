---
# Copyright (c) 2016 Docker, Inc.
# Docker and the Docker logo are trademarks or registered trademarks of Docker,
# Inc. in the United States and/or other countries.
# Docker, Inc. and other parties may also have trademark rights in other terms
# used herein.
#
# Documentation licensed under the Apache License, Version 2.0.
# The original work was translated from English into Brazilian Portuguese.
# https://github.com/docker/docs/blob/main/LICENSE

title: Docker terminology
description: Docker specific terminology and definitions
keywords: terminology, style guide, contribute
---
#### `compose.yaml`

The current designation for the Compose file, as it's a file, format as code.

#### Compose plugin

The compose plugin as an add-on (for Docker CLI) that can be enabled/disabled.

#### Digest

A long string that’s automatically created every time you push an image. You can pull an image by Digest or by Tag.

#### Docker Compose

Use when we talk about the application, or all the functionality associated with the application.

#### `docker compose`

Use code formatting for referring to the commands in text and command usage examples/code samples.

#### Docker Compose CLI

Use when referring to family of Compose commands as offered from the Docker CLI.

#### K8s

Don't use. Use `Kubernetes` instead.

#### Multi-platform

(broad meaning) Mac vs Linux vs Microsoft but also pair of platform architecture such as in Linux/amd64 and Linux/arm64; (narrow meaning) Windows/Linux/macOS.

#### Multi-architecture / multi-arch

To use when referring specifically to CPU architecture or something that is hardware-architecture-based. Avoid using it as meaning the same as multi-platform.

#### Member

A user of Docker Hub that is a part of an organization

#### Namespace

Organization or User name. Every image needs a namespace to live under.

#### Node

A node is a physical or virtual machine running an instance of the Docker Engine in swarm mode.
Manager nodes perform swarm management and orchestration duties. By default manager nodes are also worker nodes.
Worker nodes invoke tasks.

#### Registry

Online storage for Docker images.

#### Repository

Lets users share container images with their team, customers, or Docker community.
