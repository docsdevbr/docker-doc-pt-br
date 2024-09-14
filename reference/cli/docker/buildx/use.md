---
source_url: https://github.com/docker/buildx/blob/master/docs/reference/buildx_use.md
revision: 7a7a9c8e01e14a83f732a0509dd9128d271d7d2d
status: untranslated
license: https://github.com/docker/buildx/blob/master/LICENSE

datafolder: buildx
datafile: docker_buildx_use
title: docker buildx use
layout: cli
aliases:
- /engine/reference/commandline/buildx_use/
---

# docker buildx use

```
docker buildx use [OPTIONS] NAME
```

Set the current builder instance

### Options

| Name                    | Type     | Default | Description                                |
|:------------------------|:---------|:--------|:-------------------------------------------|
| [`--builder`](#builder) | `string` |         | Override the configured builder instance   |
| `-D`, `--debug`         | `bool`   |         | Enable debug logging                       |
| `--default`             | `bool`   |         | Set builder as default for current context |
| `--global`              | `bool`   |         | Builder persists context changes           |



## Description

Switches the current builder instance. Build commands invoked after this command
will run on a specified builder. Alternatively, a context name can be used to
switch to the default builder of that context.

## Examples

### <a name="builder"></a> Override the configured builder instance (--builder)

Same as [`buildx --builder`](index.md#builder).

