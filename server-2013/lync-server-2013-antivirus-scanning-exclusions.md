---
title: 'Lync Server 2013: Exclusões de verificação de antivírus'
TOCTitle: Exclusões de verificação de antivírus para Lync Server 2013
ms:assetid: 71e1f1cc-2d16-4111-9864-9276bf24dfe0
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Dn440138(v=OCS.15)
ms:contentKeyID: 59602796
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Exclusões de verificação de antivírus para Lync Server 2013

 

_**Tópico modificado em:** 2015-11-02_

Para certificar-se de que a varredura antivírus não interfere na operação do Lync Server 2013, você deve excluir os processos específicos e diretórios para cada servidor do Lync Server 2013 ou a função de servidor na qual você pode executar a varredura antivirus. Os seguintes processos e diretórios devem ser excluídos:

> [!NOTE]  
> Os locais fixos das pastas e dos arquivos listados abaixo são locais padrões para o Lync Server 2013. Para quaisquer locais, para os quais você não usa o padrão, exclua os locais que você especificou para a sua organização em vez dos locais padrão especificados neste tópico.

  - Processos do Lync Server 2013:
    
      - ABServer.exe
    
      - AcpMcuSvc.exe
    
      - ASMCUSvc.exe
    
      - AVMCUSvc.exe
    
      - ChannelService.exe
    
      - ClsAgent.exe
    
      - ComplianceService.exe
    
      - DataMCUSvc.exe
    
      - DataProxy.exe
    
      - FileTransferAgent.exe
    
      - IMMCUSvc.exe
    
      - LysSvc.exe
    
      - MasterReplicatorAgent.exe
    
      - MediaRelaySvc.exe
    
      - MediationServerSvc.exe
    
      - MRASSvc.exe
    
      - OcsAppServerHost.exe
    
      - ReplicaReplicatorAgent.exe
    
      - ReplicationApp.exe
    
      - RtcHost.exe
    
      - RTCSrv.exe
    
      - XmppProxy.exe
    
      - XmppTGW.exe

  - Processos de Serviço de Host do Windows Fabric:
    
      - Fabric.exe
    
      - FabricDCA.exe
    
      - FabricHost.exe

  - Processos IIS:
    
      - %systemroot%\\system32\\inetsrv\\w3wp.exe
    
      - %systemroot%\\SysWOW64\\inetsrv\\w3wp.exe

  - Processos SQL Server Back-End:
    
      - %ProgramFiles%\\Microsoft SQL Server\\MSSQL11.MSSQLSERVER\\MSSQL\\Binn\\SQLServr.exe
    
      - %ProgramFiles%\\Microsoft SQL Server\\MSRS11.MSSQLSERVER\\Reporting Services\\ReportServer\\Bin\\ReportingServicesService.exe
    
      - %ProgramFiles%\\Microsoft SQL Server\\MSAS11.MSSQLSERVER\\OLAP\\Bin\\MSMDSrv.exe

  - Processos SQL Server Front-End:
    
      - %ProgramFiles%\\Microsoft SQL Server\\MSSQL11.LYNCLOCAL\\MSMQL\\Binn\\SQLServr.exe
    
      - %ProgramFiles%\\Microsoft SQL Server\\MSSQL11.RTCLOCAL\\MSMQL\\Binn\\SQLServr.exe

  - Diretórios e arquivos:
    
      - %systemroot%\\System32\\LogFiles
    
      - %systemroot%\\SysWow64\\LogFiles
    
      - %systemroot%\\Microsoft.NET\\assembly\\GAC\_MSIL
    
      - %programfiles%\\Microsoft Lync Server 2013
    
      - %programfiles%\\Common Files\\Microsoft Lync Server 2013\\Watcher Node
    
      - %programfiles%\\Common Files\\Microsoft Lync Server 2013
    
      - %SystemDrive%\\RtcReplicaRoot
    
      - Repositório de compartilhamento de arquivo(específico no Construtor de Topologias). Os repositórios de arquivos são especificados no Construtor de Topologias.
    
      - Os arquivos de logs e dados do SQL Server, incluindo aqueles para o banco de dados de back-end, armazenamento de usuário, arquivamento, monitoramento, e repositório de application. Os arquivos da base de dados e os logs podem ser especificados no Construtor de Topologias. Para mais detalhes sobre os dados e arquivos de log para cada base de dados, incluindo os nomes padrão, consulte [Posicionamento de dados do Servidor SQL e do arquivo de log para Lync Server 2013](lync-server-2013-sql-server-data-and-log-file-placement.md) na Documentação de implantação.
    
      - Os arquivos de log e de dados do SQL Server, incluindo aqueles para a base de dados de fron-end, armazenamento Lync e armazenamento RtcDatabase. Normalmente, eles estão sob %localdrive%\\CSData.

