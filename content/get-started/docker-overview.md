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

source_url: https://github.com/docker/docs/blob/main/content/get-started/docker-overview.md
revision: dc95063e4cbe4a7ef46a2dc9f3c0ebb0f910b40f
status: ready

description: >-
  Obtenha uma visão geral aprofundada da plataforma Docker, incluindo para que
  ela pode ser usada, a arquitetura que ela emprega e sua tecnologia subjacente.
keywords: >-
  o que é o docker, daemon docker, por que usar docker, arquitetura docker, para
  que usar docker, cliente docker, para que serve o docker, por que docker, usos
  para o docker, para que o contêiner docker é usado, para que os contêineres
  docker são usados
title: O que é o Docker?
weight: 20
aliases:
 - /introduction/understanding-docker/
 - /engine/userguide/basics/
 - /engine/introduction/understanding-docker/
 - /engine/understanding-docker/
 - /engine/docker-overview/
 - /get-started/overview/
 - /guides/docker-overview/
---

Docker é uma plataforma aberta para desenvolver, distribuir e executar
aplicações.
O Docker permite que você separe suas aplicações da sua infraestrutura para que
você possa entregar software rapidamente.
Com o Docker, você pode gerenciar sua infraestrutura da mesma forma que gerencia
suas aplicações.
Ao aproveitar as metodologias do Docker para distribuir, testar e implantar
código, você pode reduzir significativamente o atraso entre escrever o código e
executá-lo em produção.

## A plataforma Docker

O Docker fornece a capacidade de empacotar e executar uma aplicação em um
ambiente levemente isolado chamado contêiner.
O isolamento e a segurança permitem que você execute muitos contêineres
simultaneamente em uma determinada máquina host.
Os contêineres são leves e contêm tudo o que é necessário para executar a
aplicação, então você não precisa depender do que está instalado na máquina
host.
Você pode compartilhar contêineres enquanto trabalha e ter certeza de que todas
as pessoas com quem você compartilha recebam o mesmo contêiner que funciona da
mesma maneira.

O Docker fornece ferramentas e uma plataforma para gerenciar o ciclo de vida
dos seus contêineres:

- Desenvolva sua aplicação e seus componentes de suporte usando contêineres.
- O contêiner se torna a unidade para distribuir e testar sua aplicação.
- Quando tiver terminado, implante sua aplicação em seu ambiente de produção,
  como um contêiner ou um serviço orquestrado.
  Ele funciona da mesma forma, seja seu ambiente de produção um data center
  local, um provedor de nuvem ou um híbrido dos dois.

## Para que posso usar o Docker?

### Entrega rápida e consistente das suas aplicações

O Docker simplifica o ciclo de vida do desenvolvimento permitindo que as pessoas
desenvolvedoras trabalhem em ambientes padronizados usando contêineres locais
que fornecem suas aplicações e serviços.
Os contêineres são ótimos para fluxos de trabalho de integração contínua e
entrega contínua (CI/CD).

Considere o seguinte cenário de exemplo:

- Suas pessoas desenvolvedoras escrevem código localmente e compartilham seu
  trabalho com suas colegas usando contêineres Docker.
- Elas usam o Docker para enviar suas aplicações para um ambiente de teste e
  executar testes automatizados e manuais.
- Quando as pessoas desenvolvedoras encontram falhas, elas podem corrigi-las no
  ambiente de desenvolvimento e reimplantar as aplicações no ambiente de teste
  para teste e validação.
- Quando os testes estiverem concluídos, enviar a correção ao cliente será tão
  simples quanto enviar a imagem atualizada para o ambiente de produção.

### Implantação e escalonamento responsivos

A plataforma baseada em contêineres do Docker permite cargas de trabalho
altamente portáteis.
Os contêineres do Docker podem ser executados no notebook local de uma pessoa
desenvolvedora, em máquinas físicas ou virtuais em um data center, em provedores
de nuvem ou em uma mistura de ambientes.

A portabilidade e a natureza leve do Docker também facilitam o gerenciamento
dinâmico de cargas de trabalho, aumentando ou reduzindo o escalonamento de
aplicações e serviços conforme as necessidades de negócio, quase em tempo real.

### Executando mais cargas de trabalho no mesmo equipamento

O Docker é leve e rápido.
Ele fornece uma alternativa viável e econômica às máquinas virtuais baseadas em
hipervisor, para que você possa usar mais da capacidade do seu servidor para
atingir seus objetivos de negócios.
O Docker é perfeito para ambientes de alta densidade e para implantações
pequenas e médias, nas quais você precisa fazer mais com menos recursos.

## Arquitetura do Docker

O Docker usa uma arquitetura cliente-servidor.
O cliente Docker fala com o daemon do Docker, que faz o trabalho pesado de
construir, executar e distribuir seus contêineres Docker.
O cliente e o daemon do Docker podem ser executados no mesmo sistema, ou você
pode conectar um cliente Docker a um daemon remoto do Docker.
O cliente e o daemon do Docker se comunicam usando uma API REST, por soquetes
UNIX ou uma interface de rede.
Outro cliente Docker é o Docker Compose, que permite que você trabalhe com
aplicações que consistem em um conjunto de contêineres.

![Diagrama da arquitetura do Docker](images/docker-architecture.webp)

### O daemon do Docker

O daemon do Docker (`dockerd`) escuta as requisições da API do Docker e gerencia
objetos do Docker, como imagens, contêineres, redes e volumes.
Um daemon também pode se comunicar com outros daemons para gerenciar serviços do
Docker.

### O cliente Docker

