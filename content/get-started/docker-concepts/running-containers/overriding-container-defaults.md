---
# SPDX-FileCopyrightText: 2013-2026 Docker Inc.
# Docker and the Docker logo are trademarks or registered trademarks of Docker,
# Inc. in the United States and/or other countries.
# Docker, Inc. and other parties may also have trademark rights in other terms
# used herein.
#
# SPDX-License-Identifier: Apache-2.0
# Documentation licensed under the Apache License, Version 2.0.
# The original work was translated from English into Brazilian Portuguese.
# https://github.com/docsdevbr/docker-doc-pt-br/blob/-/LICENSES/Apache-2.0.txt

source_url: https://github.com/docker/docs/blob/main/content/get-started/docker-concepts/running-containers/overriding-container-defaults.md
revision: 0220ef67450476a5e2c18f481f29a3ee1b352f56
status: ready

title: Substituindo as configurações padrão do contêiner
weight: 2
keywords: conceitos, construção, imagens, contêiner, docker desktop
description: >-
  Esta página conceitual ensinará como substituir as configurações padrão do
  contêiner usando o comando `docker run`.
aliases:
 - /guides/docker-concepts/running-containers/overriding-container-defaults/
---

{{< youtube-embed PFszWK3BB8I >}}

## Explicação

Quando um contêiner Docker é iniciado, ele executa uma aplicação ou comando.
O contêiner obtém esse executável (script ou arquivo) da configuração da sua
imagem.
Os contêineres vêm com configurações padrão que geralmente funcionam bem, mas
você pode alterá-las, se necessário.
Esses ajustes ajudam o programa do contêiner a ser executado exatamente da
maneira que você deseja.

Por exemplo, se você tiver um contêiner de banco de dados existente que escuta
na porta padrão e quiser executar uma nova instância do mesmo contêiner de banco
de dados, talvez queira alterar as configurações da porta na qual o novo
contêiner escuta para não haver conflito com o contêiner existente.
Às vezes, você pode querer aumentar a memória disponível para o contêiner se o
programa precisar de mais recursos para lidar com uma carga de trabalho pesada
ou definir as variáveis de ambiente para fornecer detalhes de configuração
específicos que o programa precisa para funcionar corretamente.

O comando `docker run` oferece uma maneira poderosa de substituir esses padrões
e personalizar o comportamento do contêiner de acordo com sua preferência.
O comando oferece várias opções que permitem personalizar o comportamento do
contêiner em tempo real.

Aqui estão algumas maneiras de fazer isso.

### Sobrescrevendo as portas de rede

Às vezes, você pode querer usar instâncias de banco de dados separadas para fins
de desenvolvimento e teste.
Executar essas instâncias de banco de dados na mesma porta pode causar
conflitos.
Você pode usar a opção `-p` no comando `docker run` para mapear as portas do
contêiner para as portas do host, permitindo que você execute várias instâncias
do contêiner sem conflitos.

```console
$ docker run -d -p HOST_PORT:CONTAINER_PORT postgres
```

### Definindo variáveis de ambiente

Esta opção define uma variável de ambiente `foo` dentro do contêiner com o valor
`bar`.

```console
$ docker run -e foo=bar postgres env
```

Você verá uma saída semelhante à seguinte:

```console
HOSTNAME=2042f2e6ebe4
foo=bar
```

> [!TIP]
>
> O arquivo `.env` serve como uma maneira prática de definir variáveis de
> ambiente para seus contêineres Docker sem sobrecarregar a linha de comando com
> inúmeras opções `-e`.
> Para usar um arquivo `.env`, você pode passar a opção `--env-file` com o
> comando `docker run`.
>
> ```console
> $ docker run --env-file .env postgres env
> ```

### Limitando o consumo de recursos do contêiner

Você pode usar as opções `--memory` e `--cpus` com o comando `docker run` para
limitar a quantidade de CPU e memória que um contêiner pode usar.
Por exemplo, você pode definir um limite de memória para o contêiner da API
Python, impedindo que ele consuma recursos excessivos no seu host.
Veja o comando:

```console
$ docker run -e POSTGRES_PASSWORD=secret --memory="512m" --cpus="0.5" postgres
 ```

