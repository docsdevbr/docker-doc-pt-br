---
# Copyright (c) 2013-2025 Docker Inc.
# Docker and the Docker logo are trademarks or registered trademarks of Docker,
# Inc. in the United States and/or other countries.
# Docker, Inc. and other parties may also have trademark rights in other terms
# used herein.
#
# Documentation licensed under the Apache License, Version 2.0.
# The original work was translated from English into Brazilian Portuguese.
# https://github.com/docker/docs/blob/main/LICENSE

title: OpenTelemetry support
description: Analyze telemetry data for builds
keywords: build, buildx buildkit, opentelemetry
aliases:
- /build/building/opentelemetry/
---
Both Buildx and BuildKit support [OpenTelemetry](https://opentelemetry.io/).

To capture the trace to [Jaeger](https://github.com/jaegertracing/jaeger),
set `JAEGER_TRACE` environment variable to the collection address using a
`driver-opt`.

First create a Jaeger container:

```console
$ docker run -d --name jaeger -p "6831:6831/udp" -p "16686:16686" --restart unless-stopped jaegertracing/all-in-one
```

Then [create a `docker-container` builder](/manuals/build/builders/drivers/docker-container.md)
that will use the Jaeger instance via the `JAEGER_TRACE` environment variable:

```console
$ docker buildx create --use \
  --name mybuilder \
  --driver docker-container \
  --driver-opt "network=host" \
  --driver-opt "env.JAEGER_TRACE=localhost:6831"
```

Boot and [inspect `mybuilder`](/reference/cli/docker/buildx/inspect.md):

```console
$ docker buildx inspect --bootstrap
```

Buildx commands should be traced at `http://127.0.0.1:16686/`:

![OpenTelemetry Buildx Bake](../images/opentelemetry.png)
