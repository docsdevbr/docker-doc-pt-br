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

description: Summary of samples related to Compose
keywords: documentation, docs, docker, compose, samples
title: Sample apps with Compose
linkTitle: Sample apps
weight: 30
aliases:
- /compose/samples-for-compose/
---
The following samples show the various aspects of how to work with Docker
Compose. As a prerequisite, be sure to [install Docker Compose](/manuals/compose/install/_index.md)
if you have not already done so.

## Key concepts these samples cover

The samples should help you to:

- Define services based on Docker images using
  [Compose files](/reference/compose-file/_index.md): `compose.yaml` and
  `docker-stack.yml`
- Understand the relationship between `compose.yaml` and
  [Dockerfiles](/reference/dockerfile/)
- Learn how to make calls to your application services from Compose files
- Learn how to deploy applications and services to a [swarm](/manuals/engine/swarm/_index.md)

## Samples tailored to demo Compose

These samples focus specifically on Docker Compose:

- [Quickstart: Compose and ELK](https://github.com/docker/awesome-compose/tree/master/elasticsearch-logstash-kibana/README.md) - Shows
  how to use Docker Compose to set up and run ELK - Elasticsearch-Logstash-Kibana.

- [Quickstart: Compose and Django](https://github.com/docker/awesome-compose/tree/master/official-documentation-samples/django/README.md) - Shows
  how to use Docker Compose to set up and run a simple Django/PostgreSQL app.

- [Quickstart: Compose and Rails](https://github.com/docker/awesome-compose/tree/master/official-documentation-samples/rails/README.md) - Shows
  how to use Docker Compose to set up and run a Rails/PostgreSQL app.

- [Quickstart: Compose and WordPress](https://github.com/docker/awesome-compose/tree/master/official-documentation-samples/wordpress/README.md) - Shows
  how to use Docker Compose to set up and run WordPress in an isolated
  environment with Docker containers.

## Awesome Compose samples

The Awesome Compose samples provide a starting point on how to integrate different frameworks and technologies using Docker Compose. All samples are available in the [Awesome-compose GitHub repo](https://github.com/docker/awesome-compose) and are ready to run with `docker compose up`.
