---
source_url: https://github.com/docker/docs/blob/main/content/get-started/docker-concepts/building-images/understanding-image-layers.md
revision: 6bce6d72cf3c0adab9f1675340a40f8718a6f5b4
status: ready
license: https://github.com/docker/docs/blob/main/LICENSE

title: Entendendo as camadas de imagem
keywords: conceitos, construção, imagens, contêiner, docker desktop
description: |
  Esta página conceitual ensinará sobre as camadas de imagem de contêiner.
summary: |
  Você já se perguntou como as imagens funcionam?
  Este guia ajudará você a entender as camadas de imagem - os blocos de
  construção fundamentais das imagens de contêiner.
  Você obterá uma compreensão abrangente de como as camadas são criadas,
  empilhadas e utilizadas para garantir contêineres eficientes e otimizados.
weight: 1
aliases:
  - /guides/docker-concepts/building-images/understanding-image-layers/
---

# Entendendo as camadas de imagem

Você já se perguntou como as imagens funcionam?
Este guia ajudará você a entender as camadas de imagem - os blocos de construção
fundamentais das imagens de contêiner.
Você obterá uma compreensão abrangente de como as camadas são criadas,
empilhadas e utilizadas para garantir contêineres eficientes e otimizados.
{: .lead }

<iframe width="895" height="487" src="https://www.youtube.com/embed/wJwqtAkmtQA"
title="Conceitos do Docker: Entendendo as camadas de imagem"
frameborder="0"
allow="accelerometer; autoplay; clipboard-write; encrypted-media;
gyroscope; picture-in-picture; web-share"
referrerpolicy="strict-origin-when-cross-origin"
allowfullscreen></iframe>

## Explicação

Como você aprendeu em
[O que é uma imagem?](../../../comecando/conceitos-do-docker/o-basico/o-que-e-uma-imagem.md),
imagens de contêiner são compostas de camadas.
E cada uma dessas camadas, uma vez criada, é imutável.
Mas o que isso realmente significa?
E como essas camadas são usadas para criar o sistema de arquivos que um
contêiner pode usar?

### Camadas de imagem

Cada camada em uma imagem contém um conjunto de alterações no sistema de
arquivos - adições, exclusões ou modificações.
Vamos dar uma olhada em uma imagem teórica:

1. A primeira camada adiciona comandos básicos e um gerenciador de pacotes, como
   o apt.
2. A segunda camada instala um tempo de execução Python e pip para gerenciamento
   de dependências.
3. A terceira camada copia o arquivo `requirements.txt` específico de uma
   aplicação.
4. A quarta camada instala as dependências específicas dessa aplicação.
5. A quinta camada copia o código fonte da aplicação.

Este exemplo pode ser parecido com:

![Captura de tela do fluxograma mostrando o conceito das camadas da imagem](images/container_image_layers.webp?border=true)

Isso é benéfico porque permite que camadas sejam reutilizadas entre imagens.
Por exemplo, imagine que você queira criar outra aplicação Python.
Devido à disposição em camadas, você pode aproveitar a mesma base Python.
Isso tornará as compilações mais rápidas e reduzirá a quantidade de
armazenamento e largura de banda necessária para distribuir as imagens.
A disposição em camadas da imagem pode ser semelhante à seguinte:

![Captura de tela do fluxograma mostrando os benefícios da sobreposição de imagens](images/container_image_layer_reuse.webp?border=true)

Camadas permitem que você estenda imagens de outras pessoas reutilizando suas
camadas base, permitindo que você adicione apenas os dados que sua aplicação
precisa.

### Empilhando as camadas

A disposição em camadas é possível por causa do armazenamento endereçável por
conteúdo e do sistemas de arquivos de união.
Embora esse seja um assunto técnico, é assim que funciona:

1. Depois que cada camada é baixada, ela é extraída em seu próprio diretório no
   sistema de arquivos da máquina hospedeira.
