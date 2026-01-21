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

title: Model Context Protocol (MCP)
description: Learn how to use Model Context Protocol (MCP) servers with Gordon to extend AI capabilities in Docker Desktop.
keywords: ai, mcp, gordon, docker desktop, docker, llm, model context protocol
grid:
- title: Built-in tools
  description: Use the built-in tools.
  icon: construction
  link: /ai/gordon/mcp/built-in-tools
- title: MCP configuration
  description: Configure MCP tools on a per-project basis.
  icon: manufacturing
  link: /ai/gordon/mcp/yaml
aliases:
 - /desktop/features/gordon/mcp/
---

[Model Context Protocol](https://modelcontextprotocol.io/introduction) (MCP) is
an open protocol that standardizes how applications provide context and
additional functionality to large language models. MCP functions as a
client-server protocol, where the client, for example an application like
Gordon, sends requests, and the server processes those requests to deliver the
necessary context to the AI. This context may be gathered by the MCP server by
executing code to perform an action and retrieving the result, calling external
APIs, or other similar operations.

Gordon, along with other MCP clients like Claude Desktop or Cursor, can interact
with MCP servers running as containers.

{{< grid >}}
