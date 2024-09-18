---
source_url: https://github.com/docker/compose/blob/main/docs/reference/compose_port.md
revision: 231ea10058c95ed6308fe4f6ccc1327a553a40ca
status: untranslated
license: https://github.com/docker/compose/blob/master/LICENSE

datafolder: compose-cli
datafile: docker_compose_port
title: docker compose port
aliases:
- /compose/reference/port/
- /engine/reference/commandline/compose_port/
layout: cli
---

# docker compose port

Prints the public port for a port binding

### Options

| Name         | Type     | Default | Description                                             |
|:-------------|:---------|:--------|:--------------------------------------------------------|
| `--dry-run`  | `bool`   |         | Execute command in dry run mode                         |
| `--index`    | `int`    | `0`     | Index of the container if service has multiple replicas |
| `--protocol` | `string` | `tcp`   | tcp or udp                                              |



## Description

Prints the public port for a port binding
