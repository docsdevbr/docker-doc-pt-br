---
source_url: https://github.com/moby/buildkit/blob/master/frontend/dockerfile/linter/docs/MaintainerDeprecated.md
revision: 37fc95a415069c542b4c0881e2fb1695e2597795
status: untranslated
license: https://github.com/moby/buildkit/blob/master/LICENSE

title: MaintainerDeprecated
---

# MaintainerDeprecated

## Output

```text
MAINTAINER instruction is deprecated in favor of using label
```

## Description

The `MAINTAINER` instruction, used historically for specifying the author of
the Dockerfile, is deprecated. To set author metadata for an image, use the
`org.opencontainers.image.authors` [OCI label](https://github.com/opencontainers/image-spec/blob/main/annotations.md#pre-defined-annotation-keys).

## Examples

❌ Bad: don't use the `MAINTAINER` instruction

```dockerfile
MAINTAINER moby@example.com
```

✅ Good: specify the author using the `org.opencontainers.image.authors` label

```dockerfile
LABEL org.opencontainers.image.authors="moby@example.com"
```
