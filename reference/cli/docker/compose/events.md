---
source_url: https://github.com/docker/compose/blob/main/docs/reference/compose_events.md
revision: 231ea10058c95ed6308fe4f6ccc1327a553a40ca
status: untranslated
license: https://github.com/docker/compose/blob/master/LICENSE

datafolder: compose-cli
datafile: docker_compose_events
title: docker compose events
aliases:
- /compose/reference/events/
- /engine/reference/commandline/compose_events/
layout: cli
---

# docker compose events

Stream container events for every container in the project.

With the `--json` flag, a json object is printed one per line with the format:

```json
{
    "time": "2015-11-20T18:01:03.615550",
    "type": "container",
    "action": "create",
    "id": "213cf7...5fc39a",
    "service": "web",
    "attributes": {
      "name": "application_web_1",
      "image": "alpine:edge"
    }
}
```

The events that can be received using this can be seen [here](../system/events.md#object-types).

### Options

| Name        | Type   | Default | Description                               |
|:------------|:-------|:--------|:------------------------------------------|
| `--dry-run` | `bool` |         | Execute command in dry run mode           |
| `--json`    | `bool` |         | Output events as a stream of json objects |



## Description

Stream container events for every container in the project.

With the `--json` flag, a json object is printed one per line with the format:

```json
{
    "time": "2015-11-20T18:01:03.615550",
    "type": "container",
    "action": "create",
    "id": "213cf7...5fc39a",
    "service": "web",
    "attributes": {
      "name": "application_web_1",
      "image": "alpine:edge"
    }
}
```

The events that can be received using this can be seen [here](https://docs.docker.com/reference/cli/docker/system/events/#object-types).
