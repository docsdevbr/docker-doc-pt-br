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

title: Containerize a R application
linkTitle: Containerize your app
weight: 10
keywords: R, containerize, initialize
description: Learn how to containerize a R application.
aliases:
  - /language/R/build-images/
  - /language/R/run-containers/
  - /language/r/containerize/
  - /guides/language/r/containerize/
---
## Prerequisites

- You have a [git client](https://git-scm.com/downloads). The examples in this section use a command-line based git client, but you can use any client.

## Overview

This section walks you through containerizing and running a R application.

## Get the sample application

The sample application uses the popular [Shiny](https://shiny.posit.co/) framework.

Clone the sample application to use with this guide. Open a terminal, change directory to a directory that you want to work in, and run the following command to clone the repository:

```console
$ git clone https://github.com/mfranzon/r-docker-dev.git && cd r-docker-dev
```

You should now have the following contents in your `r-docker-dev`
directory.

```text
├── r-docker-dev/
│ ├── src/
│ │ └── app.R
│ ├── src_db/
│ │ └── app_db.R
│ ├── compose.yaml
│ ├── Dockerfile
│ └── README.md
```

To learn more about the files in the repository, see the following:

- [Dockerfile](/reference/dockerfile.md)
- [.dockerignore](/reference/dockerfile.md#dockerignore-file)
- [compose.yaml](/reference/compose-file/_index.md)

## Run the application

Inside the `r-docker-dev` directory, run the following command in a
terminal.

```console
$ docker compose up --build
```

Open a browser and view the application at [http://localhost:3838](http://localhost:3838). You should see a simple Shiny application.

In the terminal, press `ctrl`+`c` to stop the application.

### Run the application in the background

You can run the application detached from the terminal by adding the `-d`
option. Inside the `r-docker-dev` directory, run the following command
in a terminal.

```console
$ docker compose up --build -d
```

Open a browser and view the application at [http://localhost:3838](http://localhost:3838).

You should see a simple Shiny application.

In the terminal, run the following command to stop the application.

```console
$ docker compose down
```

For more information about Compose commands, see the [Compose CLI
reference](/reference/cli/docker/compose/_index.md).

## Summary

In this section, you learned how you can containerize and run your R
application using Docker.

Related information:

- [Docker Compose overview](/manuals/compose/_index.md)

## Next steps

In the next section, you'll learn how you can develop your application using
containers.
