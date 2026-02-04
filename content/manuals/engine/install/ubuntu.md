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

source_url: https://github.com/docker/docs/blob/main/content/manuals/engine/install/ubuntu.md
revision: 556eed6f35c59f9b1e12ff159879a990caf66520
status: ready

description: >-
  Impulsione suas aplicações de servidor do lado do cliente com a Docker Engine
  no Ubuntu.
  Este guia detalha os pré-requisitos e vários métodos para instalar a Docker
  Engine no Ubuntu.
keywords: >-
  script de instalação do docker, servidor docker no ubuntu, instalar docker
  engine no ubuntu, instalar docker no servidor ubuntu, docker ce no ubuntu
  22.04, instalar docker ce no ubuntu, instalar docker engine no ubuntu
title: Instale a Docker Engine no Ubuntu
linkTitle: Ubuntu
weight: 10
toc_max: 4
aliases:
- /ee/docker-ee/ubuntu/
- /engine/installation/linux/docker-ce/ubuntu/
- /engine/installation/linux/docker-ee/ubuntu/
- /engine/installation/linux/ubuntu/
- /engine/installation/linux/ubuntulinux/
- /engine/installation/ubuntulinux/
- /install/linux/docker-ce/ubuntu/
- /install/linux/docker-ee/ubuntu/
- /install/linux/ubuntu/
- /installation/ubuntulinux/
- /linux/step_one/
download-url-base: https://download.docker.com/linux/ubuntu
---

