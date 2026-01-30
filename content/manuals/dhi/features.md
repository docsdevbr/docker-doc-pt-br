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

source_url: https://github.com/docker/docs/blob/main/content/manuals/dhi/features.md
revision: fe911f240a49b231daaa49cdd16f69b8a0651a27
status: ready

title: Recursos das Imagens Docker Reforçadas
linktitle: Recursos
description: >-
  As Imagens Docker Reforçadas oferecem total transparência, superfície de
  ataque mínima e segurança de nível corporativo para todas as aplicações —
  gratuitas e de código aberto.
weight: 5
aliases:
  - /dhi/features/secure/
  - /dhi/features/integration/
  - /dhi/features/support/
  - /dhi/features/patching/
  - /dhi/features/flexible/
  - /dhi/features/helm/
---

As Imagens Docker Reforçadas (DHI) são imagens de contêineres e aplicações
mínimas, seguras e prontas para produção, mantidas pelo Docker.
Projetadas para reduzir vulnerabilidades e simplificar a conformidade, as DHI se
integram facilmente aos seus fluxos de trabalho existentes baseados em Docker,
com pouca ou nenhuma necessidade de reconfiguração.

A DHI oferece segurança para todos:

- [DHI Gratuita](#dhi-free-features) fornece recursos de segurança essenciais
  disponíveis para todos, sem restrições de licenciamento sob a licença Apache
  2.0.
- [Recursos da assinatura DHI Enterprise](#dhi-enterprise-subscription-features)
  adicionam atualizações de segurança com garantia de SLA, variantes de
  conformidade (como FIPS e STIG), personalização de imagem e Suporte Estendido
  ao Ciclo de Vida (ELS) opcional para cobertura pós-fim de vida útil.

## Recursos gratuitos da DHI

Os principais recursos da DHI são abertos e gratuitos para usar, compartilhar e
desenvolver, sem surpresas de licenciamento, com o respaldo da licença Apache
2.0.

### Segurança por padrão

- Quase zero CVEs: Varreduras e correções contínuas para manter o mínimo de
  vulnerabilidades exploráveis conhecidas, sem compromissos de tempo com SLA
  para pessoas usuárias que não sejam do plano DHI Enterprise.
- Superfície de ataque mínima: Variantes sem distribuição reduzem a superfície
  de ataque em até 95% removendo componentes desnecessários.
- Execução sem privilégios de root: Executado sem privilégios de root por
  padrão, seguindo o princípio do menor privilégio.
- Relatórios de vulnerabilidades transparentes: Cada CVE é visível e avaliado
  usando dados públicos — sem feeds suprimidos ou pontuação proprietária.

### Transparência total

Cada imagem inclui metadados de segurança completos e verificáveis:

- Proveniência SLSA Build Nível 3: Construções verificáveis e resistentes a
  adulteração que atendem aos padrões de segurança da cadeia de suprimentos.
- SBOMs assinados: Lista completa de materiais de software para cada componente.
- Declarações VEX: Documentos da Vulnerability Exploitability eXchange fornecem
  contexto sobre CVEs conhecidos.
- Assinaturas criptográficas: Todas as imagens e metadados são assinados para
  autenticidade.

### Desenvolvido para pessoas desenvolvedoras

- Bases familiares: Construído sobre Alpine e Debian, exigindo alterações
  mínimas para adoção.
- Suporte a glibc e musl: Disponível em ambas as variantes para ampla
  compatibilidade de aplicações.
- Variantes de desenvolvimento e tempo de execução: Use imagens de
  desenvolvimento para compilação e imagens de tempo de execução mínimas para
  produção.
- Compatibilidade imediata: Funciona perfeitamente com fluxos de trabalho Docker
  existentes, pipelines de CI/CD e ferramentas.

### Manutenção contínua

- Aplicação automática de patches: As imagens são reconstruídas e atualizadas
  quando patches de segurança upstream estão disponíveis, sem compromissos de
  tempo com garantia de SLA para pessoas usuárias que não utilizam o plano DHI
  Enterprise.
- Integração com escaneadores: Integração direta com escaneadores e outras
  plataformas de segurança.

### Suporte a Kubernetes e charts Helm

Os charts das Imagens Docker Reforçadas (DHI) são charts Helm fornecidos pela
Docker, construídos a partir de fontes upstream, projetados para compatibilidade
com as Imagens Docker Reforçadas.
Esses charts estão disponíveis como artefatos OCI no catálogo DHI do Docker Hub.
Os charts DHI são rigorosamente testados após a construção para garantir que
funcionem imediatamente com as Imagens Docker Reforçadas.
Isso elimina atritos na migração e reduz a carga de trabalho das pessoas
desenvolvedoras na implementação dos charts, garantindo compatibilidade
perfeita.

Assim como as imagens reforçadas, os charts DHI incorporam múltiplas camadas de
metadados de segurança para garantir transparência e confiança:

- Conformidade com o SLSA Nível 3: Cada gráfico é construído com o sistema SLSA
  Build Nível 3 do Docker, incluindo uma procedência de construção detalhada e
  atendendo aos padrões definidos pelo framework Supply-chain Levels for
  Software Artifacts (SLSA).
- Listas de Materiais de Software (SBOMs): SBOMs abrangentes são fornecidas,
  detalhando todos os componentes referenciados no chart para facilitar o
  gerenciamento de vulnerabilidades e auditorias de conformidade.
- Assinatura criptográfica: Todos os metadados associados são assinados
  criptograficamente pelo Docker, garantindo integridade e autenticidade.
- Configuração reforçada: Os charts referenciam automaticamente Imagens Docker
  Reforçadas, garantindo segurança nas implantações.

## Recursos da assinatura DHI Enterprise

Para organizações com requisitos de segurança rigorosos, demandas regulatórias
ou necessidades operacionais, o DHI Enterprise oferece recursos adicionais.

### Variantes de conformidade {tier="DHI Enterprise"}

- Imagens compatíveis com FIPS: Para setores regulamentados e sistemas
  governamentais.
- Imagens prontas para STIG: Atendem aos requisitos do Guia de Implementação
  Técnica de Segurança do Departamento de Defesa dos EUA (DoD).

### Segurança com SLA garantido {tier="DHI Enterprise"}

- SLA de correção de CVE: SLA de 7 dias para vulnerabilidades críticas e de alta
  gravidade, com compromissos de SLA para outros níveis de gravidade.
- SLA de correção de CVE do ELS: Imagens com Suporte de Ciclo de Vida Estendido
  (ELS) possuem compromissos de SLA para correção de CVE, mesmo após o fim da
  vida útil do produto original.
- Suporte corporativo: Acesso à equipe de suporte do Docker para aplicações de
  missão crítica.

### Personalização e controle {tier="DHI Enterprise"}

- Crie imagens personalizadas: Adicione seus próprios pacotes, ferramentas,
  certificados e configurações.
- Infraestrutura de compilação segura: Personalizações criadas na infraestrutura
  confiável do Docker.
- Cadeia de confiança completa: Imagens personalizadas mantêm a procedência e a
  assinatura criptográfica.
- Atualizações automáticas: Imagens personalizadas são reconstruídas
  automaticamente quando as imagens base são corrigidas.

### Suporte Estendido ao Ciclo de Vida {tier="DHI Enterprise add-on"}

- Cobertura de segurança pós-fim de vida: Continue recebendo correções por anos
  após o término do suporte upstream.
- Conformidade contínua: SBOMs, procedência e assinatura atualizados para
  requisitos de auditoria.
- Continuidade da produção: Mantenha a produção em execução com segurança, sem
  migrações forçadas.

## Saiba mais

- [Explore como as imagens DHI são criadas e muito mais](/dhi/explore/)
- [Comece a usar DHIs](/dhi/get-started/)
- [Entre em contato com a Docker para obter o DHI Enterprise](https://www.docker.com/pricing/contact-sales/)
