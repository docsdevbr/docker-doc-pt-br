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

description: Learn how to optimize and manage your Docker Hub usage.
keywords: Docker Hub, limit, usage
title: Best practices for optimizing Docker Hub usage
linkTitle: Optimize usage
weight: 40
---
Use the following steps to help optimize and manage your Docker Hub usage for
both individuals and organizations:

1. [View your Docker Hub usage](https://hub.docker.com/usage).

2. Use the Docker Hub usage data to identify which accounts consume the most
   data, determine peak usage times, and identify which images are related to
   the most data usage. In addition, look for usage trends, such as the
   following:

   - Inefficient pull behavior: Identify frequently accessed repositories to
     assess whether you can optimize caching practices or consolidate usage to
     reduce pulls.
   - Inefficient automated systems: Check which automated tools, such as CI/CD
     pipelines, may be causing higher pull rates, and configure them to avoid
     unnecessary image pulls.

3. Optimize image pulls by:

   - Using caching: Implement local image caching via
     [mirroring](/docker-hub/mirror/) or within your CI/CD pipelines to reduce
     redundant pulls.
   - Automating manual workflows: Avoid unnecessary pulls by configuring automated
     systems to pull only when a new version of an image is available.

4. Optimize your storage by:

    - Regularly auditing and [removing entire repositories](../repos/delete.md) with untagged, unused, or outdated images.
    - Using [Image Management](../repos/manage/hub-images/manage.md) to remove stale and outdated images within a repository.

5. For organizations, monitor and enforce organizational policies by doing the
   following:

   - Routinely [view Docker Hub usage](https://hub.docker.com/usage) to monitor usage.
   - [Enforce sign-in](/security/for-admins/enforce-sign-in/) to ensure that you
     can monitor the usage of your users and users receive higher usage limits.
   - Look for duplicate user accounts in Docker and remove accounts from your organization
   as needed.
