---
# SPDX-FileCopyrightText: 2013-2026 Docker Inc.
# Docker and the Docker logo are trademarks or registered trademarks of Docker,
# Inc. in the United States and/or other countries.
# Docker, Inc. and other parties may also have trademark rights in other terms
# used herein.
#
# SPDX-License-Identifier: Apache-2.0
# Documentation licensed under the Apache License, Version 2.0.
# The original work was translated from English into Brazilian Portuguese.
# https://github.com/docsdevbr/docker-doc-pt-br/blob/-/LICENSES/Apache-2.0.txt

source_url: https://github.com/docker/docs/blob/main/content/manuals/engine/security/rootless/tips.md
source_revision: 89344f43f19c68ef2d6941de0a5633ff6f1754e5
translation_status: ready

description: Dicas para o modo rootless
keywords: segurança, namespaces, rootless
title: Dicas
weight: 20
---

## Uso avançado

### Daemon

{{< tabs >}}
{{< tab name="Com systemd (altamente recomendado)" >}}

O arquivo de unidade systemd é instalado como
`~/.config/systemd/user/docker.service`.

Use `systemctl --user` para gerenciar o ciclo de vida do daemon:

```console
$ systemctl --user start docker
```

Para iniciar o daemon na inicialização do sistema, habilite o serviço systemd e
o modo persistente:

```console
$ systemctl --user enable docker
$ sudo loginctl enable-linger $(whoami)
```

Iniciar o Docker rootless como um serviço do systemd
(`/etc/systemd/system/docker.service`) não é suportado, mesmo com a diretiva
`User=`.

{{< /tab >}}
{{< tab name="Sem systemd" >}}

Para executar o daemon diretamente sem o systemd, você precisa executar
`dockerd-rootless.sh` em vez de `dockerd`.

As seguintes variáveis de ambiente devem ser definidas:

- `$HOME`: o diretório home.
- `$XDG_RUNTIME_DIR`: um diretório temporário acessível apenas pelo usuário
  esperado, por exemplo, `~/.docker/run`.
  O diretório deve ser removido a cada desligamento do host.
  O diretório pode estar em tmpfs, porém, não deve estar em `/tmp`.
  Localizar este diretório em `/tmp` pode ser vulnerável a ataques TOCTOU.

{{< /tab >}}
{{< /tabs >}}

É importante observar que, em relação aos caminhos de diretório:

- O caminho do socket é definido como `$XDG_RUNTIME_DIR/docker.sock` por padrão.
  `$XDG_RUNTIME_DIR` geralmente é definido como `/run/user/$UID`.
- O diretório de dados é definido como `~/.local/share/docker` por padrão.
  O diretório de dados não deve estar em NFS.
- O diretório de configuração do daemon é definido como `~/.config/docker` por
  padrão.
  Este diretório é diferente de `~/.docker`, que é usado pelo cliente.

### Cliente

A partir da Docker Engine v23.0, `dockerd-rootless-setuptool.sh install`
configura automaticamente a CLI `docker` para usar o contexto `rootless`.

Antes da Docker Engine v23.0, a pessoa usuária precisava especificar
explicitamente o caminho do socket ou o contexto da CLI.

Para especificar o caminho do socket usando `$DOCKER_HOST`:

```console
$ export DOCKER_HOST=unix://$XDG_RUNTIME_DIR/docker.sock
$ docker run -d -p 8080:80 nginx
```

Para especificar o contexto da CLI usando `docker context`:

```console
$ docker context use rootless
rootless
Current context is now "rootless"
$ docker run -d -p 8080:80 nginx
```

## Boas práticas

### Docker rootless no Docker

Para executar o Docker rootless dentro do Docker com privilégios de root, use a
imagem `docker:<versão>-dind-rootless` em vez de `docker:<versão>-dind`.

```console
$ docker run -d --name dind-rootless --privileged docker:25.0-dind-rootless
```

A imagem `docker:<versão>-dind-rootless` é executada como um usuário não root
(UID 1000).
No entanto, `--privileged` é necessário para desabilitar seccomp, AppArmor e
máscaras de montagem.

### Expondo o socket da API do Docker via TCP

