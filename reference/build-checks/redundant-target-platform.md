---
source_url: https://github.com/moby/buildkit/blob/master/frontend/dockerfile/linter/docs/RedundantTargetPlatform.md
revision: fe6a7dc29e9dff5df20ba7c0644f9fd8630fa5e3
status: untranslated
license: https://github.com/moby/buildkit/blob/master/LICENSE

title: RedundantTargetPlatform
---

# RedundantTargetPlatform

## Output

```text
Setting platform to predefined $TARGETPLATFORM in FROM is redundant as this is the default behavior
```

## Description

A custom platform can be used for a base image. The default platform is the
same platform as the target output so setting the platform to `$TARGETPLATFORM`
is redundant and unnecessary.

## Examples

❌ Bad: this usage of `--platform` is redundant since `$TARGETPLATFORM` is the default.

```dockerfile
FROM --platform=$TARGETPLATFORM alpine AS builder
RUN apk add --no-cache git
```

✅ Good: omit the `--platform` argument.

```dockerfile
FROM alpine AS builder
RUN apk add --no-cache git
```
