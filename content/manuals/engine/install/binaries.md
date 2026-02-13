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

source_url: https://github.com/docker/docs/blob/main/content/manuals/engine/install/binaries.md
revision: d083617e9d835b3c2300d7952a7e4ced36635adb
status: ready

description: >-
  Aprenda como instalar o Docker como um binário.
  Estas instruções são mais adequadas para fins de teste.
keywords: >-
  binários, instalação, docker, documentação, linux, instalar a docker engine
title: Instale a Docker Engine a partir dos binários
linkTitle: Binários
weight: 80
aliases:
- /engine/installation/binaries/
- /engine/installation/linux/docker-ce/binaries/
- /install/linux/docker-ce/binaries/
- /installation/binaries/
---

> [!IMPORTANT]
>
> Esta página contém informações sobre como instalar o Docker usando binários.
> Estas instruções são mais adequadas para fins de teste.
> Não recomendamos a instalação do Docker usando binários em ambientes de
> produção, pois eles não possuem atualizações de segurança automáticas.
> Os binários do Linux descritos nesta página são vinculados estaticamente, o
> que significa que vulnerabilidades em dependências de tempo de compilação não
> são corrigidas automaticamente por atualizações de segurança da sua
> distribuição Linux.
>
> Atualizar binários também é um pouco mais complexo em comparação com pacotes
> Docker instalados usando um gerenciador de pacotes ou através do Docker
> Desktop, pois requer a atualização manual da versão instalada sempre que
> houver uma nova versão do Docker.
>
> Além disso, binários estáticos podem não incluir todas as funcionalidades
> fornecidas pelos pacotes dinâmicos.
>
> No Windows e Mac, recomendamos que você instale o
> [Docker Desktop](/manuals/desktop/_index.md).
> Para o Linux, recomendamos que você siga as instruções específicas da sua
> distribuição.

Se você deseja experimentar o Docker ou usá-lo em um ambiente de teste, mas não
está em uma plataforma compatível, pode tentar instalar a partir dos binários
estáticos.
Se possível, use pacotes criados para o seu sistema operacional e utilize o
sistema de gerenciamento de pacotes do seu sistema operacional para gerenciar a
instalação e as atualizações do Docker.

Binários estáticos para o daemon do Docker estão disponíveis apenas para Linux
(como `dockerd`) e Windows (como `dockerd.exe`).
Binários estáticos para o cliente Docker estão disponíveis para Linux, Windows e
macOS (como `docker`).

Este tópico aborda a instalação dos binários para Linux, Windows e macOS:

