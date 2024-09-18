---
source_url: https://github.com/docker/buildx/blob/master/docs/reference/buildx_prune.md
revision: 7a7a9c8e01e14a83f732a0509dd9128d271d7d2d
status: untranslated
license: https://github.com/docker/buildx/blob/master/LICENSE

datafolder: buildx
datafile: docker_buildx_prune
title: docker buildx prune
layout: cli
aliases:
- /engine/reference/commandline/buildx_prune/
---

# docker buildx prune

```text
docker buildx prune
```

Remove build cache

### Options

| Name                    | Type     | Default | Description                               |
|:------------------------|:---------|:--------|:------------------------------------------|
| `-a`, `--all`           | `bool`   |         | Include internal/frontend images          |
| [`--builder`](#builder) | `string` |         | Override the configured builder instance  |
| `-D`, `--debug`         | `bool`   |         | Enable debug logging                      |
| `--filter`              | `filter` |         | Provide filter values (e.g., `until=24h`) |
| `-f`, `--force`         | `bool`   |         | Do not prompt for confirmation            |
| `--keep-storage`        | `bytes`  | `0`     | Amount of disk space to keep for cache    |
| `--verbose`             | `bool`   |         | Provide a more verbose output             |

## Description

Clears the build cache of the selected builder.

You can finely control what cache data is kept using:

- The `--filter=until=<duration>` flag to keep images that have been used in
  the last `<duration>` time.

  `<duration>` is a duration string, e.g. `24h` or `2h30m`, with allowable
  units of `(h)ours`, `(m)inutes` and `(s)econds`.

- The `--keep-storage=<size>` flag to keep `<size>` bytes of data in the cache.

  `<size>` is a human-readable memory string, e.g. `128mb`, `2gb`, etc. Units
  are case-insensitive.

- The `--all` flag to allow clearing internal helper images and frontend images
  set using the `#syntax=` directive or the `BUILDKIT_SYNTAX` build argument.

## Examples

### <a name="builder"></a> Override the configured builder instance (--builder)

Same as [`buildx --builder`](index.md#builder).

