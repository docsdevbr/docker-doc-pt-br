---
source_url: https://github.com/docker/compose/blob/main/docs/reference/compose_logs.md
revision: 231ea10058c95ed6308fe4f6ccc1327a553a40ca
status: untranslated
license: https://github.com/docker/compose/blob/master/LICENSE

datafolder: compose-cli
datafile: docker_compose_logs
title: docker compose logs
aliases:
- /compose/reference/logs/
- /engine/reference/commandline/compose_logs/
layout: cli
---

# docker compose logs

Displays log output from services

### Options

| Name                 | Type     | Default | Description                                                                                    |
|:---------------------|:---------|:--------|:-----------------------------------------------------------------------------------------------|
| `--dry-run`          | `bool`   |         | Execute command in dry run mode                                                                |
| `-f`, `--follow`     | `bool`   |         | Follow log output                                                                              |
| `--index`            | `int`    | `0`     | index of the container if service has multiple replicas                                        |
| `--no-color`         | `bool`   |         | Produce monochrome output                                                                      |
| `--no-log-prefix`    | `bool`   |         | Don't print prefix in logs                                                                     |
| `--since`            | `string` |         | Show logs since timestamp (e.g. 2013-01-02T13:23:37Z) or relative (e.g. 42m for 42 minutes)    |
| `-n`, `--tail`       | `string` | `all`   | Number of lines to show from the end of the logs for each container                            |
| `-t`, `--timestamps` | `bool`   |         | Show timestamps                                                                                |
| `--until`            | `string` |         | Show logs before a timestamp (e.g. 2013-01-02T13:23:37Z) or relative (e.g. 42m for 42 minutes) |



## Description

Displays log output from services
