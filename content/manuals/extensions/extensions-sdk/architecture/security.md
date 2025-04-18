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

title: Extension security
linkTitle: Security
description: Aspects of the security model of extensions
keywords: Docker, extensions, sdk, security
aliases:
 - /desktop/extensions-sdk/guides/security/
 - /desktop/extensions-sdk/architecture/security/
---
## Extension capabilities

An extension can have the following optional parts: 
* A user interface in HTML or JavaScript, displayed in Docker Desktop Dashboard
* A backend part that runs as a container
* Executables deployed on the host machine.

Extensions are executed with the same permissions as the Docker Desktop user. Extension capabilities include running any Docker commands (including running containers and mounting folders), running extension binaries, and accessing files on your machine that are accessible by the user running Docker Desktop.

The Extensions SDK provides a set of JavaScript APIs to invoke commands or invoke these binaries from the extension UI code. Extensions can also provide a backend part that starts a long-lived running container in the background.

> [!IMPORTANT]
>
> Make sure you trust the publisher or author of the extension when you install it, as the extension has the same access rights as the user running Docker Desktop.
