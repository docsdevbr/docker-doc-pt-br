---
source_url: https://github.com/moby/buildkit/blob/master/frontend/dockerfile/linter/docs/UndefinedVar.md
revision: 03a7663f4ae7285a49aa95ac437a7a0ee6efee4f
status: untranslated
license: https://github.com/moby/buildkit/blob/master/LICENSE

title: UndefinedVar
---

# UndefinedVar

## Output

```text
Usage of undefined variable '$foo'
```

## Description

Before you reference an environment variable or a build argument in a `RUN`
instruction, you should ensure that the variable is declared in the Dockerfile,
using the `ARG` or `ENV` instructions.

Attempting to access an environment variable without explicitly declaring it
doesn't necessarily result in a build error, but it may yield an unexpected
result or an error later on in the build process.

This check also attempts to detect if you're accessing a variable with a typo.
For example, given the following Dockerfile:

```dockerfile
FROM alpine
ENV PATH=$PAHT:/app/bin
```

The check detects that `$PAHT` is undefined, and that it's probably a
misspelling of `PATH`.

```text
Usage of undefined variable '$PAHT' (did you mean $PATH?)
```

## Examples

❌ Bad: `$foo` is an undefined build argument.

```dockerfile
FROM alpine AS base
COPY $foo .
```

✅ Good: declaring `foo` as a build argument before attempting to access it.

```dockerfile
FROM alpine AS base
ARG foo
COPY $foo .
```