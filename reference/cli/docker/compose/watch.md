---
source_url: https://github.com/docker/compose/blob/main/docs/reference/compose_watch.md
revision: 231ea10058c95ed6308fe4f6ccc1327a553a40ca
status: untranslated
license: https://github.com/docker/compose/blob/master/LICENSE

datafolder: compose-cli
datafile: docker_compose_watch
title: docker compose watch
layout: cli
aliases:
- /engine/reference/commandline/compose_watch/
---

# docker compose watch

Watch build context for service and rebuild/refresh containers when files are updated

### Options

| Name        | Type   | Default | Description                                   |
|:------------|:-------|:--------|:----------------------------------------------|
| `--dry-run` | `bool` |         | Execute command in dry run mode               |
| `--no-up`   | `bool` |         | Do not build & start services before watching |
| `--prune`   | `bool` |         | Prune dangling images on rebuild              |
| `--quiet`   | `bool` |         | hide build output                             |
