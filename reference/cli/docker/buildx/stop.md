---
source_url: https://github.com/docker/buildx/blob/master/docs/reference/buildx_stop.md
revision: 7a7a9c8e01e14a83f732a0509dd9128d271d7d2d
status: untranslated
license: https://github.com/docker/buildx/blob/master/LICENSE

datafolder: buildx
datafile: docker_buildx_stop
title: docker buildx stop
layout: cli
aliases:
- /engine/reference/commandline/buildx_stop/
---

# docker buildx stop

```
docker buildx stop [NAME]
```

Stop builder instance

### Options

| Name                    | Type     | Default | Description                              |
|:------------------------|:---------|:--------|:-----------------------------------------|
| [`--builder`](#builder) | `string` |         | Override the configured builder instance |
| `-D`, `--debug`         | `bool`   |         | Enable debug logging                     |



## Description

Stops the specified or current builder. This does not prevent buildx build to
restart the builder. The implementation of stop depends on the driver.

## Examples

### <a name="builder"></a> Override the configured builder instance (--builder)

Same as [`buildx --builder`](index.md#builder).

