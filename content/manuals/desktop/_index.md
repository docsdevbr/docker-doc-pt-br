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

source_url: https://github.com/docker/docs/blob/main/content/manuals/desktop/_index.md
revision: befcaf0320bf6caaa13638d02f0f8fc93aa87400
status: ready

title: Docker Desktop
weight: 10
description: >-
  Explore o Docker Desktop, o que ele oferece e seus principais recursos.
  Dê o próximo passo baixando-o ou encontre recursos adicionais.
keywords: >-
  como usar o docker desktop, para que serve o docker desktop, o que o docker
  desktop faz, usando o docker desktop.
params:
  sidebar:
    group: Products
grid:
- title: Instale o Docker Desktop
  description: >-
    Instale o Docker Desktop no [Mac](/desktop/setup/install/mac-install/),
    [Windows](/desktop/setup/install/windows-install/) ou
    [Linux](/desktop/setup/install/linux/).
  icon: download
- title: Aprenda sobre o Docker Desktop
  description: Navegue pelo Docker Desktop.
  icon: feature_search
  link: /desktop/use-desktop/
- title: Explore seus principais recursos
  description: >-
    Encontre informações sobre [Rede](/desktop/features/networking/),
    [Docker VMM](/desktop/features/vmm/), [WSL](/desktop/features/wsl/) e muito
    mais.
  icon: category
- title: Veja as notas de lançamento
  description: Saiba mais sobre novos recursos, melhorias e correções de bugs.
  icon: note_add
  link: /desktop/release-notes/
- title: Navegue pelas perguntas frequentes comuns
  description: >-
    Explore as perguntas frequentes gerais ou as perguntas frequentes para
    plataformas específicas.
  icon: help
  link: /desktop/troubleshoot-and-support/faqs/general/
- title: Dê feedback
  description: >-
    Forneça feedback sobre o Docker Desktop ou sobre os recursos do Docker
    Desktop.
  icon: sms
  link: /desktop/troubleshoot-and-support/feedback/
aliases:
- /desktop/opensource/
- /docker-for-mac/dashboard/
- /docker-for-mac/opensource/
- /docker-for-windows/dashboard/
- /docker-for-windows/opensource/
---

O Docker Desktop é uma aplicação de instalação com um clique para seu ambiente
Mac, Linux ou Windows que permite criar, compartilhar e executar aplicações e
microsserviços conteinerizados.

Ele oferece uma interface gráfica de pessoa usuária (GUI) intuitiva que permite
gerenciar seus contêineres, aplicações e imagens diretamente da sua máquina.

O Docker Desktop reduz o tempo gasto em configurações complexas, para que você
possa se concentrar em escrever código.
Ele cuida do mapeamento de portas, das configurações do sistema de arquivos e de
outras configurações padrão, além de ser atualizado regularmente com correções
de bugs e atualizações de segurança.

O Docker Desktop se integra às suas ferramentas e linguagens de desenvolvimento
preferidas e oferece acesso a um vasto ecossistema de imagens e modelos
confiáveis por meio do Docker Hub.
Isso permite que os times acelerem o desenvolvimento, automatizem contruções,
habilitem fluxos de trabalho de CI/CD e colaborem com segurança por meio de
repositórios compartilhados.

## Principais recursos

- Capacidade de conteinerizar e compartilhar qualquer aplicação em qualquer
  plataforma de nuvem, em múltiplas linguagens e frameworks.
- Instalação e configuração rápidas de um ambiente de desenvolvimento Docker
  completo.
- Inclui a versão mais recente do Kubernetes.
- No Windows, a capacidade de alternar entre contêineres Linux e Windows para
  criar aplicações.
- Desempenho rápido e confiável com virtualização nativa do Windows Hyper-V.
- Capacidade de trabalhar nativamente no Linux através do WSL 2 em máquinas
  Windows.
- Montagem de volumes para código e dados, incluindo notificações de alterações
  de arquivos e fácil acesso a contêineres em execução na rede localhost.

## Produtos no Docker Desktop

- [Catálogo e Kit de Ferramentas Docker MCP](/manuals/ai/mcp-catalog-and-toolkit/_index.md)
- [Docker Model Runner](/manuals/ai/model-runner/_index.md)
- [Ask Gordon](/manuals/ai/gordon/_index.md)
- [Docker Offload](/manuals/offload/_index.md)
- [Docker Engine](/manuals/engine/_index.md)
- Cliente CLI do Docker
- [Docker Build](/manuals/build/_index.md)
- [Docker Compose](/manuals/compose/_index.md)
- [Docker Scout](../scout/_index.md)
- [Kubernetes](https://github.com/kubernetes/kubernetes/)

## Próximos passos

{{< grid >}}
