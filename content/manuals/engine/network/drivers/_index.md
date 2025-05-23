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

title: Network drivers
weight: 20
description: Learn the basics of Docker network drivers
keywords: networking, drivers, bridge, routing, routing mesh, overlay, ports
---
Docker's networking subsystem is pluggable, using drivers. Several drivers
exist by default, and provide core networking functionality:

- `bridge`: The default network driver. If you don't specify a driver, this is
  the type of network you are creating. Bridge networks are commonly used when
  your application runs in a container that needs to communicate with other
  containers on the same host.
  See [Bridge network driver](bridge.md).

- `host`: Remove network isolation between the container and the Docker host,
  and use the host's networking directly.
  See [Host network driver](host.md).

- `overlay`: Overlay networks connect multiple Docker daemons together and
  enable Swarm services and containers to communicate across nodes. This
  strategy removes the need to do OS-level routing.
  See [Overlay network driver](overlay.md).

- `ipvlan`: IPvlan networks give users total control over both IPv4 and IPv6
  addressing. The VLAN driver builds on top of that in giving operators complete
  control of layer 2 VLAN tagging and even IPvlan L3 routing for users
  interested in underlay network integration.
  See [IPvlan network driver](ipvlan.md).

- `macvlan`: Macvlan networks allow you to assign a MAC address to a container,
  making it appear as a physical device on your network. The Docker daemon
  routes traffic to containers by their MAC addresses. Using the `macvlan`
  driver is sometimes the best choice when dealing with legacy applications that
  expect to be directly connected to the physical network, rather than routed
  through the Docker host's network stack.
  See [Macvlan network driver](macvlan.md).

- `none`: Completely isolate a container from the host and other containers.
  `none` is not available for Swarm services.
  See [None network driver](none.md).

- [Network plugins](/engine/extend/plugins_network/): You can install and use
  third-party network plugins with Docker.

### Network driver summary

- The default bridge network is good for running containers that don't require
  special networking capabilities.
- User-defined bridge networks enable containers on the same Docker host to
  communicate with each other. A user-defined network typically defines an
  isolated network for multiple containers belonging to a common project or
  component.
- Host network shares the host's network with the container. When you use this
  driver, the container's network isn't isolated from the host.
- Overlay networks are best when you need containers running on different
  Docker hosts to communicate, or when multiple applications work together
  using Swarm services.
- Macvlan networks are best when you are migrating from a VM setup or need your
  containers to look like physical hosts on your network, each with a unique
  MAC address.
- IPvlan is similar to Macvlan, but doesn't assign unique MAC addresses to
  containers. Consider using IPvlan when there's a restriction on the number of
  MAC addresses that can be assigned to a network interface or port.
- Third-party network plugins allow you to integrate Docker with specialized
  network stacks.

## Networking tutorials

Now that you understand the basics about Docker networks, deepen your
understanding using the following tutorials:

- [Standalone networking tutorial](/manuals/engine/network/tutorials/standalone.md)
- [Host networking tutorial](/manuals/engine/network/tutorials/host.md)
- [Overlay networking tutorial](/manuals/engine/network/tutorials/overlay.md)
- [Macvlan networking tutorial](/manuals/engine/network/tutorials/macvlan.md)
