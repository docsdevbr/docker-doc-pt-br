---
source_url: https://github.com/docker/compose/blob/main/docs/reference/compose_create.md
revision: 231ea10058c95ed6308fe4f6ccc1327a553a40ca
status: untranslated
license: https://github.com/docker/compose/blob/master/LICENSE

datafolder: compose-cli
datafile: docker_compose_create
title: docker compose create
aliases:
- /compose/reference/create/
- /engine/reference/commandline/compose_create/
layout: cli
---

# docker compose create

Creates containers for a service

### Options

| Name               | Type          | Default  | Description                                                                                   |
|:-------------------|:--------------|:---------|:----------------------------------------------------------------------------------------------|
| `--build`          | `bool`        |          | Build images before starting containers                                                       |
| `--dry-run`        | `bool`        |          | Execute command in dry run mode                                                               |
| `--force-recreate` | `bool`        |          | Recreate containers even if their configuration and image haven't changed                     |
| `--no-build`       | `bool`        |          | Don't build an image, even if it's policy                                                     |
| `--no-recreate`    | `bool`        |          | If containers already exist, don't recreate them. Incompatible with --force-recreate.         |
| `--pull`           | `string`      | `policy` | Pull image before running ("always"\|"missing"\|"never"\|"build")                             |
| `--quiet-pull`     | `bool`        |          | Pull without printing progress information                                                    |
| `--remove-orphans` | `bool`        |          | Remove containers for services not defined in the Compose file                                |
| `--scale`          | `stringArray` |          | Scale SERVICE to NUM instances. Overrides the `scale` setting in the Compose file if present. |
