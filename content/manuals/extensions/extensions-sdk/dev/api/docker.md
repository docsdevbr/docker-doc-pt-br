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

title: Docker
description: Docker extension API
keywords: Docker, extensions, sdk, API
aliases: 
 - /desktop/extensions-sdk/dev/api/docker/
---
## Docker objects

▸ **listContainers**(`options?`): `Promise`<`unknown`\>

To get the list of containers:

```typescript
const containers = await ddClient.docker.listContainers();
```

▸ **listImages**(`options?`): `Promise`<`unknown`\>

To get the list of local container images:

```typescript
const images = await ddClient.docker.listImages();
```

See the [Docker API reference](/reference/api/extensions-sdk/Docker.md) for details about these methods.

> Deprecated access to Docker objects
>
> The methods below are deprecated and will be removed in a future version. Use the methods specified above.

```typescript
const containers = await window.ddClient.listContainers();

const images = await window.ddClient.listImages();
```

## Docker commands

Extensions can also directly execute the `docker` command line.

▸ **exec**(`cmd`, `args`): `Promise`<[`ExecResult`](/reference/api/extensions-sdk/ExecResult.md)\>

```typescript
const result = await ddClient.docker.cli.exec("info", [
  "--format",
  '"{{ json . }}"',
]);
```

The result contains both the standard output and the standard error of the executed command:

```json
{
  "stderr": "...",
  "stdout": "..."
}
```

In this example, the command output is JSON.
For convenience, the command result object also has methods to easily parse it:

- `result.lines(): string[]` splits output lines.
- `result.parseJsonObject(): any` parses a well-formed json output.
- `result.parseJsonLines(): any[]` parses each output line as a json object.

▸ **exec**(`cmd`, `args`, `options`): `void`

The command above streams the output as a result of the execution of a Docker command.
This is useful if you need to get the output as a stream or the output of the command is too long.

```typescript
await ddClient.docker.cli.exec("logs", ["-f", "..."], {
  stream: {
    onOutput(data) {
      if (data.stdout) {
        console.error(data.stdout);
      } else {
        console.log(data.stderr);
      }
    },
    onError(error) {
      console.error(error);
    },
    onClose(exitCode) {
      console.log("onClose with exit code " + exitCode);
    },
    splitOutputLines: true,
  },
});
```

The child process created by the extension is killed (`SIGTERM`) automatically when you close the dashboard in Docker Desktop or when you exit the extension UI.
If needed, you can also use the result of the `exec(streamOptions)` call in order to kill (`SIGTERM`) the process.

```typescript
const logListener = await ddClient.docker.cli.exec("logs", ["-f", "..."], {
  stream: {
    // ...
  },
});

// when done listening to logs or before starting a new one, kill the process
logListener.close();
```

This `exec(streamOptions)` API can also be used to listen to docker events:

```typescript
await ddClient.docker.cli.exec(
  "events",
  ["--format", "{{ json . }}", "--filter", "container=my-container"],
  {
    stream: {
      onOutput(data) {
        if (data.stdout) {
          const event = JSON.parse(data.stdout);
          console.log(event);
        } else {
          console.log(data.stderr);
        }
      },
      onClose(exitCode) {
        console.log("onClose with exit code " + exitCode);
      },
      splitOutputLines: true,
    },
  }
);
```

> [!NOTE]
>
>You cannot use this to chain commands in a single `exec()` invocation (like `docker kill $(docker ps -q)` or using pipe between commands).
>
> You need to invoke `exec()` for each command and parse results to pass parameters to the next command if needed.

See the [Exec API reference](/reference/api/extensions-sdk/Exec.md) for details about these methods.

> Deprecated execution of Docker commands
>
> This method is deprecated and will be removed in a future version. Use the one specified just below.

```typescript
const output = await window.ddClient.execDockerCmd(
  "info",
  "--format",
  '"{{ json . }}"'
);

window.ddClient.spawnDockerCmd("logs", ["-f", "..."], (data, error) => {
  console.log(data.stdout);
});
```
