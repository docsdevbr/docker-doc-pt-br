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

title: "Interface: SpawnOptions"
description: Docker extension API reference
keywords: Docker, extensions, sdk, API, reference
aliases:
 - /desktop/extensions-sdk/dev/api/reference/interfaces/SpawnOptions/
 - /extensions/extensions-sdk/dev/api/reference/interfaces/SpawnOptions/
---
**`Since`**

0.3.0

## Hierarchy

- [`ExecOptions`](ExecOptions.md)

  ↳ **`SpawnOptions`**

## Properties

### cwd

• `Optional` **cwd**: `string`

#### Inherited from

[ExecOptions](ExecOptions.md).[cwd](ExecOptions.md#cwd)

___

### env

• `Optional` **env**: `ProcessEnv`

#### Inherited from

[ExecOptions](ExecOptions.md).[env](ExecOptions.md#env)

___

### stream

• **stream**: [`ExecStreamOptions`](ExecStreamOptions.md)
