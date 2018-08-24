---
title: "Lync Server 2013: Restaurando conteúdos de confer. usando o Serviço de Backup"
TOCTitle: Restaurando conteúdos de conferência usando o Serviço de Backup
ms:assetid: 3e0f18ec-7319-4c07-a59b-2938e7787bc9
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ688030(v=OCS.15)
ms:contentKeyID: 49886187
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Restaurando conteúdos de conferência usando o Serviço de Backup no Lync Server 2013

 

_**Tópico modificado em:** 2012-11-01_

Se a informação de conferência armazenada no repositório de arquivo de um pool de Front Ends se tornar indisponível, você deverá restaurar essa informação para que os usuários hospedados no pool recuperem os dados de conferência. Caso o pool de Front End que perdeu os dados de conferência esteja pareado com outro pool de Front End, você pode utilizar o Serviço de Backup para restaurar os dados.

Você também deve efetuar tal tarefa caso todo um pool falhe e você tenha que executar failover nos usuários para um pool de backup. Quando esses usuários retornarem para o pool original, você deve utilizar este procedimento para copiar o conteúdo de conferência de volta para o pool original.

Presuma que o Pool1 está pareado com o Pool2, e os dados de conferência de Pool1 foram perdidos. É possível usar o seguinte cmdlet para chamar o Serviço de Backup para restaurar o conteúdo:

    Invoke-CsBackupServiceSync -PoolFqdn <Pool2 FQDN> -BackupModule ConfServices.DataConf

Restaurar o conteúdo pode levar algum tempo, dependendo do tamanho. Você pode utilizar o seguinte cmdlet para verificar o status do processo:

    Get-CsBackupServiceStatus -PoolFqdn <Pool2 FQDN> -BackupModule ConfServices.DataConf

O processo é concluído quando este cmdlet retorna um valor de Estado Estável para o módulo de conferência de dados.

