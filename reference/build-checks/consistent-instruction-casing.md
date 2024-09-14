---
source_url: https://github.com/moby/buildkit/blob/master/frontend/dockerfile/linter/docs/ConsistentInstructionCasing.md
revision: 37fc95a415069c542b4c0881e2fb1695e2597795
status: untranslated
license: https://github.com/moby/buildkit/blob/master/LICENSE

title: ConsistentInstructionCasing
---

# ConsistentInstructionCasing

## Output

```text
Command 'EntryPoint' should be consistently cased
```

## Description

Instruction keywords should use consistent casing (all lowercase or all
uppercase). Using a case that mixes uppercase and lowercase, such as
`PascalCase` or `snakeCase`, letters result in poor readability.

## Examples

❌ Bad: don't mix uppercase and lowercase.

```dockerfile
From alpine
Run echo hello > /greeting.txt
EntRYpOiNT ["cat", "/greeting.txt"]
```

✅ Good: all uppercase.

```dockerfile
FROM alpine
RUN echo hello > /greeting.txt
ENTRYPOINT ["cat", "/greeting.txt"]
```

✅ Good: all lowercase.

```dockerfile
from alpine
run echo hello > /greeting.txt
entrypoint ["cat", "/greeting.txt"]
```
