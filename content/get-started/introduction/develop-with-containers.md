---
# Copyright (c) 2013-2025 Docker Inc.
# Docker and the Docker logo are trademarks or registered trademarks of Docker,
# Inc. in the United States and/or other countries.
# Docker, Inc. and other parties may also have trademark rights in other terms
# used herein.
#
# Documentation licensed under the Apache License, Version 2.0.
# The original work was translated from English into Brazilian Portuguese.
# https://github.com/docker/docs/blob/-/LICENSE

source_url: https://github.com/docker/docs/blob/main/content/get-started/introduction/develop-with-containers.md
revision: 29e9c2d8c4c504412d677a779610dc6749da0df6
status: ready

title: Desenvolva com contêineres
keywords: conceitos, construção, imagens, contêiner, docker desktop
description: Esta página conceitual ensinará como desenvolver com contêineres.
summary: >-
  Aprenda a executar seu primeiro contêiner, ganhando experiência prática com os
  recursos poderosos do Docker.
  Abordaremos como fazer alterações em tempo real no código de back-end e
  front-end dentro do ambiente em contêiner, garantindo integração e testes
  perfeitos.
weight: 2
aliases:
 - /guides/getting-started/develop-with-containers/
---

{{< youtube-embed D0SDBrS3t9I >}}

## Explicação

Agora que você instalou o Docker Desktop, já pode fazer algum desenvolvimento de
aplicação.
Especificamente, você fará o seguinte:

1. Clonar e iniciar um projeto de desenvolvimento;
2. Fazer alterações no back-end e front-end;
3. Ver as alterações imediatamente.

## Experimente

Neste guia prático, você aprenderá como desenvolver com contêineres.

## Inicie o projeto

