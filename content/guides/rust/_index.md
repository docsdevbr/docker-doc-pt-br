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

title: Rust language-specific guide
linkTitle: Rust
description: Containerize Rust apps using Docker
keywords: Docker, getting started, Rust, language
summary: |
  This guide covers how to containerize Rust applications using Docker.
toc_min: 1
toc_max: 2
aliases:
  - /language/rust/
  - /guides/language/rust/
languages: [rust]
params:
  time: 20 minutes
---
The Rust language-specific guide teaches you how to create a containerized Rust application using Docker. In this guide, you'll learn how to:

- Containerize a Rust application
- Build an image and run the newly built image as a container
- Set up volumes and networking
- Orchestrate containers using Compose
- Use containers for development
- Configure a CI/CD pipeline for your application using GitHub Actions
- Deploy your containerized Rust application locally to Kubernetes to test and debug your deployment

After completing the Rust modules, you should be able to containerize your own Rust application based on the examples and instructions provided in this guide.

Start with building your first Rust image.
