---
title: Como o servidor de chat persistente funciona no Lync Server 2013
TOCTitle: Como o servidor de chat persistente funciona no Lync Server 2013
ms:assetid: 3d04e9a1-3f0c-458e-bcbe-d27c8c464276
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ683096(v=OCS.15)
ms:contentKeyID: 49886184
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Como o servidor de chat persistente funciona no Lync Server 2013

 

_**Tópico modificado em:** 2012-11-21_

Lync Server 2013, Servidor de Chat Persistente permite que você participe de conversas com base em tópicos com vários participantes que persiste com o tempo. Servidor de Chat Persistente pode ajudar a sua organização a fazer o seguinte:

  - Melhorar a comunicação entre equipes geograficamente distante e multifuncionais

  - Ampliar a conscientização e participação da informação

  - Melhorar a comunicação com sua organização estendida

  - Reduzir sobrecarga informacional

  - Melhorar a conscientização da informação

  - Melhorar a dispersão de informações e conhecimentos importantes

Você pode implantar o Servidor de Chat Persistente como função opcional com serviços Lync Server 2013. Chat Persistente executados em um pool dedicado, e um Pool de Servidor de Chat Persistente depende de um pool Lync Server para rotear mensagens. Os clientes utilizam eXtensible Chat Communication Over SIP (XCCOS). Os Lync ServerServidores Front-End são configurados para rotear o tráfego para um Pool de Servidor de Chat Persistente.

## Arquitetura de alto nível

Os diagramas a seguir fornecem perspectivas de alto nível da arquitetura e serviços Servidor de Chat Persistente.

**Arquitetura de alto nível de servidor de bate-papo persistente**

![Arquitetura do Servidor de Chat Persistente.](images/JJ683096.5db6f36f-4461-4d87-ba77-463b7ffe609b(OCS.15).jpg "Arquitetura do Servidor de Chat Persistente.")

**Serviços de alto nível de servidor de bate-papo persistente**

![Componentes do Servidor de Chat Persistente.](images/JJ683096.b6d743aa-3a86-4081-aaef-4fe3257db4e7(OCS.15).jpg "Componentes do Servidor de Chat Persistente.")

Dois serviços são executados no Servidor de Chat PersistenteServidores Front-End:

  - Bate-papo persistente (canal)

  - Conformidade

## Serviço de bate-papo (canal) persistente

O serviço Chat Persistente (canal) é o serviço principal responsável pelo Servidor de Chat Persistente. Este serviço fornece as seguintes funções:

  - Aceita as mensagens recebidas

  - Registra e lista os participantes em uma sala do Chat Persistente

  - Retransmite mensagens a outros assinantes do canal

  - Implementa lógica para gerenciamento de canal, convite para sala de bate-papo, busca e notificações de novo conteúdo

O serviço Chat Persistente (canal) armazena e acessa o conteúdo da sala de bate-papo e outros metadados de sistema (regras de autorização, e assim por diante) ao utilizar o Chat Persistente Store. Este serviço armazena arquivos que são enviados para as salas de bate-papo no Repositório de Arquivos Chat Persistente.

## Serviços de conformidade

O serviço de Conformidade é um componente opcional do Servidor de Chat Persistente e é responsável por arquivar conteúdo de bate-papo e eventos do Chat Persistente Repositório de Conformidade. Se sua organização possuir regulações que precisem que atividades do Chat Persistente sejam arquivadas, você pode implantar o serviço de Conformidade Chat Persistente opcional. O serviço de Conformidade é instalado em cada Servidor de Chat Persistente, em um pool Chat Persistente. Quando configurado, a conformidade do Servidor de Chat Persistente registra a atividade do usuário como a entrada e saída de salas e a postagem e leitura de mensagens. O serviço de Conformidade armazena arquivos que precisam ser arquivados no Repositório de Conformidade Chat Persistente.

## Serviços da Web Chat Persistente\]

No Lync ServerServidores Front-End, dois serviços executados dependem do IIS (Serviços de Informações da Internet) e são implementados como componentes da web:

  - Serviços da Web **Chat Persistente para Upload/Download de arquivo** Responsável pela postagem e recuperação de arquivos das salas de bate-papo.

  - **Serviços da Web Chat Persistente para Gerenciamento de salas de bate-papo** Responsável por fornecer aos usuários a capacidade de gerenciar as salas de bate-papo e criar novas salas.

