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

title: "Interface: RawExecResult"
description: Docker extension API reference
keywords: Docker, extensions, sdk, API, reference
aliases:
 - /desktop/extensions-sdk/dev/api/reference/interfaces/RawExecResult/
 - /extensions/extensions-sdk/dev/api/reference/interfaces/RawExecResult/
---
**`Since`**

0.2.0

## Hierarchy

- **`RawExecResult`**

  ↳ [`ExecResult`](ExecResult.md)

## Properties

### cmd

• `Optional` `Readonly` **cmd**: `string`

___

### killed

• `Optional` `Readonly` **killed**: `boolean`

___

### signal

• `Optional` `Readonly` **signal**: `string`

___

### code

• `Optional` `Readonly` **code**: `number`

___

### stdout

• `Readonly` **stdout**: `string`

___

### stderr

• `Readonly` **stderr**: `string`
