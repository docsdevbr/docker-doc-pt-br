---
source_url: https://github.com/docker/compose/blob/main/docs/reference/compose_push.md
revision: 231ea10058c95ed6308fe4f6ccc1327a553a40ca
status: untranslated
license: https://github.com/docker/compose/blob/master/LICENSE

datafolder: compose-cli
datafile: docker_compose_push
title: docker compose push
aliases:
- /compose/reference/push/
- /engine/reference/commandline/compose_push/
layout: cli
---

# docker compose push

Pushes images for services to their respective registry/repository.

The following assumptions are made:
- You are pushing an image you have built locally
- You have access to the build key

Examples

```yaml
services:
  service1:
    build: .
    image: localhost:5000/yourimage  ## goes to local registry

  service2:
    build: .
    image: your-dockerid/yourimage  ## goes to your repository on Docker Hub
```

### Options

| Name                     | Type   | Default | Description                                            |
|:-------------------------|:-------|:--------|:-------------------------------------------------------|
| `--dry-run`              | `bool` |         | Execute command in dry run mode                        |
| `--ignore-push-failures` | `bool` |         | Push what it can and ignores images with push failures |
| `--include-deps`         | `bool` |         | Also push images of services declared as dependencies  |
| `-q`, `--quiet`          | `bool` |         | Push without printing progress information             |



## Description

Pushes images for services to their respective registry/repository.

The following assumptions are made:
- You are pushing an image you have built locally
- You have access to the build key

Examples

```yaml
services:
  service1:
    build: .
    image: localhost:5000/yourimage  ## goes to local registry

  service2:
    build: .
    image: your-dockerid/yourimage  ## goes to your repository on Docker Hub
```
