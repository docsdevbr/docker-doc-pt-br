---
source_url: https://github.com/docker/compose/blob/main/docs/reference/compose_alpha_viz.md
revision: 231ea10058c95ed6308fe4f6ccc1327a553a40ca
status: untranslated
license: https://github.com/docker/compose/blob/master/LICENSE

datafolder: compose-cli
datafile: docker_compose_alpha_viz
title: docker compose alpha viz
layout: cli
aliases:
- /engine/reference/commandline/compose_alpha_viz/
---

# docker compose alpha viz

EXPERIMENTAL - Generate a graphviz graph from your compose file

### Options

| Name                 | Type   | Default | Description                                                                                        |
|:---------------------|:-------|:--------|:---------------------------------------------------------------------------------------------------|
| `--dry-run`          | `bool` |         | Execute command in dry run mode                                                                    |
| `--image`            | `bool` |         | Include service's image name in output graph                                                       |
| `--indentation-size` | `int`  | `1`     | Number of tabs or spaces to use for indentation                                                    |
| `--networks`         | `bool` |         | Include service's attached networks in output graph                                                |
| `--ports`            | `bool` |         | Include service's exposed ports in output graph                                                    |
| `--spaces`           | `bool` |         | If given, space character ' ' will be used to indent,<br>otherwise tab character '\t' will be used |
