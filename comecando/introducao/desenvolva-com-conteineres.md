---
source_url: https://github.com/docker/docs/blob/main/content/get-started/introduction/develop-with-containers.md
revision: abd030c3fe2b5db526fb7a16d6d9892d46d678e5
status: ready
license: https://github.com/docker/docs/blob/main/LICENSE

title: Desenvolva com contêineres
keywords: conceitos, construção, imagens, contêiner, docker desktop
description: Esta página conceitual ensinará como desenvolver com contêineres.
summary: |
  Aprenda a executar seu primeiro contêiner, ganhando experiência prática com os
  recursos poderosos do Docker.
  Abordaremos como fazer alterações em tempo real no código de _backend_ e
  _frontend_ dentro do ambiente em contêiner, garantindo integração e testes
  perfeitos.
weight: 2
aliases:
  - /guides/getting-started/develop-with-containers/
---

# Desenvolva com contêineres

Aprenda a executar seu primeiro contêiner, ganhando experiência prática com os
recursos poderosos do Docker.
Abordaremos como fazer alterações em tempo real no código de _backend_ e
_frontend_ dentro do ambiente em contêiner, garantindo integração e testes
perfeitos.
{: .lead }

<iframe width="895" height="487" src="https://www.youtube.com/embed/D0SDBrS3t9I"
        title="Conceitos do Docker: Desenvolva com contêineres"
        frameborder="0"
        allow="accelerometer; autoplay; clipboard-write; encrypted-media;
          gyroscope; picture-in-picture; web-share"
        referrerpolicy="strict-origin-when-cross-origin"
        allowfullscreen></iframe>

## Explicação

Agora que você instalou o Docker Desktop, já pode fazer algum desenvolvimento de
aplicação.
Especificamente, você fará o seguinte:

1. Clonar e iniciar um projeto de desenvolvimento;
2. Fazer alterações no backend e frontend;
3. Ver as alterações imediatamente.

## Experimente

Neste guia prático, você aprenderá como desenvolver com contêineres.

## Inicie o projeto

