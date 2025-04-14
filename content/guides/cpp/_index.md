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

title: C++ language-specific guide
linkTitle: C++
description: Containerize and develop C++ applications using Docker.
keywords: getting started, c++
summary: |
  This guide explains how to containerize C++ applications using Docker.
toc_min: 1
toc_max: 2
aliases:
  - /language/cpp/
  - /guides/language/cpp/
languages: [cpp]
params:
  time: 20 minutes
---
The C++ getting started guide teaches you how to create a containerized C++ application using Docker. In this guide, you'll learn how to:

> **Acknowledgment**
>
> Docker would like to thank [Pradumna Saraf](https://twitter.com/pradumna_saraf) and [Mohammad-Ali A'râbi](https://twitter.com/MohammadAliEN) for their contribution to this guide.

- Containerize and run a C++ application using a multi-stage Docker build
- Build and run a C++ application using Docker Compose
- Set up a local environment to develop a C++ application using containers
- Configure a CI/CD pipeline for a containerized C++ application using GitHub Actions
- Deploy your containerized application locally to Kubernetes to test and debug your deployment
- Use BuildKit to generate SBOM attestations during the build process

After completing the C++ getting started modules, you should be able to containerize your own C++ application based on the examples and instructions provided in this guide.

Start by containerizing an existing C++ application.
