---
source_url: https://github.com/moby/buildkit/blob/master/frontend/dockerfile/linter/docs/InvalidDefaultArgInFrom.md
revision: 8bcc375e122ecc0e41cd7823025ce2a7c86c7bca
status: untranslated
license: https://github.com/moby/buildkit/blob/master/LICENSE

title: InvalidDefaultArgInFrom
---

# InvalidDefaultArgInFrom

## Output

```text
Using the global ARGs with default values should produce a valid build.
```

## Description

An `ARG` used in an image reference should be valid when no build arguments are used. An image build should not require `--build-arg` to be used to produce a valid build.

## Examples

❌ Bad: don't rely on an ARG being set for an image reference to be valid

```dockerfile
ARG TAG
FROM busybox:${TAG}
```

✅ Good: include a default for the ARG

```dockerfile
ARG TAG=latest
FROM busybox:${TAG}
```

✅ Good: ARG can be empty if the image would be valid with it empty

```dockerfile
ARG VARIANT
FROM busybox:stable${VARIANT}
```

✅ Good: Use a default value if the build arg is not present

```dockerfile
ARG TAG
FROM alpine:${TAG:-3.14}
```
