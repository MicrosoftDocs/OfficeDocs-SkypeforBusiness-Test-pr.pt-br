---
title: Exibir informações do plano de discagem no Lync Server 2013
TOCTitle: Exibir informações do plano de discagem no Lync Server 2013
ms:assetid: 25ed0112-a8a7-418a-8c2c-580081be692a
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ687997(v=OCS.15)
ms:contentKeyID: 49886139
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Exibir informações do plano de discagem no Lync Server 2013

 

_**Tópico modificado em:** 2012-11-01_

Para exibir informações de um plano de discagem existente, realize as etapas no seguinte procedimento. Se deseja criar um novo plano de discagem, consulte [Criar um plano de discagem no Lync Server 2013](lync-server-2013-create-a-dial-plan.md).

## Para exibir informações sobre um plano de discagem do Painel de Controle do Lync Server

1.  Faça logon no computador como um membro do grupo RTCUniversalServerAdmins ou como um membro da função CsVoiceAdministrator, CsServerAdministrator ou CsAdministrator. Para obter detalhes, consulte [Delegar permissões de configuração no Lync Server 2013](lync-server-2013-delegate-setup-permissions.md).

2.  Abra uma janela do navegador e insira a URL do Administrador para abrir o Painel de Controle do Lync Server. Para obter detalhes sobre os diferentes métodos que você pode usar para iniciar o Painel de Controle do Lync Server, consulte [Abrir ferramentas administrativas do Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

3.  Na barra de navegação esquerda, clique em **Roteamento de Voz** e clique em **Plano de Discagem**.

4.  Na página **Plano de Discagem**, dê um duplo clique no nome de um plano de discagem.
    
    > [!NOTE]  
    > É possível exibir informações para apenas um plano de discagem por vez.

## Exibir planos de discagem usando cmdlets do Windows PowerShell

  - Os planos de discagem também podem ser exibidos utilizando o cmdlet Interface da linha de comando do Windows PowerShell e **Get-CsDialPlan**. Este cmdlet pode ser executado pelo Shell de Gerenciamento do Lync Server 2013 ou de uma sessão remota do Windows PowerShell. Para obter detalhes sobre como usar o Windows PowerShell remoto para conectar ao Lync Server, consulte o artigo de blog do Lync Server Windows PowerShell, "Quick Start: Managing Microsoft Lync Server 2010 Using Remote PowerShell" em [http://go.microsoft.com/fwlink/p/?linkId=255876 (em inglês)](http://go.microsoft.com/fwlink/p/?linkid=255876).
    
    Para exibir informações sobre todos os seus planos de discagem, digite o seguinte comando no Shell de Gerenciamento do Lync Server e pressione ENTER:
    
        Get-CsDialPlan
    
    Este comando retornará informações semelhantes ao seguinte:
    
        Identity                 : Global
        Description              :
        DialinConferencingRegion :
        NormalizationRules       : {Description=;
                                   Pattern=^(\d+)$;Translation=$1;Name=
                                   KeepAll;IsInternalExtension=False}
        CountryCode              :
        State                    :
        City                     :
        ExternalAccessPrefix     :
        SimpleName               : DefaultProfile
        OptimizeDeviceDialing    : False

## Consulte Também

#### Tarefas

[Criar um plano de discagem no Lync Server 2013](lync-server-2013-create-a-dial-plan.md)  
[Modificar um plano de discagem no Lync Server 2013](lync-server-2013-modify-a-dial-plan.md)

