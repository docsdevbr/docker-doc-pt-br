---
source_url: https://github.com/docker/compose/blob/main/docs/reference/compose_config.md
revision: 231ea10058c95ed6308fe4f6ccc1327a553a40ca
status: untranslated
license: https://github.com/docker/compose/blob/master/LICENSE

datafolder: compose-cli
datafile: docker_compose_config
title: docker compose config
aliases:
- /compose/reference/config/
- /engine/reference/commandline/compose_convert/
- /engine/reference/commandline/compose_config/
layout: cli
---

# docker compose config

`docker compose config` renders the actual data model to be applied on the Docker Engine.
It merges the Compose files set by `-f` flags, resolves variables in the Compose file, and expands short-notation into
the canonical format.

### Aliases

`docker compose config`, `docker compose convert`

### Options

| Name                      | Type     | Default | Description                                                                 |
|:--------------------------|:---------|:--------|:----------------------------------------------------------------------------|
| `--dry-run`               | `bool`   |         | Execute command in dry run mode                                             |
| `--environment`           | `bool`   |         | Print environment used for interpolation.                                   |
| `--format`                | `string` | `yaml`  | Format the output. Values: [yaml \| json]                                   |
| `--hash`                  | `string` |         | Print the service config hash, one per line.                                |
| `--images`                | `bool`   |         | Print the image names, one per line.                                        |
| `--no-consistency`        | `bool`   |         | Don't check model consistency - warning: may produce invalid Compose output |
| `--no-interpolate`        | `bool`   |         | Don't interpolate environment variables                                     |
| `--no-normalize`          | `bool`   |         | Don't normalize compose model                                               |
| `--no-path-resolution`    | `bool`   |         | Don't resolve file paths                                                    |
| `-o`, `--output`          | `string` |         | Save to file (default to stdout)                                            |
| `--profiles`              | `bool`   |         | Print the profile names, one per line.                                      |
| `-q`, `--quiet`           | `bool`   |         | Only validate the configuration, don't print anything                       |
| `--resolve-image-digests` | `bool`   |         | Pin image tags to digests                                                   |
| `--services`              | `bool`   |         | Print the service names, one per line.                                      |
| `--variables`             | `bool`   |         | Print model variables and default values.                                   |
| `--volumes`               | `bool`   |         | Print the volume names, one per line.                                       |



## Description

`docker compose config` renders the actual data model to be applied on the Docker Engine.
It merges the Compose files set by `-f` flags, resolves variables in the Compose file, and expands short-notation into
the canonical format.
