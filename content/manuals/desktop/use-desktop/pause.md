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

description: understand what pausing Docker Desktop Dashboard means
keywords: Docker Desktop Dashboard, manage, containers, gui, dashboard, pause, user manual
title: Pause Docker Desktop
weight: 60
---
When Docker Desktop is paused, the Linux VM running Docker Engine is paused, the current state of all your containers are saved in memory, and all processes are frozen. This reduces the CPU and memory usage and helps you retain a longer battery life on your laptop.

You can manually pause Docker Desktop by selecting the Docker menu {{< inline-image src="../images/whale-x.svg" alt="whale menu" >}} and then **Pause**. To manually resume Docker Desktop, select the **Resume** option in the Docker menu, or run any Docker CLI command.

When you manually pause Docker Desktop, a paused status displays on the Docker menu and on the Docker Desktop Dashboard. You can still access the **Settings** and the **Troubleshoot** menu.

> [!TIP]
>
> The Resource Saver feature, available in Docker Desktop version 4.24 and later, is enabled by default and provides better
> CPU and memory savings than the manual Pause feature. See [here](resource-saver.md) for more info.
