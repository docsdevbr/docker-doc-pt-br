---
# Copyright (c) 2016 Docker, Inc.
# Docker and the Docker logo are trademarks or registered trademarks of Docker,
# Inc. in the United States and/or other countries.
# Docker, Inc. and other parties may also have trademark rights in other terms
# used herein.
#
# Documentation licensed under the Apache License, Version 2.0.
# The original work was translated from English into Brazilian Portuguese.
# https://github.com/docker/docs/blob/main/LICENSE

description: components and formatting examples used in Docker's docs
title: Lists
toc_max: 3
---
## Examples

Use dashes (`-`) or asterisks (`*`) for bullet points.

- Bullet list item 1
- Bullet list item 2
- Bullet list item 3

1.  Numbered list item 1. Two spaces between the period and the first letter
    helps with alignment.

2.  Numbered list item 2. Let's put a note in it.

    > [!NOTE]: We did it!

3.  Numbered list item 3 with a code block in it. You need the blank line before
    the code block happens.

    ```bash
    $ docker run hello-world
    ```

4.  Numbered list item 4 with a bullet list inside it and a numbered list
    inside that.

    - Sub-item 1
    - Sub-item 2

      1.  Sub-sub-item 1
      2.  Sub-sub-item-2 with a table inside it because we like to party!
          Indentation is super important.

          | Header 1 | Header 2 |
          | -------- | -------- |
          | Thing 1  | Thing 2  |
          | Thing 3  | Thing 4  |

## Markdown

````md
- Bullet list item 1
- Bullet list item 2
- Bullet list item 3

1.  Numbered list item 1. Two spaces between the period and the first letter
    helps with alignment.

2.  Numbered list item 2. Let's put a note in it.

    > [!NOTE]: We did it!

3.  Numbered list item 3 with a code block in it. You need the blank line before
    the code block happens.

    ```bash
    $ docker run hello-world
    ```

4.  Numbered list item 4 with a bullet list inside it and a numbered list
    inside that.

    - Sub-item 1
    - Sub-item 2

      1.  Sub-sub-item 1
      2.  Sub-sub-item-2 with a table inside it.
          Indentation is super important.

          | Header 1 | Header 2 |
          | -------- | -------- |
          | Thing 1  | Thing 2  |
          | Thing 3  | Thing 4  |
````
