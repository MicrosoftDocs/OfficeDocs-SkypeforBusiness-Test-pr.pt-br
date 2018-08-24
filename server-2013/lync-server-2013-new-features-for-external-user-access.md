---
title: 'Lync Server 2013: Novos recursos para acesso de usuário externo'
TOCTitle: Novos recursos para acesso de usuário externo
ms:assetid: 99da6bd5-ec14-4ad9-8f7d-37fbddf567dd
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398794(v=OCS.15)
ms:contentKeyID: 49307568
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Novos recursos para acesso de usuário externo no Lync Server 2013

 

_**Tópico modificado em:** 2012-10-17_

O Lync Server 2013 apresenta novos recursos que ampliam os métodos de comunicação e os recursos para seus usuários. Além disso, o Lync Server 2013 introduz alterações a serviços existentes para integrar e estender melhor os serviços disponíveis em sua organização. A seguir, encontra-se um resumo das alterações que podem afetar seu planejamento e implantação dos serviços do Lync Server 2013  Servidor de Borda.

  - **Suporte para endereços IPv6**    O Lync Server 2013 suporta endereços IPv6 para todos os serviços do Servidor de Borda. Se você forneceu endereços IPv6 para as interfaces através da configuração no Windows Server, é possível usar os endereços IPv6 em sua configuração do Servidor de Borda através da configuração de endereço IP no Construtor de Topologias.
    
    > [!IMPORTANT]  
    > O uso dos endereços IPv6 no Lync Server 2013 depende do suporte de IPv6 em roteadores e firewalls que sua organização implantar, assim como suporte através do seu provedor de serviços de Internet.

  - **Extensible Messaging and Presence Protocol (XMPP)**    O Lync Server 2013 apresenta um proxy XMPP totalmente integrado (implantado no Servidores de Borda) e um gateway XMPP implantado em seu Servidores Front-End. Você pode implantar federação XMPP como componente adicional. Adicionar e configurar o proxy XMPP e gateway XMPP permitirá que seus usuários do Microsoft Lync 2013 adicionem contatos de parceiros baseados em XMPP para mensagem instantânea (IM) e presença.
    
    > [!NOTE]  
    > No momento, os serviços XMPP no Lync Server 2013 fornecem apenas mensagem instantânea e presença entre clientes do Lync e contatos baseados em XMPP.

  - **Serviços de mobilidade para clientes móveis**    Introduzido em uma atualização para o cliente do Lync Server 2010, os serviços de mobilidade do Lync Server 2013 permitem que clientes do Microsoft Lync Mobile em celulares e tablet usando Apple iOS, Android, Windows Phone, ou celulares Nokia executem atividades como enviar e receber mensagens instantâneas, exibir contatos e visualizar a presença. Além disso, os dispositivos móveis suportam alguns recursos do Enterprise Voice, como clicar para participar da conferência, Chamada via Trabalho, acesso por um único número, caixa postal e notificação de ligação não atendida.
    
    > [!NOTE]  
    > Os serviços de mobilidade usam o proxy reverso e serviços publicados que são implantados nos seus Servidores Front-End. Nenhuma alteração é necessária para os Servidores de Borda.

  - **Os Diretores são uma função opcional**   A função do servidor do Diretor na topologia do Lync Server 2013 não mudou. Ela ainda hospeda serviços web, pré-autentica solicitações de usuários de entrada e direciona usuários externos a seu pool principal. Alterar o Diretor de uma função recomendada para uma opcional não reduz o valor do Diretor, mas enfatiza a redução de contagem do servidor e outros requisitos de hardware (por exemplo, balanceadores de carga de hardware para o Diretor) sem comprometer os recursos e funcionalidade. Como os Servidores Front-End podem fazer o mesmo trabalho do Diretor sem impacto nos serviços fornecidos, você pode implantar opcionalmente os Diretores se escolher. Você pode excluir com segurança o Diretor confiando que os Servidores Front-End fornecerão os mesmos serviços em seu lugar.

## Consulte Também

#### Conceitos

[Planejamento e configuração do IPv6 no Lync Server 2013](lync-server-2013-planning-for-and-configuring-ipv6.md)  

#### Outros Recursos

[Planejamento para acesso de usuário externo no Lync Server 2013](lync-server-2013-planning-for-external-user-access.md)  
[Planejamento para Mensagens Extensíveis e Federação de Protocolo de Presença (XMPP) no Lync Server 2013](lync-server-2013-planning-for-extensible-messaging-and-presence-protocol-xmpp-federation.md)