- [Instale os binários do daemon e do cliente no Linux](#instale-os-binários-do-daemon-e-do-cliente-no-linux)
- [Instale os binários do cliente no macOS](#instale-os-binários-do-cliente-no-macos)
- [Instale os binários do servidor e do cliente no Windows](#instale-os-binários-do-servidor-e-do-cliente-no-windows)

## Instale os binários do daemon e do cliente no Linux

### Pré-requisitos

Antes de tentar instalar o Docker a partir dos binários, certifique-se de que
sua máquina host atende aos pré-requisitos:

- Uma instalação de 64 bits.
- Versão 3.10 ou superior do kernel Linux.
  A versão mais recente do kernel disponível para sua plataforma é recomendada.
- `iptables` versão 1.4 ou superior.
- `git` versão 1.7 ou superior.
- Um executável `ps`, geralmente fornecido por `procps` ou um pacote similar.
- [XZ Utils](https://tukaani.org/xz/) 4.9 ou superior.
- Uma hierarquia `cgroupfs`
  [montada corretamente](https://github.com/tianon/cgroupfs-mount/blob/master/cgroupfs-mount);
  um único ponto de montagem `cgroup` abrangente não é suficiente.
  Consulte as issues no Github:
  [#2683](https://github.com/moby/moby/issues/2683),
  [#3485](https://github.com/moby/moby/issues/3485),
  [#4568](https://github.com/moby/moby/issues/4568)).

#### Proteja seu ambiente ao máximo

##### Considerações sobre o sistema operacional

Habilite o SELinux ou o AppArmor, se possível.

Recomenda-se o uso do AppArmor ou do SELinux se sua distribuição Linux for
compatível com algum dos dois.
Isso ajuda a melhorar a segurança e bloqueia certos tipos de explorações.
Consulte a documentação da sua distribuição Linux para obter instruções sobre
como habilitar e configurar o AppArmor ou o SELinux.

> **Aviso de segurança**
>
> Se algum dos mecanismos de segurança estiver habilitado, não o desabilite como
> uma solução alternativa para fazer o Docker ou seus contêineres funcionarem.
> Em vez disso, configure-o corretamente para corrigir quaisquer problemas.

##### Considerações sobre o daemon do Docker

- Habilite os perfis de segurança `seccomp`, se possível.
  Consulte [Habilitando `seccomp` para Docker](../security/seccomp.md).
- Habilite os namespaces de usuário, se possível.
  Consulte as
  [Opções de namespace de usuário do daemon](/reference/cli/dockerd/#daemon-user-namespace-options).

### Instale os binários estáticos

1. Baixe o arquivo binário estático.
   Acesse
   [https://download.docker.com/linux/static/stable/](https://download.docker.com/linux/static/stable/),
   escolha sua plataforma de hardware e baixe o arquivo `.tgz` correspondente à
   versão da Docker Engine que você deseja instalar.

2. Extraia o arquivo usando o utilitário `tar`.
   Os binários `dockerd` e `docker` serão extraídos.

   ```console
   $ tar xzvf /caminho/para/o/<arquivo>.tar.gz
   ```

3. **Opcional**: Mova os binários para um diretório no seu caminho executável,
   como por exemplo, `/usr/bin/`.
   Se você pular esta etapa, deverá fornecer o caminho para o executável ao
   invocar os comandos `docker` ou `dockerd`.

   ```console
   $ sudo cp docker/* /usr/bin/
   ```

4. Inicie o daemon do Docker:

   ```console
   $ sudo dockerd &
   ```

   Se precisar iniciar o daemon com opções adicionais, modifique o comando acima
   de acordo ou crie e edite o arquivo `/etc/docker/daemon.json` para adicionar
   as opções de configuração personalizadas.

5. Verifique se o Docker está instalado corretamente executando a imagem
   `hello-world`.

   ```console
   $ sudo docker run hello-world
   ```

   Este comando baixa uma imagem de teste e a executa em um contêiner.
   Quando o contêiner é executado, ele imprime uma mensagem e é encerrado.

Você instalou e iniciou a Docker Engine com sucesso.

{{% include "root-errors.md" %}}

## Instale os binários do cliente no macOS

> [!NOTE]
>
> As instruções a seguir são mais adequadas para fins de teste.
> O binário para macOS inclui apenas o cliente Docker.
> Ele não inclui o daemon `dockerd` necessário para executar contêineres.
> Portanto, recomendamos que você instale o
> [Docker Desktop](/manuals/desktop/_index.md).

Os binários para Mac também não contêm:

- Um ambiente de execução.
  Você deve configurar um mecanismo funcional em uma máquina virtual ou em uma
  máquina Linux remota.
- Componentes do Docker, como `buildx` e `docker compose`.

Para instalar os binários do cliente, execute os seguintes passos:

1. Baixe o arquivo binário estático.
   Acesse
   [https://download.docker.com/mac/static/stable/](https://download.docker.com/mac/static/stable/)
   e selecione `x86_64` (para Mac com chip Intel) ou `aarch64` (para Mac com
   chip Apple), e então baixe o arquivo `.tgz` correspondente à versão da Docker
   Engine que você deseja instalar.

2. Extraia o arquivo usando o utilitário `tar`.
   O binário `docker` será extraído.

   ```console
   $ tar xzvf /caminho/para/o/<arquivo>.tar.gz
   ```

3. Limpe os atributos estendidos para permitir a execução.

   ```console
   $ sudo xattr -rc docker
   ```

   Agora, ao executar o seguinte comando, você poderá ver as instruções de uso
   da CLI do Docker:

   ```console
   $ docker/docker
   ```

4. **Opcional**: Mova o binário para um diretório no seu caminho de executáveis,
   como por exemplo, `/usr/local/bin/`.
   Se você pular esta etapa, você deve fornecer o caminho para o executável ao
   invocar os comandos `docker` ou `dockerd`.

   ```console
   $ sudo cp docker/docker /usr/local/bin/
   ```

5. Verifique se o Docker está instalado corretamente executando a imagem
   `hello-world`.
   O valor de `<hostname>` é um nome de host ou endereço IP que executa o daemon
   do Docker e é acessível ao cliente.

   ```console
   $ sudo docker -H <hostname> run hello-world
   ```

   Este comando baixa uma imagem de teste e a executa em um contêiner.
   Quando o contêiner é executado, ele imprime uma mensagem e é encerrado.

## Instale os binários do servidor e do cliente no Windows

> [!NOTE]
>
> A seção a seguir descreve como instalar o daemon do Docker no Windows Server,
> que permite executar apenas contêineres do Windows.
> Ao instalar o daemon do Docker no Windows Server, o daemon não contém
> componentes do Docker, como `buildx` e `compose`.
> Se você estiver usando o Windows 10 ou 11, recomendamos que instale o
> [Docker Desktop](/manuals/desktop/_index.md).

Os pacotes binários no Windows incluem `dockerd.exe` e `docker.exe`.
No Windows, esses binários fornecem apenas a capacidade de executar contêineres
nativos do Windows (não contêineres do Linux).

Para instalar os binários do servidor e do cliente, siga estes passos:

1. Baixe o arquivo binário estático.
   Acesse
   [https://download.docker.com/win/static/stable/x86_64](https://download.docker.com/win/static/stable/x86_64)
   e selecione a versão mais recente da lista.

2. Execute os seguintes comandos do PowerShell para instalar e extrair o arquivo
   para a pasta Arquivos de Programas:

   ```powershell
   PS C:\> Expand-Archive /caminho/para/o/<arquivo>.zip -DestinationPath $Env:ProgramFiles
   ```

3. Registre o serviço e inicie a Docker Engine:

   ```powershell
   PS C:\> &$Env:ProgramFiles\Docker\dockerd --register-service
   PS C:\> Start-Service docker
   ```

4. Verifique se o Docker foi instalado corretamente executando a imagem
   `hello-world`.

   ```powershell
   PS C:\> &$Env:ProgramFiles\Docker\docker run hello-world:nanoserver
   ```

   Este comando baixa uma imagem de teste e a executa em um contêiner.
   Quando o contêiner é executado, ele imprime uma mensagem e é encerrado.

## Atualize os binários estáticos

Para atualizar sua instalação manual da Docker Engine, primeiro interrompa
quaisquer processos `dockerd` ou `dockerd.exe` em execução localmente e, em
seguida, siga os passos de instalação regulares para instalar a nova versão
sobre a versão existente.

## Próximos passos

- Continue para [Passos da pós-instalação no Linux](linux-postinstall.md).
