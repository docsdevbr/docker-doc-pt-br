---
source_url: https://github.com/docker/buildx/blob/master/docs/reference/buildx_rm.md
revision: 7a7a9c8e01e14a83f732a0509dd9128d271d7d2d
status: untranslated
license: https://github.com/docker/buildx/blob/master/LICENSE

datafolder: buildx
datafile: docker_buildx_rm
title: docker buildx rm
layout: cli
aliases:
- /engine/reference/commandline/buildx_rm/
---

# docker buildx rm

```text
docker buildx rm [OPTIONS] [NAME] [NAME...]
```

Remove one or more builder instances

### Options

| Name                                | Type     | Default | Description                              |
|:------------------------------------|:---------|:--------|:-----------------------------------------|
| [`--all-inactive`](#all-inactive)   | `bool`   |         | Remove all inactive builders             |
| [`--builder`](#builder)             | `string` |         | Override the configured builder instance |
| `-D`, `--debug`                     | `bool`   |         | Enable debug logging                     |
| [`-f`](#force), [`--force`](#force) | `bool`   |         | Do not prompt for confirmation           |
| [`--keep-daemon`](#keep-daemon)     | `bool`   |         | Keep the BuildKit daemon running         |
| [`--keep-state`](#keep-state)       | `bool`   |         | Keep BuildKit state                      |



## Description

Removes the specified or current builder. It is a no-op attempting to remove the
default builder.

## Examples

### <a name="all-inactive"></a> Remove all inactive builders (--all-inactive)

Remove builders that are not in running state.

```console
$ docker buildx rm --all-inactive
WARNING! This will remove all builders that are not in running state. Are you sure you want to continue? [y/N] y
```

### <a name="builder"></a> Override the configured builder instance (--builder)

Same as [`buildx --builder`](index.md#builder).

### <a name="force"></a> Do not prompt for confirmation (--force)

Do not prompt for confirmation before removing inactive builders.

```console
$ docker buildx rm --all-inactive --force
```

### <a name="keep-daemon"></a> Keep the BuildKit daemon running (--keep-daemon)

Keep the BuildKit daemon running after the buildx context is removed. This is
useful when you manage BuildKit daemons and buildx contexts independently.
Only supported by the
[`docker-container`](https://docs.docker.com/build/drivers/docker-container/)
and [`kubernetes`](https://docs.docker.com/build/drivers/kubernetes/) drivers.

### <a name="keep-state"></a> Keep BuildKit state (--keep-state)

Keep BuildKit state, so it can be reused by a new builder with the same name.
Currently, only supported by the [`docker-container` driver](https://docs.docker.com/build/drivers/docker-container/).

