---
title: 'Lync Server 2013: Fazendo failover de um pool'
TOCTitle: Fazendo failover de um pool
ms:assetid: 10b13732-bc80-4cb2-a71c-56b1d6cb5bbb
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ204678(v=OCS.15)
ms:contentKeyID: 49305916
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Fazendo failover de um pool no Lync Server 2013

 

_**Tópico modificado em:** 2014-10-10_

Se um único pool de Front End falhar e for necessário fazer failover, use o procedimento a seguir. Neste procedimento, o Datacenter1 contém o Pool1, que falhou. Você fará failover no Pool2 localizado no Datacenter2.

A maior parte do trabalho para o failover do pool envolver o failover do Repositório de Gerenciamento Central, se necessário. Isso é importante porque o Repositório de Gerenciamento Central deve estar funcional no momento do failover dos usuários do pool.

Além disso, se um pool de Front End falhar mas o pool de Borda no local ainda estiver em execução, você deve saber se o pool de Borda usa o pool com falha como pool do próximo salto. Se usar, você deve alterar o pool de Borda para usar um pool de Front End diferente antes de fazer o failover do pool de Front End com falha. Como a configuração do próximo salto será alterada dependerá de a Borda usar um pool no mesmo local do pool de Borda ou em um local diferente.

**Para definir um pool de Borda para usar um pool do próximo salto no mesmo local**

1.  Abra o Construtor de Topologias, clique com o botão direito no pool de Borda que precisa ser alterado e clique em **Editar Propriedades** .

2.  Clique em **Próximo Salto** . Na lista **Pool do próximo salto:** , selecione o pool que servirá como pool do próximo salto.

3.  Clique em **OK** e publique as alterações.

**Para definir um pool de Borda para usar um pool do próximo salto em um local diferente**

1.  Abra uma janela do Shell de Gerenciamento do Lync Server e digite o seguinte cmdlet:
    
        Set-CsEdgeServer -Identity EdgeServer:<Edge Server pool FQDN> -Registrar Registrar:<NextHopPoolFQDN>

**Para fazer failover de um pool em um desastre**

1.  Encontre o pool que hospeda o Servidor de Gerenciamento Central digitando o cmdlet a seguir em um servidor de Front End no Pool2:
    
        Invoke-CsManagementServerFailover -Whatif
    
    Os resultados deste cmdlet exibem qual pool hospeda o Servidor de Gerenciamento Central atualmente. No restante deste procedimento, este pool será conhecido como CMS\_Pool.

2.  Use o Construtor de Topologias para encontrar a versão do Lync Server que está em execução no CMS\_Pool. Se estiver executando o Lync Server 2013, use o cmdlet a seguir para encontrar o pool de backup do Pool 1.
    
        Get-CsPoolBackupRelationship -PoolFQDN <CMS_Pool FQDN>
    
    Digamos que Backup\_Pool será o pool de backup.

3.  Verifique o status do Repositório de Gerenciamento Central com o seguinte cmdlet:
    
        Get-CsManagementStoreReplicationStatus -CentralManagementStoreStatus 
    
    Este cmdlet deve exibir que ambos, ActiveMasterFQDN e ActiveFileTransferAgents, estão apontando para o FQDN do CMS\_Pool. Se estiverem vazios, o Servidor de Gerenciamento Central não está disponível e você deve fazer o failover.

4.  Se o Repositório de Gerenciamento Central não estiver disponível ou se o Repositório de Gerenciamento Central estava em execução no Pool1 (ou seja, o pool que falhou), você deve fazer failover do Servidor de Gerenciamento Central antes de fazer failover do pool. Se for necessário fazer failover do Servidor de Gerenciamento Central que estava hospedado em um pool executando o Lync Server 2013, use o cmdlet da etapa 5 deste procedimento. Se for necessário fazer failover do Servidor de Gerenciamento Central que estava hospedado em um pool executando o Lync Server 2010, use o cmdlet da etapa 6 deste procedimento. Se não for necessário fazer failover do Servidor de Gerenciamento Central, pule para a etapa 7 deste procedimento.