2. Quando você executa um contêiner de uma imagem, um sistema de arquivos de
   união é criado onde as camadas são empilhadas umas sobre as outras, criando
   uma visualização nova e unificada.
3. Quando o contêiner é iniciado, seu diretório raiz é definido como o local
   deste diretório unificado, usando `chroot`.

Quando o sistema de arquivos de união é criado, além das camadas de imagem, um
diretório é criado especificamente para o contêiner em execução.
Isso permite que o contêiner faça alterações no sistema de arquivos, e também
permite que as camadas de imagem originais permaneçam intocadas.
Isso te habilita a executar vários contêineres da mesma imagem subjacente.

## Experimente

Neste guia prático, você criará novas camadas de imagem manualmente usando o
comando
[`docker container commit`](../../../reference/cli/docker/container/commit.md).
Observe que você raramente criará imagens dessa forma, pois normalmente
[usará um Dockerfile](../../../get-started/docker-concepts/building-images/writing-a-dockerfile.md).
Mas, isso torna mais fácil entender como tudo funciona.

### Crie uma imagem base

Neste primeiro passo, você criará sua própria imagem base que você usará para os
passos seguintes.

1. [Baixe e instale](https://www.docker.com/products/docker-desktop/) o Docker
   Desktop.

2. Em um terminal, execute o seguinte comando para iniciar um novo contêiner:

```shell
docker run --name=base-container -ti ubuntu
```

   Depois que a imagem for baixada e o contêiner for iniciado, você deverá ver
   um novo _prompt_ de _shell_.
   Ele está sendo executado dentro do seu contêiner.
   Ele será parecido com o seguinte (o ID do contêiner pode variar):

```shell
root@d8c5ca119fcd:/#
```

3. Dentro do contêiner, execute o seguinte comando para instalar o Node.js:

```shell
apt update && apt install -y nodejs
```

   Quando esse comando é executado, ele baixa e instala o Node dentro do
   contêiner.
   No contexto do sistema de arquivos de união, essas alterações no sistema de
   arquivos ocorrem dentro do diretório exclusivo desse contêiner.

4. Valide se o Node está instalado, executando o seguinte comando:

```shell
node -e 'console.log("Olá, mundo!")'
```

   Você deve então ver um "Olá, mundo!" aparecer no console.

5. Agora que você tem o Node instalado, você já pode salvar as alterações que
   fez como uma nova camada de imagem, a partir da qual você pode iniciar novos
   contêineres ou construir novas imagens.
   Para fazer isso, você usará o comando
   [`docker container commit`](../../../reference/cli/docker/container/commit.md).
   Execute o seguinte comando em um novo terminal:

```shell
docker container commit -m "Adiciona o Node" base-container node-base
```

6. Visualize as camadas da sua imagem usando o comando `docker image history`:

```shell
docker image history node-base
```

   Você verá uma saída semelhante à seguinte:

```shell
IMAGE          CREATED          CREATED BY                                      SIZE      COMMENT
d5c1fca2cdc4   10 seconds ago   /bin/bash                                       126MB     Adiciona o Node
2b7cc08dcdbb   5 weeks ago      /bin/sh -c #(nop)  CMD ["/bin/bash"]            0B
<missing>      5 weeks ago      /bin/sh -c #(nop) ADD file:07cdbabf782942af0…   69.2MB
<missing>      5 weeks ago      /bin/sh -c #(nop)  LABEL org.opencontainers.…   0B
<missing>      5 weeks ago      /bin/sh -c #(nop)  LABEL org.opencontainers.…   0B
<missing>      5 weeks ago      /bin/sh -c #(nop)  ARG LAUNCHPAD_BUILD_ARCH     0B
<missing>      5 weeks ago      /bin/sh -c #(nop)  ARG RELEASE                  0B
```

   Observe o comentário "Adiciona o Node" na linha superior.
   Esta camada contém a instalação do Node.js que você acabou de fazer.

7. Para provar que sua imagem tem o Node instalado, você pode iniciar um novo
    contêiner usando esta nova imagem:

```shell
docker run node-base node -e "console.log('Olá de novo')"
```

   Com isso, você deve obter uma saída "Olá de novo" no terminal, mostrando que
   o Node foi instalado e está funcionando.

8. Agora que você terminou de criar sua imagem base, você pode remover esse
   contêiner:

```shell
docker rm -f base-container
```

> **Definição da imagem base**
>
> Uma imagem base é uma fundação para construir outras imagens.
> É possível usar qualquer imagem como uma imagem base.
> No entanto, algumas imagens são criadas intencionalmente como blocos de
> construção, fornecendo uma fundação ou ponto de partida para uma aplicação.
>
> Neste exemplo, você provavelmente não implantará esta imagem `node-base`, pois
> ela não faz nada ainda.
> Mas é uma base que você pode usar para outras construções.

### Construa uma imagem de aplicação

Agora que você tem uma imagem base, você pode estender essa imagem para criar
imagens adicionais.

1. Inicie um novo contêiner usando a imagem `node-base` recém-criada:

```shell
docker run --name=app-container -ti node-base
```

2. Dentro deste contêiner, execute o seguinte comando para criar um programa
   Node:

```shell
echo 'console.log("Olá de uma aplicação")' > app.js
```

   Para executar este programa Node, você pode usar o seguinte comando e ver a
   mensagem impressa na tela:

```shell
node app.js
```

3. Em outro terminal, execute o seguinte comando para salvar as alterações deste
   contêiner como uma nova imagem:

```shell
docker container commit -c "CMD node app.js" -m "Adiciona aplicação" app-container sample-app`
```

   Este comando não apenas cria uma nova imagem chamada `sample-app`, mas também
   adiciona configuração adicional à imagem para definir o comando padrão ao
   iniciar um contêiner.
   Neste caso, você está configurando a imagem para executar automaticamente
   `node app.js`.

4. Em um terminal fora do contêiner, execute o seguinte comando para visualizar
   as camadas atualizadas:

```shell
docker image history sample-app
```

   Você verá então uma saída que se parece com a seguinte.
   Observe que o comentário da camada superior tem "Adiciona aplicação" e a
   próxima camada tem "Adiciona o Node":

```shell
IMAGE          CREATED              CREATED BY                                      SIZE      COMMENT
c1502e2ec875   About a minute ago   /bin/bash                                       33B       Adiciona aplicação
5310da79c50a   4 minutes ago        /bin/bash                                       126MB     Adiciona o Node
2b7cc08dcdbb   5 weeks ago          /bin/sh -c #(nop)  CMD ["/bin/bash"]            0B
<missing>      5 weeks ago          /bin/sh -c #(nop) ADD file:07cdbabf782942af0…   69.2MB
<missing>      5 weeks ago          /bin/sh -c #(nop)  LABEL org.opencontainers.…   0B
<missing>      5 weeks ago          /bin/sh -c #(nop)  LABEL org.opencontainers.…   0B
<missing>      5 weeks ago          /bin/sh -c #(nop)  ARG LAUNCHPAD_BUILD_ARCH     0B
<missing>      5 weeks ago          /bin/sh -c #(nop)  ARG RELEASE                  0B
```

5. Por fim, inicie um novo contêiner usando a nova imagem.
   Como você especificou o comando padrão, você pode usar o seguinte comando:

```shell
docker run sample-app
```

   Você deve ver sua saudação aparecer no terminal, vinda do seu programa Node.

6. Agora que você terminou com seus contêineres, você pode removê-los usando o
   seguinte comando:

```shell
docker rm -f app-container
```

## Recursos adicionais

Se você quiser se aprofundar mais nas coisas que aprendeu, confira os seguintes
recursos:

* [`docker image history`](../../../reference/cli/docker/image/history.md)
* [`docker container commit`](../../../reference/cli/docker/container/commit.md)

## Próximos passos

Como sugerido anteriormente, a maioria das construções de imagem não usa
`docker container commit`.
Em vez disso, você usará um Dockerfile que automatiza essas etapas para você.
