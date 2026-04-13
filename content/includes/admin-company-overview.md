---
# SPDX-FileCopyrightText: 2013-2026 Docker Inc.
# Docker and the Docker logo are trademarks or registered trademarks of Docker,
# Inc. in the United States and/or other countries.
# Docker, Inc. and other parties may also have trademark rights in other terms
# used herein.
#
# SPDX-License-Identifier: Apache-2.0
# Documentation licensed under the Apache License, Version 2.0.
# The original work was translated from English into Brazilian Portuguese.
# https://github.com/docsdevbr/docker-doc-pt-br/blob/-/LICENSES/Apache-2.0.txt
---

A company provides a single point of visibility across multiple organizations. This view simplifies the management of Docker organizations and settings. Organization owners with a Docker Business subscription can create a company and then manage it through the [Docker Admin Console](https://app.docker.com/admin).

The following diagram depicts the setup of a company and how it relates to associated organizations.

![company-hierarchy](/admin/images/docker-admin-structure.webp)

## Key features

With a company, administrators can:

- View and manage all nested organizations and configure settings centrally
- Carefully control access to the company and company settings
- Have up to ten unique users assigned the company owner role
- Configure SSO and SCIM for all nested organizations
- Enforce SSO for all users in the company

## Prerequisites

Before you create a company, verify the following:

- Any organizations you want to add to a company have a Docker Business subscription
- You're an organization owner for your organization and any additional organizations you want to add
