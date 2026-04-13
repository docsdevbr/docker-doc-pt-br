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

title: R language-specific guide
linkTitle: R
description: Containerize R apps using Docker
keywords: Docker, getting started, R, language
summary: |
  This guide details how to containerize R applications using Docker.
toc_min: 1
toc_max: 2
aliases:
  - /languages/r/
  - /guides/languages/r/
languages: [r]
params:
  time: 10 minutes
---
The R language-specific guide teaches you how to containerize a R application using Docker. In this guide, you’ll learn how to:

- Containerize and run a R application
- Set up a local environment to develop a R application using containers
- Configure a CI/CD pipeline for a containerized R application using GitHub Actions
- Deploy your containerized R application locally to Kubernetes to test and debug your deployment

Start by containerizing an existing R application.