## Como eu começo a usar o Servidor de Chat Persistente?

Servidor de Chat Persistente é uma função de servidor opcional na infraestrutura do Lync Server 2013. Se você instalar a função Servidor de Chat Persistente, qualquer usuário que tiver sido ativado na política por um administrador pode utilizar o Chat Persistente com o cliente Lync 2013. Para detalhes sobre como implantar o Servidor de Chat Persistente e permitir que os usuários aproveitem as capacidades por política, consulte [Implantando Servidor de Chat Persistente no Lync Server 2013](lync-server-2013-deploying-persistent-chat-server.md).

Para detalhes sobre como configurar as definições na sua implantação do Servidor de Chat Persistente, consulte [Implantando Servidor de Chat Persistente no Lync Server 2013](lync-server-2013-deploying-persistent-chat-server.md) e [Gerenciar Lync Server 2013, Servidor de Chat Persistente](managing-lync-server-2013-persistent-chat-server.md).

Para detalhes sobre como permitir usuários através da política para que eles possam aproveitar a funcionalidade Chat Persistente no cliente Lync 2013, consulte [Implantando Servidor de Chat Persistente no Lync Server 2013](lync-server-2013-deploying-persistent-chat-server.md) e [Gerenciar Lync Server 2013, Servidor de Chat Persistente](managing-lync-server-2013-persistent-chat-server.md).

Se você implantou a conformidade Chat Persistente, consulte [Gerenciar Lync Server 2013, Servidor de Chat Persistente](managing-lync-server-2013-persistent-chat-server.md) para detalhes sobre como definir as configurações para a conformidade.

## Chat Persistente Fluxos de chamada

O cliente Lync se comunica com o serviço Chat Persistente utilizando o XCCOS. A sequência a seguir descreve o processo de inscrição e assinatura de sala típica e cenário de postagem de mensagem..

## Inscrição

A sequência a seguir descreve o processo de inscrição.

1.  O cliente Lync primeiro envia um SIP SUBSCRIBE para recuperar o documento de provisionamento em banda a partir do servidor. Esse documento indica se o Chat Persistente está ativado ou não para o usuário e lista os URIs SIP para o Pool de Servidor de Chat Persistente.

2.  O cliente Lync envia uma mensagem SIP INVITE para o SIP URI do Servidor de Chat Persistente, que foi obtido na etapa anterior. A sequência INVITE é seguida por 200 OK e ACK, e o cliente Lync agora possui uma sessão SIP aberta com um ponto de extremidade Servidor de Chat Persistente. Consequentemente, o cliente se comunica com Servidor de Chat Persistente ao enviar mensagens SIP INFO que contém mensagens de bate-papo ou comandos solicitando que o servidor excute uma ação. Todas essas mensagens são reconhecidas com 200 OK ou 503 Serviço Não Disponível (isto é, no caso de uma grande carga no servidor). Se o cliente receber uma resposta 503, irá tentar novamente a mensagem. (Esse exemplo não inclui uma resposta 503.) Se o servidor aceitar a mensagem ou comando e enviar 200 OK, fornecerá uma resposta ao cliente na forma de uma mensagem SIP INFO separada. Essa resposta inclui uma referência ao comando que a originou.

3.  O cliente Lync envia uma mensagem SIP INFO que contém o comando XCCOS **getserverinfo**. Servidor de Chat Persistente responde com uma nova mensagem SIP INFO que contém informações sobre a configuração do serviço Chat Persistente.

4.  O cliente Lync envia uma mensagem SIP INFO que contém o comando XCCOS **getassociations**. Servidor de Chat Persistente responde com uma nova mensagem SIP INFO que contém a lista de salas o qual o usuário é membro. O cliente Lync repete o comando para recuperar a lista de salas o qual o usuário é gerente.

