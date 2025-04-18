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

description: Drain nodes on the swarm
keywords: tutorial, cluster management, swarm, service, drain, get started
title: Drain a node on the swarm
weight: 80
notoc: true
---
In earlier steps of the tutorial, all the nodes have been running with `Active`
availability. The swarm manager can assign tasks to any `Active` node, so up to
now all nodes have been available to receive tasks.

Sometimes, such as planned maintenance times, you need to set a node to `Drain`
availability. `Drain` availability  prevents a node from receiving new tasks
from the swarm manager. It also means the manager stops tasks running on the
node and launches replica tasks on a node with `Active` availability.

> [!IMPORTANT]: 
>
> Setting a node to `Drain` does not remove standalone containers from that node,
> such as those created with `docker run`, `docker compose up`, or the Docker Engine
> API. A node's status, including `Drain`, only affects the node's ability to schedule
> swarm service workloads.

1.  If you haven't already, open a terminal and ssh into the machine where you
    run your manager node. For example, the tutorial uses a machine named
    `manager1`.

2.  Verify that all your nodes are actively available.

    ```console
    $ docker node ls

    ID                           HOSTNAME  STATUS  AVAILABILITY  MANAGER STATUS
    1bcef6utixb0l0ca7gxuivsj0    worker2   Ready   Active
    38ciaotwjuritcdtn9npbnkuz    worker1   Ready   Active
    e216jshn25ckzbvmwlnh5jr3g *  manager1  Ready   Active        Leader
    ```

3.  If you aren't still running the `redis` service from the
    [rolling update](rolling-update.md) tutorial, start it now:

    ```console
    $ docker service create --replicas 3 --name redis --update-delay 10s redis:7.4.0

    c5uo6kdmzpon37mgj9mwglcfw
    ```

4.  Run `docker service ps redis` to see how the swarm manager assigned the
tasks to different nodes:

    ```console
    $ docker service ps redis

    NAME                               IMAGE        NODE     DESIRED STATE  CURRENT STATE
    redis.1.7q92v0nr1hcgts2amcjyqg3pq  redis:7.4.0  manager1 Running        Running 26 seconds
    redis.2.7h2l8h3q3wqy5f66hlv9ddmi6  redis:7.4.0  worker1  Running        Running 26 seconds
    redis.3.9bg7cezvedmkgg6c8yzvbhwsd  redis:7.4.0  worker2  Running        Running 26 seconds
    ```

    In this case the swarm manager distributed one task to each node. You may
    see the tasks distributed differently among the nodes in your environment.

5.  Run `docker node update --availability drain <NODE-ID>` to drain a node that
had a task assigned to it:

    ```console
    $ docker node update --availability drain worker1

    worker1
    ```

6.  Inspect the node to check its availability:

    ```console
    $ docker node inspect --pretty worker1

    ID:			38ciaotwjuritcdtn9npbnkuz
    Hostname:		worker1
    Status:
     State:			Ready
     Availability:		Drain
    ...snip...
    ```

    The drained node shows `Drain` for `Availability`.

7.  Run `docker service ps redis` to see how the swarm manager updated the
task assignments for the `redis` service:

    ```console
    $ docker service ps redis

    NAME                                    IMAGE        NODE      DESIRED STATE  CURRENT STATE           ERROR
    redis.1.7q92v0nr1hcgts2amcjyqg3pq       redis:7.4.0  manager1  Running        Running 4 minutes
    redis.2.b4hovzed7id8irg1to42egue8       redis:7.4.0  worker2   Running        Running About a minute
     \_ redis.2.7h2l8h3q3wqy5f66hlv9ddmi6   redis:7.4.0  worker1   Shutdown       Shutdown 2 minutes ago
    redis.3.9bg7cezvedmkgg6c8yzvbhwsd       redis:7.4.0  worker2   Running        Running 4 minutes
    ```

    The swarm manager maintains the desired state by ending the task on a node
    with `Drain` availability and creating a new task on a node with `Active`
    availability.

8.  Run  `docker node update --availability active <NODE-ID>` to return the
drained node to an active state:

    ```console
    $ docker node update --availability active worker1

    worker1
    ```

9.  Inspect the node to see the updated state:

    ```console
    $ docker node inspect --pretty worker1

    ID:			38ciaotwjuritcdtn9npbnkuz
    Hostname:		worker1
    Status:
     State:			Ready
     Availability:		Active
    ...snip...
    ```

    When you set the node back to `Active` availability, it can receive new tasks:

    * during a service update to scale up
    * during a rolling update
    * when you set another node to `Drain` availability
    * when a task fails on another active node

## Next steps

Next, you'll learn how to use a Swarm mode routing mesh

{{< button text="Use a Swarm mode routing mesh" url="../ingress.md" >}}
