---
source_url: https://github.com/docker/compose/blob/main/docs/reference/compose_down.md
revision: 231ea10058c95ed6308fe4f6ccc1327a553a40ca
status: untranslated
license: https://github.com/docker/compose/blob/master/LICENSE

datafolder: compose-cli
datafile: docker_compose_down
title: docker compose down
aliases:
- /compose/reference/down/
- /engine/reference/commandline/compose_down/
layout: cli
---

# docker compose down

Stops containers and removes containers, networks, volumes, and images created by `up`.

By default, the only things removed are:

- Containers for services defined in the Compose file.
- Networks defined in the networks section of the Compose file.
- The default network, if one is used.

Networks and volumes defined as external are never removed.

Anonymous volumes are not removed by default. However, as they don’t have a stable name, they are not automatically
mounted by a subsequent `up`. For data that needs to persist between updates, use explicit paths as bind mounts or
named volumes.

### Options

| Name               | Type     | Default | Description                                                                                                             |
|:-------------------|:---------|:--------|:------------------------------------------------------------------------------------------------------------------------|
| `--dry-run`        | `bool`   |         | Execute command in dry run mode                                                                                         |
| `--remove-orphans` | `bool`   |         | Remove containers for services not defined in the Compose file                                                          |
| `--rmi`            | `string` |         | Remove images used by services. "local" remove only images that don't have a custom tag ("local"\|"all")                |
| `-t`, `--timeout`  | `int`    | `0`     | Specify a shutdown timeout in seconds                                                                                   |
| `-v`, `--volumes`  | `bool`   |         | Remove named volumes declared in the "volumes" section of the Compose file and anonymous volumes attached to containers |



## Description

Stops containers and removes containers, networks, volumes, and images created by `up`.

By default, the only things removed are:

- Containers for services defined in the Compose file.
- Networks defined in the networks section of the Compose file.
- The default network, if one is used.

Networks and volumes defined as external are never removed.

Anonymous volumes are not removed by default. However, as they don’t have a stable name, they are not automatically
mounted by a subsequent `up`. For data that needs to persist between updates, use explicit paths as bind mounts or
named volumes.