1. Para começar, clone ou
   [baixe o projeto como um arquivo ZIP para sua máquina local](https://github.com/docker/getting-started-todo-app/archive/refs/heads/main.zip).

   ```console
   $ git clone https://github.com/docker/getting-started-todo-app
   ```

   E depois que o projeto for clonado, navegue até o novo diretório criado pelo
   comando:

   ```console
   $ cd getting-started-todo-app
   ```

2. Depois de ter o projeto, inicie o ambiente de desenvolvimento usando o Docker
   Compose.

   Para iniciar o projeto usando a CLI, execute o seguinte comando:

   ```console
   $ docker compose watch
   ```

   Você verá uma saída que mostra imagens de contêineres sendo baixadas,
   contêineres iniciando e mais.
   Não se preocupe se você não entender tudo neste ponto.
   Mas, dentro de um momento ou dois, as coisas devem se estabilizar e terminar.

3. Abra seu navegador em [http://localhost](http://localhost) para ver a
   aplicação instalada e funcionando.
   Pode levar alguns minutos para a aplicação ser executada.
   A aplicação é uma aplicação de tarefas simples, então sinta-se à vontade para
   adicionar um ou dois itens, marcar alguns como concluídos ou até mesmo
   excluir um item.

   ![Captura de tela da aplicação de tarefas inicial após seu primeiro lançamento](images/develop-getting-started-app-first-launch.webp)

### O que há no ambiente?

Agora que o ambiente está instalado e funcionando, o que realmente há nele?
Em um alto nível, há vários contêineres (ou processos) que atendem a uma
necessidade específica da aplicação:

* Front-end React - um contêiner Node que está executando o servidor de
  desenvolvimento React, usando [Vite](https://vitejs.dev/).
* Back-end Node - o back-end fornece uma API que fornece a capacidade de
  recuperar, criar e excluir itens de tarefas.
* Banco de dados MySQL - um banco de dados para armazenar a lista de itens.
* phpMyAdmin - uma interface web para interagir com o banco de dados que pode
  ser acessada em [http://db.localhost](http://db.localhost).
* Proxy Traefik - Traefik é um proxy de aplicação que roteia requisições para o
  serviço correto.
  Ele envia todas as requisições para `localhost/api/*` para o back-end,
  requisições para `localhost/*` para o front-end e, finalmente, requisições
  para `db.localhost` para o phpMyAdmin.
  Isso fornece a capacidade de acessar todas as aplicações usando a porta `80`
  (em vez de portas diferentes para cada serviço).

Com esse ambiente, você, como pessoa desenvolvedora, não precisa instalar ou
configurar nenhum serviço, preencher um esquema de banco de dados, configurar
credenciais de banco de dados ou qualquer coisa.
Você só precisa do Docker Desktop.
O resto simplesmente funciona.

## Faça alterações na aplicação

Com esse ambiente instalado e funcionando, você já pode fazer algumas alterações
na aplicação e ver como o Docker ajuda a fornecer um ciclo rápido de resposta.

### Altere a saudação

A saudação no topo da página é preenchida por uma chamada de API a
`/api/greeting`.
Atualmente, ela sempre retorna "Hello world!".
Agora você a modificará para retornar uma das três mensagens aleatórias (que
você poderá escolher).

1. Abra o arquivo `backend/src/routes/getGreeting.js` em um editor de texto.
   Este arquivo fornece o manipulador para o endpoint da API.

2. Modifique a variável no topo para um array de saudações.
   Sinta-se à vontade para usar as seguintes modificações ou personalizá-la
   conforme sua preferência.
   Além disso, atualize o endpoint para enviar uma saudação aleatória desta
   lista.

   ```js {linenos=table,hl_lines=["1-5",9],linenostart=1}
   const GREETINGS = [
       "Olá, mundo!",
       "Todas as pessoas a postos!",
       "Traçando o curso à frente!",
   ];

   module.exports = async (req, res) => {
       res.send({
           greeting: GREETINGS[ Math.floor( Math.random() * GREETINGS.length )],
       });
   };
   ```

3. Se você ainda não fez isso, salve o arquivo.
   Se você atualizar seu navegador, deverá ver uma nova saudação.
   Se você continuar atualizando, deverá ver todas as mensagens aparecerem.

   ![Captura de tela da aplicação de tarefas com uma nova saudação](images/develop-app-with-greetings.webp)

### Altere o texto do espaço reservado

Quando você acessar a aplicação, notará que o texto do espaço reservado é
simplesmente "New Item".
Agora você tornará isso um pouco mais descritivo e divertido.
Você também fará algumas alterações no estilo da aplicação.

1. Abra o arquivo `client/src/components/AddNewItemForm.jsx`.
   Ele fornece o componente para adicionar um novo item à lista de tarefas.

2. Modifique o atributo `placeholder` do elemento `Form.Control` para o que você
   quiser exibir.

   ```js {linenos=table,hl_lines=[5],linenostart=33}
   <Form.Control
       value={newItem}
       onChange={(e) => setNewItem(e.target.value)}
       type="text"
       placeholder="What do you need to do?"
       aria-label="New item"
   />
   ```

3. Salve o arquivo e volte para o seu navegador.
   Você deve notar a alteração já recarregada no seu navegador.
   Se não gostar, sinta-se à vontade para ajustá-la até que fique perfeita.

![Captura de tela da aplicação de tarefas com um espaço reservado atualizado no campo de texto "Add Item"](images/develop-app-with-updated-placeholder.webp)

### Altere a cor de fundo

Antes de considerar a aplicação finalizada, você precisa melhorar as cores.

1. Abra o arquivo `client/src/index.scss`.

2. Ajuste o atributo `background-color` para qualquer cor que desejar.
   O trecho de código fornecido é um azul suave para combinar com o tema náutico
   do Docker.

   Se estiver usando uma IDE, você pode escolher uma cor usando os seletores de
   cores integrados.
   Caso contrário, sinta-se à vontade para usar um
   [seletor de cores](https://www.w3schools.com/colors/colors_picker.asp)
   online.

   ```css {linenos=table,hl_lines=2,linenostart=3}
   body {
       background-color: #99bbff;
       margin-top: 50px;
       font-family: 'Lato';
   }
   ```

   Cada salvamento deve permitir que você veja a alteração imediatamente no
   navegador.
   Continue ajustando até que esteja na configuração perfeita para você.

   ![Captura de tela da aplicação de tarefas com um novo espaço reservado e cor de fundo"](images/develop-app-with-updated-client.webp)

E com isso, você terminou. Parabéns por atualizar seu site.

## Recapitulando

Antes de prosseguir, reserve um momento e reflita sobre o que aconteceu aqui.
Em poucos instantes, você conseguiu:

* Iniciar um projeto de desenvolvimento completo com esforço zero de instalação.
  O ambiente conteinerizado forneceu o ambiente de desenvolvimento, garantindo
  que você tenha tudo o que precisa.
  Você não precisou instalar o Node, MySQL ou qualquer outra dependência
  diretamente na sua máquina.
  Tudo o que você precisou foi o Docker Desktop e um editor de código.

* Fazer alterações e vê-las imediatamente.
  Isso foi possível porque:
    1. Os processos em execução em cada contêiner estão observando e respondendo
      às alterações de arquivo e;
    2. Os arquivos são compartilhados com o ambiente em contêiner.

O Docker Desktop permite tudo isso e muito mais.
Depois que você começar a pensar com contêineres, poderá criar quase qualquer
ambiente e compartilhá-lo facilmente com seu time.

## Próximos passos

Agora que a aplicação foi atualizada, você já pode aprender sobre como
empacotá-la como uma imagem de contêiner e enviá-la para um registro,
especificamente o Docker Hub.

{{< button text="Crie e envie sua primeira imagem" url="build-and-push-first-image" >}}

