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

title: Using the Docker Desktop CLI
linkTitle: Docker Desktop CLI
weight: 120
description: How to use the Docker Desktop CLI
keywords: cli, docker desktop, macos, windows, linux
params:
  sidebar:
    badge:
      color: green
      text: New
---
{{< summary-bar feature_name="Docker Desktop CLI" >}}

The Docker Desktop CLI lets you perform key operations such as starting, stopping, restarting, and updating Docker Desktop directly from the command line.

The Docker Desktop CLI provides:

- Simplified automation for local development: Execute Docker Desktop operations more efficiently in scripts and tests.
- An improved developer experience: Restart, quit, or reset Docker Desktop from the command line, reducing dependency on the Docker Desktop Dashboard and improving flexibility and efficiency.

## Usage

```console
docker desktop COMMAND [OPTIONS]
```

## Commands

| Command              | Description                              |
|:---------------------|:-----------------------------------------|
| `start`              | Starts Docker Desktop                    |
| `stop`               | Stops Docker Desktop                     |
| `restart`            | Restarts Docker Desktop                  |
| `status`             | Displays whether Docker Desktop is running or stopped.       |
| `engine ls`          | Lists available engines (Windows only)   |
| `engine use`         | Switch between Linux and Windows containers (Windows only) |
| `update`             | Manage Docker Desktop updates. Available for Mac only with Docker Desktop version 4.38, or all OSs with Docker Desktop version 4.39 and later. |
| `logs`               | Print log entries                        |


For more details on each command, see the [Docker Desktop CLI reference](/reference/cli/docker/desktop/_index.md).
