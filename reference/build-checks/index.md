---
source_url: https://github.com/moby/buildkit/blob/master/frontend/dockerfile/linter/docs/_index.md
revision: 13104703c87c63f151fd799b185d7331f7aa9a3a
status: untranslated
license: https://github.com/moby/buildkit/blob/master/LICENSE

title: Build checks
description: |
    BuildKit has built-in support for analyzing your build configuration based on
    a set of pre-defined rules for enforcing Dockerfile and building best
    practices.
keywords: buildkit, linting, dockerfile, frontend, rules
---

BuildKit has built-in support for analyzing your build configuration based on a
set of pre-defined rules for enforcing Dockerfile and building best practices.
Adhering to these rules helps avoid errors and ensures good readability of your
Dockerfile.

Checks run as a build invocation, but instead of producing a build output, it
performs a series of checks to validate that your build doesn't violate any of
the rules. To run a check, use the `--check` flag:

```console
$ docker build --check .
```

To learn more about how to use build checks, see
[Checking your build configuration](https://docs.docker.com/build/checks/).

| Name                                                                      | Description                                                                                                                  |
|---------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------|
| [ConsistentInstructionCasing](consistent-instruction-casing.md)           | All commands within the Dockerfile should use the same casing (either upper or lower)                                        |
| [CopyIgnoredFile](copy-ignored-file.md) (experimental)                    | Attempting to Copy file that is excluded by .dockerignore                                                                    |
| [DuplicateStageName](duplicate-stage-name.md)                             | Stage names should be unique                                                                                                 |
| [FromAsCasing](from-as-casing.md)                                         | The 'as' keyword should match the case of the 'from' keyword                                                                 |
| [FromPlatformFlagConstDisallowed](from-platform-flag-const-disallowed.md) | FROM --platform flag should not use a constant value                                                                         |
| [InvalidDefaultArgInFrom](invalid-default-arg-in-from.md)                 | Default value for global ARG results in an empty or invalid base image name                                                  |
| [JSONArgsRecommended](json-args-recommended.md)                           | JSON arguments recommended for ENTRYPOINT/CMD to prevent unintended behavior related to OS signals                           |
| [LegacyKeyValueFormat](legacy-key-value-format.md)                        | Legacy key/value format with whitespace separator should not be used                                                         |
| [MaintainerDeprecated](maintainer-deprecated.md)                          | The MAINTAINER instruction is deprecated, use a label instead to define an image author                                      |
| [MultipleInstructionsDisallowed](multiple-instructions-disallowed.md)     | Multiple instructions of the same type should not be used in the same stage                                                  |
| [NoEmptyContinuation](no-empty-continuation.md)                           | Empty continuation lines will become errors in a future release                                                              |
| [RedundantTargetPlatform](redundant-target-platform.md)                   | Setting platform to predefined $TARGETPLATFORM in FROM is redundant as this is the default behavior                          |
| [ReservedStageName](reserved-stage-name.md)                               | Reserved words should not be used as stage names                                                                             |
| [SecretsUsedInArgOrEnv](secrets-used-in-arg-or-env.md)                    | Sensitive data should not be used in the ARG or ENV commands                                                                 |
| [StageNameCasing](stage-name-casing.md)                                   | Stage names should be lowercase                                                                                              |
| [UndefinedArgInFrom](undefined-arg-in-from.md)                            | FROM command must use declared ARGs                                                                                          |
| [UndefinedVar](undefined-var.md)                                          | Variables should be defined before their use                                                                                 |
| [WorkdirRelativePath](workdir-relative-path.md)                           | Relative workdir without an absolute workdir declared within the build can have unexpected results if the base image changes |
