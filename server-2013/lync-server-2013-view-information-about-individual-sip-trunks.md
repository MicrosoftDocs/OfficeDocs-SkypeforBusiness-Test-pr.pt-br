---
title: Exibir Informações sobre Troncos SIP Individuais no Lync Server 2013
TOCTitle: Exibir Informações sobre Troncos SIP Individuais no Lync Server 2013
ms:assetid: adfacb74-7ea5-4c53-934e-ba7ec59879eb
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ721847(v=OCS.15)
ms:contentKeyID: 49886357
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Exibir Informações sobre Troncos SIP Individuais no Lync Server 2013

 

_**Tópico modificado em:** 2013-02-21_

Os troncos SIP são usados para conectar a rede telefônica de VoIP do Microsoft Lync Server 2013 com a Rede telefônica pública comutada. Na versão anterior do produto, os troncos foram usados para rotear chamadas de saída de um Servidor de mediação para um gateway PSTN e cada gateway estava limitado a um único tronco. Como resultado, um gateway PSTN e um tronco SIP eram essencialmente idênticos. Para os administradores isso significava que seria possível exibir informações sobre um tronco SIP individual exibindo informações sobre o gateway PSTN associado.

No entanto, no Lync Server 2013 é possível atribuir vários troncos a um único gateway PSTN; isso significa que os gateways e os troncos não são mais iguais. Por outro lado, isso significa que os administradores devem usar o novo cmdlet [Get-CsTrunk](https://docs.microsoft.com/en-us/powershell/module/skype/Get-CsTrunk) para exibir informações sobre um tronco SIP individual.

O cmdlet Get-CsTrunk pode ser executado do Shell de Gerenciamento do Lync Server 2013 ou de uma sessão remota do Windows PowerShell. Para obter detalhes sobre como usar o Windows PowerShell remoto para conectar ao Lync Server, consulte o artigo de blog do Lync Server Windows PowerShell, "Quick Start: Managing Microsoft Lync Server 2010 Using Remote PowerShell" em [http://go.microsoft.com/fwlink/p/?linkId=255876 (em inglês)](http://go.microsoft.com/fwlink/p/?linkid=255876).

## Exibindo informações para todos os seus Troncos SIP

  - O seguinte comando retorna informações sobre todos os troncos SIP usados em sua organização:
    
        Get-CsTrunk

## Exibindo informações de um Tronco SIP específico

  - Este comando retorna informações somente para o tronco SIP com a Identidade PstnGateway:192.168.0.240:
    
        Get-CsTrunk -Identity "PstnGateway:192.168.0.240"

## Exibindo informações para todos os Troncos SIP atribuídos a um pool

  - Neste exemplo, as informações são retornada para todos os troncos SIP atribuídos ao pool atl-cs-001.litwareinc.com:
    
        Get-CsTrunk -PoolFqdn "atl-cs-001.litwareinc.com"

