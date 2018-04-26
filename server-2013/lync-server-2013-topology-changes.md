---
title: 'Lync Server 2013: Alterações de topologia'
TOCTitle: Alterações de topologia
ms:assetid: 9e40ef93-9ab0-498c-9bbf-f94584353e53
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ688153(v=OCS.15)
ms:contentKeyID: 49886332
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Alterações de topologia no Lync Server 2013

 

_**Tópico modificado em:** 2012-10-02_

Os requisitos e as considerações de topologia para o Lync Server 2013 são diferentes dos aplicados às versões anteriores, conforme explicado nas seções a seguir.

## Nova arquitetura de pools de front end

No Lync Server 2013, a arquitetura do Enterprise EditionPools de Front-Ends foi alterada para uma arquitetura de sistemas distribuídos.

Com essa nova arquitetura, o banco de dados de backend não é mais o armazenamento de dados em tempo real no pool. Informações sobre um usuário específico são mantidas em três servidores de front end no pool. Para cada usuário, um servidor de front end age como o mestre das informações desse usuário, e os outros dois servidores de front end servem como réplicas. Se um servidor de front end cair, outro servidor de front end que servia como réplica será automaticamente promovido a mestre.

Isso acontece nos bastidores e os administradores não precisam saber quais servidores de front end são os mestres para quais usuários. Essa distribuição de armazenamento de dados melhora o desempenho e dimensionamento dentro do pool e elimina o ponto único de falha de um único Servidor Back-End.

O servidor de back end serve como armazenamento de back up do usuário e dados de conferência, e também é o armazenamento principal de outros bancos de dados, como o banco de dados do Grupo de Resposta.

Essas melhorias também significam que há mudanças em como planejar e manter seus pools. Recomendamos que todos seus Enterprise EditionPools de Front-Ends incluam pelo menos três Servidores Front-End, para fornecer o número completo de réplicas para a qual a arquitetura do Pool de Front-Ends foi projetada. Além disso, é necessário seguir alguns procedimentos ao adicionar servidores a um Pool de Front-Ends, remover servidores dele ou atualizar servidores. Para obter mais informações, consulte [Topologias e componentes para Servidores Front-End, serviço de mensagens instantâneas e presença no Lync Server 2013](lync-server-2013-topologies-and-components-for-front-end-servers-instant-messaging-and-presence.md).

## Alterações na topologia de função do servidor

Algumas funções de servidor que eram executadas antes em servidores separados são agora consolidadas na função de servidor de front end, permitindo economizar em custos de hardware

  - No Lync Server 2013, o servidor de conferência A/V é sempre colocado com o servidor de front end.

  - Os servidores de front end de Monitoramento e arquivamento são sempre colocados com o servidor de front end. O Monitoramento e arquivamento exigem, cada um deles, um banco de dados de backend separado, que pode ser colocado no mesmo servidor do banco de dados de backend do pool de front end, ou pode ser hospedado em servidores de backend separados.

  - O Servidor de Chat Persistente é agora uma função de servidor. No Microsoft Lync Server 2010, o Servidor de Chat de Grupo era um aplicativo confiável de terceiros Microsoft Lync Server 2010. No Lync Server 2013, a funcionalidade do Servidor de Chat Persistente é implementada usando três novas funções de servidor:
    
      - **PersistentChatService :** Serviços principais do Servidor de Chat Persistente implementados como uma função de front
    
      - **PersistentChatStore :** Função de servidor de back end
    
      - **PersistentChatComplianceStore :** Função de servidor de back end para conformidade do Chat Persistente

