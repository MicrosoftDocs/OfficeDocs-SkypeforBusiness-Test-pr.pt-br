---
title: "Lync Server 2013: Certifique-se de que os planos de discagem têm opções atribuídas"
TOCTitle: Certifique-se de que os planos de discagem têm opções atribuídas
ms:assetid: 3da3a907-0dbf-4440-b12f-370f94dd4c17
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg425903(v=OCS.15)
ms:contentKeyID: 49306480
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Certifique-se de que os planos de discagem do Lync Server 2013 têm opções atribuídas

 

_**Tópico modificado em:** 2010-11-02_

Os planos de discagem que serão usados em conferências discadas precisam ter uma **Região de conferência discada** especificada para associar os números de acesso de conferência discada ao plano de discagem apropriado. Ao configurar um plano de discagem, especifique a região de conferência discada que se aplica ao plano de discagem. Em seguida, ao criar o número de acesso discado, selecione as regiões que associam esse número de acesso aos planos de discagem apropriados.

Como é importante especificar uma região para todos os planos de discagem, recomendamos usar este procedimento para verificar se todos os planos de discagem têm regiões. Esta etapa é opcional.

Use o cmdlet **Get-CsDialPlan** para verificar se a região está definida para todos os planos de discagem da conferência discada. Se a região não existir nos planos de discagem, você poderá usar o cmdlet **Set-CsDialPlan** para defini-la. Também é possível usar o Painel de Controle do Lync Server para atualizar a região nos planos de discagem existentes. Para obter detalhes sobre como usar o Painel de Controle do Lync Server, consulte [Modificar um plano de discagem no Lync Server 2013](lync-server-2013-modify-a-dial-plan.md).

## Para verificar se os planos de discagem têm a propriedade de região definida

1.  Efetue logon no computador como membro do grupo RTCUniversalServerAdmins ou como membro da função **Cs-VoiceAdministrator** , **Cs-ServerAdministrator** ou **CsAdministrator** .

2.  Inicie o Shell de Gerenciamento do Lync Server: clique em **Iniciar**, em **Todos os Programas**, em **Microsoft Lync Server 2013** e em **Shell de Gerenciamento do Lync Server**.

3.  Execute o seguinte no prompt de comando:
    
        Get-CsDialPlan [-Identity <Identifier of the dial plans to be retrieved>]
    
    Por exemplo:
    
        Get-CsDialPlan
    
    Neste exemplo, todos os planos de discagem configurados para sua organização são retornados.

4.  Revise os planos de discagem retornados para identificar todos que estão faltando na região da conferência discada. Para obter detalhes, consulte a documentação do Shell de Gerenciamento do Lync Server.

## Para definir a propriedade de região de um plano de discagem

1.  Efetue logon no computador como membro do grupo RTCUniversalServerAdmins ou como membro da função **Cs-VoiceAdministrator** , **Cs-ServerAdministrator** ou **CsAdministrator** .

2.  Inicie o Shell de Gerenciamento do Lync Server: clique em **Iniciar**, em **Todos os Programas**, em **Microsoft Lync Server 2013** e em **Shell de Gerenciamento do Lync Server**.

3.  Para todos os planos de discagem que não têm a região de conferência discada, execute:
    
        Set-CsDialPlan [-Identity <Identity of the dial plan to be modified>] -DialinConferencingRegion "<new region>"
    
    Por exemplo:
    
        Set-CsDialPlan -Identity Redmond -DialinConferencingRegion "US West Coast"
    
    Neste exemplo, o plano de discagem com Identidade de Redmond é modificado para definir a propriedade DialinConferencingRegion como "Costa Leste dos EUA". Para obter detalhes, consulte a documentação do Shell de Gerenciamento do Lync Server.

