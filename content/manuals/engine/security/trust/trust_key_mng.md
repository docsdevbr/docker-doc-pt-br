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

description: Manage keys for content trust
keywords: trust, security, root,  keys, repository
title: Manage keys for content trust
---
Trust for an image tag is managed through the use of keys. Docker's content
trust makes use of five different types of keys:

| Key        | Description |                                                                                                                                                                                                                         
|:-----------|:----------- |
| root key   | Root of content trust for an image tag. When content trust is enabled, you create the root key once. Also known as the offline key, because it should be kept offline. |
| targets    | This key allows you to sign image tags, to manage delegations including delegated keys or permitted delegation paths. Also known as the repository key, since this key determines what tags can be signed into an image repository. |
| snapshot   | This key signs the current collection of image tags, preventing mix and match attacks. |                                                                                                                                         
| timestamp  | This key allows Docker image repositories to have freshness security guarantees without requiring periodic content refreshes on the client's side. |
| delegation | Delegation keys are optional tagging keys and allow you to delegate signing image tags to other publishers without having to share your targets key. |

When doing a `docker push` with Content Trust enabled for the first time, the
root, targets, snapshot, and timestamp keys are generated automatically for
the image repository:

- The root and targets key are generated and stored locally client-side.

- The timestamp and snapshot keys are safely generated and stored in a signing server
	that is deployed alongside the Docker registry. These keys are generated in a backend
	service that isn't directly exposed to the internet and are encrypted at rest. Use the Notary CLI to [manage your snapshot key locally](https://github.com/theupdateframework/notary/blob/master/docs/advanced_usage.md#rotate-keys).

Delegation keys are optional, and not generated as part of the normal `docker`
workflow. They need to be
[manually generated and added to the repository](trust_delegation.md#creating-delegation-keys).

## Choose a passphrase

The passphrases you chose for both the root key and your repository key should
be randomly generated and stored in a password manager. Having the repository key
allows users to sign image tags on a repository. Passphrases are used to encrypt
your keys at rest and ensure that a lost laptop or an unintended backup doesn't
put the private key material at risk.

## Back up your keys

All the Docker trust keys are stored encrypted using the passphrase you provide
on creation. Even so, you should still take care of the location where you back them up.
Good practice is to create two encrypted USB keys.

> [!WARNING]
>
> It is very important that you back up your keys to a safe, secure location.
The loss of the repository key is recoverable, but the loss of the root key is not.

The Docker client stores the keys in the `~/.docker/trust/private` directory.
Before backing them up, you should `tar` them into an archive:

```console
$ umask 077; tar -zcvf private_keys_backup.tar.gz ~/.docker/trust/private; umask 022
```

## Hardware storage and signing

Docker Content Trust can store and sign with root keys from a Yubikey 4. The
Yubikey is prioritized over keys stored in the filesystem. When you initialize a
new repository with content trust, Docker Engine looks for a root key locally. If a
key is not found and the Yubikey 4 exists, Docker Engine creates a root key in the
Yubikey 4. Consult the [Notary documentation](https://github.com/theupdateframework/notary/blob/master/docs/advanced_usage.md#use-a-yubikey)
for more details.

Prior to Docker Engine 1.11, this feature was only in the experimental branch.

## Key loss

> [!WARNING]
>
> If a publisher loses keys it means losing the ability to sign images for the repositories in
question. If you lose a key, send an email to [Docker Hub Support](mailto:hub-support@docker.com).
As a reminder, the loss of a root key is not recoverable.

This loss also requires manual intervention from every consumer that used a signed
tag from this repository prior to the loss.  
Image consumers get the following error for content previously downloaded from the affected repo(s):

```console
Warning: potential malicious behavior - trust data has insufficient signatures for remote repository docker.io/my/image: valid signatures did not meet threshold
```

To correct this, they need to download a new image tag that is signed with
the new key.

## Related information

* [Content trust in Docker](index.md)
* [Automation with content trust](trust_automation.md)
* [Delegations for content trust](trust_delegation.md)
* [Play in a content trust sandbox](trust_sandbox.md)
