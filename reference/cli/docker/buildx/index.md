---
source_url: https://github.com/docker/buildx/blob/master/docs/reference/buildx.md
revision: 7a7a9c8e01e14a83f732a0509dd9128d271d7d2d
status: untranslated
license: https://github.com/docker/buildx/blob/master/LICENSE

datafolder: buildx
datafile: docker_buildx
title: docker buildx
layout: cli
aliases:
- /engine/reference/commandline/buildx/
---

# docker buildx

```text
docker buildx [OPTIONS] COMMAND
```

Extended build capabilities with BuildKit

## Subcommands

| Name                                | Description                                     |
|:------------------------------------|:------------------------------------------------|
| [`bake`](bake.md)                   | Build from a file                               |
| [`build`](build.md)                 | Start a build                                   |
| [`create`](create.md)               | Create a new builder instance                   |
| [`debug`](debug/index.md)           | Start debugger (EXPERIMENTAL)                   |
| [`dial-stdio`](dial-stdio.md)       | Proxy current stdio streams to builder instance |
| [`du`](du.md)                       | Disk usage                                      |
| [`imagetools`](imagetools/index.md) | Commands to work on images in registry          |
| [`inspect`](inspect.md)             | Inspect current builder instance                |
| [`ls`](ls.md)                       | List builder instances                          |
| [`prune`](prune.md)                 | Remove build cache                              |
| [`rm`](rm.md)                       | Remove one or more builder instances            |
| [`stop`](stop.md)                   | Stop builder instance                           |
| [`use`](use.md)                     | Set the current builder instance                |
| [`version`](version.md)             | Show buildx version information                 |

## Options

| Name                    | Type     | Default | Description                              |
|:------------------------|:---------|:--------|:-----------------------------------------|
| [`--builder`](#builder) | `string` |         | Override the configured builder instance |
| `-D`, `--debug`         | `bool`   |         | Enable debug logging                     |

## Examples

### <a name="builder"></a> Override the configured builder instance (--builder)

You can also use the `BUILDX_BUILDER` environment variable.
