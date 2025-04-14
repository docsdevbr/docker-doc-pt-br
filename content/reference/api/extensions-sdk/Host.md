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

title: "Interface: Host"
description: Docker extension API reference
keywords: Docker, extensions, sdk, API, reference
aliases: 
 - /desktop/extensions-sdk/dev/api/reference/interfaces/Host/
 - /extensions/extensions-sdk/dev/api/reference/interfaces/Host/
---
**`Since`**

0.2.0

## Methods

### openExternal

▸ **openExternal**(`url`): `void`

Opens an external URL with the system default browser.

**`Since`**

0.2.0

```typescript
ddClient.host.openExternal("https://docker.com");
```

#### Parameters

| Name | Type | Description |
| :------ | :------ | :------ |
| `url` | `string` | The URL the browser will open (must have the protocol `http` or `https`). |

#### Returns

`void`

## Properties

### platform

• **platform**: `string`

Returns a string identifying the operating system platform. See https://nodejs.org/api/os.html#osplatform

**`Since`**

0.2.2

___

### arch

• **arch**: `string`

Returns the operating system CPU architecture. See https://nodejs.org/api/os.html#osarch

**`Since`**

0.2.2

___

### hostname

• **hostname**: `string`

Returns the host name of the operating system. See https://nodejs.org/api/os.html#oshostname

**`Since`**

0.2.2
