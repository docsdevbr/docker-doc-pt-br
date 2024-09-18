---
source_url: https://github.com/docker/compose/blob/main/docs/reference/compose_attach.md
revision: 231ea10058c95ed6308fe4f6ccc1327a553a40ca
status: untranslated
license: https://github.com/docker/compose/blob/master/LICENSE

title: docker compose attach
---

# docker compose attach

Attach local standard input, output, and error streams to a service's running container

### Options

| Name            | Type     | Default | Description                                               |
|:----------------|:---------|:--------|:----------------------------------------------------------|
| `--detach-keys` | `string` |         | Override the key sequence for detaching from a container. |
| `--dry-run`     | `bool`   |         | Execute command in dry run mode                           |
| `--index`       | `int`    | `0`     | index of the container if service has multiple replicas.  |
| `--no-stdin`    | `bool`   |         | Do not attach STDIN                                       |
| `--sig-proxy`   | `bool`   | `true`  | Proxy all received signals to the process                 |
