---
# Copyright (c) 2013-2026 Docker Inc.
# Docker and the Docker logo are trademarks or registered trademarks of Docker,
# Inc. in the United States and/or other countries.
# Docker, Inc. and other parties may also have trademark rights in other terms
# used herein.
#
# Documentation licensed under the Apache License, Version 2.0.
# The original work was translated from English into Brazilian Portuguese.
# https://github.com/docker/docs/blob/-/LICENSE

title: Deploy with Jamf Pro
description: Use Jamf Pro to deploy Docker Desktop for Mac
keywords: jamf, mac, docker desktop, deploy, mdm, enterprise, administrator, pkg
tags: [admin]
weight: 50
aliases:
 - /desktop/setup/install/enterprise-deployment/use-jamf-pro/
---

{{< summary-bar feature_name="Jamf Pro" >}}

Learn how to deploy Docker Desktop for Mac using Jamf Pro, including uploading the installer and creating a deployment policy.

First, upload the package:

1. From the Jamf Pro console, navigate to **Computers** > **Management Settings** > **Computer Management** > **Packages**.
2. Select **New** to add a new package.
3. Upload the `Docker.pkg` file.

Next, create a policy for deployment:

1. Navigate to **Computers** > **Policies**.
2. Select **New** to create a new policy.
3. Enter a name for the policy, for example "Deploy Docker Desktop".
4. Under the **Packages** tab, add the Docker package you uploaded.
5. Configure the scope to target the devices or device groups on which you want to install Docker.
6. Save the policy and deploy.

For more information, see [Jamf Pro's official documentation](https://learn.jamf.com/en-US/bundle/jamf-pro-documentation-current/page/Policies.html).

## Additional resources

- Learn how to [enforce sign-in](/manuals/enterprise/security/enforce-sign-in/_index.md) for your users.
