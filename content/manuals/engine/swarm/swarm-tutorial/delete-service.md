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

description: Remove the service from the swarm
keywords: tutorial, cluster management, swarm, service, get started
title: Delete the service running on the swarm
weight: 60
notoc: true
---
The remaining steps in the tutorial don't use the `helloworld` service, so now
you can delete the service from the swarm.

1.  If you haven't already, open a terminal and ssh into the machine where you
    run your manager node. For example, the tutorial uses a machine named
    `manager1`.

2.  Run `docker service rm helloworld` to remove the `helloworld` service.

    ```console
    $ docker service rm helloworld

    helloworld
    ```

3.  Run `docker service inspect <SERVICE-ID>` to verify that the swarm manager
    removed the service. The CLI returns a message that the service is not
    found:

    ```console
    $ docker service inspect helloworld
    []
    Status: Error: no such service: helloworld, Code: 1
    ```

4.  Even though the service no longer exists, the task containers take a few
    seconds to clean up. You can use `docker ps` on the nodes to verify when the
    tasks have been removed.

    ```console
    $ docker ps

    CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS              PORTS     NAMES
    db1651f50347        alpine:latest       "ping docker.com"        44 minutes ago      Up 46 seconds                 helloworld.5.9lkmos2beppihw95vdwxy1j3w
    43bf6e532a92        alpine:latest       "ping docker.com"        44 minutes ago      Up 46 seconds                 helloworld.3.a71i8rp6fua79ad43ycocl4t2
    5a0fb65d8fa7        alpine:latest       "ping docker.com"        44 minutes ago      Up 45 seconds                 helloworld.2.2jpgensh7d935qdc857pxulfr
    afb0ba67076f        alpine:latest       "ping docker.com"        44 minutes ago      Up 46 seconds                 helloworld.4.1c47o7tluz7drve4vkm2m5olx
    688172d3bfaa        alpine:latest       "ping docker.com"        45 minutes ago      Up About a minute             helloworld.1.74nbhb3fhud8jfrhigd7s29we

    $ docker ps
    CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS              PORTS     NAMES

    ```

## Next steps

Next, you'll set up a new service and apply a rolling update.

{{< button text="Apply rolling updates" url="rolling-update.md" >}}
