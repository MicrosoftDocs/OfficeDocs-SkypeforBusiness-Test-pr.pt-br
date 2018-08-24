---
title: Habilitar ou desabilitar hot-desk
TOCTitle: Habilitar ou desabilitar hot-desk
ms:assetid: 93a7fed6-f61a-4b41-9336-a8320afa87cf
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ994057(v=OCS.15)
ms:contentKeyID: 52057679
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Habilitar ou desabilitar hot-desk

 

_**Tópico modificado em:** 2013-02-20_

Você pode configurar telefones de área comum como *telefones do hot-desk*. Com os telefones do hot-desk, os usuários podem fazer logon em suas próprias contas de usuário e, depois de conectados, use os recursos do Lync Server e as configurações de perfil próprias do usuário. O Hot desk é gerenciado usando as políticas do cliente: para ativar ou desativar hot desk, você deve modificar as políticas do cliente que foram usadas pelos telefones de área comum. Para obter detalhes sobre como determinar as políticas de conferência que foram atribuídas aos telefones de área comum, consulte [Exibir informações sobre os telefones de área comum](lync-server-2013-view-common-area-phone-information.md).

Você usa o parâmetro EnableHotdesking do cmdlet **New-CSClientPolicy** ou o cmdlet **Set-CSClientPolicy** para ativar ou desativar o hot desk em um telefone, como segue. Execute esses cmdlets a partir do Shell de Gerenciamento do Lync Server 2013 ou de uma sessão remota do Windows PowerShell. Para obter detalhes sobre como usar o Windows PowerShell remoto para conectar ao Lync Server, consulte o artigo de blog do Lync Server Windows PowerShell, "Quick Start: Managing Microsoft Lync Server 2010 Using Remote PowerShell" em [http://go.microsoft.com/fwlink/p/?linkId=255876 (em inglês)](http://go.microsoft.com/fwlink/p/?linkid=255876).


## Ativar hot desk

  - Para ativar hot desk para um telefone de área comum, você deve modificar a política do cliente que foi atribuída a esse telefone (ou conjunto de telefones).
    
    Após você ter identificado a política que precisa ser modificada, a próxima etapa é usar o cmdlet **Set-CsClientPolicy** para definir o parâmetro EnableHotdesking como Verdadeiro. Por exemplo:
    
        Set-CsClientPolicy -Identity "CommonAreaPhonePolicy" - EnableHotdesking $True

  - Como alternativa, você pode usar o cmdlet **New-CsClientPolicy** para criar uma nova política do cliente que ativa hot desk. Por exemplo:
    
        New-CsClientPolicy -Identity "NewCommonAreaPhonePolicy" - EnableHotdesking $True

> [!IMPORTANT]  
> Após essa política ter sido criada, você deve atribuí-la aos telefones de área comum apropriados. Para obter detalhes, consulte <a href="lync-server-2013-assign-policies-to-a-common-area-phone.md">Atribuir políticas a um telefone de área comum</a>.

## Desativar hot desk

  - Para desativar hot desk para um telefone de área comum, redefina o parâmetro EnableHotdesking do cmdlet **Set-CsClientPolicy** para o valor padrão como Falso. Por exemplo:
    
        Set-CsClientPolicy -Identity "CommonAreaPhonePolicy" - EnableHotdesking $False

Para obter detalhes, consulte os tópicos de Ajuda para o cmdlet [New-CsClientPolicy](https://docs.microsoft.com/en-us/powershell/module/skype/New-CsClientPolicy) e o cmdlet [Set-CsClientPolicy](https://docs.microsoft.com/en-us/powershell/module/skype/Set-CsClientPolicy).

