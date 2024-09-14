---
source_url: https://github.com/moby/buildkit/blob/master/frontend/dockerfile/linter/docs/ReservedStageName.md
revision: 03a7663f4ae7285a49aa95ac437a7a0ee6efee4f
status: untranslated
license: https://github.com/moby/buildkit/blob/master/LICENSE

title: ReservedStageName
---

# ReservedStageName

## Output

```text
'scratch' is reserved and should not be used as a stage name
```

## Description

Reserved words should not be used as names for stages in multi-stage builds.
The reserved words are:

- `context`
- `scratch`

## Examples

❌ Bad: `scratch` and `context` are reserved names.

```dockerfile
FROM alpine AS scratch
FROM alpine AS context
```

✅ Good: the stage name `builder` is not reserved.

```dockerfile
FROM alpine AS builder
```
