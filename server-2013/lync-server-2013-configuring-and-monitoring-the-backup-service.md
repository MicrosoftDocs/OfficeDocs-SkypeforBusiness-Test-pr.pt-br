---
title: 'Lync Server 2013: Configurando e monitorando o Serviço de Backup'
TOCTitle: Configurando e monitorando o Serviço de Backup
ms:assetid: c608280e-a7d1-4ae0-a75c-da6b524752fa
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ205252(v=OCS.15)
ms:contentKeyID: 49308054
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Configurando e monitorando o Serviço de Backup no Lync Server 2013

 

_**Tópico modificado em:** 2012-11-01_

É possível usar os seguintes comandos do Shell de Gerenciamento do Lync Server para configurar e monitorar o Serviço de Backup.

> [!NOTE]  
> O grupo RTCUniversalServerAdmins é o único grupo que possui permissões para executar o <strong>Get-CsBackupServiceStatus</strong> por padrão. Para usar este cmdlet, faça o login como membro deste grupo. Em alternativa, é possível conceder acesso a este comando para outros grupos (por exemplo, CSAdministrator) usando o cmdlet <strong>Set-CsBackupServiceConfiguration</strong>.

## Para ver a configuração do Serviço de Backup

Execute o seguinte cmdlet:

    Get-CsBackupServiceConfiguration

O padrão para SyncInterval é dois minutos.

## Para definir o intervalo de sincronização do Serviço de Backup

Execute o seguinte cmdlet:

    Set-CsBackupServiceConfiguration -SyncInterval interval

Por exemplo, o seguinte define o intervalo para três minutos.

    Set-CsBackupServiceConfiguration -SyncInterval 00:03:00

> [!IMPORTANT]  
> Embora seja possível usar este cmdlet para alterar o intervalo de sincronização padrão para o Serviço de Backup, você não deve fazer menos do que o absolutamente necessário, pois o intervalo de sincronização possui um grande impacto no desempenho do Serviço de Backup e o objetivo de ponto de recuperação (RPO).

## Para obter o status do Serviço de Backup para um determinado pool

Execute o seguinte cmdlet:

    Get-CsBackupServiceStatus -PoolFqdn <pool-FQDN>

> [!NOTE]  
> O status de sincronização do Serviço de Backup é definido unidirecionalmente de um pool (P1) para seu pool de backup (P2). O status de sincronização de P1 para P2 pode ser diferente do que de P2 para P1. Para P1 para P2, o Serviço de Backup está em estado &quot;pronto&quot; se todas as alterações realizadas em P1 são completamente replicadas para P2 dentro do intervalo de sincronização. Está no estado “final” se não há mais mudanças a serem sincronizadas de P1 para P2. Ambos os estados indicam um instantâneo do Serviço de Backup no momento que o cmdlet é executado. Não implica que o estado retornado permanecerá como é posteriormente. Em particular, o estado “final” continuará a manter apenas se P1 não gerar qualquer mudança após o cmdlet ser executado. Isto é verdadeiro em caso de falha de P1 por P2 após P1 ser inserido no modo somente leitura como parte da lógica de execução do <strong>Invoke-CsPoolfailover</strong>.

## Para obter informações sobre a relação de backup de um determinado pool

Execute o seguinte cmdlet:

    Get-CsPoolBackupRelationship -PoolFQDN <poolFQDN>

## Para forçar uma sincronização do Serviço de Backup

Execute o seguinte cmdlet:

    Invoke-CsBackupServiceSync -PoolFqdn <poolFqdn> [-BackupModule  {All|PresenceFocus|DataConf|CMSMaster}]

