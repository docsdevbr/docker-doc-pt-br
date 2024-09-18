---
source_url: https://github.com/docker/compose/blob/main/docs/reference/compose_rm.md
revision: 231ea10058c95ed6308fe4f6ccc1327a553a40ca
status: untranslated
license: https://github.com/docker/compose/blob/master/LICENSE

datafolder: compose-cli
datafile: docker_compose_rm
title: docker compose rm
aliases:
- /compose/reference/rm/
- /engine/reference/commandline/compose_rm/
layout: cli
---

# docker compose rm

Removes stopped service containers.

By default, anonymous volumes attached to containers are not removed. You can override this with `-v`. To list all
volumes, use `docker volume ls`.

Any data which is not in a volume is lost.

Running the command with no options also removes one-off containers created by `docker compose run`:

```console
$ docker compose rm
Going to remove djangoquickstart_web_run_1
Are you sure? [yN] y
Removing djangoquickstart_web_run_1 ... done
```

### Options

| Name              | Type   | Default | Description                                         |
|:------------------|:-------|:--------|:----------------------------------------------------|
| `--dry-run`       | `bool` |         | Execute command in dry run mode                     |
| `-f`, `--force`   | `bool` |         | Don't ask to confirm removal                        |
| `-s`, `--stop`    | `bool` |         | Stop the containers, if required, before removing   |
| `-v`, `--volumes` | `bool` |         | Remove any anonymous volumes attached to containers |



## Description

Removes stopped service containers.

By default, anonymous volumes attached to containers are not removed. You can override this with `-v`. To list all
volumes, use `docker volume ls`.

Any data which is not in a volume is lost.

Running the command with no options also removes one-off containers created by `docker compose run`:

```console
$ docker compose rm
Going to remove djangoquickstart_web_run_1
Are you sure? [yN] y
Removing djangoquickstart_web_run_1 ... done
```
