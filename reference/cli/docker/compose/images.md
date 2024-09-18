---
source_url: https://github.com/docker/compose/blob/main/docs/reference/compose_images.md
revision: 231ea10058c95ed6308fe4f6ccc1327a553a40ca
status: untranslated
license: https://github.com/docker/compose/blob/master/LICENSE

datafolder: compose-cli
datafile: docker_compose_images
title: docker compose images
aliases:
- /compose/reference/images/
- /engine/reference/commandline/compose_images/
layout: cli
---

# docker compose images

List images used by the created containers

### Options

| Name            | Type     | Default | Description                                |
|:----------------|:---------|:--------|:-------------------------------------------|
| `--dry-run`     | `bool`   |         | Execute command in dry run mode            |
| `--format`      | `string` | `table` | Format the output. Values: [table \| json] |
| `-q`, `--quiet` | `bool`   |         | Only display IDs                           |
