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

title: "Interface: OpenDialogResult"
description: Docker extension API reference
keywords: Docker, extensions, sdk, API, reference
aliases:
 - /desktop/extensions-sdk/dev/api/reference/interfaces/OpenDialogResult/
 - /extensions/extensions-sdk/dev/api/reference/interfaces/OpenDialogResult/
---
**`Since`**

0.2.3

## Properties

### canceled

• `Readonly` **canceled**: `boolean`

Whether the dialog was canceled.

___

### filePaths

• `Readonly` **filePaths**: `string`[]

An array of file paths chosen by the user. If the dialog is cancelled this will be an empty array.

___

### bookmarks

• `Optional` `Readonly` **bookmarks**: `string`[]

macOS only. An array matching the `filePaths` array of `base64` encoded strings which contains security scoped bookmark data. `securityScopedBookmarks` must be enabled for this to be populated.
