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

description: >
  Learn how to read container logs locally when using a third party logging
  solution.
keywords: >
  docker, logging, driver, dual logging, dual logging, cache, ring-buffer,
  configuration
title: Use docker logs with remote logging drivers
aliases:
  - /config/containers/logging/dual-logging/
---
## Overview

You can use the `docker logs` command to read container logs regardless of the
configured logging driver or plugin. Docker Engine uses the [`local`](drivers/local.md)
logging driver to act as cache for reading the latest logs of your containers.
This is called dual logging. By default, the cache has log-file rotation
enabled, and is limited to a maximum of 5 files of 20 MB each (before
compression) per container.

Refer to the [configuration options](#configuration-options) section to customize
these defaults, or to the [disable dual logging](#disable-the-dual-logging-cache)
section to disable this feature.

## Prerequisites

Docker Engine automatically enables dual logging if the configured logging
driver doesn't support reading logs.

The following examples show the result of running a `docker logs` command with
and without dual logging availability:

### Without dual logging capability

When a container is configured with a remote logging driver such as `splunk`, and
dual logging is disabled, an error is displayed when attempting to read container
logs locally:

- Step 1: Configure Docker daemon

  ```console
  $ cat /etc/docker/daemon.json
  {
    "log-driver": "splunk",
    "log-opts": {
      "cache-disabled": "true",
      ... (options for "splunk" logging driver)
    }
  }
  ```

- Step 2: Start the container

  ```console
  $ docker run -d busybox --name testlog top
  ```

- Step 3: Read the container logs

  ```console
  $ docker logs 7d6ac83a89a0
  Error response from daemon: configured logging driver does not support reading
  ```

### With dual logging capability

With the dual logging cache enabled, the `docker logs` command can be used to
read logs, even if the logging driver doesn't support reading logs. The following
example shows a daemon configuration that uses the `splunk` remote logging driver
as a default, with dual logging caching enabled:

- Step 1: Configure Docker daemon

  ```console
  $ cat /etc/docker/daemon.json
  {
    "log-driver": "splunk",
    "log-opts": {
      ... (options for "splunk" logging driver)
    }
  }
  ```

- Step 2: Start the container

  ```console
  $ docker run -d busybox --name testlog top
  ```

- Step 3: Read the container logs

  ```console
  $ docker logs 7d6ac83a89a0
  2019-02-04T19:48:15.423Z [INFO]  core: marked as sealed
  2019-02-04T19:48:15.423Z [INFO]  core: pre-seal teardown starting
  2019-02-04T19:48:15.423Z [INFO]  core: stopping cluster listeners
  2019-02-04T19:48:15.423Z [INFO]  core: shutting down forwarding rpc listeners
  2019-02-04T19:48:15.423Z [INFO]  core: forwarding rpc listeners stopped
  2019-02-04T19:48:15.599Z [INFO]  core: rpc listeners successfully shut down
  2019-02-04T19:48:15.599Z [INFO]  core: cluster listeners successfully shut down
  ```

> [!NOTE]
>
> For logging drivers that support reading logs, such as the `local`, `json-file`
> and `journald` drivers, there is no difference in functionality before or after
> the dual logging capability became available. For these drivers, Logs can be
> read using `docker logs` in both scenarios.

### Configuration options

The dual logging cache accepts the same configuration options as the
[`local` logging driver](drivers/local.md), but with a `cache-` prefix. These options
can be specified per container, and defaults for new containers can be set using
the [daemon configuration file](/reference/cli/dockerd/#daemon-configuration-file).

By default, the cache has log-file rotation enabled, and is limited to a maximum
of 5 files of 20MB each (before compression) per container. Use the configuration
options described below to customize these defaults.

| Option           | Default   | Description                                                                                                                                       |
| :--------------- | :-------- | :------------------------------------------------------------------------------------------------------------------------------------------------ |
| `cache-disabled` | `"false"` | Disable local caching. Boolean value passed as a string (`true`, `1`, `0`, or `false`).                                                           |
| `cache-max-size` | `"20m"`   | The maximum size of the cache before it is rotated. A positive integer plus a modifier representing the unit of measure (`k`, `m`, or `g`).       |
| `cache-max-file` | `"5"`     | The maximum number of cache files that can be present. If rotating the logs creates excess files, the oldest file is removed. A positive integer. |
| `cache-compress` | `"true"`  | Enable or disable compression of rotated log files. Boolean value passed as a string (`true`, `1`, `0`, or `false`).                              |

## Disable the dual logging cache

Use the `cache-disabled` option to disable the dual logging cache. Disabling the
cache can be useful to save storage space in situations where logs are only read
through a remote logging system, and if there is no need to read logs through
`docker logs` for debugging purposes.

Caching can be disabled for individual containers or by default for new containers,
when using the [daemon configuration file](/reference/cli/dockerd/#daemon-configuration-file).

The following example uses the daemon configuration file to use the [`splunk`](drivers/splunk.md)
logging driver as a default, with caching disabled:

```console
$ cat /etc/docker/daemon.json
{
  "log-driver": "splunk",
  "log-opts": {
    "cache-disabled": "true",
    ... (options for "splunk" logging driver)
  }
}
```

> [!NOTE]
>
> For logging drivers that support reading logs, such as the `local`, `json-file`
> and `journald` drivers, dual logging isn't used, and disabling the option has
> no effect.

## Limitations

- If a container using a logging driver or plugin that sends logs remotely
  has a network issue, no `write` to the local cache occurs.
- If a write to `logdriver` fails for any reason (file system full, write
  permissions removed), the cache write fails and is logged in the daemon log.
  The log entry to the cache isn't retried.
- Some logs might be lost from the cache in the default configuration because a
  ring buffer is used to prevent blocking the stdio of the container in case of
  slow file writes. An admin must repair these while the daemon is shut down.
