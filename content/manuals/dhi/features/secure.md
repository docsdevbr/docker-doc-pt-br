---
# Copyright (c) 2013-2026 Docker Inc.
# Docker and the Docker logo are trademarks or registered trademarks of Docker,
# Inc. in the United States and/or other countries.
# Docker, Inc. and other parties may also have trademark rights in other terms
# used herein.
#
# Documentation licensed under the Apache License, Version 2.0.
# The original work was translated from English into Brazilian Portuguese.
# https://github.com/docker/docs/blob/-/LICENSE

title: Hardened, secure images
description: Learn how Docker Hardened Images reduce vulnerabilities, enforce non-root execution, and include SLSA-compliant metadata for supply chain security.
keywords: non-root containers, slsa build level 3, signed sbom, vex document, hardened container image
---

Docker Hardened Images (DHI) are engineered to provide a robust security
foundation for containerized applications, addressing the evolving challenges of
software supply chain security.

## Near-zero vulnerabilities and non-root execution

Each DHI is meticulously built to eliminate known vulnerabilities, achieving
near-zero Common Vulnerabilities and Exposures (CVEs) through continuous
scanning and updates. By adhering to the principle of least privilege, DHI
images run as non-root by default, reducing the risk of privilege escalation
attacks in production environments.

## Comprehensive supply chain security

DHI incorporates multiple layers of security metadata to ensure transparency and
trust:

- SLSA Level 3 compliance: Each image includes detailed build provenance,
  meeting the standards set by the Supply-chain Levels for Software Artifacts
  (SLSA) framework.

- Software Bill of Materials (SBOMs): Comprehensive SBOMs are provided,
  detailing all components within the image to facilitate vulnerability
  management and compliance audits.

- Vulnerability Exploitability eXchange (VEX) statements: VEX documents
  accompany each image, providing context about known vulnerabilities and their
  exploitability status.

- Cryptographic signing and attestations: All images and associated metadata are
  cryptographically signed, ensuring integrity and authenticity.

## Minimal and developer-friendly options

DHI provides both minimal and development-friendly image variants:

- Minimal images: Built using a distroless approach, these images remove
  unnecessary components, reducing the attack surface by up to 95% and improving
  startup times.

- Development images: Equipped with essential development tools and libraries,
  these images facilitate secure application building and testing.
