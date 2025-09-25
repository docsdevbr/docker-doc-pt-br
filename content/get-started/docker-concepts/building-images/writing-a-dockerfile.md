---
# Copyright (c) 2013-2025 Docker Inc.
# Docker and the Docker logo are trademarks or registered trademarks of Docker,
# Inc. in the United States and/or other countries.
# Docker, Inc. and other parties may also have trademark rights in other terms
# used herein.
#
# Documentation licensed under the Apache License, Version 2.0.
# The original work was translated from English into Brazilian Portuguese.
# https://github.com/docker/docs/blob/main/LICENSE

source_url: https://github.com/docker/docs/blob/main/content/get-started/docker-concepts/building-images/writing-a-dockerfile.md
revision: b38d18578f4e66b186ff209d7234403c5bc32466
status: ready

title: Escrevendo um Dockerfile
keywords: conceitos, construção, imagens, container, docker desktop
description: |
  Esta página conceitual ensinará como criar imagens usando o Dockerfile.
summary: |
  Dominar as práticas do Dockerfile é vital para alavancar a tecnologia de
  contêiner efetivamente, aumentando a confiabilidade da aplicação e dando
  suporte a DevOps e metodologias de CI/CD.
  Neste guia, você aprenderá como escrever um Dockerfile, como definir uma
  imagem base e instruções de configuração, incluindo instalação de programas e
  cópia dos arquivos necessários.
weight: 2
aliases:
 - /guides/docker-concepts/building-images/writing-a-dockerfile/
---
{{< youtube-embed Jx8zoIhiP4c >}}

## Explicação

Um Dockerfile é um documento baseado em texto que é usado para criar uma imagem
de contêiner.
Ele fornece instruções ao construtor de imagens sobre os comandos a serem
executados, arquivos a serem copiados, comando de inicialização e muito mais.

Como exemplo, o Dockerfile a seguir produziria uma aplicação Python pronta para
execução:

```dockerfile
FROM python:3.12
WORKDIR /usr/local/app

# Instala as dependências da aplicação
COPY requirements.txt ./
RUN pip install --no-cache-dir -r requirements.txt

# Copia o código fonte
COPY src ./src
EXPOSE 5000

# Configura o usuário da aplicação para que o contêiner não seja executado como
# usuário root
RUN useradd app
USER app

CMD ["uvicorn", "app.main:app", "--host", "0.0.0.0", "--port", "8080"]
```

### Instruções comuns

Algumas das instruções mais comuns em um `Dockerfile` incluem:

- `FROM <imagem>` - especifica a imagem base que a construção estenderá.
- `WORKDIR <caminho>` - esta instrução especifica o "diretório de trabalho" ou o
  caminho na imagem onde os arquivos serão copiados e os comandos serão
- executados.
- `COPY <caminho-na-maquina-hospedeira> <caminho-na-imagem>` - esta instrução
  informa ao construtor para copiar os arquivos da máquina hospedeira e
  colocá-los na imagem do contêiner.
- `RUN <comando>` - esta instrução informa ao construtor para executar o comando
  especificado.
- `ENV <nome> <valor>` - esta instrução define uma variável de ambiente que um
  contêiner em execução usará.
- `EXPOSE <numero-da-porta>` - esta instrução define a configuração na imagem
  que indica uma porta que a imagem gostaria de expor.
- `USER <usuario-ou-uid>` - esta instrução define o usuário padrão para todas as
  instruções subsequentes.
- `CMD ["<comando>", "<arg1>"]` - esta instrução define o comando padrão que um
  contêiner usando esta imagem executará.


