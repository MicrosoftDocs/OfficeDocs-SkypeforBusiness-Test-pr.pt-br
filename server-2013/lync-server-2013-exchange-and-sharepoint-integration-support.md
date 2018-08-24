---
title: 'Lync Server 2013: Suporte a Servidor Exchange e à integração com SharePoint'
TOCTitle: Suporte a Servidor Exchange e à integração com SharePoint
ms:assetid: 72bf8aa5-55b1-4851-8a59-c96bf85d215a
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ205005(v=OCS.15)
ms:contentKeyID: 49307094
ms.date: 01/20/2017
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Suporte a Servidor Exchange e à integração com SharePoint no Lync Server 2013

 

_**Tópico modificado em:** 2017-01-18_

O Lync Server 2013 e o Lync 2013 podem se comunicar de forma segura e ininterrupta com outros aplicativos e produtos de servidor, inclusive Office 2013, Exchange 2013, e SharePoint, caso você integre esses produtos. A integração do Lync Server 2013 e do Office proporciona aos usuários acesso contextual a mensagens instantâneas (IM), presença aprimorada, telefonia e recursos de conferência do Lync. Os usuários do Office podem acessar os recursos do Lync no cliente de mensagem e colaboração do Outlook 2013 e outros programas do Office, ou em uma página do Microsoft SharePoint Server 2010. Os usuários também podem exibir uma gravação de conversas do Lync na pasta Histórico de Conversas do Outlook. Quando integrado ao Exchange 2013, Exchange Online, ou Lync Server 2013 também oferece suporte a:

  - Repositório de contatos unificado, que permite que os usuários armazenem todas as informações de contato do Exchange 2013 ou Exchange Online de modo que as informações fiquem disponíveis globalmente no Lync 2013, Exchange, Outlook e Outlook Web App.

  - Histórico de conversas e histórico de Webconferências, armazenados nas pastas de usuários do Exchange.

  - Conteúdo arquivado do Lync, como IM e conteúdo da reunião, pode ser guardado em armazenamento do Exchange.

> [!NOTE]  
> O Lync Server 2013 oferece suporte à integração com versões anteriores do Microsoft Exchange Server e do SharePoint, mas nem todas as funcionalidades são compatíveis com essas versões anteriores, como a integração do armazenamento de Arquivamento com Microsoft Exchange.<br />Caso esteja migrando usuários para o Exchange 2013, você pode usar o armazenamento do Exchange e do Lync Server temporariamente, enquanto conclui a migração. Não há suporte ao uso permanente do armazenamento do Exchange e Lync Server.

A integração do Lync Server 2013 com Exchange 2013 e SharePoint Server exige autenticação servidor a servidor entre clientes que executam o Lync Server 2013, Microsoft Exchange Server e SharePoint Server. O Lync Server 2013 oferece suporte ao protocolo OAuth para autenticação e autorização servidor a servidor.Para autenticação local servidor a servidor entre dois servidores da Microsoft, não há necessidade de usar um servidor de token de terceiros. O Lync Server 2013, Exchange 2013 e SharePoint possuem um servidor de token interno que pode ser usado para fins de autenticação uns com os outros. Por exemplo, o Lync Server 2013 pode emitir e assinar um token de segurança por conta própria, usando-o na comunicação com o Exchange 2013. Nesse caso, não há necessidade de usar um servidor de token de terceiros.

O Lync Server 2013 oferece suporte a dois cenários de autenticação servidor a servidor. Eles incluem a configuração da autenticação servidor a servidor entre:

  - Uma instalação local do Lync Server 2013 e uma instalação local do Exchange 2013 e/ou SharePoint Server.

  - Um par de componentes do Office (por exemplo, entre Microsoft Exchange 365 e Microsoft Lync Server 365, ou entre Microsoft Lync Server 365 e Microsoft SharePoint 365).

> [!NOTE]  
> Não há suporte à autenticação servidor a servidor entre um servidor local e um componente do Office 365 nesta versão do Lync Server 2013. Entre outras coisas, isso significa que você não pode configurar a autenticação servidor a servidor entre uma instalação local do Lync Server 2013 e o Microsoft Exchange 365.

Para obter detalhes sobre a autenticação servidor a servidor, consulte [Gerenciando autenticação de servidor para servidor (Oauth) e inscrições de parceiros no Lync Server 2013](lync-server-2013-managing-server-to-server-authentication-oauth-and-partner-applications.md) nas documentações de implantação e operações.

