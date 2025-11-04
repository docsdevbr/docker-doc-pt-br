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

title: CLI reference
description: Docker extension CLI
keywords: Docker, extensions, sdk, CLI
aliases:
 - /desktop/extensions-sdk/dev/cli/usage/
 - /desktop/extensions-sdk/dev/usage/
weight: 30
---
The Extensions CLI is an extension development tool that is used to manage Docker extensions. Actions include install, list, remove, and validate extensions.

- `docker extension enable` turns on Docker extensions.
- `docker extension dev` commands for extension development.
- `docker extension disable` turns off Docker extensions.
- `docker extension init` creates a new Docker extension.
- `docker extension install` installs a Docker extension with the specified image.
- `docker extension ls` list installed Docker extensions.
- `docker extension rm` removes a Docker extension.
- `docker extension update` removes and re-installs a Docker extension.
- `docker extension validate` validates the extension metadata file against the JSON schema.
