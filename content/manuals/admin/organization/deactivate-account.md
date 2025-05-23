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

title: Deactivate an organization
description: Learn how to deactivate a Docker organization.
keywords: Docker Hub, delete, deactivate organization, account, organization management
weight: 42
aliases:
- /docker-hub/deactivate-account/
---
{{< summary-bar feature_name="General admin" >}}

You can deactivate an account at any time. This section describes the prerequisites and steps to deactivate an organization account. For information on deactivating a user account, see [Deactivate a user account](../../accounts/deactivate-user-account.md).

> [!WARNING]
>
> All Docker products and services that use your Docker account or organization account will be inaccessible after deactivating your account.

## Prerequisites

Before deactivating an organization, complete the following:

- Download any images and tags you want to keep:
  `docker pull -a <image>:<tag>`.

- If you have an active Docker subscription, [downgrade it to a free subscription](../../subscription/change.md).

- Remove all other members within the organization.

- Unlink your [Github and Bitbucket accounts](../../docker-hub/repos/manage/builds/link-source.md#unlink-a-github-user-account).

- For Business organizations, [remove your SSO connection](../../security/for-admins/single-sign-on/manage/#remove-an-organization).

## Deactivate

Once you have completed all the previous steps, you can deactivate your organization.

> [!WARNING]
>
> This cannot be undone. Be sure you've gathered all the data you need from your organization before deactivating it.

{{< tabs >}}
{{< tab name="Admin Console" >}}

1. In Admin Console, choose the organization you want to deactivate.
2. Under **Organization settings**, select **Deactivate**.
3. Enter the organization name to confirm deactivation.
4. Select **Deactivate organization**.

{{< /tab >}}
{{< tab name="Docker Hub" >}}

1. On Docker Hub, select **My Hub**.
2. Choose the organization you want to deactivate.
3. In **Settings**, select the **Deactivate org** and then **Deactivate organization**.

{{< /tab >}}
{{< /tabs >}}
