---
title: 'Lync Server 2013: (Opcional) Verificar configurações de conferência discada'
TOCTitle: (Opcional) Verificar configurações de conferência discada
ms:assetid: a85efdda-97b0-4f3b-bd26-04416bee8ef5
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg412789(v=OCS.15)
ms:contentKeyID: 49307726
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# (Opcional) Verificar configurações de conferência discada no Lync Server 2013

 

_**Tópico modificado em:** 2010-11-02_

Como verificação final da configuração da conferência discada, você pode pesquisar planos de discagem com uma região de conferência discada que não seja usada por nenhum número de acesso e números de acesso que não possuem uma região de conferência discada especificada. Essa etapa é opcional.

## Para encontrar planos de discagem com uma região de conferência discada que não seja usada por um número de acesso

1.  Faça logon no computador como membro do grupo RTCUniversalServerAdmins ou como membro da função **Cs-ServerAdministrator** ou **CsAdministrator** .

2.  Inicie o Shell de Gerenciamento do Lync Server: clique em **Iniciar**, em **Todos os Programas**, em **Microsoft Lync Server 2013** e em **Shell de Gerenciamento do Lync Server**.

3.  Execute o seguinte no prompt de comando:
    
        Get-CsDialinConferencingAccessNumber -EmptyRegion
    
    Este cmdlet retorna todos os planos de discagem que possuem uma região de conferência discada que não é usada por um número de acesso.

## Para encontrar números de acesso sem regiões atribuídas

1.  Faça logon no computador como membro do grupo RTCUniversalServerAdmins ou como membro da função **Cs-ServerAdministrator** ou **CsAdministrator** .

2.  Inicie o Shell de Gerenciamento do Lync Server: clique em **Iniciar**, em **Todos os Programas**, em **Microsoft Lync Server 2013** e em **Shell de Gerenciamento do Lync Server**.

3.  Execute o seguinte no prompt de comando:
    
        Get-CsDialinConferencingAccessNumber -Region NULL
    
    Este cmdlet retorna todos números de acesso de conferência discada que não estão associados a uma região.

