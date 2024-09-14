---
source_url: https://github.com/moby/buildkit/blob/master/frontend/dockerfile/linter/docs/NoEmptyContinuation.md
revision: ff10dcc14e99b2367feb69fd0380e8a9d6431964
status: untranslated
license: https://github.com/moby/buildkit/blob/master/LICENSE

title: NoEmptyContinuation
---

# NoEmptyContinuation

## Output

```text
Empty continuation line found in: RUN apk add     gnupg     curl
```

## Description

Support for empty continuation (`/`) lines have been deprecated and will
generate errors in future versions of the Dockerfile syntax.

Empty continuation lines are empty lines following a newline escape:

```dockerfile
FROM alpine
RUN apk add \

    gnupg \

    curl
```

Support for such empty lines is deprecated, and a future BuildKit release will
remove support for this syntax entirely, causing builds to break. To avoid
future errors, remove the empty lines, or add comments, since lines with
comments aren't considered empty.

## Examples

❌ Bad: empty continuation line between `EXPOSE` and 80.

```dockerfile
FROM alpine
EXPOSE \

80
```

✅ Good: comments do not count as empty lines.

```dockerfile
FROM alpine
EXPOSE \
# Port
80
```
