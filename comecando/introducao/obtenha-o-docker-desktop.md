---
source_url: https://github.com/docker/docs/blob/main/content/get-started/introduction/get-docker-desktop.md
revision: 50e986c308252f63bb0f9ff5f734f4a167f2fdfd
status: ready
license: https://github.com/docker/docs/blob/main/LICENSE

title: Obtenha o Docker Desktop
keywords: conceitos, contêiner, docker desktop
description: |
  Esta página conceitual ensinará você a baixar o Docker Desktop e instalá-lo no
  Windows, Mac e Linux.
summary: |
  Colocar o Docker Desktop em funcionamento é o primeiro passo crucial para
  pessoas desenvolvedoras que estão mergulhando na conteinerização, oferecendo
  uma interface perfeita e amigável para gerenciar contêineres Docker.
  O Docker Desktop simplifica o processo de construção, compartilhamento e
  execução de aplicações em contêineres, garantindo consistência em diferentes
  ambientes.
weight: 1
aliases:
  - /getting-started/get-docker-desktop/
---

# Obtenha o Docker Desktop

Colocar o Docker Desktop em funcionamento é o primeiro passo crucial para
pessoas desenvolvedoras que estão mergulhando na conteinerização, oferecendo uma
interface perfeita e amigável para gerenciar contêineres Docker.
O Docker Desktop simplifica o processo de construção, compartilhamento e
execução de aplicações em contêineres, garantindo consistência em diferentes
ambientes.

<iframe width="895" height="487" src="https://www.youtube.com/embed/C2bPVhiNU-0"
        title="Conceitos do Docker: Obtenha o Docker Desktop"
        frameborder="0"
        allow="accelerometer; autoplay; clipboard-write; encrypted-media;
          gyroscope; picture-in-picture; web-share"
        referrerpolicy="strict-origin-when-cross-origin"
        allowfullscreen></iframe>

## Explicação

O Docker Desktop é o pacote completo para criar imagens, executar contêineres e
muito mais.
Este guia te guiará pelo processo de instalação, permitindo que você experimente
o Docker Desktop em primeira mão.

> **Termos do Docker Desktop**
> O uso comercial do Docker Desktop em empresas maiores (mais de 250
> funcionários OU mais de US$ 10 milhões em receita anual) requer uma
> [assinatura paga](https://www.docker.com/pricing/?_gl=1*1nyypal*_ga*MTYxMTUxMzkzOS4xNjgzNTM0MTcw*_ga_XJWPQMJYHQ*MTcxNjk4MzU4Mi4xMjE2LjEuMTcxNjk4MzkzNS4xNy4wLjA.).

* Docker Desktop para Mac:
    * [Baixar (Apple Silicon)](https://desktop.docker.com/mac/main/arm64/Docker.dmg?utm_source=docker&utm_medium=webreferral&utm_campaign=docs-driven-download-mac-arm64)
    * [Baixar (Intel)](https://desktop.docker.com/mac/main/amd64/Docker.dmg?utm_source=docker&utm_medium=webreferral&utm_campaign=docs-driven-download-mac-amd64)
    * [Instruções de instalação](../../manuals/desktop/install/mac-install.md)
* Docker Desktop para Windows
    * [Baixar](https://desktop.docker.com/win/main/amd64/Docker%20Desktop%20Installer.exe?utm_source=docker&utm_medium=webreferral&utm_campaign=docs-driven-download-windows)
    * [Instruções de instalação](../../manuals/desktop/install/windows-install.md)
* Docker Desktop para Linux
    * [Instruções de instalação](../../manuals/desktop/install/linux/index.md)

Após a instalação, conclua o processo de configuração e você conseguirá executar
um contêiner do Docker.

## Experimente

Neste guia prático, você verá como executar um contêiner Docker usando o Docker
Desktop.

Siga as instruções para executar um contêiner usando a CLI.

## Execute seu primeiro contêiner

Abra seu terminal CLI e inicie um contêiner executando o comando `docker run`:

```shell
docker run -d -p 8080:80 docker/welcome-to-docker
```

## Acesse o _frontend_

Para este contêiner, o _frontend_ é acessível na porta `8080`.
Para abrir o _site_, visite [http://localhost:8080](http://localhost:8080) no
seu navegador.

![Captura de tela da página inicial do servidor _web_ Nginx, vinda do contêiner em execução](../conceitos-do-docker/o-basico/images/access-the-frontend.webp?border=true)

## Gerencie contêineres usando o Docker Desktop

1. Abra o Docker Desktop e selecione o campo **Containers** na barra lateral
   esquerda;
2. Você pode visualizar informações sobre seu contêiner, incluindo _logs_ e
   arquivos, e até mesmo acessar o _shell_ selecionando a guia **Exec**;
   ![Captura de tela do exec no contêiner em execução no Docker Desktop](images/exec-into-docker-container.webp?border=true)
3. Selecione o campo **Inspect** para obter informações detalhadas sobre o
   contêiner.
   Você pode executar várias ações, como pausar, retomar, iniciar ou parar
   contêineres, ou explorar as guias **Logs**, **Bind mounts**, **Exec**,
   **Files** e **Stats**.
   ![Captura de tela da inspeção do contêiner em execução no Docker Desktop](images/inspecting-container.webp?border=true)

O Docker Desktop simplifica o gerenciamento de contêineres para pessoas
desenvolvedoras ao otimizar a instalação, configuração e compatibilidade de
aplicações em diferentes ambientes, abordando assim os pontos problemáticos de
inconsistências de ambiente e desafios de implantação.

## O que vem a seguir?

Agora que você instalou o Docker Desktop e executou seu primeiro contêiner, é
hora de começar a desenvolver com contêineres.
