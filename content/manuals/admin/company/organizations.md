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

description: Learn how to manage organizations in a company.
keywords: company, multiple organizations, manage organizations
title: Manage company organizations
---
{{< summary-bar feature_name="Company" >}}

You can manage the organizations in a company in the Docker Admin Console.

## View all organizations

1. Sign in to the [Admin Console](https://admin.docker.com).
2. Select your company on the **Choose profile** page.
3. Under **Organizations**, select **Overview**.

The organization overview page displays all organizations under your company.

## Add seats to an organization

When you have a [self-serve](../../subscription/details.md#self-serve) subscription that has no pending subscription changes, you can add seats using the following steps. If you have a sales-assisted subscription, you can contact Docker support or sales to add seats.

For more information about adding seats, see [Manage seats](/manuals/subscription/manage-seats.md#add-seats).

## Add organizations to a company

You must be a company owner to add an organization to a company. You must also be an organization owner of the organization you want to add. There is no limit to the number of organizations you can have under a company layer. All organizations must have a Business subscription.

> [!IMPORTANT]
>
> Once you add an organization to a company, you can't remove it from the company.

1. Sign in to the [Admin Console](https://admin.docker.com).
2. Select your company on the **Choose profile** page.
3. Select **Organizations**, then **Overview**.
4. Select **Add organization**.
5. Choose the organization you want to add from the drop-down menu.
6. Select **Add organization** to confirm.

## Manage an organization

1. Sign in to the [Admin Console](https://admin.docker.com).
2. Select your company on the **Choose profile** page.
3. Select the organization that you want to manage.

For more details about managing an organization, see [Organization administration](../organization/_index.md).

## More resources

- [Video: Managing a company and nested organizations](https://youtu.be/XZ5_i6qiKho?feature=shared&t=229)
- [Video: Adding nested organizations to a company](https://youtu.be/XZ5_i6qiKho?feature=shared&t=454)
