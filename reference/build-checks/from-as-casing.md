---
source_url: https://github.com/moby/buildkit/blob/master/frontend/dockerfile/linter/docs/FromPlatformFlagConstDisallowed.md
revision: 58753e89212e07d54d3e0825b28b67b7ac89d506
status: untranslated
license: https://github.com/moby/buildkit/blob/master/LICENSE

title: FromPlatformFlagConstDisallowed
---

# FromPlatformFlagConstDisallowed

## Output

```text
'as' and 'FROM' keywords' casing do not match
```

## Description

While Dockerfile keywords can be either uppercase or lowercase, mixing case
styles is not recommended for readability. This rule reports violations where
mixed case style occurs for a `FROM` instruction with an `AS` keyword declaring
a stage name.

## Examples

❌ Bad: `FROM` is uppercase, `AS` is lowercase.

```dockerfile
FROM debian:latest as builder
```

✅ Good: `FROM` and `AS` are both uppercase

```dockerfile
FROM debian:latest AS deb-builder
```

✅ Good: `FROM` and `AS` are both lowercase.

```dockerfile
from debian:latest as deb-builder
```

## Related errors

- [`FileConsistentCommandCasing`](./consistent-instruction-casing.md)
