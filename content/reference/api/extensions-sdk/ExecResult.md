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

title: "Interface: ExecResult"
description: Docker extension API reference
keywords: Docker, extensions, sdk, API, reference
aliases:
 - /desktop/extensions-sdk/dev/api/reference/interfaces/ExecResult/
 - /extensions/extensions-sdk/dev/api/reference/interfaces/ExecResult/
---
**`Since`**

0.2.0

## Hierarchy

- [`RawExecResult`](RawExecResult.md)

  ↳ **`ExecResult`**

## Methods

### lines

▸ **lines**(): `string`[]

Split output lines.

#### Returns

`string`[]

The list of lines.

___

### parseJsonLines

▸ **parseJsonLines**(): `any`[]

Parse each output line as a JSON object.

#### Returns

`any`[]

The list of lines where each line is a JSON object.

___

### parseJsonObject

▸ **parseJsonObject**(): `any`

Parse a well-formed JSON output.

#### Returns

`any`

The JSON object.

## Properties

### cmd

• `Optional` `Readonly` **cmd**: `string`

#### Inherited from

[RawExecResult](RawExecResult.md).[cmd](RawExecResult.md#cmd)

___

### killed

• `Optional` `Readonly` **killed**: `boolean`

#### Inherited from

[RawExecResult](RawExecResult.md).[killed](RawExecResult.md#killed)

___

### signal

• `Optional` `Readonly` **signal**: `string`

#### Inherited from

[RawExecResult](RawExecResult.md).[signal](RawExecResult.md#signal)

___

### code

• `Optional` `Readonly` **code**: `number`

#### Inherited from

[RawExecResult](RawExecResult.md).[code](RawExecResult.md#code)

___

### stdout

• `Readonly` **stdout**: `string`

#### Inherited from

[RawExecResult](RawExecResult.md).[stdout](RawExecResult.md#stdout)

___

### stderr

• `Readonly` **stderr**: `string`

#### Inherited from

[RawExecResult](RawExecResult.md).[stderr](RawExecResult.md#stderr)
