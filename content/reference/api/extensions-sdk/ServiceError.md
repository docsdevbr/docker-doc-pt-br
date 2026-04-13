---
# SPDX-FileCopyrightText: 2013-2026 Docker Inc.
# Docker and the Docker logo are trademarks or registered trademarks of Docker,
# Inc. in the United States and/or other countries.
# Docker, Inc. and other parties may also have trademark rights in other terms
# used herein.
#
# SPDX-License-Identifier: Apache-2.0
# Documentation licensed under the Apache License, Version 2.0.
# The original work was translated from English into Brazilian Portuguese.
# https://github.com/docsdevbr/docker-doc-pt-br/blob/-/LICENSES/Apache-2.0.txt

title: "Interface: ServiceError"
description: Docker extension API reference
keywords: Docker, extensions, sdk, API, reference
aliases:
 - /desktop/extensions-sdk/dev/api/reference/interfaces/ServiceError/
 - /extensions/extensions-sdk/dev/api/reference/interfaces/ServiceError/
---
Error thrown when an HTTP response is received with a status code that falls
out to the range of 2xx.

**`Since`**

0.2.0

## Properties

### name

• **name**: `string`

___

### message

• **message**: `string`

___

### statusCode

• **statusCode**: `number`
