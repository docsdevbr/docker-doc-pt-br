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

title: Develop with Docker Engine SDKs
linkTitle: SDK
weight: 10
description: Learn how to use Docker Engine SDKs to automate Docker tasks in your language of choice
keywords: developing, sdk, Docker Engine SDKs, install SDKs, SDK versions
aliases:
  - /develop/sdk/
  - /engine/api/sdks/
  - /engine/api/sdk/
---
Docker provides an API for interacting with the Docker daemon (called the Docker
Engine API), as well as SDKs for Go and Python. The SDKs allow you to efficiently build and
scale Docker apps and solutions. If Go or Python don't work
for you, you can use the Docker Engine API directly.

The Docker Engine API is a RESTful API accessed by an HTTP client such as `wget` or
`curl`, or the HTTP library which is part of most modern programming languages.

## Install the SDKs

Use the following commands to install the Go or Python SDK. Both SDKs can be
installed and coexist together.

### Go SDK

```console
$ go get github.com/docker/docker/client
```

The client requires a recent version of Go. Run `go version` and ensure that you're running a currently supported version of Go.


For more information, see [Docker Engine Go SDK reference](https://godoc.org/github.com/docker/docker/client).

### Python SDK

- Recommended: Run `pip install docker`.

- If you can't use `pip`:

  1.  [Download the package directly](https://pypi.python.org/pypi/docker/).
  2.  Extract it and change to the extracted directory.
  3.  Run `python setup.py install`.

For more information, see [Docker Engine Python SDK reference](https://docker-py.readthedocs.io/).

## View the API reference

You can
[view the reference for the latest version of the API](/reference/api/engine/latest/)
or [choose a specific version](/reference/api/engine/version-history/).

## Versioned API and SDK

The version of the Docker Engine API you should use depends on the version of
your Docker daemon and Docker client. See the [versioned API and SDK](/reference/api/engine/#versioned-api-and-sdk)
section in the API documentation for details.

## SDK and API quickstart

Use the following guidelines to choose the SDK or API version to use in your
code:

- If you're starting a new project, use the [latest version](/reference/api/engine/latest/),
  but use API version negotiation or specify the version you are using. This
  helps prevent surprises.
- If you need a new feature, update your code to use at least the minimum version
  that supports the feature, and prefer the latest version you can use.
- Otherwise, continue to use the version that your code is already using.

As an example, the `docker run` command can be implemented using the
Docker API directly, or using the Python or Go SDK.

{{< tabs >}}
{{< tab name="Go" >}}

```go
package main

import (
	"context"
	"io"
	"os"

	"github.com/docker/docker/api/types/container"
        "github.com/docker/docker/api/types/image"
	"github.com/docker/docker/client"
	"github.com/docker/docker/pkg/stdcopy"
)

func main() {
    ctx := context.Background()
    cli, err := client.NewClientWithOpts(client.FromEnv, client.WithAPIVersionNegotiation())
    if err != nil {
        panic(err)
    }
    defer cli.Close()

    reader, err := cli.ImagePull(ctx, "docker.io/library/alpine", image.PullOptions{})
    if err != nil {
        panic(err)
    }
    io.Copy(os.Stdout, reader)

    resp, err := cli.ContainerCreate(ctx, &container.Config{
        Image: "alpine",
        Cmd:   []string{"echo", "hello world"},
    }, nil, nil, nil, "")
    if err != nil {
        panic(err)
    }

    if err := cli.ContainerStart(ctx, resp.ID, container.StartOptions{}); err != nil {
        panic(err)
    }

    statusCh, errCh := cli.ContainerWait(ctx, resp.ID, container.WaitConditionNotRunning)
    select {
    case err := <-errCh:
        if err != nil {
            panic(err)
        }
    case <-statusCh:
    }

    out, err := cli.ContainerLogs(ctx, resp.ID, container.LogsOptions{ShowStdout: true})
    if err != nil {
        panic(err)
    }

    stdcopy.StdCopy(os.Stdout, os.Stderr, out)
}
```

{{< /tab >}}
{{< tab name="Python" >}}

```python
import docker
client = docker.from_env()
print(client.containers.run("alpine", ["echo", "hello", "world"]))
```

{{< /tab >}}
{{< tab name="HTTP" >}}

```console
$ curl --unix-socket /var/run/docker.sock -H "Content-Type: application/json" \
  -d '{"Image": "alpine", "Cmd": ["echo", "hello world"]}' \
  -X POST http://localhost/v{{% param "latest_engine_api_version" %}}/containers/create
{"Id":"1c6594faf5","Warnings":null}

$ curl --unix-socket /var/run/docker.sock -X POST http://localhost/v{{% param "latest_engine_api_version" %}}/containers/1c6594faf5/start

$ curl --unix-socket /var/run/docker.sock -X POST http://localhost/v{{% param "latest_engine_api_version" %}}/containers/1c6594faf5/wait
{"StatusCode":0}

$ curl --unix-socket /var/run/docker.sock "http://localhost/v{{% param "latest_engine_api_version" %}}/containers/1c6594faf5/logs?stdout=1"
hello world
```

When using cURL to connect over a Unix socket, the hostname is not important. The previous
examples use `localhost`, but any hostname would work.

> [!IMPORTANT]
>
> The previous examples assume you're using cURL 7.50.0 or above. Older versions of
> cURL used a [non-standard URL notation](https://github.com/moby/moby/issues/17960)
> when using a socket connection.
>
> If you're' using an older version of cURL, use `http:/<API version>/` instead,
> for example: `http:/v{{% param "latest_engine_api_version" %}}/containers/1c6594faf5/start`.

{{< /tab >}}
{{< /tabs >}}

For more examples, take a look at the [SDK examples](examples.md).

## Unofficial libraries

There are a number of community supported libraries available for other
languages. They haven't been tested by Docker, so if you run into any issues,
file them with the library maintainers.

| Language              | Library                                                                     |
|:----------------------|:----------------------------------------------------------------------------|
| C                     | [libdocker](https://github.com/danielsuo/libdocker)                         |
| C#                    | [Docker.DotNet](https://github.com/ahmetalpbalkan/Docker.DotNet)            |
| C++                   | [lasote/docker_client](https://github.com/lasote/docker_client)             |
| Clojure               | [clj-docker-client](https://github.com/into-docker/clj-docker-client)       |
| Clojure               | [contajners](https://github.com/lispyclouds/contajners)                     |
| Dart                  | [bwu_docker](https://github.com/bwu-dart/bwu_docker)                        |
| Erlang                | [erldocker](https://github.com/proger/erldocker)                            |
| Gradle                | [gradle-docker-plugin](https://github.com/gesellix/gradle-docker-plugin)    |
| Groovy                | [docker-client](https://github.com/gesellix/docker-client)                  |
| Haskell               | [docker-hs](https://github.com/denibertovic/docker-hs)                      |
| Java                  | [docker-client](https://github.com/spotify/docker-client)                   |
| Java                  | [docker-java](https://github.com/docker-java/docker-java)                   |
| Java                  | [docker-java-api](https://github.com/amihaiemil/docker-java-api)            |
| Java                  | [jocker](https://github.com/ndeloof/jocker)                                 |
| NodeJS                | [dockerode](https://github.com/apocas/dockerode)                            |
| NodeJS                | [harbor-master](https://github.com/arhea/harbor-master)                     |
| NodeJS                | [the-moby-effect](https://github.com/leonitousconforti/the-moby-effect)     |
| Perl                  | [Eixo::Docker](https://github.com/alambike/eixo-docker)                     |
| PHP                   | [Docker-PHP](https://github.com/docker-php/docker-php)                      |
| Ruby                  | [docker-api](https://github.com/swipely/docker-api)                         |
| Rust                  | [bollard](https://github.com/fussybeaver/bollard)                           |
| Rust                  | [docker-rust](https://github.com/abh1nav/docker-rust)                       |
| Rust                  | [shiplift](https://github.com/softprops/shiplift)                           |
| Scala                 | [tugboat](https://github.com/softprops/tugboat)                             |
| Scala                 | [reactive-docker](https://github.com/almoehi/reactive-docker)               |
| Swift                 | [docker-client-swift](https://github.com/valeriomazzeo/docker-client-swift) |
