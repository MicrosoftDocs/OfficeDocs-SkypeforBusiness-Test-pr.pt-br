---
title: 'Lync Server 2013: Planejamento de conferência'
TOCTitle: Planejamento de conferência
ms:assetid: 983a272a-e1b3-4d70-8f84-836b092fe526
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398781(v=OCS.15)
ms:contentKeyID: 49307547
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Planejamento de conferência no Lync Server 2013

 

_**Tópico modificado em:** 2013-01-29_

O Lync Server 2013 oferece um conjunto rico de funcionalidades de conferências:

  - Webconferência, o que inclui colaboração de documentos, compartilhamento de aplicativos e de desktop. O Lync Server 2013 usa Office Web Apps e o Servidor Office Web Apps para lidar com o compartilhamento e renderização de apresentações do PowerPoint. Para obter informações sobre a instalação e configuração do Servidor Office Web Apps, consulte [Configurando a integração com servidor de Office Web Apps e Lync Server 2013](lync-server-2013-enabling-office-web-apps-server-and-lync-server-2013.md).

  - Conferências de áudio/vídeo (A/V), que permitem que os usuários façam conferências de áudio e/ou vídeo em tempo real, sem a necessidade de serviços externos, como o serviço do Microsoft Live Meeting ou uma ponte de áudio de terceiros.

  - Conferências discadas, que permitem que os usuários participem do áudio de uma conferência do Lync Server 2013 usando um telefone de rede telefônica pública comutada (PSTN) sem exigir um provedor de conferências de áudio de terceiros.

  - Conferências de mensagens instantâneas (IM), em que mais de dois participantes se comunicam em uma única sessão de IM. Para obter detalhes sobre conferência de IM, consulte [Planejamento de Servidores Front-End, sistema de mensagens instantâneas e presença no Lync Server 2013](lync-server-2013-planning-for-front-end-servers-instant-messaging-and-presence.md).

Lync Server 2013 suporta conferências agendadas e improvisadas.

Ao implantar o Lync Server 2013,  Servidor Front-End, você pode escolher se também implantará as funcionalidades de webconferência, conferência de A/V e conferência discada. As funcionalidades de conferência de IM sempre são automaticamente implantadas, juntamente com os recursos de conversação de IM no Lync Server 2013  Servidores Front-End.


> [!NOTE]  
> Se sua implantação incluir reuniões organizadas usando os clientes do Office Communicator 2007 R2 (incluindo o console do Live Meeting ou o Suplemento de Conferência para Microsoft Office Outlook), as reuniões terão as seguintes limitações após serem migradas para o Lync Server 2013:<ul><li><p>Os usuários na reunião não poderão usar os recursos de colaboração de dados, incluindo colaboração de documentos, compartilhamento de aplicativos e compartilhamento de área de trabalho.</p></li><li><p>Problemas de estabilidade podem surgir desde que os clientes do Office Communicator 2007 R2 não sejam suportados pelo Lync Server 2013.</p></li></ul>
Para evitar esses problemas, programe novamente qualquer reunião organizada usando os clientes do Office Communicator 2007 R2 com o Outlook 2010 ou o Outlook 2013 usando o Suplemento Reunião Online para Lync 2010 ou o Suplemento de Reunião Online para Lync 2013.


As seções a seguir descrevem o que é necessário para implantar os vários tipos de funcionalidades de conferência, incluindo o processo de planejamento, componentes, requisitos de hardware e software e o processo de implantação.

## Nesta seção

  - [Visão geral de conferência no Lync Server 2013](lync-server-2013-overview-of-conferencing.md)

  - [Definindo seus requisitos para conferência no Lync Server 2013](lync-server-2013-defining-your-requirements-for-conferencing.md)

  - [Componentes e topologias para conferências no Lync Server 2013](lync-server-2013-components-and-topologies-for-conferencing.md)

  - [Requisitos técnicos para conferência no Lync Server 2013](lync-server-2013-technical-requirements-for-conferencing.md)

  - [Lista de verificação de implantação para conferência no Lync Server 2013](lync-server-2013-deployment-checklist-for-conferencing.md)

  - [Suporte a reuniões grandes no Lync Server 2013](lync-server-2013-support-for-large-meetings.md)

