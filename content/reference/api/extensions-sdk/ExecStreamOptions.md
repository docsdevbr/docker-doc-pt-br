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

title: "Interface: ExecStreamOptions"
description: Docker extension API reference
keywords: Docker, extensions, sdk, API, reference
aliases:
 - /desktop/extensions-sdk/dev/api/reference/interfaces/ExecStreamOptions/
 - /extensions/extensions-sdk/dev/api/reference/interfaces/ExecStreamOptions/
---
**`Since`**

0.2.2

## Properties

### onOutput

• `Optional` **onOutput**: (`data`: { `stdout`: `string` ; `stderr?`: `undefined`  } \| { `stdout?`: `undefined` ; `stderr`: `string`  }) => `void`

#### Type declaration

▸ (`data`): `void`

Invoked when receiving output from command execution.
By default, the output is split into chunks at arbitrary boundaries.
If you prefer the output to be split into complete lines, set `splitOutputLines`
to true. The callback is then invoked once for each line.

**`Since`**

0.2.0

##### Parameters

| Name | Type | Description |
| :------ | :------ | :------ |
| `data` | `{ stdout: string; stderr?: undefined } \| { stdout?: undefined; stderr: string }` | Output content. Can include either stdout string, or stderr string, one at a time. |

##### Returns

`void`

___

### onError

• `Optional` **onError**: (`error`: `any`) => `void`

#### Type declaration

▸ (`error`): `void`

Invoked to report error if the executed command errors.

##### Parameters

| Name | Type | Description |
| :------ | :------ | :------ |
| `error` | `any` | The error happening in the executed command |

##### Returns

`void`

___

### onClose

• `Optional` **onClose**: (`exitCode`: `number`) => `void`

#### Type declaration

▸ (`exitCode`): `void`

Invoked when process exits.

##### Parameters

| Name | Type | Description |
| :------ | :------ | :------ |
| `exitCode` | `number` | The process exit code |

##### Returns

`void`

___

### splitOutputLines

• `Optional` `Readonly` **splitOutputLines**: `boolean`

Specifies the behaviour invoking `onOutput(data)`. Raw output by default, splitting output at any position. If set to true, `onOutput` will be invoked once for each line.
