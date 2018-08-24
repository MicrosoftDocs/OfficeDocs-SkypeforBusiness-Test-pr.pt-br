---
title: Criar políticas entre locais de rede no Lync Server 2013
TOCTitle: Criar políticas entre locais de rede no Lync Server 2013
ms:assetid: b0714aae-55dc-4587-b718-34a03f596b22
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg412844(v=OCS.15)
ms:contentKeyID: 49307837
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Criar políticas entre locais de rede no Lync Server 2013

 

_**Tópico modificado em:** 2012-10-19_

Uma *política entre sites de rede* define limitações de largura de banda entre sites com links de WAN diretos entre eles.

Para detalhes, consulte a documentação do Shell de Gerenciamento do Lync Server para os seguintes cmdlets:

  - [New-CsNetworkInterSitePolicy](https://docs.microsoft.com/en-us/powershell/module/skype/New-CsNetworkInterSitePolicy)

  - [Get-CsNetworkInterSitePolicy](https://docs.microsoft.com/en-us/powershell/module/skype/Get-CsNetworkInterSitePolicy)

  - [Set-CsNetworkInterSitePolicy](https://docs.microsoft.com/en-us/powershell/module/skype/Set-CsNetworkInterSitePolicy)

  - [Remove-CsNetworkInterSitePolicy](https://docs.microsoft.com/en-us/powershell/module/skype/Remove-CsNetworkInterSitePolicy)

> [!IMPORTANT]  
> Uma política entre sites de rede é obrigatória <em>somente</em> se houver um link cruzado direto entre dois sites de rede.

Na região América do Norte da topologia de exemplo, existe um link direto entre os sites Reno e Albuquerque. Esses dois sites exigem uma política entre sites que aplique um perfil de política de largura de banda adequado. O exemplo a seguir aplica o perfil 20Mb\_Link.

## Para criar uma política entre sites da rede

1.  Inicie o Shell de Gerenciamento do Lync Server: clique em **Iniciar**, em **Todos os Programas**, em **Microsoft Lync Server 2013** e em **Shell de Gerenciamento do Lync Server**.

2.  Execute o cmdlet New-CsNetworkInterSitePolicy para criar política entre sites de rede e aplicar um perfil de política de largura de banda apropriado para dois sites que possuem um link cruzado direto. Por exemplo, execute:
    
        New-CsNetworkInterSitePolicy -InterNetworkSitePolicyID Reno_Albuquerque -NetworkSiteID1 Reno -NetworkSiteID2 Albuquerque -BWPolicyProfileID 20Mb_Link

3.  Repita a etapa 2 conforme o necessário para criar políticas entre sites de rede para todos os pares de sites da rede que possuírem um link cruzado direto.

