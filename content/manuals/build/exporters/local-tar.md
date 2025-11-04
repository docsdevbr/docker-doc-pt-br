---
# Copyright (c) 2013-2025 Docker Inc.
# Docker and the Docker logo are trademarks or registered trademarks of Docker,
# Inc. in the United States and/or other countries.
# Docker, Inc. and other parties may also have trademark rights in other terms
# used herein.
#
# Documentation licensed under the Apache License, Version 2.0.
# The original work was translated from English into Brazilian Portuguese.
# https://github.com/docker/docs/blob/-/LICENSE

title: Local and tar exporters
keywords: build, buildx, buildkit, exporter, local, tar
description: >
  The local and tar exporters save the build result to the local filesystem
aliases:
  - /build/building/exporters/local-tar/
---
The `local` and `tar` exporters output the root filesystem of the build result
into a local directory. They're useful for producing artifacts that aren't
container images.

- `local` exports files and directories.
- `tar` exports the same, but bundles the export into a tarball.

## Synopsis

Build a container image using the `local` exporter:

```console
$ docker buildx build --output type=local[,parameters] .
$ docker buildx build --output type=tar[,parameters] .
```

The following table describes the available parameters:

| Parameter | Type   | Default | Description           |
| --------- | ------ | ------- | --------------------- |
| `dest`    | String |         | Path to copy files to |

## Further reading

For more information on the `local` or `tar` exporters, see the
[BuildKit README](https://github.com/moby/buildkit/blob/master/README.md#local-directory).
