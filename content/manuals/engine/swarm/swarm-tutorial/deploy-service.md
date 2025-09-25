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

description: Deploy a service to the swarm
keywords: tutorial, cluster management, swarm mode, get started
title: Deploy a service to the swarm
weight: 30
notoc: true
---
After you [create a swarm](create-swarm.md), you can deploy a service to the
swarm. For this tutorial, you also [added worker nodes](add-nodes.md), but that
is not a requirement to deploy a service.

1.  Open a terminal and ssh into the machine where you run your manager node.
    For example, the tutorial uses a machine named `manager1`.

2.  Run the following command:

    ```console
    $ docker service create --replicas 1 --name helloworld alpine ping docker.com

    9uk4639qpg7npwf3fn2aasksr
    ```

    * The `docker service create` command creates the service.
    * The `--name` flag names the service `helloworld`.
    * The `--replicas` flag specifies the desired state of 1 running instance.
    * The arguments `alpine ping docker.com` define the service as an Alpine
    Linux container that executes the command `ping docker.com`.

3.  Run `docker service ls` to see the list of running services:

    ```console
    $ docker service ls

    ID            NAME        SCALE  IMAGE   COMMAND
    9uk4639qpg7n  helloworld  1/1    alpine  ping docker.com
    ```

## Next steps

Now you're ready to inspect the service.

{{< button text="Inspect the service" url="inspect-service.md" >}}
