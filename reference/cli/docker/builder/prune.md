---
source_url: https://github.com/docker/cli/blob/master/docs/reference/commandline/builder.md
revision: 79c9e527a35c0c2dad8f11cde74ecec77ac59b27
status: untranslated
license: https://github.com/docker/cli/blob/master/LICENSE

title: docker builder prune
---

# builder prune

Remove build cache

### Options

| Name             | Type     | Default | Description                                           |
|:-----------------|:---------|:--------|:------------------------------------------------------|
| `-a`, `--all`    | `bool`   |         | Remove all unused build cache, not just dangling ones |
| `--filter`       | `filter` |         | Provide filter values (e.g. `until=24h`)              |
| `-f`, `--force`  | `bool`   |         | Do not prompt for confirmation                        |
| `--keep-storage` | `bytes`  | `0`     | Amount of disk space to keep for cache                |
