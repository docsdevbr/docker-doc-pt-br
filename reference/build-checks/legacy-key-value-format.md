---
source_url: https://github.com/moby/buildkit/blob/master/frontend/dockerfile/linter/docs/LegacyKeyValueFormat.md
revision: 465c93364fdf5032ff98ab8b07004110cbca56d6
status: untranslated
license: https://github.com/moby/buildkit/blob/master/LICENSE

title: LegacyKeyValueFormat
---

# LegacyKeyValueFormat

## Output

```text
"ENV key=value" should be used instead of legacy "ENV key value" format
```

## Description

The correct format for declaring environment variables and build arguments in a
Dockerfile is `ENV key=value` and `ARG key=value`, where the variable name
(`key`) and value (`value`) are separated by an equals sign (`=`).
Historically, Dockerfiles have also supported a space separator between the key
and the value (for example, `ARG key value`). This legacy format is deprecated,
and you should only use the format with the equals sign.

## Examples

❌ Bad: using a space separator for variable key and value.

```dockerfile
FROM alpine
ARG foo bar
```

✅ Good: use an equals sign to separate key and value.

```dockerfile
FROM alpine
ARG foo=bar
```

❌ Bad: multi-line variable declaration with a space separator.

```dockerfile
ENV DEPS \
    curl \
    git \
    make
```

✅ Good: use an equals sign and wrap the value in quotes.

```dockerfile
ENV DEPS="\
    curl \
    git \
    make"
```
