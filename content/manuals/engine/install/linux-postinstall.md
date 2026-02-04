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

source_url: https://github.com/docker/docs/blob/main/content/manuals/engine/install/linux-postinstall.md
revision: f4ac24cacfd7915b18c5eb0257094ebc77f663a4
status: ready

description: >-
  Encontre os passos recomendados para a pós-instalação da Docker Engine para
  pessoas usuárias Linux, incluindo como executar o Docker como um usuário não
  root e muito mais.
keywords: >-
  executar docker sem sudo, executar docker como root, pós-instalação do docker,
  executar docker como usuário não root, como executar docker no linux, como
  iniciar o docker no Linux, executar o docker no linux
title: Etapas de pós-instalação da Docker Engine no Linux
linkTitle: Etapas de pós-instalação
weight: 90
aliases:
- /engine/installation/linux/docker-ee/linux-postinstall/
- /engine/installation/linux/linux-postinstall/
- /install/linux/linux-postinstall/
---

Esses procedimentos opcionais de pós-instalação descrevem como configurar sua
máquina host Linux para funcionar melhor com o Docker.

## Gerencie o Docker como um usuário não root

O daemon do Docker se vincula a um socket Unix, não a uma porta TCP.
Por padrão, é o usuário `root` que possui o socket Unix, e outros usuários só
podem acessá-lo usando `sudo`.
O daemon do Docker sempre é executado como o usuário `root`.

Se você não quiser preceder o comando `docker` com `sudo`, crie um grupo Unix
chamado `docker` e adicione usuários a ele.
Quando o daemon do Docker é iniciado, ele cria um socket Unix acessível aos
membros do grupo `docker`.
Em algumas distribuições Linux, o sistema cria esse grupo automaticamente ao
instalar a Docker Engine usando um gerenciador de pacotes.
Nesse caso, não é necessário criar o grupo manualmente.

<!-- prettier-ignore -->
> [!WARNING]
>
> O grupo `docker` concede privilégios de nível root ao usuário.
> Para detalhes sobre como isso afeta a segurança do seu sistema, consulte
> [Superfície de ataque do daemon do Docker](../security/_index.md#superfície-de-ataque-do-daemon-do-docker).

> [!NOTE]
>
> Para executar o Docker sem privilégios de root, consulte
> [Executar o daemon Docker como um usuário não root (Modo sem root)](../security/rootless.md).

Para criar o grupo `docker` e adicionar seu usuário:

1. Crie o grupo `docker`.

   ```console
   $ sudo groupadd docker
   ```

2. Adicione seu usuário ao grupo `docker`.

   ```console
   $ sudo usermod -aG docker $USER
   ```

3. Saia da sessão e entre novamente para que sua associação ao grupo seja
   reavaliada.

   > Se você estiver executando o Linux em uma máquina virtual, pode ser
   > necessário reiniciar a máquina virtual para que as alterações entrem em
   > vigor.

   Você também pode executar o seguinte comando para ativar as alterações nos
   grupos:

   ```console
   $ newgrp docker
   ```

4. Verifique se você pode executar comandos do `docker` sem `sudo`.

   ```console
   $ docker run hello-world
   ```

   Este comando baixa uma imagem de teste e a executa em um contêiner.
   Quando o contêiner é executado, ele imprime uma mensagem de confirmação e é
   encerrado.

   Se você executou comandos da CLI do Docker usando `sudo` antes de adicionar
   seu usuário ao grupo `docker`, você pode ver o seguinte erro:

   ```text
   WARNING: Error loading config file: /home/user/.docker/config.json -
   stat /home/user/.docker/config.json: permission denied
   ```

   Este erro indica que as configurações de permissão para o diretório
   `~/.docker/` estão incorretas, devido ao uso do comando `sudo` anteriormente.

   Para corrigir esse problema, remova o diretório `~/.docker/` (ele é recriado
   automaticamente, mas quaisquer configurações personalizadas serão perdidas)
   ou altere sua propriedade e permissões usando os seguintes comandos:

   ```console
   $ sudo chown "$USER":"$USER" /home/"$USER"/.docker -R
   $ sudo chmod g+rwx "$HOME/.docker" -R
   ```

## Configure o Docker para iniciar na inicialização com o systemd

Muitas distribuições Linux modernas usam o [systemd](https://systemd.io/) para
gerenciar quais serviços são iniciados quando o sistema é inicializado.
No Debian e no Ubuntu, o serviço Docker é iniciado na inicialização por padrão.
Para iniciar automaticamente o Docker e o containerd na inicialização de outras
distribuições Linux usando o systemd, execute os seguintes comandos:

```console
$ sudo systemctl enable docker.service
$ sudo systemctl enable containerd.service
```

Para interromper esse comportamento, use `disable` em vez disso.

```console
$ sudo systemctl disable docker.service
$ sudo systemctl disable containerd.service
```

Você pode usar arquivos de unidade do systemd para configurar o serviço Docker
na inicialização, por exemplo, para adicionar um proxy HTTP, definir um
diretório ou partição diferente para os arquivos de tempo de execução do Docker
ou outras personalizações.
Para obter um exemplo, consulte
[Configure o daemon para usar um proxy](/manuals/engine/daemon/proxy.md#systemd-unit-file).

## Configure o driver de logging padrão

O Docker fornece [drivers de logging](/manuals/engine/logging/_index.md) para
coletar e visualizar dados de log de todos os contêineres em execução em um
host.
O driver de logging padrão, `json-file`, grava dados de log em arquivos
formatados em JSON no sistema de arquivos do host.
Com o tempo, esses arquivos de log aumentam de tamanho, levando a possível
esgotamento dos recursos de disco.

Para evitar problemas com o uso excessivo de disco para dados de log, considere
uma das seguintes opções:

- Configure o driver de logging `json-file` para ativar a
  [rotação de logs](/manuals/engine/logging/drivers/json-file.md).
- Use um
  [driver de logging alternativo](/manuals/engine/logging/configure.md#configure-the-default-logging-driver)
  como o [driver de logging "local"](/manuals/engine/logging/drivers/local.md)
  que realiza a rotação de logs por padrão.
- Use um driver de logging que envie logs para um agregador de logs remoto.

## Próximos passos

- Consulte o [workshop do Docker](/get-started/workshop/_index.md) para aprender
  como criar uma imagem e executá-la como uma aplicação conteinerizada.
