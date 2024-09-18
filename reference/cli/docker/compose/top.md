---
source_url: https://github.com/docker/compose/blob/main/docs/reference/compose_top.md
revision: 231ea10058c95ed6308fe4f6ccc1327a553a40ca
status: untranslated
license: https://github.com/docker/compose/blob/master/LICENSE

datafolder: compose-cli
datafile: docker_compose_top
title: docker compose top
aliases:
- /compose/reference/top/
- /engine/reference/commandline/compose_top/
layout: cli
---

# docker compose top

Displays the running processes

### Options

| Name        | Type   | Default | Description                     |
|:------------|:-------|:--------|:--------------------------------|
| `--dry-run` | `bool` |         | Execute command in dry run mode |



## Description

Displays the running processes

## Examples

```console
$ docker compose top
example_foo_1
UID    PID      PPID     C    STIME   TTY   TIME       CMD
root   142353   142331   2    15:33   ?     00:00:00   ping localhost -c 5
```
