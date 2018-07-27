---
title: Planejamento para conectividade para redes públicas de mensagens instantâneas no Lync Server 2013
TOCTitle: Planejamento para conectividade para redes públicas de mensagens instantâneas no Lync Server 2013
ms:assetid: e75e8884-05c7-414a-8014-bc9aa8126fb7
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ205349(v=OCS.15)
ms:contentKeyID: 49308438
ms.date: 03/09/2017
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Planejamento para conectividade para redes públicas de mensagens instantâneas no Lync Server 2013

 

_**Tópico modificado em:** 2017-03-09_

A Conectividade do Sistema de Mensagens Instantâneas Públicas é uma classe de federação e está configurada para permitir que seus usuários internos e externos do Lync Server 2013 adicionem contatos a partir de qualquer uma das seguintes opções:

  - Contatos do Messenger

  - Contatos do Yahoo\!

  - Contatos America Online (AOL)

> [!IMPORTANT]  
> <ul>
> <li><p>A partir de 1° de setembro de 2012, a PIC USL (Licença de Assinatura de Usuário da Conectividade de Mensagens Instantâneas Públicas) do Microsoft Lync não está mais disponível para compra nos contratos novos ou renovados. Os clientes com licenças ativas poderão continuar a federar o Yahoo! Messenger até a data de encerramento do serviço. Foi anunciada a data final do términio em junho de 2014 para o AOL e o Yahoo!. Para obter detalhes, consulte <a href="lync-server-2013-support-for-public-instant-messenger-connectivity.md">Suporte para conectividade a redes públicas de mensagens instantâneas no Lync Server 2013</a>.</p></li>
> 
> <li><p>A PIC USL é uma licença de assinatura por usuário e por mês exigida para que o Lync Server ou o Office Communications Server faça a federação com o Yahoo! Messenger. A capacidade de a Microsoft oferecer esse serviço tem sido dependente do suporte do Yahoo!, cujo contrato subjacente não será renovado.</p></li>
> 
> 
> <li><p>Mais do que nunca, o Lync é uma ferramenta poderosa de conexão entre organizações e pessoas de todo o mundo. A federação com o Windows Live Messenger não exige licenças adicionais de usuário ou dispositivo além da Lync Standard CAL. A federação com o Skype será adicionada a essa lista, permitindo que os usuários do Lync alcancem centenas de milhões de pessoas por meio de IM (mensagem instantânea) e voz.</p></li></ul>


Essa classe de federação requer as seguintes considerações de planejamento:

  - Os usuários do Windows Live Messenger podem ter comunicação audiovisual ponto a ponto com usuários do Lync Server 2013, além do sistema de mensagens instantâneas. Suas Servidores de Borda devem atender a requisitos de portas e protocolos específicos. Para obter detalhes, consulte [Determinar firewall A/V externo e requisitos de porta para Lync Server 2013](lync-server-2013-determine-external-a-v-firewall-and-port-requirements.md)

  - O sistema de mensagens instantâneas do Yahoo não tem exigências exclusivas, a não ser as geralmente usadas no planejamento e na implantação da Servidor de Borda típica que está fornecendo a federação.

  - America Online requer que o certificado de sua Servidor de Borda atribuída ao Serviço de Borda de Acesso tenha um EKU (uso avançado de chave).

## Nesta seção

  - [Resumo do Certificado – conectividade para redes públicas de mensagens instantâneas](lync-server-2013-certificate-summary-public-instant-messaging-connectivity.md)

  - [Resumo do Porta – conectividade para redes públicas de mensagens instantâneas](lync-server-2013-port-summary-public-instant-messaging-connectivity.md)

  - [Resumo de DNS – Conectividade a redes públicas de mensagens instantâneas](https://technet.microsoft.com/pt-br/library/jj618375\(v=ocs.15\))

