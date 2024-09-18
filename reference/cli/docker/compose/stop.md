---
source_url: https://github.com/docker/compose/blob/main/docs/reference/compose_stop.md
revision: 231ea10058c95ed6308fe4f6ccc1327a553a40ca
status: untranslated
license: https://github.com/docker/compose/blob/master/LICENSE

datafolder: compose-cli
datafile: docker_compose_stop
title: docker compose stop
aliases:
- /compose/reference/stop/
- /engine/reference/commandline/compose_stop/
layout: cli
---

# docker compose stop

Stops running containers without removing them. They can be started again with `docker compose start`.

### Options

| Name              | Type   | Default | Description                           |
|:------------------|:-------|:--------|:--------------------------------------|
| `--dry-run`       | `bool` |         | Execute command in dry run mode       |
| `-t`, `--timeout` | `int`  | `0`     | Specify a shutdown timeout in seconds |



## Description

Stops running containers without removing them. They can be started again with `docker compose start`.
