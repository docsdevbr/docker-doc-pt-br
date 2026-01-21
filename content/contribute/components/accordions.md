---
# Copyright (c) 2013-2026 Docker Inc.
# Docker and the Docker logo are trademarks or registered trademarks of Docker,
# Inc. in the United States and/or other countries.
# Docker, Inc. and other parties may also have trademark rights in other terms
# used herein.
#
# Documentation licensed under the Apache License, Version 2.0.
# The original work was translated from English into Brazilian Portuguese.
# https://github.com/docker/docs/blob/-/LICENSE

description: components and formatting examples used in Docker's docs
title: Accordions
toc_max: 3
---
## Example

{{< accordion title="Accordion example" >}}

```console
$ docker run hello-world
```

{{< /accordion >}}

## Markup

````markdown
{{</* accordion title="Accordion example" */>}}

```console
$ docker run hello-world
```

{{</* /accordion */>}}
````
