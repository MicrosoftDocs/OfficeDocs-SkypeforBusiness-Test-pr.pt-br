---
title: Criar uma política de caixa postal hospedada no nível local no Lync Server 2013
TOCTitle: Criar uma política de caixa postal hospedada no nível local no Lync Server 2013
ms:assetid: 145892c8-a6ca-45fb-9e83-786f709dd775
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398216(v=OCS.15)
ms:contentKeyID: 49305979
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Criar uma política de caixa postal hospedada no nível local no Lync Server 2013

 

_**Tópico modificado em:** 2012-09-24_

Uma política de *local* pode afetar todos os usuários hospedados no local em que a política foi definida. Se um usuário for configurado para acesso hospedado ao serviço de UM do Exchange e não tiver recebido uma política Por usuário, a política de local será aplicada. Caso não tenha implantado uma política de local, será aplicada a política global.

Para obter detalhes sobre como configurar políticas de site, consulte a documentação do Shell de Gerenciamento do Lync Server nos seguintes cmdlets:

  - [New-CsHostedVoicemailPolicy](https://docs.microsoft.com/en-us/powershell/module/skype/New-CsHostedVoicemailPolicy)

  - [Set-CsHostedVoicemailPolicy](https://docs.microsoft.com/en-us/powershell/module/skype/Set-CsHostedVoicemailPolicy)

  - [Get-CsHostedVoicemailPolicy](https://docs.microsoft.com/en-us/powershell/module/skype/Get-CsHostedVoicemailPolicy)

## Para criar uma política de caixa postal hospedada em um site

1.  Inicie o Shell de Gerenciamento do Lync Server: clique em **Iniciar**, em **Todos os Programas**, em **Microsoft Lync Server 2013** e em **Shell de Gerenciamento do Lync Server**.

2.  Execute o cmdlet New-CsHostedVoicemailPolicy para criar a política. Por exemplo, execute:
    
        New-CsHostedVoicemailPolicy -Identity site:Redmond -Destination ExUM.fabrikam.com -Description "Hosted voice mail policy for the Redmond site." -Organization "corp1.litwareinc.com, corp2.litwareinc.com"
    
    Esse exemplo cria uma política de caixa postal com escopo do site e define os parâmetros a seguir:
    
      - A **Identidade** especifica um identificador único para a política, o que inclui o escopo. Para uma política com escopo de site, o valor de parâmetro de identidade deve ser especificado no formato `site:`*\<nome\>*, por exemplo, `site:Redmond`.
    
      - O **Destino** especifica o nome de domínio totalmente qualificado (FQDN) do serviço hospedado de UM do Exchange. Este parâmetro é opcional, mas se se tentar habilitar um usuário para correio de voz apresentado e a diretiva atribuída ao usuário não tiver um valor Destino, a habilitação falhará.
    
      - A **Descrição** fornece informações descritivas opcionais sobre a política.
    
      - A **Organização** especifica uma lista separada por vírgulas de inquilinos do Exchange que hospedam os usuários do Lync Server 2013. Cada inquilino deve ser especificado como FQDN daquele inquilino no serviço hospedado de UM do Exchange.

