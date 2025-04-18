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

description: Extensions
keywords: Docker Extensions, Docker Desktop, Linux, Mac, Windows,
title: Non-marketplace extensions
weight: 20
aliases:
 - /desktop/extensions/non-marketplace/
---
## Install an extension not available in the Marketplace

> [!WARNING]
>
> Docker Extensions that are not in the Marketplace haven't gone through Docker's review process.
> Extensions can install binaries, invoke commands and access files on your machine. Installing them is at your own risk.

The Extensions Marketplace is the trusted and official place to install extensions from within Docker Desktop. These extensions have gone through a review process by Docker. However, other extensions can also be installed in Docker Desktop if you trust the extension author.

Given the nature of a Docker Extension (i.e. a Docker image) you can find other places where users have their extension's source code published. For example on GitHub, GitLab or even hosted in image registries like DockerHub or GHCR.
You can install an extension that has been developed by the community or internally at your company from a teammate. You are not limited to installing extensions just from the Marketplace.

> [!NOTE]
>
> Ensure the option **Allow only extensions distributed through the Docker Marketplace** is disabled. Otherwise, this prevents any extension not listed in the Marketplace, via the Extension SDK tools from, being installed.
> You can change this option in **Settings**. 

To install an extension which is not present in the Marketplace, you can use the Extensions CLI that is bundled with Docker Desktop.

In a terminal, type `docker extension install IMAGE[:TAG]` to install an extension by its image reference and optionally a tag. Use the `-f` or `--force` flag to avoid interactive confirmation.

Go to the Docker Desktop Dashboard to see the new extension installed.

## List installed extensions

Regardless whether the extension was installed from the Marketplace or manually by using the Extensions CLI, you can use the `docker extension ls` command to display the list of extensions installed.
As part of the output you'll see the extension ID, the provider, version, the title and whether it runs a backend container or has deployed binaries to the host, for example:

```console
$ docker extension ls
ID                  PROVIDER            VERSION             UI                    VM                  HOST
john/my-extension   John                latest              1 tab(My-Extension)   Running(1)          -
```

Go to the Docker Desktop Dashboard, select **Add Extensions** and on the **Managed** tab to see the new extension installed.
Notice that an `UNPUBLISHED` label displays which indicates that the extension has not been installed from the Marketplace.

## Update an extension 

To update an extension which isn't present in the Marketplace, in a terminal type `docker extension update IMAGE[:TAG]` where the `TAG` should be different from the extension that's already installed.

For instance, if you installed an extension with `docker extension install john/my-extension:0.0.1`, you can update it by running `docker extension update john/my-extension:0.0.2`.
Go to the Docker Desktop Dashboard to see the new extension updated.

> [!NOTE]
>
> Extensions that aren't installed through the Marketplace don't receive update notifications from Docker Desktop.

## Uninstall an extension

To uninstall an extension which is not present in the Marketplace, you can either navigate to the **Managed** tab in the Marketplace and select the **Uninstall** button, or from a terminal type `docker extension uninstall IMAGE[:TAG]`.