Para expor o socket da API do Docker via TCP, você precisa executar
`dockerd-rootless.sh` com
`DOCKERD_ROOTLESS_ROOTLESSKIT_FLAGS="-p 0.0.0.0:2376:2376/tcp"`.

```console
$ DOCKERD_ROOTLESS_ROOTLESSKIT_FLAGS="-p 0.0.0.0:2376:2376/tcp" \
  dockerd-rootless.sh \
  -H tcp://0.0.0.0:2376 \
  --tlsverify --tlscacert=ca.pem --tlscert=cert.pem --tlskey=key.pem
```

### Expondo o socket da API do Docker via SSH

Para expor o socket da API do Docker via SSH, você precisa garantir que
`$DOCKER_HOST` esteja configurado no host remoto.

```console
$ ssh -l <REMOTEUSER> <REMOTEHOST> 'echo $DOCKER_HOST'
unix:///run/user/1001/docker.sock
$ docker -H ssh://<REMOTEUSER>@<REMOTEHOST> run ...
```

### Roteamento de pacotes ping

Em algumas distribuições, o comando `ping` não funciona por padrão.

Adicione `net.ipv4.ping_group_range = 0 2147483647` ao arquivo
`/etc/sysctl.conf` (ou `/etc/sysctl.d`) e execute `sudo sysctl --system` para
permitir o uso do `ping`.

### Expondo portas privilegiadas

Para expor portas privilegiadas (< 1024), defina `CAP_NET_BIND_SERVICE` no
binário `rootlesskit` e reinicie o daemon.

```console
$ sudo setcap cap_net_bind_service=ep $(which rootlesskit)
$ systemctl --user restart docker
```

Ou adicione `net.ipv4.ip_unprivileged_port_start=0` ao arquivo
`/etc/sysctl.conf` (ou `/etc/sysctl.d`) e execute `sudo sysctl --system`.

### Limitando recursos

A limitação de recursos com flags do `docker run` relacionadas a cgroups, como
`--cpus`, `--memory` e `--pids-limit`, é suportada somente ao executar com
cgroup v2 e systemd.
Consulte
[Alterando a versão do cgroup](/manuals/engine/containers/runmetrics.md) para
habilitar o cgroup v2.

Se `docker info` mostrar `none` como `Cgroup Driver`, as condições não foram
satisfeitas.
Quando essas condições não são satisfeitas, o modo rootless ignora os parâmetros
`docker run` relacionados a cgroups.
Consulte
[Limitando recursos sem cgroup](#limitando-recursos-sem-cgroup) para soluções
alternativas.

Se `docker info` mostrar `systemd` como `Cgroup Driver`, as condições foram
satisfeitas.
No entanto, normalmente, apenas os controladores `memory` e `pids` são delegados
a usuários não root por padrão.

```console
$ cat /sys/fs/cgroup/user.slice/user-$(id -u).slice/user@$(id -u).service/cgroup.controllers
memory pids
```

Para permitir a delegação de todos os controladores, você precisa alterar a
configuração do systemd da seguinte forma:

```console
# mkdir -p /etc/systemd/system/user@.service.d
# cat > /etc/systemd/system/user@.service.d/delegate.conf << EOF
[Service]
Delegate=cpu cpuset io memory pids
EOF
# systemctl daemon-reload
```

> [!NOTE]
>
> Delegar `cpuset` requer o systemd 244 ou posterior.

#### Limitando recursos sem cgroup

Mesmo quando o cgroup não está disponível, você ainda pode usar os tradicionais
`ulimit` e [`cpulimit`](https://github.com/opsengine/cpulimit), embora eles
funcionem em nível de processo em vez de nível de contêiner, e possam ser
desativados arbitrariamente pelo processo do contêiner.

Por exemplo:

- Para limitar o uso da CPU a 0,5 núcleo (similar a `docker run --cpus 0.5`):
  `docker run <IMAGE> cpulimit --limit=50 --include-children <COMMAND>`.
- Para limitar o VSZ máximo a 64 MiB (similar a `docker run --memory 64m`):
  `docker run <IMAGE> sh -c "ulimit -v 65536; <COMMAND>"`.
- Para limitar o número máximo de processos a 100 por UID de namespace 2000
  (similar a `docker run --pids-limit=100`):
  `docker run --user 2000 --ulimit nproc=100 <IMAGE> <COMMAND>`.
