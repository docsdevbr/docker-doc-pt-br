---
description: Learn how single sign-on works, how to set it up, and the required SSO attributes.
keywords: Single Sign-On, SSO, sign-on, admin, docker hub, admin console, security
title: Single sign-on overview
linkTitle: Single sign-on
aliases:
- /single-sign-on/
- /admin/company/settings/sso/
- /admin/organization/security-settings/sso-management/
weight: 10
---

Single sign-on (SSO) allows users to authenticate using their identity providers (IdPs) to access Docker. SSO is available for a whole company, and all associated organizations, or an individual organization that has a Docker Business subscription. To upgrade your existing account to a Docker Business subscription, see [Upgrade your subscription](../../../subscription/core-subscription/upgrade.md).

## How it works

When you enable SSO, your users can't authenticate using their Docker login credentials (Docker ID and password). Docker supports Service Provider Initiated SSO flow. Instead, they are redirected to your IdP's authentication page to sign in. Your users must sign in to Docker Hub or Docker Desktop to initiate the SSO authentication process.

The following diagram shows how SSO operates and is managed in Docker Hub and Docker Desktop. In addition, it provides information on how to authenticate between your IdP.

![SSO architecture](images/SSO.png)

## How to set it up

1. Configure SSO by adding and verify your domain for your organization, then create an SSO connection with your IdP. Docker provides the Assertion Consumer Service (ACS) URL and Entity ID needed to establish a connection between your IdP server and Docker Hub.
2. Test your connection by attempting to sign in to Docker Hub using your domain email address.
3. Optionally, you can [enforce SSO](connect/index.md#optional-enforce-sso) sign-in.
4. Complete SSO enablement. A first-time user can sign in to Docker Hub using their company's domain email address. They're then added to your company, assigned to an organization, and optionally assigned to a team.

## Prerequisites

* You must first notify your company about the new SSO login procedures.
* Verify that your members have Docker Desktop version 4.4.2, or later, installed on their machines.
* If your organization is planning to [enforce SSO](connect/index.md#optional-enforce-sso), members using the Docker CLI are required to [create a Personal Access Token (PAT)](../../for-developers/access-tokens.md) to sign in instead of with a username and password. Docker plans to deprecate signing in to the CLI with a password in the future, so using a PAT will be required to prevent issues with authentication. For more details see the [security announcement](../../security-announcements.md#deprecation-of-password-logins-on-cli-when-sso-enforced).
* Ensure all your Docker users have a valid user on your IdP with the same email address as their Unique Primary Identifier (UPN)
* Confirm that all CI/CD pipelines have replaced their passwords with PATs.
* For your service accounts, add your additional domains or enable it in your IdP.

## What's next?

- Start [configuring SSO](configure/index.md) in Docker
- Explore the [FAQs](../../faqs/single-sign-on/faqs.md)