Para começar a usar a Docker Engine no Ubuntu, certifique-se de que você
[atende aos pré-requisitos](#pré-requisitos) e, em seguida, siga as
[etapas de instalação](#métodos-de-instalação).

## Pré-requisitos

### Limitações do firewall

> [!WARNING]
>
> Antes de instalar o Docker, certifique-se de considerar as seguintes
> implicações de segurança e incompatibilidades de firewall.

- Se você usa o ufw ou o firewalld para gerenciar as configurações do firewall,
  esteja ciente de que ao expor portas de contêiner usando o Docker, essas
  portas ignoram suas regras de firewall.
  Para obter mais informações, consulte
  [Docker e ufw](/manuals/engine/network/packet-filtering-firewalls.md#docker-and-ufw).
- O Docker é compatível apenas com `iptables-nft` e `iptables-legacy`.
  Regras de firewall criadas com `nft` não são compatíveis com um sistema com o
  Docker instalado.
  Certifique-se de que todos os conjuntos de regras de firewall que você usa
  sejam criados com `iptables` ou `ip6tables`, e que você os adicione à cadeia
  `DOCKER-USER`.
  Consulte
  [Filtragem de pacotes e firewalls](/manuals/engine/network/packet-filtering-firewalls.md).

### Requisitos do sistema operacional

Para instalar a Docker Engine, você precisa da versão de 64 bits de uma destas
versões do Ubuntu:

- Ubuntu Questing 25.10
- Ubuntu Plucky 25.04
- Ubuntu Noble 24.04 (LTS)
- Ubuntu Jammy 22.04 (LTS)

A Docker Engine para Ubuntu é compatível com as arquiteturas x86_64 (ou amd64),
armhf, arm64, s390x e ppc64le (ppc64el).

> [!NOTE]
>
> A instalação em distribuições derivadas do Ubuntu, como o Linux Mint, não é
> oficialmente suportada (embora possa funcionar).

### Desinstale versões antigas

Antes de instalar a Docker Engine, você precisa desinstalar quaisquer pacotes
conflitantes.

Sua distribuição Linux pode fornecer pacotes Docker não oficiais, que podem
entrar em conflito com os pacotes oficiais fornecidos pelo Docker.
Você deve desinstalar esses pacotes antes de instalar a versão oficial da Docker
Engine.

Os pacotes não oficiais a serem desinstalados são:

- `docker.io`
- `docker-compose`
- `docker-compose-v2`
- `docker-doc`
- `podman-docker`

Além disso, a Docker Engine depende do `containerd` e do `runc`.
A Docker Engine agrupa essas dependências em um único pacote: `containerd.io`.
Se você já instalou o `containerd` ou o `runc` anteriormente, desinstale-os para
evitar conflitos com as versões incluídas na Docker Engine.

Execute o seguinte comando para desinstalar todos os pacotes conflitantes:

```console
$ sudo apt remove $(dpkg --get-selections docker.io docker-compose docker-compose-v2 docker-doc podman-docker containerd runc | cut -f1)
```

O `apt` pode informar que você não tem nenhum desses pacotes instalado.

Imagens, contêineres, volumes e redes armazenados em `/var/lib/docker/` não são
removidos automaticamente ao desinstalar o Docker.
Se você deseja começar com uma instalação limpa e prefere remover todos os dados
existentes, leia a seção
[Desinstale a Docker Engine](#desinstale-a-docker-engine).

## Métodos de instalação

Você pode instalar a Docker Engine de diferentes maneiras, dependendo das suas
necessidades:

- A Docker Engine vem incluída no
  [Docker Desktop para Linux](/manuals/desktop/setup/install/linux/_index.md).
  Esta é a maneira mais fácil e rápida de começar.

- Configure e instale a Docker Engine a partir do
  [repositório `apt` do Docker](#instale-usando-o-repositório-apt).

- [Instale-a manualmente](#instale-a-partir-de-um-pacote) e gerencie as
  atualizações manualmente.

- Use um [script de conveniência](#instale-usando-o-script-de-conveniência).
  Recomendado apenas para ambientes de teste e desenvolvimento.

{{% include "engine-license.md" %}}

### Instale usando o repositório `apt`

Antes de instalar a Docker Engine pela primeira vez em uma nova máquina host,
você precisa configurar o repositório `apt` do Docker.
Em seguida, você pode instalar e atualizar o Docker a partir do repositório.

1. Configure o repositório `apt` do Docker.

   ```bash
   # Adicione a chave GPG oficial do Docker:
   sudo apt update
   sudo apt install ca-certificates curl
   sudo install -m 0755 -d /etc/apt/keyrings
   sudo curl -fsSL {{% param "download-url-base" %}}/gpg -o /etc/apt/keyrings/docker.asc
   sudo chmod a+r /etc/apt/keyrings/docker.asc

   # Adicione o repositório às fontes do Apt:
   sudo tee /etc/apt/sources.list.d/docker.sources <<EOF
   Types: deb
   URIs: {{% param "download-url-base" %}}
   Suites: $(. /etc/os-release && echo "${UBUNTU_CODENAME:-$VERSION_CODENAME}")
   Components: stable
   Signed-By: /etc/apt/keyrings/docker.asc
   EOF

   sudo apt update
   ```

2. Instale os pacotes do Docker.

   {{< tabs >}}
   {{< tab name="Versão mais recente" >}}

   Para instalar a versão mais recente, execute:

   ```console
   $ sudo apt install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
   ```

   {{< /tab >}}
   {{< tab name="Versão específica" >}}

   Para instalar uma versão específica da Docker Engine, comece listando as
   versões disponíveis no repositório:

   ```console
   $ apt list --all-versions docker-ce

   docker-ce/noble 5:{{% param "docker_ce_version" %}}-1~ubuntu.24.04~noble <arquitetura>
   docker-ce/noble 5:{{% param "docker_ce_version_prev" %}}-1~ubuntu.24.04~noble <arquitetura>
   ...
   ```

   Selecione e instale a versão desejada:

   ```console
   $ VERSION_STRING=5:{{% param "docker_ce_version" %}}-1~ubuntu.24.04~noble
   $ sudo apt install docker-ce=$VERSION_STRING docker-ce-cli=$VERSION_STRING containerd.io docker-buildx-plugin docker-compose-plugin
   ```

   {{< /tab >}}
   {{< /tabs >}}

   > [!NOTE]
   >
   > O serviço Docker inicia automaticamente após a instalação.
   > Para verificar se o Docker está em execução, use:
   >
   > ```console
   > $ sudo systemctl status docker
   > ```
   >
   > Alguns sistemas podem ter esse comportamento desativado e exigirão uma
   > inicialização manual:
   >
   > ```console
   > $ sudo systemctl start docker
   > ```

3. Verifique se a instalação foi bem-sucedida executando a imagem `hello-world`:

   ```console
   $ sudo docker run hello-world
   ```

   Este comando baixa uma imagem de teste e a executa em um contêiner.
   Quando o contêiner é executado, ele imprime uma mensagem de confirmação e é
   encerrado.

Você instalou e iniciou a Docker Engine com sucesso.

{{% include "root-errors.md" %}}

#### Atualize a Docker Engine

Para atualizar a Docker Engine, siga o passo 2 das
[instruções de instalação](#instale-usando-o-repositório-apt),
escolhendo a nova versão que deseja instalar.

### Instale a partir de um pacote

Se você não puder usar o repositório `apt` do Docker para instalar a Docker
Engine, você pode baixar o arquivo `deb` da sua versão e instalá-lo manualmente.
Você precisará baixar um novo arquivo sempre que quiser atualizar a Docker
Engine.

<!-- markdownlint-disable-next-line -->
1. Acesse [`{{% param "download-url-base" %}}/dists/`]({{% param "download-url-base" %}}/dists/).

2. Selecione sua versão do Ubuntu na lista.

3. Acesse `pool/stable/` e selecione a arquitetura aplicável (`amd64`, `armhf`,
   `arm64` ou `s390x`).

4. Baixe os seguintes arquivos `.deb` para a Docker Engine, CLI, containerd e
   pacotes do Docker Compose:

   - `containerd.io_<versao>_<arquitetura>.deb`
   - `docker-ce_<versao>_<arquitetura>.deb`
   - `docker-ce-cli_<versao>_<arquitetura>.deb`
   - `docker-buildx-plugin_<versao>_<arquitetura>.deb`
   - `docker-compose-plugin_<versao>_<arquitetura>.deb`

5. Instale os pacotes `.deb`.
   Atualize os caminhos no exemplo a seguir para onde você baixou os pacotes do
   Docker.

   ```console
   $ sudo dpkg -i ./containerd.io_<versao>_<arquitetura>.deb \
     ./docker-ce_<versao>_<arquitetura>.deb \
     ./docker-ce-cli_<versao>_<arquitetura>.deb \
     ./docker-buildx-plugin_<versao>_<arquitetura>.deb \
     ./docker-compose-plugin_<versao>_<arquitetura>.deb
   ```

   > [!NOTE]
   >
   > O serviço Docker inicia automaticamente após a instalação.
   > Para verificar se o Docker está em execução, use:
   >
   > ```console
   > $ sudo systemctl status docker
   > ```
   >
   > Alguns sistemas podem ter esse comportamento desativado e exigirão uma
   > inicialização manual:
   >
   > ```console
   > $ sudo systemctl start docker
   > ```

6. Verifique se a instalação foi bem-sucedida executando a imagem `hello-world`:

   ```console
   $ sudo docker run hello-world
   ```

   Este comando baixa uma imagem de teste e a executa em um contêiner.
   Quando o contêiner é executado, ele exibe uma mensagem de confirmação e é
   encerrado.

Você instalou e iniciou a Docker Engine com sucesso.

{{% include "root-errors.md" %}}

#### Atualize a Docker Engine

Para atualizar a Docker Engine, baixe os arquivos de pacote mais recentes e
repita o [procedimento de instalação](#instale-a-partir-de-um-pacote), apontando para
os novos arquivos.

{{% include "install-script.md" %}}

## Desinstale a Docker Engine

1. Desinstale os pacotes Docker Engine, CLI, containerd e Docker Compose:

   ```console
   $ sudo apt purge docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin docker-ce-rootless-extras
   ```

2. Imagens, contêineres, volumes ou arquivos de configuração personalizados em
   seu host não são removidos automaticamente.
   Para excluir todas as imagens, contêineres e volumes:

   ```console
   $ sudo rm -rf /var/lib/docker
   $ sudo rm -rf /var/lib/containerd
   ```

3. Remover a lista de fontes e os keyrings.

   ```console
   $ sudo rm /etc/apt/sources.list.d/docker.sources
   $ sudo rm /etc/apt/keyrings/docker.asc
   ```

Você precisa excluir manualmente quaisquer arquivos de configuração editados.

## Próximos passos

- Continue para [Etapas de pós-instalação para Linux](linux-postinstall.md).
