---
title: Conceitos Comunso de Conferência no Lync Server 2013
TOCTitle: Conceitos Comunso de Conferência no Lync Server 2013
ms:assetid: a21d4987-1c0a-44c8-8a39-9c17ffb57f3c
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ688158(v=OCS.15)
ms:contentKeyID: 49886343
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Conceitos Comunso de Conferência no Lync Server 2013

 

_**Tópico modificado em:** 2012-09-19_

Alguns conceitos são comuns a todos os tipos de conferências. Eles são descritos nas seções a seguir.

## Políticas e gerenciamento de largura de banda

O Lync Server 2013 permite que os administradores definam políticas sobre os tipos de reunião que os usuários podem organizar. Isso ajuda a você aplicar as políticas da sua organização e controlar a utilização de largura de banda. Você pode definir uma ampla variedade de políticas e atribuí-las a usuários individuais e grupos de usuários. Você também pode definir políticas que regem conversas ponto a ponto. Para obter detalhes sobre como definir políticas de conferência, consulte [Políticas de conferência no Lync Server 2013](lync-server-2013-conferencing-policies.md)[Visão geral do controle de admissão de chamada no Lync Server 2013](lync-server-2013-overview-of-call-admission-control.md) e [Configuriando largura de banda de vídeo no Lync Server 2013](lync-server-2013-configuring-video-bandwidth.md).

## Recursos de arquivamento e conformidade

O Lync Server 2013 fornece recursos que você pode usar se a sua organização precisa seguir normas de conformidade. Você pode usar as habilidades de arquivamento para arquivar o conteúdo apresentado nas reuniões e o conteúdo de conversas de mensagens instantâneas (IM) e de conferências de IM. Para obter detalhes, consulte [Planejando Arquivamento no Lync Server 2013](lync-server-2013-planning-for-archiving.md) na documentação de Planejamento. Você pode usar recursos de conformidade de Servidor de Chat Persistente para obter conversas com vários participantes, baseadas em tópicos, que são persistentes ao longo do tempo. Para obter detalhes, consulte [Planejando o Servidor de Chat Persistente no Lync Server 2013](lync-server-2013-planning-for-persistent-chat-server.md) na documentação de Planejamento.

## Recurso de monitoramento

O recurso de Servidor de Monitoramento pode capturar registros de detalhes de chamada (CDRs), que você pode usar para rastrear quais usuários conversaram com quais outros usuários usando o Lync Server 2013. Para obter detalhes sobre implantação e monitoramento de configuração, consulte [Implantando o monitoramento no Lync Server 2013](lync-server-2013-deploying-monitoring.md).

## Habilitando participação externa em conferências

Você pode aumentar significativamente os benefícios de seu investimento na conferência do Lync Server 2013 permitindo que os usuários externos também participem de conferências, quando convidados. Os usuários externos podem incluir:

  - **Usuários remotos** Os usuários da organização, quando eles estão trabalhando fora dos firewalls e estão usando laptops ou outros dispositivos do Lync Server 2013.

  - **Usuários federados** Os usuários de empresas que trabalham com quem também executa o Lync Server 2013. Para permitir que os usuários contatem facilmente esses usuários, você pode criar relacionamentos federados com essas empresas.

  - **Usuários anônimos** Outros usuários externos que são convidados especificamente por seus usuários para participar de conferências específicas. O organizador de uma reunião em sua empresa pode enviar um convite por email de uma conferência para um usuário externo. O email inclui um link no qual o usuário externo pode clicar para ingressar na conferência.

Para habilitar qualquer ou todos esses cenários, é necessário implantar um Servidor de Borda para ajudar a habilitar as comunicações seguras entre sua implantação do Lync Server 2013 e os usuários externos. A solução do Lync Server 2013 que usa Servidores de Borda fornece a mídia de maior qualidade que outras soluções, como uma VPN (rede virtual privada). Para obter detalhes, consulte [Planejamento para acesso de usuário externo no Lync Server 2013](lync-server-2013-planning-for-external-user-access.md).

Além disso, independentemente da implantação de Servidores de Borda, você pode permitir que os usuários (isto é, dentro ou fora da organização) disquem de telefones PSTN padrão para participar de conferências de áudio em suas instalações. Isso é feito implantando a conferência de discagem do Lync Server 2013.

## Compatibilidade entre tipos de reunião e versões de cliente

Se você pretende que o Lync Server 2013 interopere com versões anteriores do Office Communications Server e seus clientes, deve estar ciente dos seguintes problemas:

  - Os usuários que usam o Lync Server 2013 não podem agendar conferências online do Live Meetingou modificar as reuniões migradas desse tipo.

  - Os usuários que usam o Lync Server 2013, que precisam participar de conferências online do Live Meeting hospedadas em servidores que executam o Office Communications Server 2007 R2 devem ter o cliente do Live Meeting instalado no computador (além do Lync Server 2013) para participar dessas reuniões.

  - Quando as conferências online do Live Meeting são migradas para o Lync Server 2013, o conteúdo de reunião não é migrado. Se esse conteúdo for necessário, ele deverá ser carregado novamente.

