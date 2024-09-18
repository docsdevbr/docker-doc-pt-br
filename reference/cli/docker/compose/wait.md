---
source_url: https://github.com/docker/compose/blob/main/docs/reference/compose_wait.md
revision: 98e261ba3258354e7c40053aa32004a246cd6333
status: untranslated
license: https://github.com/docker/compose/blob/master/LICENSE

datafolder: compose-cli
datafile: docker_compose_wait
title: docker compose wait
layout: cli
aliases:
- /engine/reference/commandline/compose_wait/
---

# docker compose wait

Block until containers of all (or specified) services stop.

### Options

| Name             | Type   | Default | Description                                  |
|:-----------------|:-------|:--------|:---------------------------------------------|
| `--down-project` | `bool` |         | Drops project when the first container stops |
| `--dry-run`      | `bool` |         | Execute command in dry run mode              |
