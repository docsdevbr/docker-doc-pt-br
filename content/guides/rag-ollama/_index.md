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

description: Containerize RAG application using Ollama and Docker
keywords: python, generative ai, genai, llm, ollama, rag, qdrant
title: Build a RAG application using Ollama and Docker
linkTitle: RAG Ollama application
summary: |
  This guide demonstrates how to use Docker to deploy Retrieval-Augmented
  Generation (RAG) models with Ollama.
tags: [ai]
aliases:
  - /guides/use-case/rag-ollama/
params:
  time: 20 minutes
---
The Retrieval Augmented Generation (RAG) guide teaches you how to containerize an existing RAG application using Docker. The example application is a RAG that acts like a sommelier, giving you the best pairings between wines and food. In this guide, you’ll learn how to:

- Containerize and run a RAG application
- Set up a local environment to run the complete RAG stack locally for development

Start by containerizing an existing RAG application.
