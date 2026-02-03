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

source_url: https://github.com/docker/docs/blob/main/content/manuals/engine/security/_index.md
revision: b398f346a7e38451cacda1cfe54f1697d2685cdc
status: ready

description: Análise da superfície de ataque do Docker Daemon
keywords: docker, documentação do docker, segurança
title: Segurança da Docker Engine
linkTitle: Segurança
weight: 80
aliases:
- /articles/security/
- /engine/articles/security/
- /engine/security/security/
- /security/security/
---

Há quatro áreas principais a serem consideradas ao analisar a segurança do
Docker:

- A segurança intrínseca do kernel e seu suporte a namespaces e cgroups.
- A superfície de ataque do próprio daemon do Docker.
- Brechas no perfil de configuração do contêiner, seja por padrão, ou quando
  personalizado por pessoas usuárias.
- Os recursos de segurança de "reforço" do kernel e como eles interagem com os
  contêineres.

## Namespaces do kernel

Os contêineres Docker são muito semelhantes aos contêineres LXC e possuem
recursos de segurança similares.
Ao iniciar um contêiner com `docker run`, o Docker cria, nos bastidores, um
conjunto de namespaces e grupos de controle para o contêiner.

Os namespaces fornecem a primeira e mais direta forma de isolamento.
Os processos em execução em um contêiner não podem ver, e muito menos afetar, os
processos em execução em outro contêiner ou no sistema host.

Cada contêiner também recebe sua própria pilha de rede, o que significa que um
contêiner não obtém acesso privilegiado aos sockets ou interfaces de outro
contêiner.
Obviamente, se o sistema host estiver configurado de acordo, os contêineres
podem interagir entre si por meio de suas respectivas interfaces de rede — assim
como podem interagir com hosts externos.
Ao especificar portas públicas para seus contêineres ou usar
[links](/manuals/engine/network/links.md), o tráfego IP é permitido entre os
contêineres.
Eles podem se comunicar entre si, enviar/receber pacotes UDP e estabelecer
conexões TCP, mas isso pode ser restringido, se necessário.
Do ponto de vista da arquitetura de rede, todos os contêineres em um determinado
host Docker estão em interfaces de ponte.
Isso significa que eles são como máquinas físicas conectadas por meio de um
switch Ethernet comum; nada mais, nada menos.

