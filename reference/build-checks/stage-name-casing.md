---
source_url: https://github.com/moby/buildkit/blob/master/frontend/dockerfile/linter/docs/StageNameCasing.md
revision: 03a7663f4ae7285a49aa95ac437a7a0ee6efee4f
status: untranslated
license: https://github.com/moby/buildkit/blob/master/LICENSE

title: StageNameCasing
---

# StageNameCasing

## Output

```text
Stage name 'BuilderBase' should be lowercase
```

## Description

To help distinguish Dockerfile instruction keywords from identifiers, this rule
forces names of stages in a multi-stage Dockerfile to be all lowercase.

## Examples

❌ Bad: mixing uppercase and lowercase characters in the stage name.

```dockerfile
FROM alpine AS BuilderBase
```

✅ Good: stage name is all in lowercase.

```dockerfile
FROM alpine AS builder-base
```
