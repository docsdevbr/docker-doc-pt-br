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

description: Dev Environments
keywords: Dev Environments, share, Docker Desktop
title: Distribute your dev environment
weight: 30
aliases:
- /desktop/dev-environments/share/
---
{{% include "dev-envs-changing.md" %}}

The `compose-dev.yaml` config file makes distributing your dev environment easy so everyone can access the same code and any dependencies.

### Distribute your dev environment

When you are ready to share your environment, simply copy the link to the Github repo where your project is stored, and share the link with your team members. 

You can also create a link that automatically starts your dev environment when opened. This can then be placed on a GitHub README or pasted into a Slack channel, for example. 

To create the link simply join the following link with the link to your dev environment's GitHub repository:

`https://open.docker.com/dashboard/dev-envs?url=`

The following example opens a [Compose sample](https://github.com/docker/awesome-compose/tree/master/nginx-golang-mysql), a Go server with an Nginx proxy and a MariaDB/MySQL database, in Docker Desktop.

[https://open.docker.com/dashboard/dev-envs?url=https://github.com/docker/awesome-compose/tree/master/nginx-golang-mysql](https://open.docker.com/dashboard/dev-envs?url=https://github.com/docker/awesome-compose/tree/master/nginx-golang-mysql)

### Open a dev environment that has been distributed to you

To open a dev environment that has been shared with you, select the **Create** button in the top right-hand corner, select source **Existing Git repo**, and then paste the URL.