1. Para começar, clone ou
   [baixe o projeto como um arquivo ZIP para sua máquina local](https://github.com/docker/getting-started-todo-app/archive/refs/heads/main.zip).
   ```shell
   git clone https://github.com/docker/getting-started-todo-app
   ```
   E depois que o projeto for clonado, navegue até o novo diretório criado pelo
   comando:
   ```shell
   cd getting-started-todo-app
   ```

2. Depois de ter o projeto, inicie o ambiente de desenvolvimento usando o Docker
   Compose.
   Para iniciar o projeto usando a CLI, execute o seguinte comando:
   ```shell
   docker compose watch
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
   ![Captura de tela da aplicação de tarefas iniciais após seu primeiro lançamento](images/develop-getting-started-app-first-launch.webp?border=true)

### O que há no ambiente?

Agora que o ambiente está instalado e funcionando, o que realmente há nele?
Em um alto nível, há vários contêineres (ou processos) que atendem a uma
necessidade específica da aplicação:

* _Frontend_ React - um contêiner Node que está executando o servidor de
  desenvolvimento React, usando [Vite](https://vitejs.dev/).
* _Backend_ Node - o _backend_ fornece uma API que fornece a capacidade de
  recuperar, criar e excluir itens de tarefas.
* Banco de dados MySQL - um banco de dados para armazenar a lista de itens.
* phpMyAdmin - uma interface _web_ para interagir com o banco de dados que pode
  ser acessada em [http://db.localhost](http://db.localhost).
* _Proxy_ Traefik - Traefik é um _proxy_ de aplicação que roteia requisições
  para o serviço certo.
  Ele envia todas as requisições para `localhost/api/*` para o _backend_,
  requisições para `localhost/*` para o _frontend_ e, em seguida, requisições
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

A saudação no topo da página é preenchida por uma chamada de API em
`/api/greeting`.
Atualmente, ela sempre retorna "Hello world!".
Agora você a modificará para retornar uma das três mensagens aleatórias (que
você poderá escolher).

1. Abra o arquivo `backend/src/routes/getGreeting.js`.
   Este arquivo fornece o manipulador para o _endpoint_ da API.
2. Modifique a variável no topo para um _array_ de saudações.
   Sinta-se à vontade para usar as seguintes modificações ou personalizá-la
   conforme sua preferência.
   ```js
   const GREETINGS = [
       "Olá, mundo!",
       "Todas as pessoas a postos!",
       "Traçando o curso à frente!",
   ];
   module.exports = async (req, res) => {
       // ...
   }
   ```
3. Agora, atualize o _endpoint_ para enviar uma saudação aleatória desta lista
   fazendo a seguinte alteração:
   ```js
   module.exports = async (req, res) => {
       res.send(
           greeting: GREETINGS[ Math.floor( Math.random() * GREETINGS.length )],
       });
   };
   ```
4. Se você ainda não fez isso, salve o arquivo.
   Se você atualizar seu navegador, deverá ver uma nova saudação.
   Se você continuar atualizando, deverá ver todas as mensagens aparecerem.
   ![Captura de tela da aplicação de tarefas com uma nova saudação](images/develop-app-with-greetings.webp?border=true)

### Altere o texto do espaço reservado

Quando você olhar para a aplicação, verá que o texto do espaço reservado é
simplesmente "New Item".
Agora você tornará isso um pouco mais descritivo e divertido.
Você também fará algumas alterações no estilo da aplicação.

1. Abra o arquivo `client/src/components/AddNewItemForm.jsx`.
   Ele fornece o componente para adicionar um novo item à lista de tarefas.
2. Modifique o atributo `placeholder` do elemento `Form.Control` para o que você
   quiser exibir.
   ```js
   <Form.Control
       value={newItem}
       onChange={(e) => setNewItem(e.target.value)}
       type="text"
       placeholder="What do you need to do?"
       aria-label="New item"
   />
   ```
3. Salve o arquivo e volte para o seu navegador.
   Você deve ver a alteração já recarregada no seu navegador.
   Se não gostar, sinta-se à vontade para ajustá-la até que fique perfeita.
   ![Captura de tela da aplicação de tarefas com um espaço reservado atualizado no campo de texto "Add Item"](images/develop-app-with-updated-placeholder.webp?border=true)

### Altere a cor de fundo

Antes de considerar a aplicação finalizada, você precisa melhorar as cores.

1. Abra o arquivo `client/src/index.scss`.
2. Ajuste o atributo `background-color` para qualquer cor que desejar.
   O trecho de código fornecido é um azul suave para combinar com o tema náutico
   do Docker.
   Se estiver usando um IDE, você pode escolher uma cor usando os seletores de
   cores integrados.
   Caso contrário, sinta-se à vontade para usar um
   [seletor de cores](https://www.w3schools.com/colors/colors_picker.asp)
   _online_.
   ```css
   body {
       background-color: #99bbff;
       margin-top: 50px;
       font-family: 'Lato';
   }
   ```
   Cada salvamento deve permitir que você veja a alteração imediatamente no
   navegador.
   Continue ajustando até que esteja na configuração perfeita para você.
   ![Captura de tela da aplicação de tarefas com um novo espaço reservado e cor de fundo"](images/develop-app-with-updated-client.webp?border=true)

E com isso, você terminou. Parabéns por atualizar seu _site_.

## Recapitulando

Antes de prosseguir, reserve um momento e reflita sobre o que aconteceu aqui.
Em alguns momentos, você conseguiu:

* Iniciar um projeto de desenvolvimento completo com esforço zero de instalação.
  O ambiente em contêiner forneceu o ambiente de desenvolvimento, garantindo que
  você tenha tudo o que precisa.
  Você não precisou instalar o Node, MySQL ou qualquer outra dependência
  diretamente na sua máquina.
  Tudo o que você precisava era do Docker Desktop e de um editor de código.
* Fazer alterações e vê-las imediatamente.
  Isso foi possível porque:
    1. os processos em execução em cada contêiner estão observando e respondendo
      às alterações de arquivo e;
    2. os arquivos são compartilhados com o ambiente em contêiner.

O Docker Desktop permite tudo isso e muito mais.
Depois que você começar a pensar com contêineres, poderá criar quase qualquer
ambiente e compartilhá-lo facilmente com seu time.

## Próximos passos

Agora que a aplicação foi atualizada, você já pode aprender sobre como
empacotá-la como uma imagem de contêiner e enviá-la para um registro,
especificamente o Docker Hub.
