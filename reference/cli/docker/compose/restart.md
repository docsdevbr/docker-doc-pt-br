---
source_url: https://github.com/docker/compose/blob/main/docs/reference/compose_restart.md
revision: 231ea10058c95ed6308fe4f6ccc1327a553a40ca
status: untranslated
license: https://github.com/docker/compose/blob/master/LICENSE

datafolder: compose-cli
datafile: docker_compose_restart
title: docker compose restart
aliases:
- /compose/reference/restart/
- /engine/reference/commandline/compose_restart/
layout: cli
---

# docker compose restart

Restarts all stopped and running services, or the specified services only.

If you make changes to your `compose.yml` configuration, these changes are not reflected
after running this command. For example, changes to environment variables (which are added
after a container is built, but before the container's command is executed) are not updated
after restarting.

If you are looking to configure a service's restart policy, refer to
[restart](https://github.com/compose-spec/compose-spec/blob/master/spec.md#restart)
or [restart_policy](https://github.com/compose-spec/compose-spec/blob/master/deploy.md#restart_policy).

### Options

| Name              | Type   | Default | Description                           |
|:------------------|:-------|:--------|:--------------------------------------|
| `--dry-run`       | `bool` |         | Execute command in dry run mode       |
| `--no-deps`       | `bool` |         | Don't restart dependent services      |
| `-t`, `--timeout` | `int`  | `0`     | Specify a shutdown timeout in seconds |



## Description

Restarts all stopped and running services, or the specified services only.

If you make changes to your `compose.yml` configuration, these changes are not reflected
after running this command. For example, changes to environment variables (which are added
after a container is built, but before the container's command is executed) are not updated
after restarting.

If you are looking to configure a service's restart policy, refer to
[restart](https://github.com/compose-spec/compose-spec/blob/master/spec.md#restart)
or [restart_policy](https://github.com/compose-spec/compose-spec/blob/master/deploy.md#restart_policy).
