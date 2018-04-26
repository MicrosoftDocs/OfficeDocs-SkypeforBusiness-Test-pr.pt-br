---
title: 'Lync Server 2013: Failover de banco de dados espelhado'
TOCTitle: Failover de banco de dados espelhado
ms:assetid: 70185476-e3d4-440a-9316-fa24b226343e
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ204991(v=OCS.15)
ms:contentKeyID: 49307066
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Failover de banco de dados espelhado no Lync Server 2013

 

_**Tópico modificado em:** 2014-03-14_

Caso tenha configurado o banco de dados back-end para usar espelhamento sincronizado com uma testemunha, o failover será automático. Caso tenha configurado o espelhamento automático sem uma testemunha, você poderá usar os procedimentos a seguir para realizar failover e failback do banco de dados. Você também pode usar esses procedimentos para realizar failover e failback manual dos bancos de dados mesmo com uma testemunha configurada.

## Para realizar failover do banco de dados back-end

1.  Antes de realizar o failover, determine qual é o banco de dados back-end principal e qual é o espelho digitando o cmdlet a seguir:
    
        Get-CsDatabaseMirrorState -PoolFqdn <poolFQDN> -DatabaseType User

2.  Caso o Repositório de Gerenciamento Central seja hospedado neste pool, digite o cmdlet a seguir para determinar qual é o principal e qual é o espelho para Repositório de Gerenciamento Central:
    
        Get-CsDatabaseMirrorState -PoolFqdn <poolFQDN> -DatabaseType CentralMgmt

3.  Realize o failover do banco de dados do usuário:
    
      - Se o principal falhar e você estiver realizando failover para o espelho, digite:
        
            Invoke-CsDatabaseFailover -PoolFqdn <poolFQDN> -DatabaseType User -NewPrincipal mirror -Verbose
    
      - Se o espelho falhar e você estiver realizando failover para o principal, digite:
        
            Invoke-CsDatabaseFailover -PoolFqdn <poolFQDN> -DatabaseType User -NewPrincipal primary -Verbose

4.  Se o pool hospedar o Servidor de Gerenciamento Central, realize failover do Repositório de Gerenciamento Central.
    
      - Se o principal falhar e você estiver realizando failover para o espelho, digite:
        
            Invoke-CsDatabaseFailover -PoolFqdn <poolFQDN> -DatabaseType CentralMgmt -NewPrincipal mirror -Verbose
    
      - Se o espelho falhar e você estiver realizando failover para o principal, digite:
        
            Invoke-CsDatabaseFailover -PoolFqdn <poolFQDN> -DatabaseType CentralMgmt -NewPrincipal primary -Verbose

