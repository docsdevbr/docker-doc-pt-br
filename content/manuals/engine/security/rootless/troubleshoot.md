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

source_url: https://github.com/docker/docs/blob/main/content/manuals/engine/security/rootless/troubleshoot.md
revision: 6e8ef4cf2140a8f48485eb17820e5bb5bd66931c
status: ready

description: Solução de problemas no modo rootless
keywords: segurança, namespaces, rootless, solução de problemas
title: Solução de problemas
weight: 30
---

### Dica específica da distribuição

{{< tabs >}}
{{< tab name="Ubuntu" >}}

- O Ubuntu 24.04 e versões posteriores habilitam namespaces de usuário não
  privilegiados restritos por padrão, o que impede que processos não
  privilegiados criem namespaces de usuário, a menos que um perfil do AppArmor
  esteja configurado para permitir que os programas usem namespaces de usuário
  não privilegiados.

  Se você instalar o `docker-ce-rootless-extras` usando o pacote deb
  (`apt-get install docker-ce-rootless-extras`), o perfil do AppArmor para
  `rootlesskit` já estará incluído no pacote deb `apparmor`.
  Com esse método de instalação, você não precisa adicionar nenhuma configuração
  manual do AppArmor.
  Se você instalar os extras rootless usando o
  [script de instalação](https://get.docker.com/rootless), no entanto, você
  deverá adicionar um perfil do AppArmor para `rootlesskit` manualmente:

  1. Crie e instale o perfil do AppArmor do usuário atualmente conectado:

     ```console
     $ filename=$(echo $HOME/bin/rootlesskit | sed -e 's@^/@@' -e 's@/@.@g')
     $ [ ! -z "${filename}" ] && sudo cat <<EOF > /etc/apparmor.d/${filename}
     abi <abi/4.0>,
     include <tunables/global>

     "$HOME/bin/rootlesskit" flags=(unconfined) {
       userns,

       include if exists <local/${filename}>
     }
     EOF
     ```

  2. Reinicie o AppArmor:

     ```console
     $ systemctl restart apparmor.service
     ```

{{< /tab >}}
{{< tab name="Arch Linux" >}}

- Adicione `kernel.unprivileged_userns_clone=1` ao arquivo `/etc/sysctl.conf`
  (ou `/etc/sysctl.d`) e execute `sudo sysctl --system`.

{{< /tab >}}
{{< tab name="openSUSE e SLES" >}}

- O comando `sudo modprobe ip_tables iptable_mangle iptable_nat iptable_filter`
  é necessário.
  Isso também pode ser necessário em outras distribuições, dependendo da
  configuração.
- Funciona no openSUSE 15 e no SLES 15.

{{< /tab >}}
{{< tab name="CentOS, RHEL e Fedora" >}}

- Para o RHEL 8 e distribuições similares, recomenda-se a instalação do
  `fuse-overlayfs`.
  Execute `sudo dnf install -y fuse-overlayfs`.
  Esta etapa não é necessária no RHEL 9 e distribuições similares.
- Você pode precisar executar `sudo dnf install -y iptables`.

{{< /tab >}}
{{< /tabs >}}

## Limitações conhecidas

- Somente os seguintes drivers de armazenamento são suportados:
  - `overlay2` (somente se estiver executando com o kernel 5.11 ou posterior).
  - `fuse-overlayfs` (somente se estiver executando com o kernel 4.18 ou
    posterior e o `fuse-overlayfs` estiver instalado).
  - `btrfs` (somente se estiver executando com o kernel 4.18 ou posterior ou se
    `~/.local/share/docker` estiver montado com a opção de montagem
    `user_subvol_rm_allowed`).
  - `vfs`.
- O cgroup é suportado somente quando executado com cgroup v2 e systemd.
  Consulte [Limitando recursos](./tips.md#limitando-recursos).
- Os seguintes recursos não são suportados:
  - AppArmor
  - Checkpoint
  - Rede overlay
  - Expor as portas SCTP.
- Para usar o comando `ping`, consulte
  [Roteamento de pacotes ping](./tips.md#roteamento-de-pacotes-ping).
- Para expor portas TCP/UDP privilegiadas (< 1024), consulte
  [Expondo portas privilegiadas](./tips.md#expondo-portas-privilegiadas).
- O `IPAddress` exibido em `docker inspect` está dentro do namespace de rede do
  RootlessKit.
  Isso significa que o endereço IP não é acessível a partir do host sem usar o
  `nsenter` para acessar o namespace de rede.
- A rede do host (`docker run --net=host`) também está dentro do namespace do
  RootlessKit.
- Montagens NFS como "data-root" do Docker não são suportadas.
  Essa limitação não é específica do modo rootless.

## Solução de problemas

### Não é possível instalar com systemd quando o systemd está presente no sistema

``` console
$ dockerd-rootless-setuptool.sh install
[INFO] systemd not detected, dockerd-rootless.sh needs to be started manually:
...
```

`rootlesskit` não consegue detectar o systemd corretamente se você alternar para
o seu usuário via `sudo su`.
Para usuários que não podem ser autenticados, você deve usar o comando
`machinectl`, que faz parte do pacote `systemd-container`.
Após instalar o `systemd-container`, alterne para `meuusuario` com o seguinte
comando:

``` console
$ sudo machinectl shell meuusuario@
```

Onde `meuusuario@` é o nome de usuário desejado e @ representa esta máquina.

### Erros ao iniciar o daemon do Docker

**\[rootlesskit:parent\] error: failed to start the child: fork/exec /proc/self/exe: operation not permitted**

Este erro ocorre principalmente quando o valor de
`/proc/sys/kernel/unprivileged_userns_clone` está definido como 0:

```console
$ cat /proc/sys/kernel/unprivileged_userns_clone
0
```

Para corrigir esse problema, adicione `kernel.unprivileged_userns_clone=1` ao
arquivo `/etc/sysctl.conf` (ou `/etc/sysctl.d`) e execute
`sudo sysctl --system`.

**\[rootlesskit:parent\] error: failed to start the child: fork/exec /proc/self/exe: no space left on device**

Esse erro ocorre principalmente quando o valor de
`/proc/sys/user/max_user_namespaces` é muito pequeno:

```console
$ cat /proc/sys/user/max_user_namespaces
0
```

Para corrigir esse problema, adicione `user.max_user_namespaces=28633` ao
arquivo `/etc/sysctl.conf` (ou `/etc/sysctl.d`) e execute
`sudo sysctl --system`.

**\[rootlesskit:parent\] error: failed to setup UID/GID map: failed to compute uid/gid map: No subuid ranges found for user 1001 ("testuser")**

Este erro ocorre quando `/etc/subuid` e `/etc/subgid` não estão configurados.
Consulte [Pré-requisitos](./_index.md#pré-requisitos).

**could not get XDG_RUNTIME_DIR**

Esse erro ocorre quando a variável de ambiente `$XDG_RUNTIME_DIR` não está
definida.

Em um host sem systemd, você precisa criar um diretório e então definir o
caminho:

```console
$ export XDG_RUNTIME_DIR=$HOME/.docker/xrd
$ rm -rf $XDG_RUNTIME_DIR
$ mkdir -p $XDG_RUNTIME_DIR
$ dockerd-rootless.sh
```

> [!NOTE]
>
> Você deve remover o diretório sempre que fizer logout.

Em um host systemd, faça login no host usando `pam_systemd` (veja abaixo).
O valor é definido automaticamente como `/run/user/$UID` e limpo a cada logout.

**`systemctl --user` fails with "Failed to connect to bus: No such file or directory"**

Esse erro ocorre principalmente quando você alterna do usuário root para um
usuário sem privilégios de root usando o comando `sudo`:

```console
# sudo -iu testuser
$ systemctl --user start docker
Failed to connect to bus: No such file or directory
```

Em vez de `sudo -iu <nome-de-usuario>`, você precisa fazer login usando
`pam_systemd`.
Por exemplo:

- Faça login através do console gráfico.
- `ssh <nome-de-usuario>@localhost`
- `machinectl shell <nome-de-usuario>@`

**The daemon does not start up automatically**

Você precisa executar `sudo loginctl enable-linger $(whoami)` para habilitar a
inicialização automática do daemon.
Consulte [Uso avançado](./tips.md/#uso-avançado).

### Erros do `docker pull`

**docker: failed to register layer: Error processing tar file(exit status 1): lchown &lt;FILE&gt;: invalid argument**

Este erro ocorre quando o número de entradas disponíveis em `/etc/subuid` ou
`/etc/subgid` não é suficiente.
O número de entradas necessárias varia entre as imagens.
No entanto, 65.536 entradas são suficientes para a maioria das imagens.
Consulte [Pré-requisitos](./_index.md#pré-requisitos).

**docker: failed to register layer: ApplyLayer exit status 1 stdout:  stderr: lchown &lt;FILE&gt;: operation not permitted**

Esse erro ocorre principalmente quando `~/.local/share/docker` está localizado
em um sistema de arquivos NFS.

Uma solução alternativa é especificar um diretório `data-root` que não seja NFS
em `~/.config/docker/daemon.json` da seguinte forma:

```json
{"data-root":"/algum-lugar-fora-do-nfs"}
```

### Erros do `docker run`

**docker: Error response from daemon: OCI runtime create failed: ...: read unix @-&gt;/run/systemd/private: read: connection reset by peer: unknown.**

Esse erro ocorre principalmente em hosts com cgroup v2 quando o daemon dbus não
está em execução para o usuário.

```console
$ systemctl --user is-active dbus
inactive

$ docker run hello-world
docker: Error response from daemon: OCI runtime create failed: container_linux.go:380: starting container process caused: process_linux.go:385: applying cgroup configuration for process caused: error while starting unit "docker
-931c15729b5a968ce803784d04c7421f791d87e5ca1891f34387bb9f694c488e.scope" with properties [{Name:Description Value:"libcontainer container 931c15729b5a968ce803784d04c7421f791d87e5ca1891f34387bb9f694c488e"} {Name:Slice Value:"use
r.slice"} {Name:PIDs Value:@au [4529]} {Name:Delegate Value:true} {Name:MemoryAccounting Value:true} {Name:CPUAccounting Value:true} {Name:IOAccounting Value:true} {Name:TasksAccounting Value:true} {Name:DefaultDependencies Val
ue:false}]: read unix @->/run/systemd/private: read: connection reset by peer: unknown.
```

Para corrigir o problema, execute `sudo apt-get install -y dbus-user-session` ou
`sudo dnf install -y dbus-daemon` e faça o login novamente.

Se o erro persistir, tente executar `systemctl --user enable --now dbus` (sem
sudo).

**`--cpus`, `--memory` e `--pids-limit` são ignorados**

Este é o comportamento esperado no modo cgroup v1.
Para usar essas opções, o host precisa ser configurado para habilitar o cgroup
v2.
Para obter mais informações, consulte
[Limitando recursos](./tips.md#limitando-recursos).

### Erros de rede

Esta seção fornece dicas de solução de problemas para redes em modo rootless.

A rede em modo rootless é suportada por meio de drivers de rede e porta no
RootlessKit.
O desempenho e as características da rede dependem da combinação de drivers de
rede e porta que você utiliza.
Se você estiver enfrentando comportamentos inesperados ou problemas de
desempenho relacionados à rede, consulte a tabela a seguir, que mostra as
configurações suportadas pelo RootlessKit e como elas se comparam:

| Driver de rede | Driver de porta | Taxa de transferência de rede | Taxa de transferência de porta | Propagação de IP de origem | Sem SUID | Observação                                                                          |
| -------------- | --------------- | ----------------------------- | ------------------------------ | -------------------------- | -------- | ----------------------------------------------------------------------------------- |
| `slirp4netns`  | `builtin`       | Lenta                         | Rápida ✅                      | ❌                         | ✅       | Padrão em uma configuração típica                                                   |
| `vpnkit`       | `builtin`       | Lenta                         | Rápida ✅                      | ❌                         | ✅       | Padrão quando `slirp4netns` não está instalado                                      |
| `slirp4netns`  | `slirp4netns`   | Lenta                         | Lenta                          | ✅                         | ✅       |                                                                                     |
| `pasta`        | `implicit`      | Lenta                         | Rápida ✅                      | ✅                         | ✅       | Experimental; Requer a versão 2023_12_04 ou posterior do pasta                      |
| `lxc-user-nic` | `builtin`       | Rápida ✅                     | Rápida ✅                      | ❌                         | ❌       | Experimental                                                                        |
| `bypass4netns` | `bypass4netns`  | Rápida ✅                     | Rápida ✅                      | ✅                         | ✅       | **Nota:** Não integrado ao RootlessKit, pois requer um perfil seccomp personalizado |

Para obter informações sobre como solucionar problemas específicos de rede,
consulte:

- [`docker run -p` falha com `cannot expose privileged port`](#docker-run--p-falha-com-cannot-expose-privileged-port)
- [O ping não funciona](#o-ping-não-funciona)
- [O `IPAddress` exibido em `docker inspect` está inacessível](#o-ipaddress-exibido-em-docker-inspect-está-inacessível)
- [`--net=host` não escuta portas no namespace de rede do host](#--nethost-não-escuta-portas-no-namespace-de-rede-do-host)
- [Rede lenta](#rede-lenta)
- [`docker run -p` não propaga endereços IP de origem](#docker-run--p-não-propaga-endereços-ip-de-origem)

#### `docker run -p` falha com `cannot expose privileged port`

O comando `docker run -p` falha com este erro quando uma porta privilegiada
(< 1024) é especificada como a porta do host.

```console
$ docker run -p 80:80 nginx:alpine
docker: Error response from daemon: driver failed programming external connectivity on endpoint focused_swanson (9e2e139a9d8fc92b37c36edfa6214a6e986fa2028c0cc359812f685173fa6df7): Error starting userland proxy: error while calling PortManager.AddPort(): cannot expose privileged port 80, you might need to add "net.ipv4.ip_unprivileged_port_start=0" (currently 1024) to /etc/sysctl.conf, or set CAP_NET_BIND_SERVICE on rootlesskit binary, or choose a larger port number (>= 1024): listen tcp 0.0.0.0:80: bind: permission denied.
```

Quando você se deparar com esse erro, considere usar uma porta não privilegiada.
Por exemplo, 8080 em vez de 80.

```console
$ docker run -p 8080:80 nginx:alpine
```

Para permitir a exposição de portas privilegiadas, consulte
[Expondo portas privilegiadas](./tips.md#expondo-portas-privilegiadas).

#### O ping não funciona

O comando ping não funciona quando `/proc/sys/net/ipv4/ping_group_range` está
definido como `1 0`:

```console
$ cat /proc/sys/net/ipv4/ping_group_range
1       0
```

Para mais detalhes, consulte
[Roteamento de pacotes ping](./tips.md#roteamento-de-pacotes-ping).

#### O `IPAddress` exibido em `docker inspect` está inacessível

Este é o comportamento esperado, já que o daemon está em um namespace dentro do
namespace de rede do RootlessKit.
Use `docker run -p` em vez disso.

#### `--net=host` não escuta portas no namespace de rede do host

Este é o comportamento esperado, já que o daemon está em um namespace dentro do
namespace de rede do RootlessKit.
Use `docker run -p` em vez disso.

#### Rede lenta

O Docker em modo rootless usa o
[slirp4netns](https://github.com/rootless-containers/slirp4netns) como pilha de
rede padrão, caso a versão 0.4.0 ou posterior do slirp4netns esteja instalada.
Se o slirp4netns não estiver instalado, o Docker usa o
[VPNKit](https://github.com/moby/vpnkit).
A instalação do slirp4netns pode melhorar a taxa de transferência da rede.

Para mais informações sobre os drivers de rede do RootlessKit, consulte a
[documentação do RootlessKit](https://github.com/rootless-containers/rootlesskit/blob/v2.0.0/docs/network.md).

Além disso, alterar o valor do MTU também pode melhorar a taxa de transferência.
O valor do MTU pode ser especificado criando o arquivo
`~/.config/systemd/user/docker.service.d/override.conf` com o seguinte conteúdo:

```systemd
[Service]
Environment="DOCKERD_ROOTLESS_ROOTLESSKIT_MTU=<inteiro>"
```

Em seguida, reinicie o daemon:

```console
$ systemctl --user daemon-reload
$ systemctl --user restart docker
```

#### `docker run -p` não propaga endereços IP de origem

Isso ocorre porque o Docker no modo rootless usa o driver de porta `builtin` do
RootlessKit por padrão, que não suporta a propagação de IP de origem.
Para habilitar a propagação de IP de origem, você pode:

- Usar o driver de porta `slirp4netns` do RootlessKit.
- Usar o driver de rede `pasta` do RootlessKit, com o driver de porta
  `implicit`.

O driver de rede `pasta` é experimental, mas oferece melhor desempenho de
throughput em comparação com o driver de porta `slirp4netns`.
O driver `pasta` requer a Docker Engine versão 25.0 ou posterior.

Para alterar a configuração de rede do RootlessKit:

1. Crie um arquivo em `~/.config/systemd/user/docker.service.d/override.conf`.
2. Adicione o seguinte conteúdo, dependendo da configuração que você deseja
   usar:

   - `slirp4netns`

      ```systemd
      [Service]
      Environment="DOCKERD_ROOTLESS_ROOTLESSKIT_NET=slirp4netns"
      Environment="DOCKERD_ROOTLESS_ROOTLESSKIT_PORT_DRIVER=slirp4netns"
      ```

   - Driver de rede `pasta` com driver de porta `implicit`:

      ```systemd
      [Service]
      Environment="DOCKERD_ROOTLESS_ROOTLESSKIT_NET=pasta"
      Environment="DOCKERD_ROOTLESS_ROOTLESSKIT_PORT_DRIVER=implicit"
      ```

3. Reinicie o daemon:

   ```console
   $ systemctl --user daemon-reload
   $ systemctl --user restart docker
   ```

Para obter mais informações sobre as opções de rede do RootlessKit, consulte:

- [Drivers de rede](https://github.com/rootless-containers/rootlesskit/blob/v2.0.0/docs/network.md)
- [Drivers de porta](https://github.com/rootless-containers/rootlesskit/blob/v2.0.0/docs/port.md)

### Dicas para depuração

**Acessando os namespaces do `dockerd`**

O script `dockerd-rootless.sh` executa o `dockerd` em seus próprios namespaces
de usuário, montagem e rede.

Para depuração, você pode acessar os namespaces executando:
`nsenter -U --preserve-credentials -n -m -t $(cat $XDG_RUNTIME_DIR/docker.pid)`.

## Desinstalação

Para remover o serviço systemd do daemon do Docker, execute
`dockerd-rootless-setuptool.sh uninstall`:

```console
$ dockerd-rootless-setuptool.sh uninstall
+ systemctl --user stop docker.service
+ systemctl --user disable docker.service
Removed /home/testuser/.config/systemd/user/default.target.wants/docker.service.
[INFO] Uninstalled docker.service
[INFO] This uninstallation tool does NOT remove Docker binaries and data.
[INFO] To remove data, run: `/usr/bin/rootlesskit rm -rf /home/testuser/.local/share/docker`
```

Remova as variáveis de ambiente PATH e DOCKER_HOST, caso as tenha adicionado ao
arquivo `~/.bashrc`.

Para remover o diretório de dados, execute
`rootlesskit rm -rf ~/.local/share/docker`.

Para remover os binários, remova o pacote `docker-ce-rootless-extras` caso tenha
instalado o Docker com um gerenciador de pacotes.
Se você instalou o Docker com https://get.docker.com/rootless
([Instalação sem pacotes](./_index.md#instalação)), remova os arquivos binários
em `~/bin`:

```console
$ cd ~/bin
$ rm -f containerd containerd-shim containerd-shim-runc-v2 ctr docker docker-init docker-proxy dockerd dockerd-rootless-setuptool.sh dockerd-rootless.sh rootlesskit rootlesskit-docker-proxy runc vpnkit
```
