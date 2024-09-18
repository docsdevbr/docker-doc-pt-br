---
source_url: https://github.com/docker/compose/blob/main/docs/reference/compose_cp.md
revision: 231ea10058c95ed6308fe4f6ccc1327a553a40ca
status: untranslated
license: https://github.com/docker/compose/blob/master/LICENSE

datafolder: compose-cli
datafile: docker_compose_cp
title: docker compose cp
layout: cli
aliases:
- /engine/reference/commandline/compose_cp/
---

# docker compose cp

Copy files/folders between a service container and the local filesystem

### Options

| Name                  | Type   | Default | Description                                             |
|:----------------------|:-------|:--------|:--------------------------------------------------------|
| `-a`, `--archive`     | `bool` |         | Archive mode (copy all uid/gid information)             |
| `--dry-run`           | `bool` |         | Execute command in dry run mode                         |
| `-L`, `--follow-link` | `bool` |         | Always follow symbol link in SRC_PATH                   |
| `--index`             | `int`  | `0`     | Index of the container if service has multiple replicas |