O cliente Docker (`docker`) é a principal maneira pela qual muitas pessoas
usuárias do Docker interagem com o Docker.
Quando você usa comandos como `docker run`, o cliente envia esses comandos para
o `dockerd`, que os executa.
O comando `docker` usa a API do Docker.
O cliente Docker pode se comunicar com mais de um daemon.

### Docker Desktop

O Docker Desktop é uma aplicação fácil de instalar para seu ambiente Mac,
Windows ou Linux que permite que você crie e compartilhe aplicações e
microsserviços em contêineres.
O Docker Desktop inclui o daemon do Docker (`dockerd`), o cliente Docker
(`docker`), o Docker Compose, o Docker Content Trust, o Kubernetes e o
Credential Helper.
Para obter mais informações, consulte
[Docker Desktop](/manuals/desktop/_index.md).

### Registros do Docker

Um registro do Docker armazena imagens do Docker.
O Docker Hub é um registro público que qualquer pessoa pode usar, e o Docker
procura imagens no Docker Hub por padrão.
Você pode até mesmo executar seu próprio registro privado.

Quando você usa os comandos `docker pull` ou `docker run`, o Docker baixa as
imagens necessárias do seu registro configurado.
Quando você usa o comando `docker push`, o Docker envia sua imagem para o seu
registro configurado.

### Objetos do Docker

Quando você usa o Docker, você está criando e usando imagens, contêineres,
redes, volumes, plugins e outros objetos.
Esta seção é uma breve visão geral de alguns desses objetos.

#### Imagens

Uma imagem é um template somente leitura com instruções para criar um contêiner
Docker.
Frequentemente, uma imagem é baseada em outra imagem, com algumas
personalizações adicionais.
Por exemplo, você pode criar uma imagem baseada na imagem do Ubuntu, mas que
inclua o servidor web Apache e sua aplicação, bem como os detalhes de
configuração necessários para fazer com que sua aplicação seja executada.

Você pode criar suas próprias imagens ou pode usar apenas aquelas criadas por
outras pessoas e publicadas em um registro.
Para construir sua própria imagem, você cria um Dockerfile com uma sintaxe
simples para definir as etapas necessárias para construir a imagem e executá-la.
Cada instrução em um Dockerfile cria uma camada na imagem.
Quando você altera o Dockerfile e reconstrói a imagem, apenas as camadas que
foram alteradas são reconstruídas.
Isso é parte do que torna as imagens tão leves, pequenas e rápidas, quando
comparadas a outras tecnologias de virtualização.

#### Contêineres

Um contêiner é uma instância executável de uma imagem.
Você pode criar, iniciar, parar, mover ou excluir um contêiner usando a API ou a
CLI do Docker.
Você pode conectar um contêiner a uma ou mais redes, anexar armazenamento a ele
ou até mesmo criar uma nova imagem com base em seu estado atual.

Por padrão, um contêiner é relativamente bem isolado de outros contêineres e de
sua máquina host.
Você pode controlar o quão isolados a rede, o armazenamento ou outros
subsistemas subjacentes de um contêiner são de outros contêineres ou da máquina
host.

Um contêiner é definido por sua imagem, bem como por quaisquer opções de
configuração que você fornece a ele ao criá-lo ou iniciá-lo.
Quando um contêiner é removido, quaisquer alterações em seu estado que não
estejam armazenadas em armazenamento persistente desaparecem.

##### Exemplo de comando `docker run`

O comando a seguir executa um contêiner `ubuntu`, se conecta interativamente à
sua sessão de linha de comando local e executa `/bin/bash`.

```console
$ docker run -i -t ubuntu /bin/bash
```

Ao executar este comando, o seguinte acontece (supondo que você esteja usando a
configuração padrão do registro):

1. Se você não tiver a imagem `ubuntu` localmente, o Docker a baixa do seu
   registro configurado, como se você tivesse executado `docker pull ubuntu`
   manualmente.

2. O Docker cria um novo contêiner, como se você tivesse executado um comando
   `docker container create` manualmente.

3. O Docker aloca um sistema de arquivos de leitura e escrita para o contêiner
   como sua camada final.
   Isso permite que um contêiner em execução crie ou modifique arquivos e
   diretórios em seu sistema de arquivos local.

4. O Docker cria uma interface de rede para conectar o contêiner à rede padrão,
   já que você não especificou nenhuma opção de rede.
   Isso inclui atribuir um endereço IP ao contêiner.
   Por padrão, os contêineres podem se conectar a redes externas usando a
   conexão de rede da máquina host.

5. O Docker inicia o contêiner e executa `/bin/bash`.
   Como o contêiner está sendo executado interativamente e conectado ao seu
   terminal (devido às flags `-i` e `-t`), você pode fornecer entrada usando seu
   teclado enquanto o Docker envia a saída para o seu terminal.

6. Quando você executa `exit` para encerrar o comando `/bin/bash`, o contêiner
   para, mas não é removido.
   Você pode iniciá-lo novamente ou removê-lo.

## A tecnologia subjacente

O Docker é escrito na [linguagem de programação Go](https://golang.org/) e
aproveita vários recursos do kernel Linux para fornecer sua funcionalidade.
O Docker usa uma tecnologia chamada `namespaces` para fornecer o espaço de
trabalho isolado chamado contêiner.
Quando você executa um contêiner, o Docker cria um conjunto de namespaces para
esse contêiner.

Esses namespaces fornecem uma camada de isolamento.
Cada aspecto de um contêiner é executado em um namespace separado e seu acesso é
limitado a esse namespace.

## Próximos passos

- [Instale o Docker](/get-started/get-docker.md)
- [Comece a usar o Docker](/get-started/introduction/_index.md)
