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

description: components and formatting examples used in Docker's docs
title: Tables
toc_max: 3
---
## Example

### Basic table

| Permission level                                                         | Access                                                        |
| :----------------------------------------------------------------------- | :------------------------------------------------------------ |
| **Bold** or _italic_ within a table cell. Next cell is empty on purpose. |                                                               |
|                                                                          | Previous cell is empty. A `--flag` in mono text.              |
| Read                                                                     | Pull                                                          |
| Read/Write                                                               | Pull, push                                                    |
| Admin                                                                    | All of the above, plus update description, create, and delete |

### Feature-support table

| Platform   | x86_64 / amd64 |
| :--------- | :------------: |
| Ubuntu     |       ✅       |
| Debian     |       ✅       |
| Fedora     |                |
| Arch (btw) |       ✅       |

## Markdown

### Basic table

```md
| Permission level                                                         | Access                                                        |
| :----------------------------------------------------------------------- | :------------------------------------------------------------ |
| **Bold** or _italic_ within a table cell. Next cell is empty on purpose. |                                                               |
|                                                                          | Previous cell is empty. A `--flag` in mono text.              |
| Read                                                                     | Pull                                                          |
| Read/Write                                                               | Pull, push                                                    |
| Admin                                                                    | All of the above, plus update description, create, and delete |
```

The alignment of the cells in the source doesn't really matter. The ending pipe
character is optional (unless the last cell is supposed to be empty).

### Feature-support table

```md
| Platform   | x86_64 / amd64 |
| :--------- | :------------: |
| Ubuntu     |       ✅       |
| Debian     |       ✅       |
| Fedora     |                |
| Arch (btw) |       ✅       |
```
