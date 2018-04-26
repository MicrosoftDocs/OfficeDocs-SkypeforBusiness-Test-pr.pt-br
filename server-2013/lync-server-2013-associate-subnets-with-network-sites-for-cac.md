---
title: Associar subredes com locais de rede para o CAC no Lync Server 2013
TOCTitle: Associar subredes com locais de rede para o CAC no Lync Server 2013
ms:assetid: a749c9b3-15f3-4e74-9f43-1507d3c2c940
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg412786(v=OCS.15)
ms:contentKeyID: 49307719
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Associar subredes com locais de rede para o CAC no Lync Server 2013

 

_**Tópico modificado em:** 2012-10-20_

Todas as sub-redes em sua rede devem ser associadas a um site de rede específico. A razão para isso é que as informações de sub-rede são usadas para determinar o site de rede em que um ponto de extremidade está localizado. Quando os locais de ambas as partes de uma sessão são conhecidos, o controle de admissão de chamadas (CAC) pode determinar se há largura de banda suficiente para estabelecer uma chamada.

O controle de admissão de chamadas não possui requisitos especiais para associar sub-redes a sites de rede. Para criar uma associação entre as sub-redes e sites de rede em sua topologia, siga os procedimentos em [Associar uma subrede a um site de rede no Lync Server 2013](lync-server-2013-associate-a-subnet-with-a-network-site.md). Para exibir os sites de rede (e suas respectivas sub-redes) na topologia de rede de exemplo para o controle de admissão de chamadas, consulte [Exemplo: Coletando seus requisitos para controle de admissão de chamada no Lync Server 2013](lync-server-2013-example-of-gathering-your-requirements-for-call-admission-control.md) na documentação de Planejamento.

