---
# Copyright (c) 2013-2025 Docker Inc.
# Docker and the Docker logo are trademarks or registered trademarks of Docker,
# Inc. in the United States and/or other countries.
# Docker, Inc. and other parties may also have trademark rights in other terms
# used herein.
#
# Documentation licensed under the Apache License, Version 2.0.
# The original work was translated from English into Brazilian Portuguese.
# https://github.com/docker/docs/blob/-/LICENSE

description: Single sign-on domain FAQs
keywords: Docker, Docker Hub, SSO FAQs, single sign-on, domains, domain verification, domain management
title: FAQS on SSO and domains
tags: [FAQ]
aliases:
- /single-sign-on/domain-faqs/
- /faq/security/single-sign-on/domain-faqs/
---
### Can I add sub-domains?

Yes, you can add sub-domains to your SSO connection, however all email addresses should also be on that domain. Verify that your DNS provider supports multiple TXT records for the same domain.

### Can the DNS provider configure it once for one-time verification and remove it later or will it be needed permanently?

You can do it one time to add the domain to a connection. If your organization ever changes IdPs and has to set up SSO again, your DNS provider will need to verify again.

### Is adding domain required to configure SSO? What domains should I be adding? And how do I add it?

Adding and verifying a domain is required to enable and enforce SSO. See [Configure single sign-on](/manuals/security/for-admins/single-sign-on/configure.md) for more information. This should include all email domains users will use to access Docker. Public domains, for example `gmail.com` or `outlook.com`, are not permitted. Also, the email domain should be set as the primary email.

### Is IdP-initiated authentication supported?

IdP-initiated authentication isn't supported by Docker SSO. Users must initiate sign-in through Docker Desktop or Hub.

### Can I verify the same domain on multiple organizations?

You can't verify the same domain for multiple orgnaizations at the organization level. If you want to verify one domain for multiple organizations, you must have a Docker Business subscription, and [create a company](/manuals/admin/company/new-company.md). A company enables centralized management of organizations and allows domain verification at the company level.
