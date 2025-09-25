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

title: Why Docker Build Cloud?
description: Learn how Docker Build Cloud makes your builds faster.
weight: 10
---
Docker Build Cloud is a service that lets you build container images faster,
both locally and in CI. Builds run on cloud infrastructure optimally
dimensioned for your workloads, with no configuration required. The service
uses a remote build cache, ensuring fast builds anywhere and for all team
members.

Docker Build Cloud provides several benefits over local builds:

- Improved build speed
- Shared build cache
- Native multi-platform builds

There’s no need to worry about managing builders or infrastructure — simply
connect to your builders and start building. Each cloud builder provisioned to
an organization is completely isolated to a single Amazon EC2 instance, with a
dedicated EBS volume for build cache and encryption in transit. That means
there are no shared processes or data between cloud builders.

{{< youtube-embed "8AqKhEO2PQA" >}}

<div id="dbc-lp-survey-anchor"></div>