5.  O cliente Lync obtém a lista das salas subsequentes do documento "presença", onde cada sala subsequente é representada por uma categoria "roomSetting". Todas as salas seguintes são reunidas por uma única mensagem SIP INFO que contém o comando XCCOS **bjoin**, que contém a lista de salas URIs. Por a lista de salas subsequentes ser mantida no servidor, qualquer cliente em qualquer computador possui a mesma lista de salas subsequentes para o usuário URI especificado. O cliente Lync também mantém a lista de salas abertas (se esta opção estiver ativada pelo usuário) no registro do computador local e se une a cada uma dessas salas no momento de inscrição ao enviar uma mensagem SIP INFO que contém o comando XCCOS **join** para cada sala aberta. Uma vez que essa lista é mantida no registro, ela pode ser diferente em dois clientes Lync em execução em computadores diferentes.

6.  Para cada sala participante, o cliente Lync envia uma mensagem SIP INFO que contém o comando XCCOS **bccontext**. Servidor de Chat Persistente responde com uma nova mensagem SIP INFO que contém a mensagem de bate-papo mais recente na sala.

7.  O cliente Lync envia uma mensagem SIP INFO que contém o comando XCCOS **getinv** (isto é, obter convite) para solicitar qualquer convite para novas salas que o cliente ainda não tenha visto. Em uma mensagem SIP INFO separada, Servidor de Chat Persistente retorna uma lista dessas salas.

## Inscrever-se para uma sala e postar uma mensagem

A seguinte sequência descreve uma inscrição de sala típica e um cenário de postagem de mensagem.

1.  Do cliente Lync, o User1 clica em **Entrar em uma sala de bate-papo**, clica em **Buscar** e, então, insere alguns critérios de busca. O cliente envia uma mensagem SIP INFO que contém o comando XCCOS **chansrch** (busca de sala), junto com o critério de pesquisa. Servidor de Chat Persistente consulta o banco de dados back-end responde em uma nova mensagem SIP INFO que contém uma lista de salas disponíveis que atendam ao critério.

2.  O User1 seleciona a sala de bate-papo que deseja participar e, então, clica em **Seguir esta sala**. O cliente envia Servidor de Chat Persistente uma mensagem SIP INFO que contém o comando XCCOS **join** e o ID da sala da sala de bate-papo que o usuário selecionou. Servidor de Chat Persistente responde com uma mensagem SIP INFO que contém os dados de provisionamento.

3.  O cliente Lync envia Servidor de Chat Persistente uma mensagem SIP INFO que contém o comando XCCOS **bccontext** (contexto backchat). Servidor de Chat Persistente retorna o histórico de conversa e o envia para o cliente em uma mensagem SIP INFO separada. Neste ponto, o usuário insere a sala de bate-papo e está pronto para participar.

4.  O User1 insere uma nova mensagem e clica em **Enviar**. O cliente Lync posta a mensagem na sala de bate-papo em um comando SIP INFO XCCOS **grpchat**. Servidor de Chat Persistente armazena uma cópia dessa mensagem no banco de dados de Chat Persistente back-end.

5.  Servidor de Chat Persistente envia uma cópia separada da mensagem SIP INFO XCCOS **grpchat** ao User2, que já havia entrado na sala de bate-papo.

## Chat Persistente Fluxos de chamada de conformidade

Servidor de Chat Persistente utiliza o Serviço de Enfileiramento de Mensagens (também conhecido como MSMQ) e um banco de dados de conformidade adicional (mgccomp) para processar os dados de conformidade. Como exemplo de como os eventos de conformidade são processados, a sequência de eventos a seguir descreve como um evento de postagem de mensagem é processado.

1.  Um usuário posta uma mensagem em uma sala.

2.  Servidor de Chat Persistente insere a informação pertinente ao evento em uma fila do Serviço de Enfileiramento de Mensagens privado.

3.  Chat Persistente O servidor de conformidade lê este evento da fila e coloca-o no banco de dados mgccomp para processamento mais tarde.

4.  Periodicamente, o Chat Persistente servidor de Conformidade processa um conjunto de eventos no banco de dados e envia-os para o Chat Persistente adaptador de Conformidade para processamento.

5.  Se um adaptador processa os dados com sucesso, Chat Persistente o servidor de Conformidade exclui os eventos do banco de dados mgccomp.

