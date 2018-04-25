---
title: Cmdlets de infraestrutura e implantação
TOCTitle: Cmdlets de infraestrutura e implantação
ms:assetid: 0a6e872a-9f70-4f23-a4a5-8820dbf55370
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398153(v=OCS.15)
ms:contentKeyID: 49305829
ms.date: 12/10/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Cmdlets de infraestrutura e implantação

 

_**Tópico modificado em:** 2016-12-08_

Os cmdlets de infraestrutura e implantação incluídos no Microsoft Lync Server 2013 podem ser úteis na configuração e implantação iniciais do produto; após a implantação do Lync Server, esses cmdlets poderão ser usados para verificar se os componentes estão funcionando como esperado, gerenciar configurações de replicação e fazer o backup e a restauração da topologia, das políticas e das configurações do Lync Server.

## Cmdlets de infraestrutura e implantação

Os administradores raramente precisarão chamar muitas das infraestruturas e implantações diretamente. Isso porque esses cmdlets são invocados automaticamente quando você executa o arquivo de Instalação ou o Construtor de Topologias. (Uma grande exceção pode ser o cmdlet **Export-CsConfiguration**, o qual permite que você faça uma cópia de da sua topologia Lync Server, das suas políticas e das definições de configuração). Porém, e quando necessário, os cmdlets da infraestrutura e da implantação também podem ser executados a partir do Shell de Gerenciamento do Lync Server ou de dentro de um script. Usar um script permite que você automatize determinadas tarefas. A seguir, é apresentada uma lista de cmdlets que se relacionam diretamente à infraestrutura e implantação:

**[Cmdlets do Active Directory](lync-server-2013-active-directory-cmdlets.md)**

  -   
    [Disable-CsAdDomain](disable-csaddomain.md)

  -   
    [Enable-CsAdDomain](enable-csaddomain.md)

  -   
    [Get-CsAdDomain](get-csaddomain.md)

  -   
    [Disable-CsAdForest](disable-csadforest.md)

  -   
    [Enable-CsAdForest](enable-csadforest.md)

  -   
    [Get-CsAdForest](get-csadforest.md)

  -   
    [Get-CsAdServerSchema](get-csadserverschema.md)

  -   
    [Install-CsAdServerSchema](install-csadserverschema.md)

**[Cmdlets de replicação](lync-server-2013-replication-cmdlets.md)**

  -   
    [Debug-CsInterPoolReplication](debug-csinterpoolreplication.md)

  -   
    [Invoke-CsManagementStoreReplication](invoke-csmanagementstorereplication.md)

  -   
    [Get-CsManagementStoreReplicationStatus](get-csmanagementstorereplicationstatus.md)

  -   
    [Enable-CsReplica](enable-csreplica.md)

  -   
    [Test-CsReplica](test-csreplica.md)

  -   
    [Get-CsUserReplicatorConfiguration](get-csuserreplicatorconfiguration.md)

  -   
    [New-CsUserReplicatorConfiguration](new-csuserreplicatorconfiguration.md)

  -   
    [Remove-CsUserReplicatorConfiguration](remove-csuserreplicatorconfiguration.md)

  -   
    [Set-CsUserReplicatorConfiguration](set-csuserreplicatorconfiguration.md)

**[Cmdlets de topologia](lync-server-2013-topology-cmdlets.md)**

  -   
    [Get-CsPool](get-cspool.md)

  -   
    [Get-CsSite](get-cssite.md)

  -   
    [Set-CsSite](set-cssite.md)

  -   
    [Enable-CsTopology](enable-cstopology.md)

  -   
    [Get-CsTopology](get-cstopology.md)

  -   
    [Publish-CsTopology](publish-cstopology.md)

  -   
    [Test-CsTopology](test-cstopology.md)

  -   
    [Export-CsConfiguration](export-csconfiguration.md)

  -   
    [Import-CsConfiguration](import-csconfiguration.md)

  -   
    [Get-CsServerVersion](get-csserverversion.md)

  -   
    [Disable-CsComputer](disable-cscomputer.md)

  -   
    [Enable-CsComputer](enable-cscomputer.md)

  -   
    [Get-CsComputer](get-cscomputer.md)

  -   
    [Test-CsComputer](test-cscomputer.md)

  -   
    [Get-CsNetworkInterface](get-csnetworkinterface.md)

**[Cmdlets de Backup e Alta Disponibilidade](lync-server-2013-backup-and-high-availability-cmdlets.md)**

  - [Get-CsBackupServiceConfiguration](get-csbackupserviceconfiguration.md)

  - [Remove-CsBackupServiceConfiguration](remove-csbackupserviceconfiguration.md)

  - [Set-CsBackupServiceConfiguration](set-csbackupserviceconfiguration.md)

  - [Get-CsBackupServiceStatus](get-csbackupservicestatus.md)

  - [Invoke-CsBackupServiceSync](invoke-csbackupservicesync.md)

  - [Debug-CsIntraPoolReplication](debug-csintrapoolreplication.md)

  - [Backup-CsPool](backup-cspool.md)

  - [Get-CsPoolBackupRelationship](get-cspoolbackuprelationship.md)

  - [Get-CsPoolFabricState](get-cspoolfabricstate.md)

  - [Invoke-CsPoolFailBack](invoke-cspoolfailback.md)

  - [Invoke-CsPoolFailOver](invoke-cspoolfailover.md)

  - [Get-CsPoolUpgradeReadinessState](get-cspoolupgradereadinessstate.md)

  - [Invoke-CsStorageServiceFlush](invoke-csstorageserviceflush.md)

  - [Sync-CsUserData](sync-csuserdata.md)

  - [Remove-CsUserStoreBackupData](remove-csuserstorebackupdata.md)

## Consulte Também

#### Outros Recursos

[Blog Lync Server PowerShell](http://go.microsoft.com/fwlink/?linkid=203150%26clcid=0x416)

