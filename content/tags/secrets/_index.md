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

title: Secrets
description: Use sensitive information in containers securely
---
A secret is a piece of data, such as a password, SSH private key, SSL
certificate, or anything that should not be transmitted over a network or
stored unencrypted in a Dockerfile or in your application's source code.

Docker provides specially designated features for managing secrets.
