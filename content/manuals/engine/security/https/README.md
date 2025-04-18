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

_build:
  list: never
  publishResources: false
  render: never
---
This is an initial attempt to make it easier to test the TLS (HTTPS) examples in the protect-access.md
doc.

At this point, it is a manual thing, and I've been running it in boot2docker.

My process is as following:

    $ boot2docker ssh
    root@boot2docker:/# git clone https://github.com/moby/moby
    root@boot2docker:/# cd docker/docs/articles/https
    root@boot2docker:/# make cert

lots of things to see and manually answer, as openssl wants to be interactive

> [!NOTE]: make sure you enter the hostname (`boot2docker` in my case) when prompted for `Computer Name`)

    root@boot2docker:/# sudo make run

Start another terminal:

    $ boot2docker ssh
    root@boot2docker:/# cd docker/docs/articles/https
    root@boot2docker:/# make client

The last connects first with `--tls` and then with `--tlsverify`, both should succeed.
