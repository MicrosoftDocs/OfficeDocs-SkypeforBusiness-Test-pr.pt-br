---
title: 'Lync Server 2013: Roteamento do Exchange UM hospedado'
TOCTitle: Roteamento do Exchange UM hospedado
ms:assetid: 6c90dc8b-6aef-4ce8-b483-37c7b5a553c2
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398512(v=OCS.15)
ms:contentKeyID: 49307037
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Roteamento do Exchange UM hospedado no Lync Server 2013

 

_**Tópico modificado em:** 2012-10-01_

O aplicativo UM do Exchange Routing application é executado no Servidor Front-End para rotear chamadas, tanto para uma implantação local do serviço de Unificação de Mensagens (UM) do Microsoft Exchange Server como para o serviço UM do Exchange hospedado.

## O aplicativo ExUM Routing

O Lync Server 2013UM do Exchange Routing usa informações de configurações de conta de usuário e de parâmetros de políticas de caixa postal hospedada para determinar como rotear as chamadas de caixa postal hospedada, como mostrado no diagrama a seguir.

**Exemplo de implantação mista de encaminhamento do UM do Exchange**

![Implantação UM do Lync Server Exchange local](images/Gg398512.75258286-1f23-487b-bf46-d8538e7d540e(OCS.15).jpg "Implantação UM do Lync Server Exchange local")

O UM do Exchange pode ser configurado para rotear chamadas a usuários habilitados para UM do Exchange local, a usuários habilitados para UM do Exchange hospedado ou uma combinação de ambos.

Por exemplo, suponha que a caixa postal de Roy e o serviço UM do Exchange estejam hospedados em uma implantação do Exchange no local.

  - As informações de endereço de proxy da conta de usuário de Roy fornecem as informações que o aplicativo ExUM Routing usa para rotear suas chamadas para um servidor UM do Exchange no local.

A caixa postal de Alice e o serviço UM do Exchange estão localizados no datacenter do provedor de serviços hospedados do Exchange. O encaminhamento de chamadas ao UM do Exchange está configurado da seguinte maneira:

  - Os valores definidos no atributo msExchUCVoiceMailSettings de conta de usuário de Alice solicitam que o aplicativo ExUM Routing verifique os detalhes de encaminhamento em uma política de caixa postal hospedada.
    
    > [!NOTE]  
    > O valor do atributo msExchUCVoiceMailSettings pode ser definido por um provedor de serviços do Exchange ou pelo administrador do Lync Server 2013. No exemplo mostrado no diagrama acima, o valor (CsHostedVoiceMail=1) foi definido pelo administrador do Lync Server 2013 para habilitar a caixa postal hospedada de Alice. Para obter detalhes sobre esse atributo, consulte <a href="lync-server-2013-hosted-exchange-user-management.md">Gerenciamento de usuário no Exchange hospedado no Lync Server 2013</a>.

  - A política de caixa postal hospedada atribuída à conta de usuário de Alice fornece os detalhes de encaminhamento:
    
      - O destino é um provedor de serviços hospedados do UM do Exchange (ls.ExUm. *\<hostedExchangeServer\>* .com neste exemplo).
    
      - As organizações são identificadas pelas IDs de locatários, que são os FQDNs de encaminhamento de mensagens SIP para os locatários do Exchange Server localizados em ls.ExUm. *\<ServidorHospedadoExchange\>* .com (corp.contoso.com e corp.litwareinc.com neste exemplo).
        
        > [!NOTE]  
        > O FQDN para Exchange Online é exap.um.outlook.com.        
        Para obter detalhes, consulte [Políticas de correio de voz hospedado no Lync Server 2013](lync-server-2013-hosted-voice-mail-policies.md).

> [!NOTE]  
> Se o atributo msExchUCVoiceMailSettings e as configurações de endereço proxy do UM estiverem presentes em uma conta de usuário, o atributo msExchUCVoiceMailSettings prevalecerá.
