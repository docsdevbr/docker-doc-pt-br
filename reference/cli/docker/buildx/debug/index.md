---
source_url: https://github.com/docker/buildx/blob/master/docs/reference/buildx_debug.md
revision: 7a7a9c8e01e14a83f732a0509dd9128d271d7d2d
status: untranslated
license: https://github.com/docker/buildx/blob/master/LICENSE

datafolder: buildx
datafile: docker_buildx_debug
title: docker buildx debug
layout: cli
aliases:
- /engine/reference/commandline/buildx_debug-shell/
- /engine/reference/commandline/buildx_debug/
---

# docker buildx debug

|             |                       |
|-------------|-----------------------|
| Description | Start debugger        |
| Usage       | `docker buildx debug` |

## Description

Start debugger

## Options

| Name              | Type     | Default | Description                                                                                                         |
|:------------------|:---------|:--------|:--------------------------------------------------------------------------------------------------------------------|
| `--builder`       | `string` |         | Override the configured builder instance                                                                            |
| `-D`, `--debug`   | `bool`   |         | Enable debug logging                                                                                                |
| `--detach`        | `bool`   | `true`  | Detach buildx server for the monitor (supported only on linux) (EXPERIMENTAL)                                       |
| `--invoke`        | `string` |         | Launch a monitor with executing specified command (EXPERIMENTAL)                                                    |
| `--on`            | `string` | `error` | When to launch the monitor ([always, error]) (EXPERIMENTAL)                                                         |
| `--progress`      | `string` | `auto`  | Set type of progress output (`auto`, `plain`, `tty`, `rawjson`) for the monitor. Use plain to show container output |
| `--root`          | `string` |         | Specify root directory of server to connect for the monitor (EXPERIMENTAL)                                          |
| `--server-config` | `string` |         | Specify buildx server config file for the monitor (used only when launching new server) (EXPERIMENTAL)              |

## Subcommands

| Name                                    | Description   |
|:----------------------------------------|:--------------|
| [`docker buildx debug build`](build.md) | Start a build |