5.  Para fazer failover do Repositório de Gerenciamento Central em um pool executando o Lync Server 2013, faça o seguinte:
    
      - Primeiro, verifique qual Servidor de Back End no Backup\_Pool executa a instância principal do Repositório de Gerenciamento Central digitando:
        
            Get-CsDatabaseMirrorState -DatabaseType Centralmgmt -PoolFqdn <Backup_Pool Fqdn>
    
      - Se o servidor primário de Back End no Backup\_Pool for o principal, digite:
        
            Invoke-CSManagementServerFailover -BackupSQLServerFqdn <Backup_Pool Primary BackEnd Server FQDN> -BackupSQLInstanceName <Backup_Pool Primary SQL Instance Name>
        
        Se o servidor espelho de Back End no Backup\_Pool for o principal, digite:
        
            Invoke-CSManagementServerFailover -MirrorSQLServerFqdn <Backup_Pool Mirror BackEnd Server FQDN> -MirrorSQLInstanceName <Backup_Pool Mirror SQL Instance Name>
    
      - Valide se o failover do Servidor de Gerenciamento Central está concluído. Digite:
        
            Get-CsManagementStoreReplicationStatus -CentralManagementStoreStatus 
        
        Verifique se ambos, ActiveMasterFQDN e ActiveFileTransferAgents, estão apontando para o FQDN do Backup\_Pool.
    
      - Finalmente, verifique o status da réplica para todos os Servidores Front-End, digitando:
        
            Get-CsManagementStoreReplicationStatus 
        
        Verifique se todas as réplicas possuem o valor Verdadeiro (True).
        
        Pule para a etapa 7 neste procedimento.

6.  Instale o Repositório de Gerenciamento Central no Servidor de Back End do Backup\_Pool.
    
      - Primeiro, execute o seguinte comando:
        
        ``` 
        Install-CsDatabase -CentralManagementDatabase -Clean -SqlServerFqdn <Backup_Pool Back End Server FQDN> -SqlInstanceName rtc  
        ```
    
      - Execute o próximo comando em um dos servidores de Front End do Backup\_Pool para forçar a movimentação do Repositório de Gerenciamento Central:
        
            Move-CsManagementServer -ConfigurationFileName c:\CsConfigurationFile.zip -LisConfigurationFileName c:\CsLisConfigurationFile.zip -Force 
    
      - Valide se a movimentação está concluída:
        
            Get-CsManagementStoreReplicationStatus -CentralManagementStoreStatus 
        
        Verifique se ambos, ActiveMasterFQDN e ActiveFileTransferAgents, estão apontando para o FQDN do Backup\_Pool.
    
      - Verifique o status da réplica para todos os servidores de Front End digitando:
        
            Get-CsManagementStoreReplicationStatus 
        
        Verifique se todas as réplicas possuem o valor Verdadeiro (True).
    
      - Instale o serviço do Servidor de Gerenciamento Central no restante dos servidores de Front End no Backup\_Pool. Para isso, execute o comando a seguir em todos os servidores de Front End, exceto aquele usado ao forçar a movimentação do Repositório de Gerenciamento Central anteriormente neste procedimento:
        
            Bootstrapper /Setup 

7.  Faça o failover dos usuários do Pool1 para o Pool2 executando o cmdlet a seguir em uma janela do Shell de Gerenciamento do Lync Server:
    
        Invoke-CsPoolFailover -PoolFQDN <Pool1 FQDN> -DisasterMode -Verbose
    
    Como as etapas executadas nas partes anteriores deste procedimento para verificar o status do Repositório de Gerenciamento Central não são universais, ainda existe uma chance de que este cmdlet falhe devido ao failover do Repositório de Gerenciamento Central ainda não estar totalmente concluído. Neste caso, você deve corrigir o Repositório de Gerenciamento Central com base nas mensagens de erro exibidas e executar o cmdlet novamente.
    
    Se a mensagem de erro a seguir for apresentada, será necessário alterar o pool de Borda neste local para usar um pool diferente como próximo salto antes da fazer o failover do pool. Para detalhes, consulte os procedimentos no início deste tópico.
    
        Invoke-CsPoolFailOver : This Front-end pool "pool1.contoso.com" is specified in
        topology as the next hop for the Edge server. Failing over this pool may cause External
        access/Federation/Split-domain/XMPP features to stop working. Please use Topology Builder to
        change the Edge internal next hop setting to point to a different Front-end pool,  before you
        proceed.

