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

title: Interacting with Kubernetes from an extension
linkTitle: Interacting with Kubernetes
description: How to connect to a Kubernetes cluster from an extension
keywords: Docker, Extensions, sdk, Kubernetes
aliases:
 - /desktop/extensions-sdk/dev/kubernetes/
 - /desktop/extensions-sdk/guides/kubernetes/
---
The Extensions SDK does not provide any API methods to directly interact with the Docker Desktop managed Kubernetes cluster or any other created using other tools such as KinD. However, this page provides a way for you to use other SDK APIs to interact indirectly with a Kubernetes cluster from your extension.

To request an API that directly interacts with Docker Desktop-managed Kubernetes, you can upvote [this issue](https://github.com/docker/extensions-sdk/issues/181) in the Extensions SDK GitHub repository.

## Prerequisites

### Turn on Kubernetes

You can use the built-in Kubernetes in Docker Desktop to start a Kubernetes single-node cluster.
A `kubeconfig` file is used to configure access to Kubernetes when used in conjunction with the `kubectl` command-line tool, or other clients.
Docker Desktop conveniently provides the user with a local preconfigured `kubeconfig` file and `kubectl` command within the user’s home area. It is a convenient way to fast-tracking access for those looking to leverage Kubernetes from Docker Desktop.

## Ship the `kubectl` as part of the extension

If your extension needs to interact with Kubernetes clusters, it is recommended that you include the `kubectl` command line tool as part of your extension. By doing this, users who install your extension get `kubectl` installed on their host.

To find out how to ship the `kubectl` command line tool for multiple platforms as part of your Docker Extension image, see [Build multi-arch extensions](../extensions/multi-arch.md#adding-multi-arch-binaries).

## Examples

The following code snippets have been put together in the [Kubernetes Sample Extension](https://github.com/docker/extensions-sdk/tree/main/samples/kubernetes-sample-extension). It shows how to interact with a Kubernetes cluster by shipping the `kubectl` command-line tool.

### Check the Kubernetes API server is reachable

Once the `kubectl` command-line tool is added to the extension image in the `Dockerfile`, and defined in the `metadata.json`, the Extensions framework deploys `kubectl` to the users' host when the extension is installed.

You can use the JS API `ddClient.extension.host?.cli.exec` to issue `kubectl` commands to, for instance, check whether the Kubernetes API server is reachable given a specific context:

```typescript
const output = await ddClient.extension.host?.cli.exec("kubectl", [
  "cluster-info",
  "--request-timeout",
  "2s",
  "--context",
  "docker-desktop",
]);
```

### List Kubernetes contexts

```typescript
const output = await ddClient.extension.host?.cli.exec("kubectl", [
  "config",
  "view",
  "-o",
  "jsonpath='{.contexts}'",
]);
```

### List Kubernetes namespaces

```typescript
const output = await ddClient.extension.host?.cli.exec("kubectl", [
  "get",
  "namespaces",
  "--no-headers",
  "-o",
  'custom-columns=":metadata.name"',
  "--context",
  "docker-desktop",
]);
```

## Persisting the kubeconfig file

Below there are different ways to persist and read the `kubeconfig` file from the host filesystem. Users can add, edit, or remove Kubernetes context to the `kubeconfig` file at any time.

> Warning
>
> The `kubeconfig` file is very sensitive and if found can give an attacker administrative access to the Kubernetes Cluster.

### Extension's backend container

If you need your extension to persist the `kubeconfig` file after it's been read, you can have a backend container that exposes an HTTP POST endpoint to store the content of the file either in memory or somewhere within the container filesystem. This way, if the user navigates out of the extension to another part of Docker Desktop and then comes back, you don't need to read the `kubeconfig` file again.

```typescript
export const updateKubeconfig = async () => {
  const kubeConfig = await ddClient.extension.host?.cli.exec("kubectl", [
    "config",
    "view",
    "--raw",
    "--minify",
    "--context",
    "docker-desktop",
  ]);
  if (kubeConfig?.stderr) {
    console.log("error", kubeConfig?.stderr);
    return false;
  }

  // call backend container to store the kubeconfig retrieved into the container's memory or filesystem
  try {
    await ddClient.extension.vm?.service?.post("/store-kube-config", {
      data: kubeConfig?.stdout,
    });
  } catch (err) {
    console.log("error", JSON.stringify(err));
  }
};
```

### Docker volume

Volumes are the preferred mechanism for persisting data generated by and used by Docker containers. You can make use of them to persist the `kubeconfig` file.
By persisting the `kubeconfig` in a volume you won't need to read the `kubeconfig` file again when the extension pane closes. This makes it ideal for persisting data when navigating out of the extension to other parts of Docker Desktop.

```typescript
const kubeConfig = await ddClient.extension.host?.cli.exec("kubectl", [
  "config",
  "view",
  "--raw",
  "--minify",
  "--context",
  "docker-desktop",
]);
if (kubeConfig?.stderr) {
  console.log("error", kubeConfig?.stderr);
  return false;
}

await ddClient.docker.cli.exec("run", [
  "--rm",
  "-v",
  "my-vol:/tmp",
  "alpine",
  "/bin/sh",
  "-c",
  `"touch /tmp/.kube/config && echo '${kubeConfig?.stdout}' > /tmp/.kube/config"`,
]);
```

### Extension's `localStorage`

`localStorage` is one of the mechanisms of a browser's web storage. It allows users to save data as key-value pairs in the browser for later use.
`localStorage` does not clear data when the browser (the extension pane) closes. This makes it ideal for persisting data when navigating out of the extension to other parts of Docker Desktop.

```typescript
localStorage.setItem("kubeconfig", kubeConfig);
```

```typescript
localStorage.getItem("kubeconfig");
```
