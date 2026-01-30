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

source_url: https://github.com/docker/docs/blob/main/content/manuals/dhi/get-started.md
revision: 52e4c9824e133cc83e8f20ee9c33c2d9db0ceaa9
status: ready

linktitle: Início rápido
title: Início rápido das Imagens Docker Reforçadas
description: >-
  Siga um guia de início rápido para explorar e executar uma Imagem Docker
  Reforçada.
weight: 2
keywords: início rápido das imagens docker reforçadas, executar imagem segura
---

Este guia mostra como executar uma Imagem Docker Reforçada (DHI) do zero usando
um exemplo real.
Ao final, você comparará a DHI com uma imagem Docker padrão para entender melhor
as diferenças.
Embora as etapas usem uma imagem específica como exemplo, elas podem ser
aplicadas a qualquer DHI.

> [!NOTE]
>
> As Imagens Docker Reforçadas estão disponíveis gratuitamente para todas as
> pessoas, sem necessidade de assinatura, restrições de uso ou dependência de
> fornecedor.
> Você pode atualizar para uma assinatura DHI Enterprise quando precisar de
> recursos corporativos, como variantes de conformidade com FIPS ou STIG,
> recursos de personalização ou suporte com SLA.

## Passo 1: encontre uma imagem para usar

1. Acesse o catálogo de Imagens Reforçadas no
   [Docker Hub](https://hub.docker.com/hardened-images/catalog).
2. Use a barra de pesquisa ou os filtros para encontrar uma imagem (por exemplo,
   `python`, `node`, `golang`).
   Para este guia, use a imagem do Python como exemplo.
3. Selecione o repositório do Python para visualizar seus detalhes.

Continue para o próximo passo para baixar e executar a imagem.
Para explorar as imagens com mais detalhes, consulte
[Explore as Imagens Reforçadas do Docker](./how-to/explore.md).

## Passo 2: baixe e execute a imagem

Você pode baixar e executar uma imagem DHI como qualquer outra imagem do Docker.
Observe que as Imagens Docker Reforçadas são projetadas para serem minimalistas
e seguras, portanto, podem não incluir todas as ferramentas ou bibliotecas que
você espera em uma imagem típica.
Você pode ver as diferenças típicas em
[Considerações ao adotar DHIs](./how-to/use.md#considerations-when-adopting-dhis).

> [!TIP]
>
> Em cada página de repositório no catálogo de DHIs, você encontrará instruções
> para baixar e analisar a imagem selecionando **Use this image**.

O exemplo a seguir demonstra que você pode executar a imagem Python e executar
um comando Python simples, assim como faria com qualquer outra imagem Docker:

1. Abra um terminal e faça o login no registro de Imagens Docker Reforçadas
   usando suas credenciais do Docker ID.

   ```console
   $ docker login dhi.io
   ```

2. Baixe a imagem:

   ```console
   $ docker pull dhi.io/python:3.13
   ```

3. Execute a imagem para confirmar que tudo funciona:

   ```console
   $ docker run --rm dhi.io/python:3.13 python -c "print('Olá da DHI')"
   ```

   Isso inicia um contêiner a partir da imagem `python:3.13` e executa um script
   Python simples que imprime `Olá da DHI`.

Para obter mais informações sobre como usar imagens, consulte:

- [Use uma Imagem Docker Reforçada](./how-to/use.md) para uso geral.
- [Use no Kubernetes](./how-to/k8s.md) para implantações no Kubernetes.
- [Use um chart do Helm](./how-to/helm.md) para implantações com o Helm.

## Passo 3: compare com outras imagens

Você pode comparar rapidamente DHIs com outras imagens para ver as melhorias de
segurança e as diferenças.
Essa comparação ajuda você a entender o valor de usar imagens reforçadas.

Execute o seguinte comando para ver uma comparação resumida entre a Imagem
Docker Reforçada do Python e a Imagem Docker Oficial não-reforçada do Python do
Docker Hub:

```console
$ docker scout compare dhi.io/python:3.13 \
    --to python:3.13 \
    --platform linux/amd64 \
    --ignore-unchanged \
    2>/dev/null | sed -n '/## Overview/,/^  ## /p' | head -n -1
```

Exemplo de saída:

```plaintext
  ## Overview

                      │                    Analyzed Image                     │               Comparison Image
  ────────────────────┼───────────────────────────────────────────────────────┼───────────────────────────────────────────────
    Target            │  dhi.io/python:3.13                                   │  python:3.13
      digest          │  c215e9da9f84                                         │  7f48e892134c
      tag             │  3.13                                                 │  3.13
      platform        │ linux/amd64                                           │ linux/amd64
      provenance      │ https://github.com/docker-hardened-images/definitions │ https://github.com/docker-library/python.git
                      │  77a629b3d0db035700206c2a4e7ed904e5902ea8             │  3f2d7e4c339ab883455b81a873519f1d0f2cd80a
      vulnerabilities │    0C     0H     0M     0L                            │    0C     1H     5M   141L     2?
                      │           -1     -5   -141     -2                     │
      size            │ 35 MB (-377 MB)                                       │ 412 MB
      packages        │ 80 (-530)                                             │ 610
                      │                                                       │
```

> [!NOTE]
>
> Este é um exemplo de saída.
> Seus resultados podem variar dependendo de novas CVEs descobertas e
> atualizações de imagem.
>
> O Docker mantém quase zero CVEs em suas Imagens Docker Reforçadas.
> Para assinaturas DHI Enterprise, quando novas CVEs são descobertas, elas são
> corrigidas dentro do prazo do SLA líder do setor.
> Saiba mais sobre os
> [recursos de segurança com garantia de SLA](./features.md#sla-backed-security).

Esta comparação mostra que a Imagem Docker Reforçada:

- Remove vulnerabilidades: 1 CVE de alta gravidade, 5 de gravidade média, 141 de
  baixa gravidade e 2 de gravidade não especificada removidas.
- Reduz o tamanho: de 412 MB para 35 MB (redução de 91%).
- Minimiza pacotes: de 610 pacotes para 80 (redução de 87%).

Para obter mais detalhes sobre a comparação de imagens, consulte
[Compare Imagens Docker Reforçadas](./how-to/compare.md).

## Próximos passos

Você baixou e executou sua primeira Imagem Docker Reforçada.
Aqui estão algumas maneiras de continuar:

- [Migre aplicações existentes para DHIs](./migration/migrate-with-ai.md): Use
  o assistente de IA do Docker para atualizar seus Dockerfiles e usar as Imagens
  Docker Reforçadas como base.

- [Inicie um teste gratuito](https://hub.docker.com/hardened-images/start-free-trial)
  para explorar os benefícios de uma assinatura DHI Enterprise, como acesso a
  variantes FIPS e STIG, imagens personalizadas e atualizações com garantia de
  SLA.

- [Espelhe um repositório](./how-to/mirror.md): Após assinar o DHI Enterprise
  ou iniciar um teste gratuito, aprenda como espelhar um repositório DHI para
  habilitar a personalização, acessar variantes de conformidade e obter
  atualizações com garantia de SLA.

- [Verifique DHIs](./how-to/verify.md): Use ferramentas como o
  [Docker Scout](/scout/) ou o Cosign para inspecionar e verificar atestados
  assinados, como SBOMs e procedência.

- [Escaneie DHIs](./how-to/scan.md): Analise a imagem com o Docker Scout ou
  outros scanners para identificar CVEs conhecidos.
