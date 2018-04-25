---
title: 'Lync Server 2013: Failback de pool'
TOCTitle: Failback de pool
ms:assetid: 6232b644-ef57-4c9c-abec-14ff8ffc9fe7
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ204945(v=OCS.15)
ms:contentKeyID: 49306899
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Failback de pool no Lync Server 2013

 

_**Tópico modificado em:** 2012-11-01_

Depois que o pool que passou por desastre voltar a ficar online (ou seja, o Pool1 neste exemplo), execute as etapas a seguir para restaurar sua implantação para o status funcional normal.

O processo de failback leva vários minutos para ser concluído.  Como referência, espera-se que leve até 60 minutos para um pool de 20 mil usuários.

1.  Para fazer failback dos usuários que estavam originalmente hospedados no Pool1 e dos quais foi feito failover para o Pool2, digite o seguinte cmdlet:
    
        Invoke-CsPoolFailback -PoolFQDN <Pool1 FQDN> -Verbose

Nenhuma outra etapa é necessária. Se você tiver feito failover do Servidor de Gerenciamento Central, poderá deixá-lo no Pool2.

