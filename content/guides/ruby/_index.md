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

title: Ruby on Rails language-specific guide
linkTitle: Ruby
description: Containerize Ruby on Rails apps using Docker
keywords: Docker, getting started, ruby, language
summary: |
  This guide explains how to containerize Ruby on Rails applications using
  Docker.
toc_min: 1
toc_max: 2
aliases:
  - /language/ruby/
  - /guides/language/ruby/
languages: [ruby]
tags: [frameworks]
params:
  time: 20 minutes
---
The Ruby language-specific guide teaches you how to containerize a Ruby on Rails application using Docker. In this guide, you’ll learn how to:

- Containerize and run a Ruby on Rails application
- Configure a GitHub Actions workflow to build and push a Docker image to Docker Hub
- Set up a local environment to develop a Ruby on Rails application using containers
- Deploy your containerized Ruby on Rails application locally to Kubernetes to test and debug your deployment

Start by containerizing an existing Ruby on Rails application.
