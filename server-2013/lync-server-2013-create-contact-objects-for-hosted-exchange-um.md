---
title: 'Lync Server 2013: Criar objetos de contato para Exchange UM hospedado'
TOCTitle: Criar objetos de contato para Exchange UM hospedado
ms:assetid: a39be52f-488a-4523-ad5f-ce1f0d681959
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg412765(v=OCS.15)
ms:contentKeyID: 49307671
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Criar objetos de contato para Exchange UM hospedado no Lync Server 2013

 

_**Tópico modificado em:** 2012-09-24_

O procedimento a seguir explica como criar objetos de contato no AA (Atendedor Automático) ou no SA (Acesso do Assinante) para o serviço de UM (Unificação de Mensagens) do Exchange hospedado.

Para obter detalhes, consulte [Gerenciamento de objeto de Contato no Exchange hospedado no Lync Server 2013](lync-server-2013-hosted-exchange-contact-object-management.md) na documentação de Planejamento.

Para detalhes sobre como configurar objetos de contato, consulte a documentação do Shell de Gerenciamento do Lync Server para os seguintes cmdlets:

  - [New-CsExUmContact](https://docs.microsoft.com/en-us/powershell/module/skype/New-CsExUmContact)

  - [Set-CsExUmContact](https://docs.microsoft.com/en-us/powershell/module/skype/Set-CsExUmContact)

> [!IMPORTANT]  
> Antes que objetos de contato do Lync Server 2013 possam ser habilitados para a UM do Exchange hospedado, uma política de caixa postal hospedada que se aplique a eles deve ser implantada. Para detalhes, consulte <a href="lync-server-2013-hosted-voice-mail-policies.md">Políticas de correio de voz hospedado no Lync Server 2013</a>.

## Para criar objetos de contato no AA ou SA para a UM do Exchange hospedado

1.  Inicie o Shell de Gerenciamento do Lync Server: clique em **Iniciar**, em **Todos os Programas**, em **Microsoft Lync Server 2013** e em **Shell de Gerenciamento do Lync Server**.

2.  Execute o cmdlet New-CsExUmContact para criar objetos de contato obrigatórios para a sua implantação. Por exemplo, para criar um objeto de contato no AA e um no SA, execute:
    
    ```
        New-CsExUmContact -SipAddress "sip:exumaa1@fabrikam.com" -RegistrarPool "RedmondPool.litwareinc.com" -OU "HostedExUM Integration" -DisplayNumber "+14255550101" -AutoAttendant $True
    ```
    ```    
        New-CsExUmContact -SipAddress "sip:exumsa1@fabrikam.com" -RegistrarPool "RedmondPool.litwareinc.com" -OU "HostedExUM Integration" -DisplayNumber "+14255550101"
    ```

    Estes exemplos definem os seguintes parâmetros:
    
      - **SipAddress** especifica o endereço SIP do objeto de contato. Este deve ser um endereço que ainda não tenha sido usado para configurar um objeto de contato ou de usuário nos Serviços de Domínio do Active Directory. Este valor deve estar no formato “sip:\< *endereço SIP* \>“, conforme mostrado em exemplos anteriores.
    
      - **RegistrarPool** especifica o nome de domínio totalmente qualificado (FQDN) do pool em que o serviço do Registrador Avançado está sendo executado.
        
        > [!NOTE]  
        > Objetos de contato da UM do Exchange não podem ser movidos para pools que sejam parte de implantações do Lync Server 2013 antes do Lync Server 2013.    
      - **OU** especifica a unidade organizacional do Active Directory em que este objeto de contato estará localizado.
    
      - **DisplayNumber** especifica o número de telefone do objeto de contato. O número de telefone para cada objeto de contato deve ser único.
    
      - **AutoAttendant** especifica se o objeto de Contato é um Atendedor Automático. O Atendedor Automático fornece um conjunto de prompts de voz que permite aos chamadores navegar no sistema telefônico e alcançar a pessoa que desejam contatar. O valor **False** (o padrão) para este parâmetro indica um objeto de contato de Acesso do Assinante.

