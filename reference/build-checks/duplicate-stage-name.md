---
source_url: https://github.com/moby/buildkit/blob/master/frontend/dockerfile/linter/docs/DuplicateStageName.md
revision: 03a7663f4ae7285a49aa95ac437a7a0ee6efee4f
status: untranslated
license: https://github.com/moby/buildkit/blob/master/LICENSE

title: DuplicateStageName
---

# DuplicateStageName

## Output

```text
Duplicate stage name 'foo-base', stage names should be unique
```

## Description

Defining multiple stages with the same name results in an error because the
builder is unable to uniquely resolve the stage name reference.

## Examples

❌ Bad: `builder` is declared as a stage name twice.

```dockerfile
FROM debian:latest AS builder
RUN apt-get update; apt-get install -y curl

FROM golang:latest AS builder
```

✅ Good: stages have unique names.

```dockerfile
FROM debian:latest AS deb-builder
RUN apt-get update; apt-get install -y curl

FROM golang:latest AS go-builder
```
