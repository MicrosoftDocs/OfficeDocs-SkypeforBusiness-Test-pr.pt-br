---
title: 'Lync Server 2013: Componentes e topologias para o Sistema de Mensagens Instantâneas local'
TOCTitle: Componentes e topologias para o Sistema de Mensagens Instantâneas local
ms:assetid: 22fc87cf-a7e5-4c8c-bb9b-101e5380cdcf
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg425711(v=OCS.15)
ms:contentKeyID: 49306140
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Componentes e topologias para o Sistema de Mensagens Instantâneas local no Lync Server 2013

 

_**Tópico modificado em:** 2012-09-25_

Este tópico descreve os componentes do Microsoft Exchange Server 2013 necessários para oferecer os recursos do Unificação de Mensagens (UM) do Exchange para a implantação do Lync Server 2013. Também descreve as topologias de suporte para integração do UM do Exchange local.

## Componentes de Exchange Server

Para oferecer os recursos e serviços do UM do Exchange descritos em [Recursos de Unificação de Mensagens integrada e do Lync Server 2013](lync-server-2013-features-of-integrated-unified-messaging.md) para usuários do Enterprise Voice na sua organização, você deve implantar um servidor de Caixa de Correio e servidor de Acesso do Cliente do Microsoft Exchange, que hospeda as caixas de correio do usuário e oferece um único local de armazenamento para email e caixa postal. O UM do Exchange funciona como um serviço na Caixa de Correio do Exchange e servidores de Acesso do Cliente.

Para obter detalhes sobre os componentes UM do Exchange no Microsoft Exchange Server 2007 e no Microsoft Exchange Server 2010, consulte [Implantando Exchange UM no local para fornecer correio de voz do Lync Server 2013](lync-server-2013-deploying-on-premises-exchange-um-to-provide-lync-server-2013-voice-mail.md) na documentação de Implantação.

## Topologias suportadas

É possível implantar o Lync Server 2013 e o Unificação de Mensagens (UM) do Exchange na mesma floresta ou em várias florestas. Se a implantação abrange várias florestas, você deve executar as etapas de integração do Exchange para cada floresta do UM do Exchange. Além disso, você deve configurar cada floresta do Microsoft Exchange para confiar na floresta do Lync Server 2013 e a floresta do Lync Server 2013 para confiar na floresta do UM do Exchange. Além desta confiança de floresta, as configurações do UM do Exchange para todos os usuários devem ser definidas em objetos de usuário na floresta do Lync Server 2013.

O Lync Server 2013 suporta as seguintes topologias da integração do UM do Exchange:

  - Floresta única

  - Domínio único (ou seja, uma única floresta com um único domínio). O Lync Server 2013, Microsoft Exchange e os usuários residem no mesmo domínio.

  - Vários domínios (ou seja, um domínio raiz com um ou mais domínios filhos). Os servidores do Lync Server 2013 e do Microsoft Exchange são implantados em domínios diferentes do domínio onde cria usuários. Os servidores do UM do Exchange podem ser implantados em diferentes domínios do pool do Lync Server 2013 que suportam.

  - Várias floresta (ou seja, floresta de recursos). O Lync Server 2013 é implantado em uma única floresta e os usuários são distribuídos entre várias florestas. Os atributos UM do Exchange dos usuários devem ser replicados pela floresta do Lync Server 2013.
    
    > [!NOTE]  
    > O Exchange pode ser implantado em várias florestas. Cada organização do Exchange pode oferecer o UM do Exchange para seus usuários ou o UM do Exchange pode ser implantado na mesma floresta que o Lync Server 2013.
