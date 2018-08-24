---
title: Criar ou modificar o objeto de contato de um dispositivo de conferência
TOCTitle: Criar ou modificar o objeto de contato de um dispositivo de conferência
ms:assetid: 62ed64be-379c-417d-9453-511881cf5604
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ994035(v=OCS.15)
ms:contentKeyID: 52057620
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Criar ou modificar o objeto de contato de um dispositivo de conferência

 

_**Tópico modificado em:** 2013-10-02_

Para criar um objeto da sala de conferências, primeiro, crie uma conta de usuário do Active Directory para representar o dispositivo. Depois, use o cmdlet **Enable-CsMeetingRoom** para permitir que a conta funcione como um dispositivo de conferência. Se for necessário alterar as propriedades de um dispositivo de conferência existente, use o cmdlet **Set-CsMeetingRoom**.

Esses cmdlets podem ser executados a partir do Shell de Gerenciamento do Lync Server 2013 ou de uma sessão remota do Windows PowerShell.

> [!NOTE]  
> Para obter detalhes sobre como usar o Windows PowerShell remoto para conectar ao Lync Server, consulte o artigo de blog do Lync Server Windows PowerShell, &quot;Quick Start: Managing Microsoft Lync Server 2010 Using Remote PowerShell&quot; em <a href="http://go.microsoft.com/fwlink/p/?linkid=255876">http://go.microsoft.com/fwlink/p/?linkId=255876 (em inglês)</a>.


## Criando um dispositivo de conferência

  - Após criar uma conta de usuário do Active Directory que represente o novo dispositivo de conferência, permita que ela use o cmdlet **Enable-CsMeetingRoom**. Certifique-se de incluir a) a identidade do dispositivo de conferência, b) o pool de registradores no qual a conta da sala será hospedada e c) o endereço SIP a ser atribuído a essa conta. Por exemplo:
    
        Enable-CsMeetingRoom -Identity "Redmond Conferencing device" -RegistrarPool "atl-cs-001.litwareinc.com" -SipAddress "sip:RedmondMeetingRoom@litwareinc.com"

## Modificando um dispositivo de conferência

  - Para modificar os valores de propriedades de um dispositivo de conferência existente, use o cmdlet **Set-CsMeetingRoom**. Por exemplo, o comando a seguir atualiza o número de telefone (LineUri) associado a um dispositivo de conferência:
    
        Set-CsMeetingRoom -Identity "Redmond Conferencing device" -LineUri "tel:+12065551219"

Para obter detalhes, consulte os tópicos de Ajuda para o cmdlet [Enable-CsMeetingRoom](https://docs.microsoft.com/en-us/powershell/module/skype/Enable-CsMeetingRoom) e o cmdlet [Set-CsMeetingRoom](https://docs.microsoft.com/en-us/powershell/module/skype/Set-CsMeetingRoom).

