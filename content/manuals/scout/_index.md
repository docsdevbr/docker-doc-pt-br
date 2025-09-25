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

title: Docker Scout
weight: 40
keywords: scout, supply chain, vulnerabilities, packages, cves, scan, analysis, analyze
description:
  Get an overview on Docker Scout to proactively enhance your software supply chain security
aliases:
  - /engine/scan/
params:
  sidebar:
    group: Products
grid:
  - title: Quickstart
    link: /scout/quickstart/
    description: Learn what Docker Scout can do, and how to get started.
    icon: explore
  - title: Image analysis
    link: /scout/image-analysis/
    description: Reveal and dig into the composition of your images.
    icon: radar
  - title: Advisory database
    link: /scout/advisory-db-sources/
    description: Learn about the information sources that Docker Scout uses.
    icon: database
  - title: Integrations
    description: |
      Connect Docker Scout with your CI, registries, and other third-party services.
    link: /scout/integrations/
    icon: multiple_stop
  - title: Dashboard
    link: /scout/dashboard/
    description: |
      The web interface for Docker Scout.
    icon: dashboard
  - title: Policy
    link: /scout/policy/
    description: |
      Ensure that your artifacts align with supply chain best practices.
    icon: policy
  - title: Upgrade
    link: /subscription/change/
    description: |
      The free plan includes up to 1 repository. Upgrade for more.
    icon: upgrade
---
Container images consist of layers and software packages, which are susceptible to vulnerabilities.
These vulnerabilities can compromise the security of containers and applications.

Docker Scout is a solution for proactively enhancing your software supply chain security.
By analyzing your images, Docker Scout compiles an inventory of components, also known as a Software Bill of Materials (SBOM).
The SBOM is matched against a continuously updated vulnerability database to pinpoint security weaknesses.

Docker Scout is a standalone service and platform that you can interact with
using Docker Desktop, Docker Hub, the Docker CLI, and the Docker Scout Dashboard.
Docker Scout also facilitates integrations with third-party systems, such as container registries and CI platforms.

{{< grid >}}