Este comando limita o uso de memória do contêiner a 512 MB e define a cota de
CPU em 0,5 para meio núcleo.

> **Monitore o uso de recursos em tempo real**
>
> Você pode usar o comando `docker stats` para monitorar o uso de recursos em
> tempo real dos contêineres em execução.
> Isso ajuda a entender se os recursos alocados são suficientes ou se precisam
> de ajustes.

Ao usar efetivamente esses parâmetros do `docker run`, você pode personalizar o
comportamento da sua aplicação conteinerizada para atender às suas necessidades
específicas.

## Experimente

Neste guia prático, você verá como usar o comando `docker run` para substituir
as configurações padrão do contêiner.

1. [Baixe e instale](/get-started/get-docker/) o Docker Desktop.

### Execute várias instâncias do banco de dados Postgres

1. Inicie um contêiner usando a
   [imagem do Postgres](https://hub.docker.com/_/postgres) com o seguinte
   comando:

   ```console
   $ docker run -d -e POSTGRES_PASSWORD=secret -p 5432:5432 postgres
   ```

   Isso iniciará o banco de dados Postgres em segundo plano, escutando na porta
   padrão do contêiner `5432` e mapeada para a porta `5432` na máquina host.

2. Inicie um segundo contêiner Postgres mapeado para uma porta diferente.

   ```console
   $ docker run -d -e POSTGRES_PASSWORD=secret -p 5433:5432 postgres
   ```

   Isso iniciará outro contêiner Postgres em segundo plano, escutando na porta
   padrão do Postgres (5432) no contêiner, mas mapeado para a porta 5433 na
   máquina host.
   Você sobrescreve a porta do host apenas para garantir que este novo contêiner
   não entre em conflito com o contêiner em execução existente.

3. Verifique se ambos os contêineres estão em execução acessando a visualização
   **Containers** no painel do Docker Desktop.

   ![Uma captura de tela do painel do Docker Desktop mostrando as instâncias em execução dos contêineres Postgres](images/running-postgres-containers.webp?border=true)

### Execute um contêiner Postgres em uma rede controlada

Por padrão, os contêineres se conectam automaticamente a uma rede especial
chamada rede bridge quando são executados.
Essa rede bridge atua como uma ponte virtual, permitindo que os contêineres no
mesmo host se comuniquem entre si, mantendo-os isolados do mundo externo e de
outros hosts.
É um ponto de partida conveniente para a maioria das interações entre
contêineres.
No entanto, para cenários específicos, você pode querer mais controle sobre a
configuração da rede.

É aqui que entra a rede personalizada.
Você cria uma rede personalizada passando a flag `--network` com o comando
`docker run`.
Todos os contêineres sem a flag `--network` são conectados à rede bridge padrão.

Siga os passos para ver como conectar um contêiner Postgres a uma rede
personalizada.

1. Crie uma nova rede personalizada usando o seguinte comando:

   ```console
   $ docker network create mynetwork
   ```

2. Verifique a rede executando o seguinte comando:

   ```console
   $ docker network ls
   ```

   Este comando lista todas as redes, incluindo a recém-criada "mynetwork".

3. Conecte o Postgres à rede personalizada usando o seguinte comando:

   ```console
   $ docker run -d -e POSTGRES_PASSWORD=secret -p 5434:5432 --network mynetwork postgres
   ```

   Isso iniciará o contêiner Postgres em segundo plano, mapeado para a porta
   5434 do host e conectado à rede `mynetwork`.
   Você passou o parâmetro `--network` para substituir o padrão do contêiner,
   conectando-o a uma rede Docker personalizada para melhor isolamento e
   comunicação com outros contêineres.
   Você pode usar o comando `docker network inspect` para verificar se o
   contêiner está vinculado a essa nova rede bridge.

   > **Diferença principal entre a rede bridge padrão e redes personalizadas**
   >
   > 1. Resolução de DNS: Por padrão, os contêineres conectados à rede bridge
   >    padrão podem se comunicar entre si, mas apenas por endereço IP (a menos
   >    que você use a opção `--link`, considerada legada).
   >    Isso não é recomendado para uso em produção devido às várias
   >    [deficiências técnicas](/engine/network/drivers/bridge/#differences-between-user-defined-bridges-and-the-default-bridge).
   >    Em uma rede personalizada, os contêineres podem se resolver por nome ou
   >    alias.
   > 2. Isolamento: Todos os contêineres sem um parâmetro `--network`
   >    especificado são conectados à rede bridge padrão, o que pode representar
   >    um risco, já que contêineres não relacionados podem se comunicar entre
   >    si.
   >    O uso de uma rede personalizada fornece uma rede com escopo definido, na
   >    qual apenas os contêineres conectados a essa rede podem se comunicar,
   >    proporcionando, assim, um melhor isolamento.

### Gerencie os recursos

Por padrão, os contêineres não têm limite de uso de recursos.
No entanto, em sistemas compartilhados, é crucial gerenciar os recursos de forma
eficaz.
É importante não deixar que um contêiner em execução consuma muita memória da
máquina host.

É aqui que o comando `docker run` se destaca novamente.
Ele oferece opções como `--memory` e `--cpus` para restringir a quantidade de
CPU e memória que um contêiner pode usar.

```console
$ docker run -d -e POSTGRES_PASSWORD=secret --memory="512m" --cpus=".5" postgres
```

A flag `--cpus` especifica a cota de CPU para o contêiner.
Aqui, ela está definida para meio núcleo de CPU (0,5), enquanto a flag
`--memory` especifica o limite de memória para o contêiner.
Neste caso, está definido para 512 MB.

### Substitua o CMD e o ENTRYPOINT padrão no Docker Compose

Às vezes, pode ser necessário substituir os comandos (`CMD`) ou pontos de
entrada (`ENTRYPOINT`) padrão definidos em uma imagem Docker, especialmente ao
usar o Docker Compose.

1. Crie um arquivo `compose.yml` com o seguinte conteúdo:

   ```yaml
   services:
     postgres:
       image: postgres
       entrypoint: ["docker-entrypoint.sh", "postgres"]
       command: ["-h", "localhost", "-p", "5432"]
       environment:
         POSTGRES_PASSWORD: secret
   ```

   O arquivo Compose define um serviço chamado `postgres` que usa a imagem
   oficial do Postgres, configura um script de ponto de entrada e inicia o
   contêiner com autenticação por senha.

2. Inicie o serviço executando o seguinte comando:

   ```console
   $ docker compose up -d
   ```

   Este comando inicia o serviço Postgres definido no arquivo Docker Compose.

3. Verifique a autenticação com o painel do Docker Desktop.

   Abra o painel do Docker Desktop, selecione o contêiner **Postgres** e
   selecione **Exec** para entrar no shell do contêiner.
   Você pode digitar o seguinte comando para se conectar ao banco de dados
   Postgres:

   ```console
   # psql -U postgres
   ```

   ![Uma captura de tela do painel do Docker Desktop selecionando o contêiner Postgres e entrando em seu shell usando o botão EXEC](images/exec-into-postgres-container.webp?border=true)

   > [!NOTE]
   >
   > A imagem do PostgreSQL configura a autenticação de confiança localmente,
   > portanto, você pode notar que uma senha não é necessária ao conectar-se do
   > localhost (dentro do mesmo contêiner).
   > No entanto, uma senha será necessária se a conexão for feita a partir de um
   > host/contêiner diferente.

### Substitua o CMD e o ENTRYPOINT padrão com `docker run`

Você também pode substituir os padrões usando diretamente o comando `docker run`
com o seguinte comando:

```console
$ docker run -e POSTGRES_PASSWORD=secret postgres docker-entrypoint.sh -h localhost -p 5432
```

Este comando executa um contêiner Postgres, define uma variável de ambiente para
autenticação por senha, substitui os comandos de inicialização padrão e
configura o mapeamento de hostname e porta.

## Recursos adicionais

- [Como definir variáveis de ambiente com o Compose](/compose/how-tos/environment-variables/set-environment-variables/)
- [O que é um contêiner](/get-started/docker-concepts/the-basics/what-is-a-container/)

## Próximos passos

Agora que você aprendeu sobre como sobrescrever as configurações padrão de um
contêiner, é hora de aprender como persistir os dados do contêiner.

{{< button text="Persistindo dados do contêiner" url="persisting-container-data" >}}
