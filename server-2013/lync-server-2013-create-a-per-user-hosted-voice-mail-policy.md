---
title: Criar uma política de caixa postal hospedada por usuário no Lync Server 2013
TOCTitle: Criar uma política de caixa postal hospedada por usuário no Lync Server 2013
ms:assetid: 39018a7c-e0c3-46a2-be4e-05604ec67a50
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg425867(v=OCS.15)
ms:contentKeyID: 49306404
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Criar uma política de caixa postal hospedada por usuário no Lync Server 2013

 

_**Tópico modificado em:** 2012-09-24_

Uma política *por usuário* pode afetar somente usuários individuais, grupos ou objetos de contato. Para implantar uma política por usuário, atribua explicitamente a política a um ou mais usuários, grupos ou objetos de contato. Para obter mais detalhes, consulte [Atribuir uma política de caixa postal hospedada por usuário no Lync Server 2013](lync-server-2013-assign-a-per-user-hosted-voice-mail-policy.md).

Para obter os detalhes de como trabalhar com políticas de correio de voz hospedadas por usuário, consulte a documentação do Shell de Gerenciamento do Lync Server sobre os seguintes cmdlets:

  - [New-CsHostedVoicemailPolicy](https://docs.microsoft.com/en-us/powershell/module/skype/New-CsHostedVoicemailPolicy)

  - [Set-CsHostedVoicemailPolicy](https://docs.microsoft.com/en-us/powershell/module/skype/Set-CsHostedVoicemailPolicy)

  - [Get-CsHostedVoicemailPolicy](https://docs.microsoft.com/en-us/powershell/module/skype/Get-CsHostedVoicemailPolicy)

## Para criar uma política de correio de voz hospedada por usuário

1.  Inicie o Shell de Gerenciamento do Lync Server: clique em **Iniciar**, em **Todos os Programas**, em **Microsoft Lync Server 2013** e em **Shell de Gerenciamento do Lync Server**.

2.  Execute o cmdlet New-CsHostedVoicemailPolicy para criar a política. Por exemplo, execute:
    
        New-CsHostedVoicemailPolicy -Identity ExRedmond -Destination ExUM.fabrikam.com -Description "Hosted voice mail policy for Redmond users." -Organization "corp1.litwareinc.com, corp2.litwareinc.com"
    
    O exemplo anterior cria uma política de correio de voz hospedada com o escopo por usuário, e define os seguintes parâmetros:
    
      - **Identidade** especifica um identificador exclusivo para a política, que inclui o escopo. Para uma política com escopo por usuário, esse valor de parâmetro é especificado como uma cadeia de caracteres simples, por exemplo, ExRedmond.
    
      - **Destino** especifica o nome de domínio completamente qualificado (FQDN) do serviço Exchange UM hospedado. Esse parâmetro é opcional, mas se você tentar ativar um usuário para o correio de voz hospedado e a política atribuída ao usuário não possui um valor de Destino, a ativação irá falhar.
    
      - **Descrição** fornece informações descritivas opcionais sobre a política.
    
      - **Organização** especifica uma lista separada por vírgulas dos inquilinos do Exchange que hospedam os usuários do Lync Server 2013. Cada inquilino deve ser especificado como o seu próprio FQDN no serviço do Exchange UM hospedado.

## Consulte Também

#### Tarefas

[Atribuir uma política de caixa postal hospedada por usuário no Lync Server 2013](lync-server-2013-assign-a-per-user-hosted-voice-mail-policy.md)

