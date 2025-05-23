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
# About these files

The files in this directory are stub files which include the file
`/_includes/cli.md`, which parses YAML files generated from the
[`docker/cli`](https://github.com/docker/cli) repository. The YAML files
are parsed into output files like
</reference/cli/docker/build/>.

## How the output is generated

The output files are composed from two sources:

- The **Description** and **Usage** sections comes directly from
  the CLI source code in that repository.

- The **Extended Description** and **Examples** sections are pulled into the
  YAML from the files in [https://github.com/docker/cli/tree/master/docs/reference/commandline](https://github.com/docker/cli/tree/master/docs/reference/commandline) for Docker CLI commands and [https://github.com/docker/compose/tree/v2/docs/reference](https://github.com/docker/compose/tree/v2/docs/reference) for Docker Compose commands.
  Specifically, the Markdown inside the `## Description` and `## Examples`
  headings are parsed. Submit corrections to the text in those repositories.

## Updating the YAML files

The process for generating the YAML files is still in flux. Check with
@thaJeztah. Be sure to generate the YAML files with the correct
release branch of `docker/cli`, for example, the `19.03` branch.

After generating the YAML files, replace the YAML files in
[https://github.com/docker/docs/tree/main/_data/engine-cli](https://github.com/docker/docs/tree/main/_data/engine-cli)
with the newly-generated files. Submit a pull request.
