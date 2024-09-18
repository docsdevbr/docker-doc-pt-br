---
source_url: https://github.com/docker/compose/blob/main/docs/reference/compose_exec.md
revision: 231ea10058c95ed6308fe4f6ccc1327a553a40ca
status: untranslated
license: https://github.com/docker/compose/blob/master/LICENSE

datafolder: compose-cli
datafile: docker_compose_exec
title: docker compose exec
aliases:
- /compose/reference/exec/
- /engine/reference/commandline/compose_exec/
layout: cli
---

# docker compose exec

This is the equivalent of `docker exec` targeting a Compose service.

With this subcommand, you can run arbitrary commands in your services. Commands allocate a TTY by default, so
you can use a command such as `docker compose exec web sh` to get an interactive prompt.

### Options

| Name              | Type          | Default | Description                                                                      |
|:------------------|:--------------|:--------|:---------------------------------------------------------------------------------|
| `-d`, `--detach`  | `bool`        |         | Detached mode: Run command in the background                                     |
| `--dry-run`       | `bool`        |         | Execute command in dry run mode                                                  |
| `-e`, `--env`     | `stringArray` |         | Set environment variables                                                        |
| `--index`         | `int`         | `0`     | Index of the container if service has multiple replicas                          |
| `-T`, `--no-TTY`  | `bool`        | `true`  | Disable pseudo-TTY allocation. By default `docker compose exec` allocates a TTY. |
| `--privileged`    | `bool`        |         | Give extended privileges to the process                                          |
| `-u`, `--user`    | `string`      |         | Run the command as this user                                                     |
| `-w`, `--workdir` | `string`      |         | Path to workdir directory for this command                                       |



## Description

This is the equivalent of `docker exec` targeting a Compose service.

With this subcommand, you can run arbitrary commands in your services. Commands allocate a TTY by default, so
you can use a command such as `docker compose exec web sh` to get an interactive prompt.
