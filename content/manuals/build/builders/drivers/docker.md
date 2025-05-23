---
# Copyright (c) 2016 Docker, Inc.
# Docker and the Docker logo are trademarks or registered trademarks of Docker,
# Inc. in the United States and/or other countries.
# Docker, Inc. and other parties may also have trademark rights in other terms
# used herein.
#
# Documentation licensed under the Apache License, Version 2.0.
# The original work was translated from English into Brazilian Portuguese.
# https://github.com/docker/docs/blob/main/LICENSE

title: Docker driver
description: |
  The Docker driver is the default driver.
  It uses the BuildKit bundled with the Docker Engine.
keywords: build, buildx, driver, builder, docker
aliases:
  - /build/buildx/drivers/docker/
  - /build/building/drivers/docker/
  - /build/drivers/docker/
---
The Buildx Docker driver is the default driver. It uses the BuildKit server
components built directly into the Docker Engine. The Docker driver requires no
configuration.

Unlike the other drivers, builders using the Docker driver can't be manually
created. They're only created automatically from the Docker context.

Images built with the Docker driver are automatically loaded to the local image
store.

## Synopsis

```console
# The Docker driver is used by buildx by default
docker buildx build .
```

It's not possible to configure which BuildKit version to use, or to pass any
additional BuildKit parameters to a builder using the Docker driver. The
BuildKit version and parameters are preset by the Docker Engine internally.

If you need additional configuration and flexibility, consider using the
[Docker container driver](./docker-container.md).

## Further reading

For more information on the Docker driver, see the
[buildx reference](/reference/cli/docker/buildx/create.md#driver).
