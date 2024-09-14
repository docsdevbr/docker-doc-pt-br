---
source_url: https://github.com/docker/buildx/blob/master/docs/reference/buildx_imagetools.md
revision: 7a7a9c8e01e14a83f732a0509dd9128d271d7d2d
status: untranslated
license: https://github.com/docker/buildx/blob/master/LICENSE

datafolder: buildx
datafile: docker_buildx_imagetools
title: docker buildx imagetools
layout: cli
aliases:
- /engine/reference/commandline/buildx_imagetools/
---

# docker buildx imagetools

```text
docker buildx imagetools [OPTIONS] COMMAND
```

Commands to work on images in registry

### Subcommands

| Name                                      | Description                               |
|:------------------------------------------|:------------------------------------------|
| [`create`](imagetools_create.md)   | Create a new image based on source images |
| [`inspect`](imagetools_inspect.md) | Show details of an image in the registry  |


### Options

| Name                    | Type     | Default | Description                              |
|:------------------------|:---------|:--------|:-----------------------------------------|
| [`--builder`](#builder) | `string` |         | Override the configured builder instance |
| `-D`, `--debug`         | `bool`   |         | Enable debug logging                     |



## Description

The `imagetools` commands contains subcommands for working with manifest lists
in container registries. These commands are useful for inspecting manifests
to check multi-platform configuration and attestations.

## Examples

### <a name="builder"></a> Override the configured builder instance (--builder)

Same as [`buildx --builder`](index.md#builder).

