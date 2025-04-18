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

title: Start the daemon
weight: 10
description: Starting the Docker daemon manually
keywords: docker, daemon, configuration, troubleshooting
aliases:
  - /config/daemon/start/
---
This page shows how to start the daemon, either manually or using OS utilities.

## Start the daemon using operating system utilities

On a typical installation the Docker daemon is started by a system utility, not
manually by a user. This makes it easier to automatically start Docker when the
machine reboots.

The command to start Docker depends on your operating system. Check the correct
page under [Install Docker](/manuals/engine/install/_index.md).

### Start with systemd

On some operating systems, like Ubuntu and Debian, the Docker daemon service
starts automatically. Use the following command to start it manually:

```console
$ sudo systemctl start docker
```

If you want Docker to start at boot, see
[Configure Docker to start on boot](/manuals/engine/install/linux-postinstall.md#configure-docker-to-start-on-boot-with-systemd).

## Start the daemon manually

If you don't want to use a system utility to manage the Docker daemon, or just
want to test things out, you can manually run it using the `dockerd` command.
You may need to use `sudo`, depending on your operating system configuration.

When you start Docker this way, it runs in the foreground and sends its logs
directly to your terminal.

```console
$ dockerd

INFO[0000] +job init_networkdriver()
INFO[0000] +job serveapi(unix:///var/run/docker.sock)
INFO[0000] Listening for HTTP on unix (/var/run/docker.sock)
```

To stop Docker when you have started it manually, issue a `Ctrl+C` in your
terminal.
