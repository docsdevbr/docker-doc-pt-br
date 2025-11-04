---
# Copyright (c) 2013-2025 Docker Inc.
# Docker and the Docker logo are trademarks or registered trademarks of Docker,
# Inc. in the United States and/or other countries.
# Docker, Inc. and other parties may also have trademark rights in other terms
# used herein.
#
# Documentation licensed under the Apache License, Version 2.0.
# The original work was translated from English into Brazilian Portuguese.
# https://github.com/docker/docs/blob/-/LICENSE

title: "Demo: Using Docker Build Cloud in CI"
description: Learn how to use Docker Build Cloud to build your app faster in CI.
weight: 30
---
Docker Build Cloud can significantly decrease the time it takes for your CI builds
take to run, saving you time and money.

Since the builds run remotely, your CI runner can still use the Docker tooling CLI
without needing elevated permissions, making your builds more secure by default.

In this demo, you will see:

- How to integrate Docker Build Cloud into a variety of CI platforms
- How to use Docker Build Cloud in GitHub Actions to build multi-architecture images
- Speed differences between a workflow using Docker Build Cloud and a workflow running natively
- How to use Docker Build Cloud in a GitLab Pipeline

{{< youtube-embed "wvLdInoVBGg" >}}

<div id="dbc-lp-survey-anchor"></div>