Quão maduro é o código que fornece namespaces do kernel e redes privadas?
Os namespaces do kernel foram introduzidos
[entre as versões 2.6.15 e 2.6.26 do kernel](https://man7.org/linux/man-pages/man7/namespaces.7.html).
Isso significa que, desde julho de 2008 (data do lançamento da versão 2.6.26), o
código de namespaces foi testado e analisado em inúmeros sistemas de produção.
E tem mais: o design e a inspiração para o código de namespaces são ainda mais
antigos.
Na verdade, os namespaces são um esforço para reimplementar os recursos do
[OpenVZ](https://en.wikipedia.org/wiki/OpenVZ) de forma que pudessem ser
integrados ao kernel principal.
E o OpenVZ foi lançado inicialmente em 2005, então tanto o design quanto a
implementação são bem maduros.

## Grupos de controle

Os grupos de controle são outro componente essencial dos contêineres Linux.
Eles implementam a responsabilização e a limitação de recursos.
Fornecem muitas métricas úteis, mas também ajudam a garantir que cada contêiner
receba sua parte justa de memória, CPU e E/S de disco; e, mais importante, que
um único contêiner não possa derrubar o sistema esgotando um desses recursos.

Portanto, embora não impeçam um contêiner de acessar ou afetar os dados e
processos de outro contêiner, eles são essenciais para repelir alguns ataques de
negação de serviço.
São particularmente importantes em plataformas multi-tenant, como PaaS públicas
e privadas, para garantir um tempo de atividade (e desempenho) consistente,
mesmo quando algumas aplicações começam a apresentar comportamento inadequado.

Os grupos de controle também existem há algum tempo: o código foi iniciado em
2006 e inicialmente integrado ao kernel 2.6.24.

## Superfície de ataque do daemon do Docker

Executar contêineres (e aplicações) com o Docker implica executar o daemon do
Docker.
Este daemon requer privilégios de `root`, a menos que você opte pelo
[Modo sem root](rootless.md), e, portanto, você deve estar ciente de alguns
detalhes importantes.

Primeiramente, somente pessoas usuárias confiáveis devem ter permissão para
controlar o seu daemon do Docker.
Isso é uma consequência direta de alguns recursos poderosos do Docker.
Especificamente, o Docker permite que você compartilhe um diretório entre o host
do Docker e um contêiner convidado; e permite que você faça isso sem limitar os
direitos de acesso do contêiner.
Isso significa que você pode iniciar um contêiner onde o diretório `/host` é o
diretório `/` em seu host; e o contêiner pode alterar o sistema de arquivos do
seu host sem qualquer restrição.
Isso é semelhante à forma como os sistemas de virtualização permitem o
compartilhamento de recursos do sistema de arquivos.
Nada impede que você compartilhe seu sistema de arquivos raiz (ou mesmo seu
dispositivo de bloco raiz) com uma máquina virtual.

Isso tem uma forte implicação de segurança: por exemplo, se você instrumentar o
Docker a partir de um servidor web para provisionar contêineres por meio de uma
API, você deve ser ainda mais cuidadoso do que o normal com a verificação de
parâmetros, para garantir que uma pessoa usuária maliciosa não possa passar
parâmetros manipulados que façam o Docker criar contêineres arbitrários.

Por esse motivo, o endpoint da API REST (usado pela CLI do Docker para se
comunicar com o daemon do Docker) foi alterado no Docker 0.5.2 e agora usa um
socket Unix em vez de um socket TCP vinculado a 127.0.0.1 (este sendo vulnerável
a ataques de falsificação de requisições entre sites se você executar o Docker
diretamente em sua máquina local, fora de uma VM).
Você pode então usar verificações de permissão Unix tradicionais para limitar o
acesso ao socket de controle.

Você também pode expor a API REST via HTTP, se assim o desejar explicitamente.
No entanto, se fizer isso, esteja ciente das implicações de segurança
mencionadas acima.
Observe que, mesmo que você tenha um firewall para limitar o acesso ao endpoint
da API REST a partir de outros hosts na rede, o endpoint ainda poderá ser
acessado de contêineres, o que pode facilmente resultar em escalonamento de
privilégios.
Portanto, é *obrigatório* proteger os endpoints da API com
[HTTPS e certificados](protect-access.md).
Expor a API do daemon via HTTP sem TLS não é permitido, e tal configuração faz
com que o daemon falhe logo no início da inicialização, consulte
[Conexões TCP não autenticadas](../deprecated.md#unauthenticated-tcp-connections).
Também é recomendável garantir que ela seja acessível apenas a partir de uma
rede confiável ou VPN.

Você também pode usar `DOCKER_HOST=ssh://USER@HOST` ou
`ssh -L /caminho/para/docker.sock:/var/run/docker.sock` se preferir SSH em vez
de TLS.

O daemon também é potencialmente vulnerável a outras entradas, como o
carregamento de imagens do disco com `docker load` ou da rede com `docker pull`.
A partir do Docker 1.3.2, as imagens são extraídas em um subprocesso chroot em
plataformas Linux/Unix, sendo este o primeiro passo em um esforço mais amplo em
direção à separação de privilégios.
A partir do Docker 1.10.0, todas as imagens são armazenadas e acessadas pelos
checksums criptográficos de seu conteúdo, limitando a possibilidade de um
invasor causar uma colisão com uma imagem existente.

Por fim, se você executar o Docker em um servidor, recomenda-se executar
exclusivamente o Docker no servidor e mover todos os outros serviços para
containers controlados pelo Docker.
Claro, não há problema em manter suas ferramentas administrativas favoritas
(provavelmente pelo menos um servidor SSH), bem como processos de
monitoramento/supervisão existentes, como NRPE e collectd.

## Capacidades do kernel Linux

Por padrão, o Docker inicia contêineres com um conjunto restrito de capacidades.
O que isso significa?

As capacidades transformam a dicotomia binária "root/não-root" em um sistema de
controle de acesso granular.
Processos (como servidores web) que precisam apenas se conectar a uma porta
abaixo de 1024 não precisam ser executados como root: eles podem simplesmente
receber a capacidade `net_bind_service`.
E existem muitas outras capacidades, para quase todas as áreas específicas onde
privilégios de root geralmente são necessários.
Isso significa muito para a segurança de contêineres.

Servidores típicos executam vários processos como `root`, incluindo o daemon
SSH, o daemon `cron`, daemons de logging, módulos do kernel, ferramentas de
configuração de rede, e muito mais.
Um contêiner é diferente, porque quase todas essas tarefas são gerenciadas pela
infraestrutura ao redor do contêiner:

- O acesso SSH é geralmente gerenciado por um único servidor em execução no host
  Docker.
- O `cron`, quando necessário, deve ser executado como um processo de usuário
  dedicado e personalizado para a aplicação que precisa do seu serviço de
  agendamento, em vez de como um recurso de toda a plataforma.
- O gerenciamento de logs também geralmente é delegado ao Docker ou a serviços
  de terceiros como Loggly ou Splunk.
- O gerenciamento de hardware é irrelevante, o que significa que você nunca
  precisa executar `udevd` ou daemons equivalentes dentro de contêineres.
- O gerenciamento de redes ocorre fora dos contêineres, reforçando a separação
  de responsabilidades o máximo possível, o que significa que um contêiner nunca
  deve precisar executar comandos `ifconfig`, `route` ou `ip` (exceto quando um
  contêiner é especificamente projetado para se comportar como um roteador ou
  firewall, é claro).

Isso significa que, geralmente, os contêineres não precisam de privilégios de
root "reais" e, portanto, podem ser executados com um conjunto de capacidades
reduzido; isso significa que o "root" em um contêiner tem muito menos
privilégios do que o "root" real.
Por exemplo, é possível:

- Negar todas as operações de "montagem".
- Negar acesso a sockets brutos (para evitar falsificação de pacotes).
- Negar acesso a algumas operações do sistema de arquivos, como criar novos nós
  de dispositivo, alterar o proprietário de arquivos ou alterar atributos
  (incluindo a flag imutável).
- Negar o carregamento de módulos.

Isso significa que, mesmo que uma pessoa invasora consiga escalar para root em
um contêiner, é muito mais difícil causar danos sérios ou escalar para o host.

Isso não afeta aplicações web comuns, mas reduz consideravelmente os vetores de
ataque por pessoas usuárias maliciosas.
Por padrão, o Docker descarta todas as capacidades, exceto
[aquelas necessárias](https://github.com/moby/moby/blob/master/daemon/pkg/oci/caps/defaults.go#L6-L19),
adotando uma abordagem de lista de permissões em vez de lista de bloqueios.
Você pode ver uma lista completa das capacidades disponíveis nas
[páginas de manual do Linux](https://man7.org/linux/man-pages/man7/capabilities.7.html).

Um dos principais riscos ao executar contêineres Docker é que o conjunto padrão
de capacidades e montagens fornecido a um contêiner pode oferecer isolamento
incompleto, seja de forma independente ou quando usado em combinação com
vulnerabilidades do kernel.

O Docker suporta a adição e remoção de capacidades, permitindo o uso de um
perfil não padrão.
Isso pode tornar o Docker mais seguro por meio da remoção de capacidades ou
menos seguro por meio da adição de capacidades.
A melhor prática para as pessoas usuárias seria remover todas as capacidades,
exceto aquelas explicitamente necessárias para seus processos.

## Verificação de assinatura do Docker Content Trust

A Docker Engine pode ser configurada para executar apenas imagens assinadas.
O recurso de verificação de assinatura do Docker Content Trust está integrado
diretamente ao binário `dockerd`.
Isso é configurado no arquivo de configuração do Dockerd.

Para habilitar esse recurso, o trustpinning pode ser configurado em
`daemon.json`, permitindo que apenas repositórios assinados com uma chave raiz
especificada pela pessoa usuária sejam baixados e executados.

Esse recurso oferece às pessoas administradoras mais informações do que as
disponíveis anteriormente com a CLI para impor e realizar a verificação de
assinatura de imagem.

Para obter mais informações sobre como configurar a verificação de assinatura do
Docker Content Trust, consulte
[Confiança de conteúdo no Docker](trust/_index.md).

## Outros recursos de segurança do kernel

As capacidades são apenas um dos muitos recursos de segurança fornecidos pelos
kernels Linux modernos.
Também é possível aproveitar sistemas existentes e conhecidos, como TOMOYO,
AppArmor, SELinux, GRSEC, etc., com o Docker.

Embora o Docker atualmente habilite apenas capacidades, ele não interfere com os
outros sistemas.
Isso significa que existem muitas maneiras de reforçar a segurança de um host
Docker.
Aqui estão alguns exemplos:

- Você pode executar um kernel com GRSEC e PAX.
  Isso adiciona muitas verificações de segurança, tanto em tempo de compilação
  quanto em tempo de execução; também impede muitas explorações, graças a
  técnicas como randomização de endereços.
  Não requer configuração específica do Docker, já que esses recursos de
  segurança se aplicam a todo o sistema, independentemente dos contêineres.
- Se sua distribuição vier com modelos de segurança para contêineres Docker,
  você pode usá-los imediatamente.
  Por exemplo, nós fornecemos um template que funciona com o AppArmor e a Red
  Hat vem com políticas SELinux para o Docker.
  Esses templates fornecem uma camada extra de segurança (mesmo que haja grande
  sobreposição com as capacidades).
- Você pode definir suas próprias políticas usando seu mecanismo de controle de
  acesso favorito.

Assim como você pode usar ferramentas de terceiros para aprimorar contêineres
Docker, incluindo topologias de rede especiais ou sistemas de arquivos
compartilhados, existem ferramentas para reforçar a segurança de contêineres
Docker sem a necessidade de modificar o próprio Docker.

A partir do Docker 1.10, os namespaces de usuário são suportados diretamente
pelo daemon do Docker.
Esse recurso permite que o usuário root em um contêiner seja mapeado para um
usuário com UID diferente de 0 fora do contêiner, o que pode ajudar a mitigar os
riscos de vazamento de dados do contêiner.
Esse recurso está disponível, mas não habilitado por padrão.

Consulte o
[comando daemon](/reference/cli/dockerd.md#daemon-user-namespace-options)
na referência da linha de comando para obter mais informações sobre esse
recurso.
Informações adicionais sobre a implementação de namespaces de usuário no Docker
podem ser encontradas
[nesta postagem de blog](https://integratedcode.us/2015/10/13/user-namespaces-have-arrived-in-docker/).

## Conclusões

Os contêineres Docker são, por padrão, bastante seguros; especialmente se você
executar seus processos como usuários sem privilégios de administrador dentro do
contêiner.

Você pode adicionar uma camada extra de segurança habilitando o AppArmor,
SELinux, GRSEC ou outro sistema de reforço de segurança apropriado.

Se você tiver ideias para tornar o Docker mais seguro, ficaremos felizes em
receber sugestões de recursos, pull requests ou comentários nos fóruns da
comunidade Docker.

## Informações relacionadas

- [Use imagens confiáveis](trust/_index.md)
- [Perfis de segurança Seccomp para o Docker](seccomp.md)
- [Perfis de segurança AppArmor para o Docker](apparmor.md)
- [Sobre a segurança de contêineres (2014)](https://medium.com/@ewindisch/on-the-security-of-containers-2c60ffe25a9e)
- [Modelo de segurança de rede overlay do modo swarm do Docker](/manuals/engine/network/drivers/overlay.md)
