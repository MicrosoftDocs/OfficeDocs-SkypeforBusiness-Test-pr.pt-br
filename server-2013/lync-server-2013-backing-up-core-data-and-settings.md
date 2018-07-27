---
title: Fazendo backup dos dados principais e das configurações
TOCTitle: Fazendo backup dos dados principais e das configurações
ms:assetid: 278bc95a-7b8d-4e01-a872-a844830459de
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Hh202170(v=OCS.15)
ms:contentKeyID: 52057585
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Fazendo backup dos dados principais e das configurações

 

_**Tópico modificado em:** 2014-04-23_

Os procedimentos a seguir usam os cmdlets do Shell de Gerenciamento do Lync Server para criar arquivos de backup para configurações e dados para serviços básicos. Para obter detalhes sobre as ferramentas usadas nesta seção, incluindo onde estão localizadas, consulte [Requisitos de backup e restauração: ferramentas e permissões](lync-server-2013-backup-and-restoration-requirements-tools-and-permissions.md). Para obter detalhes sobre como fazer backup de dados de arquivamento e de monitoramento, consulte [Fazendo backup de bancos de dados de monitoramento e arquivamento](lync-server-2013-backing-up-archiving-and-monitoring-databases.md).

> [!NOTE]  
> A etapa nesta seção para fazer backup do Repositório de Gerenciamento Central inclui as configurações para arquivamento e monitoramento.

É possível executar os cmdlets descritos nesta seção local ou remotamente.

## Para fazer o backup dos principais dados e configurações

1.  Em uma conta de usuário membro do grupo RTCUniversalServerAdmins, faça logon em qualquer computador em sua implantação interna.

2.  Para armazenar os backups criados nas etapas a seguir, crie uma nova pasta compartilhada e atualize o caminho referido por **$Backup** para a nova pasta compartilhada.

3.  Inicie o Shell de Gerenciamento do Lync Server: clique em **Iniciar**, em **Todos os Programas**, em **Microsoft Lync Server 2013** e em **Shell de Gerenciamento do Lync Server**.

4.  Faça o backup do arquivo de configuração do Repositório de Gerenciamento Central. Na linha de comando, digite o seguinte:
    
        Export-CsConfiguration -FileName <path and file name for backup>
    
    Por exemplo:
    
        Export-CsConfiguration -FileName "C:\Config.zip"
    
    > [!NOTE]  
    > Esta etapa exporta a topologia, as políticas e configurações de seu Lync Server para um arquivo. Nenhuma outra etapa é necessária para fazer backup dos dados de topologia.

5.  Copie o arquivo de configuração do Repositório de Gerenciamento Central de backup para $Backup\\.

6.  Faça o backup dos dados do serviço de Informações de Local. Na linha de comando, digite o seguinte:
    
        Export-CsLisConfiguration -FileName <path and file name for backup>
    
    Por exemplo:
    
        Export-CsLisConfiguration -FileName "C:\E911Config.zip"

7.  Copie o arquivo de configuração do serviço de Informações de Local de backup para $Backup\\.

8.  Fala o backup dos dados do usuário em cada banco de dados back-end de um Pool de Front-Ends e em cada Servidor Standard Edition. Na linha de comando, digite o seguinte:
    
        Export-CsUserData -PoolFQDN <Fqdn> -FileName <String>
    
    Por exemplo:
    
        Export-CsUserData -PoolFQDN "atl-cs-001.litwareinc.com" -FileName "C:\Logs\ExportedUserData.zip"

9.  Copie o arquivo de usuário armazenado em backup para $Backup\\.

10. Em cada pool que executa o Aplicativo Grupo de Resposta, faça backup da configuração do Grupo de Resposta. Faça o seguinte:
    
    1.  Na linha de comando, digite:
        
            Export-CsRgsConfiguration -Source "service:ApplicationServer:<pool FQDN>" -FileName <path and file name for backup>
        
        Por exemplo:
        
            Export-CsRgsConfiguration -Source ApplicationServer:pool01.contoso.com -FileName C:\RgsConfiguration.zip

11. Copie o arquivo de configuração do Grupo de Resposta armazenado em backup para $Backup\\.

