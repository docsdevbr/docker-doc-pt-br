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

title: Extension image labels
linkTitle: Add labels
description: Docker extension labels
keywords: Docker, extensions, sdk, labels
aliases: 
 - /desktop/extensions-sdk/extensions/labels/
weight: 10
---
Extensions use image labels to provide additional information such as a title, description, screenshots, and more.

This information is then displayed as an overview of the extension, so users can choose to install it.

![An extension overview, generated from labels](images/marketplace-details.png)

You can define [image labels](/reference/dockerfile.md#label) in the extension's `Dockerfile`.

> [!IMPORTANT]
>
> If any of the **required** labels are missing in the `Dockerfile`, Docker Desktop considers the extension invalid and doesn't list it in the Marketplace.


Here is the list of labels you can or need to specify when building your extension:

| Label                                       | Required | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           | Example                                                                                                                                                                                                                                                         |
| ------------------------------------------- | -------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `org.opencontainers.image.title`            | Yes      | Human-readable title of the image (string). This appears in the UI for Docker Desktop.                                                                                                                                                                                                                                                                                                                                                                                                                | my-extension                                                                                                                                                                                                                                                    |
| `org.opencontainers.image.description`      | Yes      | Human-readable description of the software packaged in the image (string)                                                                                                                                                                                                                                                                                                                                                                                                                             | This extension is cool.                                                                                                                                                                                                                                         |
| `org.opencontainers.image.vendor`           | Yes      | Name of the distributing entity, organization, or individual.                                                                                                                                                                                                                                                                                                                                                                                                                                         | Acme, Inc.                                                                                                                                                                                                                                                      |
| `com.docker.desktop.extension.api.version`  | Yes      | Version of the Docker Extension manager that the extension is compatible with. It must follow [semantic versioning](https://semver.org/).                                                                                                                                                                                                                                                                                                                                                             | A specific version like `0.1.0` or, a constraint expression: `>= 0.1.0`, `>= 1.4.7, < 2.0` . For your first extension, you can use `docker extension version` to know the SDK API version and specify `>= <SDK_API_VERSION>`.                                   |
| `com.docker.desktop.extension.icon`         | Yes      | The extension icon (format: .svg .png .jpg)                                                                                                                                                                                                                                                                                                                                                                                                                                                           | `https://example.com/assets/image.svg`                                                                                                                                                                                                                          |
| `com.docker.extension.screenshots`          | Yes      | A JSON array of image URLs and an alternative text displayed to users (in the order they appear in your metadata) in your extension's details page. **Note:** The recommended size for screenshots is 2400x1600 pixels.                                                                                                                                                                                                                                                                               | `[{"alt":"alternative text for image 1",` `"url":"https://example.com/image1.png"},` `{"alt":"alternative text for image2",` `"url":"https://example.com/image2.jpg"}]`                                                                                         |
| `com.docker.extension.detailed-description` | Yes      | Additional information in plain text or HTML about the extension to display in the details dialog.                                                                                                                                                                                                                                                                                                                                                                                                    | `My detailed description` or `<h1>My detailed description</h1>`                                                                                                                                                                                                 |
| `com.docker.extension.publisher-url`        | Yes      | The publisher website URL to display in the details dialog.                                                                                                                                                                                                                                                                                                                                                                                                                                           | `https://example.com`                                                                                                                                                                                                                                           |
| `com.docker.extension.additional-urls`      | No       | A JSON array of titles and additional URLs displayed to users (in the order they appear in your metadata) in your extension's details page. Docker recommends you display the following links if they apply: documentation, support, terms of service, and privacy policy links.                                                                                                                                                                                                                      | `[{"title":"Documentation","url":"https://example.com/docs"},` `{"title":"Support","url":"https://example.com/bar/support"},` `{"title":"Terms of Service","url":"https://example.com/tos"},` `{"title":"Privacy policy","url":"https://example.com/privacy"}]` |
| `com.docker.extension.changelog`            | Yes      | Changelog in plain text or HTML containing the change for the current version only.                                                                                                                                                                                                                                                                                                                                                                                                                   | `Extension changelog` or `<p>Extension changelog<ul>` `<li>New feature A</li>` `<li>Bug fix on feature B</li></ul></p>`                                                                                                                                         |
| `com.docker.extension.account-info`         | No       | Whether the user needs to register to a SaaS platform to use some features of the extension.                                                                                                                                                                                                                                                                                                                                                                                                          | `required` in case it does, leave it empty otherwise.                                                                                                                                                                                                           |
| `com.docker.extension.categories`           | No       | The list of Marketplace categories that your extension belongs to: `ci-cd`, `container-orchestration`, `cloud-deployment`, `cloud-development`, `database`, `kubernetes`, `networking`, `image-registry`, `security`, `testing-tools`, `utility-tools`,`volumes`. If you don't specify this label, users won't be able to find your extension in the Extensions Marketplace when filtering by a category. Extensions published to the Marketplace before the 22nd of September 2022 have been auto-categorized by Docker. | Specified as comma separated values in case of having multiple categories e.g: `kubernetes,security` or a single value e.g. `kubernetes`.                                                                                                   |

> [!TIP]
>
> Docker Desktop applies CSS styles to the provided HTML content. You can make sure that it renders correctly 
> [within the Marketplace](#preview-the-extension-in-the-marketplace). It is recommended that you follow the 
> [styling guidelines](../design/_index.md).

## Preview the extension in the Marketplace

You can validate that the image labels render as you expect.

When you create and install your unpublished extension, you can preview the extension in the Marketplace's **Managed** tab. You can see how the extension labels render in the list and in the details page of the extension.

> Preview extensions already listed in Marketplace
>
> When you install a local image of an extension already published in the Marketplace, for example with the tag `latest`, your local image is not detected as "unpublished".
>
> You can re-tag your image in order to have a different image name that's not listed as a published extension.
> Use `docker tag org/published-extension unpublished-extension` and then `docker extension install unpublished-extension`.

![List preview](images/list-preview.png)
