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

title: Deploy
description: Deploy your Docker setup across your company.
weight: 40
---
> [!WARNING]
> Ensure you communicate with your users before proceeding, and confirm that your IT and MDM teams are prepared to handle any unexpected issues, as these steps will affect all existing users signing into your Docker organization.

## Step one: Enforce SSO

Enforcing SSO means that anyone who has a Docker profile with an email address that matches your verified domain must sign in using your SSO connection. Make sure the Identity provider groups associated with your SSO connection cover all the developer groups that you want to have access to the Docker subscription.

## Step two: Deploy configuration settings and enforce sign-in to users

Have the MDM team deploy the configuration files for Docker to all users.

Congratulations, you have successfully completed the admin implementation process for Docker.
