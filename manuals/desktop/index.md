---
title: Overview of Docker Desktop
linkTitle: Docker Desktop
weight: 100
description: Explore Docker Desktop, what it has to offer, and its key features. Take the next step by downloading or find additional resources
keywords: how to use docker desktop, what is docker desktop used for, what does docker
  desktop do, using docker desktop
grid:
- title: Install Docker Desktop
  description: |
    Install Docker Desktop on
    [Mac](../../../manuals/desktop/install/mac-install/index.md),
    [Windows](../../../manuals/desktop/install/windows-install/index.md), or
    [Linux](../../../manuals/desktop/install/linux/index.md).
  icon: download
- title: Explore Docker Desktop
  description: Navigate Docker Desktop and learn about its key features.
  icon: feature_search
  link: /desktop/use-desktop/
- title: View the release notes
  description: Find out about new features, improvements, and bug fixes.
  icon: note_add
  link: /desktop/release-notes/
- title: Browse common FAQs
  description: Explore general FAQs or FAQs for specific platforms.
  icon: help
  link: /desktop/faqs/
- title: Find additional resources
  description: |
    Find information on networking features, deploying on Kubernetes, and more.
  icon: category
  link: /desktop/kubernetes/
- title: Give feedback
  description: Provide feedback on Docker Desktop or Docker Desktop features.
  icon: sms
  link: /desktop/feedback/
aliases:
- /desktop/opensource/
- /docker-for-mac/dashboard/
- /docker-for-mac/opensource/
- /docker-for-windows/dashboard/
- /docker-for-windows/opensource/
---

Docker Desktop is a one-click-install application for your Mac, Linux, or Windows environment
that lets you build, share, and run containerized applications and microservices.

It provides a straightforward GUI (Graphical User Interface) that lets you manage your containers, applications, and images directly from your machine.

Docker Desktop reduces the time spent on complex setups so you can focus on writing code. It takes care of port mappings, file system concerns, and other default settings, and is regularly updated with bug fixes and security updates.

{{< tabs >}}
{{< tab name="What's included in Docker Desktop?" >}}

- [Docker Engine](../../../manuals/engine/index.md)
- Docker CLI client
- [Docker Scout](../scout/) (additional subscription may apply)
- [Docker Build](../../../manuals/build/index.md)
- [Docker Extensions](../extensions/)
- [Docker Compose](../../../manuals/compose/index.md)
- [Docker Content Trust](../../../manuals/engine/security/trust/index.md)
- [Kubernetes](https://github.com/kubernetes/kubernetes/)
- [Credential Helper](https://github.com/docker/docker-credential-helpers/)

{{< /tab >}}
{{< tab name="What are the key features of Docker Desktop?">}}

* Ability to containerize and share any application on any cloud platform, in multiple languages and frameworks.
* Quick installation and setup of a complete Docker development environment.
* Includes the latest version of Kubernetes.
* On Windows, the ability to toggle between Linux and Windows containers to build applications.
* Fast and reliable performance with native Windows Hyper-V virtualization.
* Ability to work natively on Linux through WSL 2 on Windows machines.
* Volume mounting for code and data, including file change notifications and easy access to running containers on the localhost network.

{{< /tab >}}
{{< /tabs >}}

Docker Desktop works with your choice of development tools and languages and
gives you access to a vast library of certified images and templates in
[Docker Hub](https://hub.docker.com/). This allows development teams to extend
their environment to rapidly auto-build, continuously integrate, and collaborate
using a secure repository.

{{< grid >}}