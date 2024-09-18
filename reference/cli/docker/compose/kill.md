---
source_url: https://github.com/docker/compose/blob/main/docs/reference/compose_kill.md
revision: 1601ead7bcb831dafe5ea0d675581df8b89917ab
status: untranslated
license: https://github.com/docker/compose/blob/master/LICENSE

datafolder: compose-cli
datafile: docker_compose_kill
title: docker compose kill
aliases:
- /compose/reference/kill/
- /engine/reference/commandline/compose_kill/
layout: cli
---

# docker compose kill

Forces running containers to stop by sending a `SIGKILL` signal. Optionally the signal can be passed, for example:

```console
$ docker compose kill -s SIGINT
```

### Options

| Name               | Type     | Default   | Description                                                    |
|:-------------------|:---------|:----------|:---------------------------------------------------------------|
| `--dry-run`        | `bool`   |           | Execute command in dry run mode                                |
| `--remove-orphans` | `bool`   |           | Remove containers for services not defined in the Compose file |
| `-s`, `--signal`   | `string` | `SIGKILL` | SIGNAL to send to the container                                |



## Description

Forces running containers to stop by sending a `SIGKILL` signal. Optionally the signal can be passed, for example:

```console
$ docker compose kill -s SIGINT
```
