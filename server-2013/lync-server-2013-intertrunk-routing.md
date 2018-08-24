---
title: 'Lync Server 2013: Roteamento entre troncos'
TOCTitle: Roteamento entre troncos
ms:assetid: d3a33b4a-8bf4-4a8c-a371-8ef79e740780
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ205272(v=OCS.15)
ms:contentKeyID: 49308220
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Roteamento entre troncos no Lync Server 2013

 

_**Tópico modificado em:** 2012-10-20_

O Lync Server 2013 pode interconectar um IP-PBX a um gateway PSTN para que as chamadas de um telefone PBX possam ser roteadas para o PSTN e as chamadas de entrada do PSTN possam ser roteadas para um telefone PBX. Da mesma forma, o Lync Server 2013 pode interconectar dois ou mais sistemas IP-PBX para que as chamadas possam ser posicionadas e recebidas entre telefones PBX de sistemas IP-PBX diferentes.

Este recurso de roteamento entre troncos pode ser configurado usando o cmdlet Shell de Gerenciamento do Lync Server, **Set-CsTrunkConfiguration**, com o novo parâmetro, PstnUsages. Este parâmetro especifica o conjunto de registros de uso PSTN para utilizar. Um tronco usa este uso PSTN para determinar uma rota e rotear todas as chamadas de entrada da mesma forma.

    Set-CsTrunkConfiguration -Identity <TrunkId> -PstnUsages @{add="<UsageString>"}

O diagrama a seguir ilustra o Lync Server 2013 oferecendo interconectividade entre um gateway PSTN e um IP-PBX.

**Roteamento entre troncos entre o gateway e IP PBX**

![Diagrama do gateway PSTN de conexão/IP-PBX do Lync Server](images/JJ721940.cc3858ca-2ee3-4d51-8a51-db078366b50b(OCS.15).jpg "Diagrama do gateway PSTN de conexão/IP-PBX do Lync Server")

O diagrama a seguir ilustra a interconexão do Lync Server 2013 de dois sistemas IP-PBX.

**Roteamento entre troncos entre dois IP PBXs**

![Diagrama de sistemas IP-PAX de interconexão do Lync Server](images/JJ721940.6ba18ec9-df70-498a-9cf7-7fc41e5ec432(OCS.15).jpg "Diagrama de sistemas IP-PAX de interconexão do Lync Server")

