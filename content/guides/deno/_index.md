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

description: Containerize and develop Deno applications using Docker.
keywords: getting started, deno
title: Deno language-specific guide
summary: |
  Learn how to containerize JavaScript applications with the Deno runtime using Docker.
linkTitle: Deno
languages: [js]
params:
  time: 10 minutes
---
The Deno getting started guide teaches you how to create a containerized Deno application using Docker. In this guide, you'll learn how to:

> **Acknowledgment**
>
> Docker would like to thank [Pradumna Saraf](https://twitter.com/pradumna_saraf) for his contribution to this guide.

## What will you learn?

* Containerize and run a Deno application using Docker
* Set up a local environment to develop a Deno application using containers
* Use Docker Compose to run the application.
* Configure a CI/CD pipeline for a containerized Deno application using GitHub Actions
* Deploy your containerized application locally to Kubernetes to test and debug your deployment

## Prerequisites

- Basic understanding of JavaScript is assumed.
- You must have familiarity with Docker concepts like containers, images, and Dockerfiles. If you are new to Docker, you can start with the [Docker basics](/get-started/docker-concepts/the-basics/what-is-a-container.md) guide.

After completing the Deno getting started modules, you should be able to containerize your own Deno application based on the examples and instructions provided in this guide.

Start by containerizing an existing Deno application.
