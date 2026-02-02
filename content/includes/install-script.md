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

source_url: https://github.com/docker/docs/blob/main/content/includes/install-script.md
revision: 2a483c25468533e3b377b323f01f4854dd492628
status: ready
---

### Instale usando o script de conveniência

O Docker fornece um script de conveniência em
[https://get.docker.com/](https://get.docker.com/) para instalar o Docker em
ambientes de desenvolvimento de forma não interativa.
O script de conveniência não é recomendado para ambientes de produção, mas é
útil para criar um script de provisionamento personalizado para suas
necessidades.
Consulte também as etapas de
[instalação usando o repositório](#install-using-the-repository) para saber mais
sobre as etapas de instalação usando o repositório de pacotes.
O código-fonte do script é de código aberto e você pode encontrá-lo no
[repositório `docker-install` no GitHub](https://github.com/docker/docker-install).

<!-- prettier-ignore -->
Sempre examine os scripts baixados da internet antes de executá-los localmente.
Antes de instalar, familiarize-se com os riscos e limitações potenciais do
script de conveniência:

- O script requer privilégios de `root` ou `sudo` para ser executado.
- O script tenta detectar sua distribuição e versão do Linux e configurar seu
  sistema de gerenciamento de pacotes para você.
- O script não permite personalizar a maioria dos parâmetros de instalação.
- O script instala dependências e recomendações sem pedir confirmação.
  Isso pode instalar muitos pacotes, dependendo da configuração atual da sua
  máquina host.
- Por padrão, o script instala a versão estável mais recente do Docker,
  containerd e runc.
  Ao usar este script para provisionar uma máquina, isso pode resultar em
  atualizações inesperadas de versões principais do Docker.
  Sempre teste as atualizações em um ambiente de teste antes de implantá-las em
  seus sistemas de produção.
- O script não foi projetado para atualizar uma instalação existente do Docker.
  Ao usar o script para atualizar uma instalação existente, as dependências
  podem não ser atualizadas para a versão esperada, resultando em versões
  desatualizadas.

> [!TIP]
>
> Visualize as etapas do script antes de executá-lo.
> Você pode executar o script com a opção `--dry-run` para saber quais etapas o
> script executará quando invocado:
>
> ```console
> $ curl -fsSL https://get.docker.com -o get-docker.sh
> $ sudo sh ./get-docker.sh --dry-run
> ```

Este exemplo baixa o script de
[https://get.docker.com/](https://get.docker.com/) e o executa para instalar a
versão estável mais recente do Docker no Linux:

```console
$ curl -fsSL https://get.docker.com -o get-docker.sh
$ sudo sh get-docker.sh
Executing docker install script, commit: 7cae5f8b0decc17d6571f9f52eb840fbc13b2737
<...>
```

Você instalou e iniciou a Docker Engine com sucesso.
O serviço `docker` inicia automaticamente em distribuições baseadas em Debian.
Em distribuições baseadas em `RPM`, como CentOS, Fedora, RHEL ou SLES, você
precisa iniciá-lo manualmente usando o comando `systemctl` ou `service`
apropriado.
Como a mensagem indica, usuários sem privilégios de root não podem executar
comandos do Docker por padrão.

> **Usar o Docker como um usuário sem privilégios ou instalar no modo
> sem root?**
>
> O script de instalação requer privilégios de `root` ou `sudo` para instalar e
> usar o Docker.
> Se você deseja conceder acesso ao Docker a usuários sem privilégios de root,
> consulte as etapas de
> [pós-instalação para Linux](/engine/install/linux-postinstall/#manage-docker-as-a-non-root-user).
> Você também pode instalar o Docker sem privilégios de `root` ou configurá-lo
> para ser executado no modo sem root.
> Para obter instruções sobre como executar o Docker no modo sem root, consulte
> [execute o daemon do Docker como um usuário não root (modo sem root)](/engine/security/rootless/).

#### Instale versões prévias

O Docker também fornece um script de conveniência em
[https://test.docker.com/](https://test.docker.com/) para instalar versões
prévias do Docker no Linux.
Este script é equivalente ao script em `get.docker.com`, mas configura seu
gerenciador de pacotes para usar o canal de teste do repositório de pacotes do
Docker.
O canal de teste inclui versões estáveis e prévias (versões beta, versões
candidatas a lançamento) do Docker.
Use este script para obter acesso antecipado a novos lançamentos e avaliá-los em
um ambiente de teste antes que sejam lançados como estáveis.

Para instalar a versão mais recente do Docker no Linux a partir do canal de
teste, execute:

```console
$ curl -fsSL https://test.docker.com -o test-docker.sh
$ sudo sh test-docker.sh
```

#### Atualize o Docker após usar o script de conveniência

Se você instalou o Docker usando o script de conveniência, você deve atualizá-lo
usando seu gerenciador de pacotes diretamente.
Não há vantagem em executar o script de conveniência novamente.
Executá-lo novamente pode causar problemas se ele tentar reinstalar repositórios
que já existem na máquina host.