Para ler todas as instruções ou entrar em maiores detalhes, confira a
[referência do Dockerfile](https://docs.docker.com/engine/reference/builder/).

## Experimente

Assim como você viu no exemplo anterior, um Dockerfile normalmente segue estes
passos:

1. Determinar a imagem base
2. Instalar dependências da aplicação
3. Copiar qualquer código fonte e/ou binários relevantes
4. Configurar a imagem final

Neste guia prático rápido, você escreverá um Dockerfile que cria uma aplicação
Node.js simples.
Se você não estiver familiarizado com aplicações baseadas em JavaScript, não se
preocupe.
Isso não é necessário para acompanhar este guia.

### Configuração

[Baixe este arquivo ZIP](https://github.com/docker/getting-started-todo-app/raw/build-image-from-scratch/app.zip)
e extraia o conteúdo em um diretório em sua máquina.

### Criando o Dockerfile

Agora que você tem o projeto, pode criar o `Dockerfile`.

1. [Baixe e instale](https://www.docker.com/products/docker-desktop/) o Docker
   Desktop.

2. Crie um arquivo chamado `Dockerfile` na mesma pasta do arquivo
   `package.json`.

   > **Extensão de arquivo do Dockerfile**
    >
   > É importante notar que o `Dockerfile` _não_ tem extensão de arquivo.
   > Alguns editores adicionarão automaticamente uma extensão ao arquivo (ou
   > reclamarão que ele não tem uma).

3. No `Dockerfile`, defina sua imagem base adicionando a seguinte linha:

    ```dockerfile
    FROM node:20-alpine
    ```

4. Agora, defina o diretório de trabalho usando a instrução `WORKDIR`.
   Isso especificará onde os futuros comandos serão executados e o diretório
   para onde os arquivos serão copiados dentro da imagem do contêiner.

    ```dockerfile
    WORKDIR /app
    ```

5. Copie todos os arquivos do seu projeto na sua máquina para a imagem do
   contêiner usando a instrução `COPY`:

    ```dockerfile
    COPY . .
    ```

6. Instale as dependências da aplicação usando a CLI do `yarn` e o gerenciador
   de pacotes.
   Para fazer isso, execute um comando usando a instrução `RUN`:

    ```dockerfile
    RUN yarn install --production
    ```

7. Por fim, especifique o comando padrão a ser executado usando a instrução
    `CMD`:

    ```dockerfile
    CMD ["node", "./src/index.js"]
    ```
   E com isso, você deve ter o seguinte Dockerfile:


    ```dockerfile
    FROM node:20-alpine
    WORKDIR /app
    COPY . .
    RUN yarn install --production
    CMD ["node", "./src/index.js"]
    ```

> **Este Dockerfile ainda não está pronto para produção**
>
> É importante observar que este Dockerfile ainda _não_ segue todas as práticas
> recomendadas (intencionalmente).
> Ele criará a aplicação, mas as construções não serão tão rápidas, ou as
> imagens tão seguras, quanto poderiam ser.
>
> Continue lendo para saber mais sobre como fazer a imagem maximizar o _cache_
> de construção, executar como um usuário não root e construções em vários
> estágios.

> **Conteinerize novos projetos rapidamente com `docker init`**
>
> O comando `docker init` analisará seu projeto e criará rapidamente um
> `Dockerfile`, um `compose.yaml` e um `.dockerignore`, ajudando você a começar.
> Como aqui você está aprendendo especificamente sobre Dockerfiles, não o usará
> agora.
> Mas, [aprenda mais sobre ele aqui](/engine/reference/commandline/init/).

## Recursos adicionais

Para saber mais sobre como escrever um Dockerfile, visite os seguintes recursos:

* [Referência do Dockerfile](/reference/dockerfile/)
* [Melhores práticas do Dockerfile](/develop/develop-images/dockerfile_best-practices/)
* [Imagens base](/build/building/base-images/)
* [Introdução ao `docker init`](/reference/cli/docker/init/)

## Próximos passos

Agora que você criou um Dockerfile e aprendeu o básico, é hora de aprender sobre
como construir, adicionar _tags_ e enviar as imagens.

{{< button text="Build, tag and publish the Image" url="build-tag-and-publish-an-image" >}}

