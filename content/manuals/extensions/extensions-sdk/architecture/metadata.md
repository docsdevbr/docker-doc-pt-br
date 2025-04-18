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

title: Extension metadata
linkTitle: Metadata
description: Docker extension metadata
keywords: Docker, extensions, sdk, metadata
aliases:
 - /desktop/extensions-sdk/extensions/METADATA
 - /desktop/extensions-sdk/architecture/metadata/
---
## The metadata.json file

The `metadata.json` file is the entry point for your extension. It contains the metadata for your extension, such as the
name, version, and description. It also contains the information needed to build and run your extension. The image for
a Docker extension must include a `metadata.json` file at the root of its filesystem.

The format of the `metadata.json` file must be:

```json
{
    "icon": "extension-icon.svg",
    "ui": ...
    "vm": ...
    "host": ...
}
```

The `ui`, `vm`, and `host` sections are optional and depend on what a given extension provides. They describe the extension content to be installed.

### UI section

The `ui` section defines a new tab that's added to the dashboard in Docker Desktop. It follows the form:

```json
"ui":{
    "dashboard-tab":
    {
        "title":"MyTitle",
        "root":"/ui",
        "src":"index.html"
    }
}
```

`root` specifies the folder where the UI code is within the extension image filesystem.
`src` specifies the entrypoint that should be loaded in the extension tab.

Other UI extension points will be available in the future.

### VM section

The `vm` section defines a backend service that runs inside the Desktop VM. It must define either an `image` or a
`compose.yaml` file that specifies what service to run in the Desktop VM.

```json
"vm": {
    "image":"${DESKTOP_PLUGIN_IMAGE}"
},
```

When you use `image`, a default compose file is generated for the extension.

> `${DESKTOP_PLUGIN_IMAGE}` is a specific keyword that allows an easy way to refer to the image packaging the extension.
> It is also possible to specify any other full image name here. However, in many cases using the same image makes
> things easier for extension development.

```json
"vm": {
    "composefile": "compose.yaml"
},
```

The Compose file, with a volume definition for example, would look like:

```yaml
services:
  myExtension:
    image: ${DESKTOP_PLUGIN_IMAGE}
    volumes:
      - /host/path:/container/path
```

### Host section

The `host` section defines executables that Docker Desktop copies on the host.

```json
  "host": {
    "binaries": [
      {
        "darwin": [
          {
            "path": "/darwin/myBinary"
          },
        ],
        "windows": [
          {
            "path": "/windows/myBinary.exe"
          },
        ],
        "linux": [
          {
            "path": "/linux/myBinary"
          },
        ]
      }
    ]
  }
```

`binaries` defines a list of binaries Docker Desktop copies from the extension image to the host.

`path` specifies the binary path in the image filesystem. Docker Desktop is responsible for copying these files in its own location, and the JavaScript API allows invokes these binaries.

Learn how to [invoke executables](../guides/invoke-host-binaries.md).
