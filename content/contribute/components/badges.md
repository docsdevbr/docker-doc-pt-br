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

description: components and formatting examples used in Docker's docs
title: Badges
toc_max: 3
---
### Examples

{{< badge color=blue text="blue badge" >}}
{{< badge color=amber text="amber badge" >}}
{{< badge color=red text="red badge" >}}
{{< badge color=green text="green badge" >}}
{{< badge color=violet text="violet badge" >}}

You can also make a badge a link.

[{{< badge color="blue" text="badge with a link" >}}](../_index.md)

### Usage guidelines

We use badges to indicate new content and product content in various stages of the release lifecycle: 

- The violet badge to highlight new early access or experimental content 
- The blue badge to highlight beta content 
- The green badge to highlight new content that is either GA or not product-related content, such as guides/learning paths

Best practice is to use this badge for no longer than 2 months post release of the feature.

### Markup

```go
{{</* badge color=amber text="amber badge" */>}}
[{{</* badge color="blue" text="badge with a link" */>}}](../overview.md)
```
