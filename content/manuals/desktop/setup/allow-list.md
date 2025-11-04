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

description: A list of domain URLs required for Docker Desktop to function correctly within an organization.
keywords: Docker Desktop, allowlist, allow list, firewall, authentication URLs, analytics
title: Allowlist for Docker Desktop
tags: [admin]
linkTitle: Allowlist
weight: 100
aliases:
  - /desktop/allow-list/
---
{{< summary-bar feature_name="Allow list" >}}

This page contains the domain URLs that you need to add to a firewall allowlist to ensure Docker Desktop works properly within your organization.

## Domain URLs to allow

| Domains                                                                              | Description                                  |
| ------------------------------------------------------------------------------------ | -------------------------------------------- |
| https://api.segment.io                                                               | Analytics                                    |
| https://cdn.segment.com                                                              | Analytics                                    |
| https://experiments.docker.com                                                       | A/B testing                                  |
| https://notify.bugsnag.com                                                           | Error reports                                |
| https://sessions.bugsnag.com                                                         | Error reports                                |
| https://auth.docker.io                                                               | Authentication                               |
| https://cdn.auth0.com                                                                | Authentication                               |
| https://login.docker.com                                                             | Authentication                               |
| https://desktop.docker.com                                                           | Update                                       |
| https://hub.docker.com                                                               | Docker Hub                                   |
| https://registry-1.docker.io                                                         | Docker Pull/Push                             |
| https://production.cloudflare.docker.com                                             | Docker Pull/Push (Paid plans)                |
| https://docker-images-prod.6aa30f8b08e16409b46e0173d6de2f56.r2.cloudflarestorage.com | Docker Pull/Push (Personal plan / Anonymous) |
| https://docker-pinata-support.s3.amazonaws.com                                       | Troubleshooting                              |
| https://api.dso.docker.com                                                           | Docker Scout service                         |
| https://api.docker.com                                                               | New API                                      |
