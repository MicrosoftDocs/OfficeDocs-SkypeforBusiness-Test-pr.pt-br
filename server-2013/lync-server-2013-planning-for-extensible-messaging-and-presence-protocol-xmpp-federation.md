---
title: Planejamento para Mensagens Extensíveis e Federação de Protocolo de Presença (XMPP) no Lync Server 2013
TOCTitle: Planejamento para Mensagens Extensíveis e Federação de Protocolo de Presença (XMPP) no Lync Server 2013
ms:assetid: 952b33e2-1f58-4831-9a39-1dfec2a316ad
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ205107(v=OCS.15)
ms:contentKeyID: 49307499
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Planejamento para Mensagens Extensíveis e Federação de Protocolo de Presença (XMPP) no Lync Server 2013

 

_**Tópico modificado em:** 2012-10-22_

As versões anteriores do Lync Server e Office Communications Server forneciam um gateway de protocolo XMPP que podia ser implantado como uma função de servidor separada para permitir federação com implantações de XMPP. No Microsoft Lync Server 2013, a funcionalidade XMPP pode ser implantada como um recurso. A funcionalidade XMPP é instalada em duas partes: um proxy XMPP que é executado no Servidor de Borda e o gateway XMPP que é executado no Servidores Front-End.

A implantação e configuração do XMPP são abordadas no [Implantação de acesso do usuário externo no Lync Server 2013](lync-server-2013-deploying-external-user-access.md). Planeje o suporte a XMPP em sua organização definindo as regras de porta e de protocolo em seu firewall, a configuração de certificados e adicionando registros DNS. Os tópicos a seguir nesta seção resumem as informações necessárias para planejar federação XMPP com sucesso para sua implantação.

> [!IMPORTANT]  
> O recurso XMPP do Lync Server 2013 é testado pela Microsoft e ela oferece suporte para federação de mensagens instantâneas com o Google Talk. Para quaisquer outros sistemas XMPP, entre em contato com o fornecedor do mesmo para verificar se eles suportam federação com o Lync Server 2013, e para quaisquer recomendações de implantação ou solução de problemas.

## Nesta seção

  - [Resumo de Certificado - Mensagens Extensíveis e Federação de Protocolo de Presença (XMPP)](lync-server-2013-certificate-summary-extensible-messaging-and-presence-protocol-xmpp-federation.md)

  - [Resumo de Porta - Mensagens Extensíveis e Federação de Protocolo de Presença (XMPP)](lync-server-2013-port-summary-extensible-messaging-and-presence-protocol-xmpp-federation.md)

  - [Resumo DNS - Mensagens Extensíveis e Federação de Protocolo de Presença (XMPP)](lync-server-2013-dns-summary-extensible-messaging-and-presence-protocol-xmpp-federation.md)

## Consulte Também

#### Tarefas

[Configurando federação de XMPP no Lync Server 2013](lync-server-2013-setting-up-xmpp-federation.md)  
[Configurar políticas para controlar o acesso de usuário federado no Lync Server 2013](lync-server-2013-configure-policies-to-control-xmpp-federated-user-access.md)  

#### Outros Recursos

[Gerenciar parceiros XMPP federados no Lync Server 2013](lync-server-2013-manage-xmpp-federated-partners-for-your-organization.md)  
[Get-CsExternalAccessPolicy](https://docs.microsoft.com/en-us/powershell/module/skype/Get-CsExternalAccessPolicy)  
[Get-CsXmppAllowedPartner](https://docs.microsoft.com/en-us/powershell/module/skype/Get-CsXmppAllowedPartner)  
[Get-CsXmppGatewayConfiguration](https://docs.microsoft.com/en-us/powershell/module/skype/Get-CsXmppGatewayConfiguration)

