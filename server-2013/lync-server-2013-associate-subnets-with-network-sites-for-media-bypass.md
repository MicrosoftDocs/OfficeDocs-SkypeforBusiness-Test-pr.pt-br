---
title: Associar subredes com locais de rede para bypass de mídia
TOCTitle: Associar subredes com locais de rede para bypass de mídia
ms:assetid: 5bc632b7-1446-470f-b332-48ea0ca4d1fd
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398401(v=OCS.15)
ms:contentKeyID: 49306830
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Associar subredes com locais de rede para bypass de mídia

 

_**Tópico modificado em:** 2012-09-12_

> [!NOTE]  
> Este tópico assume que você tenha definido as configurações globais de desvio de mídia, a região da rede e os locais de rede para desvio de mídia.

Cada sub-rede em sua rede deve ser associada a um site de rede específico. Isso ocorre porque as informações da sub-rede são usadas para determinar o site de rede no qual um ponto de extremidade está localizado. Quando os locais de ambas as partes em uma sessão são conhecidos, os desvio de mídia pode determinar para onde a mídia é enviada para processamento.

O desvio de mídia não tem requisitos especiais para associar sub-redes a sites de rede. Para criar uma associação entre os sites de rede e as sub-redes em sua topologia, siga os procedimentos em [Associar uma subrede a um site de rede no Lync Server 2013](lync-server-2013-associate-a-subnet-with-a-network-site.md).

## Próximas etapas: criar perfis de políticas de largura de banda

Depois de associar sub-redes a sites da rede para o desvio de mídia, você deverá criar um ou mais perfis de política de largura de banda que dividirão as sub-redes entre aquelas com boa conectividade e aquelas sem, para fins de desvio de mídia. Todas as sub-redes em uma região com sites de rede que não têm restrições de largura de banda possuem boa conectividade e, portanto, essas sub-redes podem usar o desvio de mídia.

Para obter procedimentos para configurar os perfis de políticas de largura de banda, consulte [Criar perfis da política de largura de banda no Lync Server 2013](lync-server-2013-create-bandwidth-policy-profiles.md).

