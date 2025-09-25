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

description: How to setup Docker Scout in continuous integration pipelines
keywords: scanning, vulnerabilities, Hub, supply chain, security, ci, continuous integration,
  github actions, gitlab
title: Using Docker Scout in continuous integration
linkTitle: Continuous Integration
aliases:
- /scout/ci/
---
You can analyze Docker images in continuous integration pipelines as you build
them using a GitHub action or the Docker Scout CLI plugin.

Available integrations:

- [GitHub Actions](gha.md)
- [GitLab](gitlab.md)
- [Microsoft Azure DevOps Pipelines](azure.md)
- [Circle CI](circle-ci.md)
- [Jenkins](jenkins.md)

You can also add runtime integration as part of your CI/CD pipeline, which lets
you assign an image to an environment, such as `production` or `staging`, when
you deploy it. For more information, see [Environment monitoring](../environment/_index.md).
