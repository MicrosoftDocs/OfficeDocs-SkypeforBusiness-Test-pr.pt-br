---
title: Mover o Servidor de Gerenciamento Central do Lync Server 2010 para o Lync Server 2013
TOCTitle: Mover o Servidor de Gerenciamento Central do Lync Server 2010 para o Lync Server 2013
ms:assetid: 30cc98f2-1916-4dbe-99d0-8df5368ed3ec
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ688013(v=OCS.15)
ms:contentKeyID: 49886161
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Mover o Servidor de Gerenciamento Central do Lync Server 2010 para o Lync Server 2013

 

_**Tópico modificado em:** 2013-11-25_

Após migrar do Lync Server 2010 para o Lync Server 2013, você precisa mover o Lync Server 2010Servidor de Gerenciamento Central para o Lync Server 2013Servidor Front-End ou pool antes de poder remover o servidor herdado Lync Server 2010.

O Servidor de Gerenciamento Central é um sistema de resposta múltipla/principal único, onde a cópia de gravação/leitura do banco de dados é mantida pelo Servidor Front-End contendo o Servidor de Gerenciamento Central. Cada computador na topologia, incluindo o Servidor Front-End que contém o Servidor de Gerenciamento Central, possui uma cópia somente leitura dos dados do Repositório de Gerenciamento Central no banco de dados do SQL Server (chamado RTCLOCAL por padrão) instalado no computador durante a instalação e implantação. O banco de dados local recebe atualizações de réplica através do Agente Replicador de Réplica do Lync Server que executa como um serviço em todos os computadores. O nome do banco de dados reais no Servidor de Gerenciamento Central e a réplica local é XDS, que é composta de arquivos xds.mdf e xds.ldf. O local do banco de dados principal é referenciado por um ponto de controle de serviço (SCP) no Serviços de Domínio Active Directory. Todas as ferramentas que usam o Servidor de Gerenciamento Central para gerenciar e configurar o Lync Server usam o SCP para localizar o Repositório de Gerenciamento Central.

Após ter movido com sucesso o Servidor de Gerenciamento Central, você deve remover os bancos de dados do Servidor de Gerenciamento Central do Servidor Front-End original. Para obter informações sobre como remover bancos de dados do Servidor de Gerenciamento Central, consulte [Remover o banco de dados do Servidor SQL para um pool Front-End](remove-the-sql-server-database-for-a-front-end-pool.md).

Você usa o cmdlet Windows PowerShell**Move-CsManagementServer** no Shell de Gerenciamento do Lync Server para mover o banco de dados do banco de dados do SQL Server Lync Server 2010 para o banco de dados do SQL Server Lync Server 2013 e atualiza o SCP para apontar para o local do Lync Server 2013Servidor de Gerenciamento Central.

## Preparando o Lync Server 2013Servidores Front-End antes de mover o Servidor de Gerenciamento Central

Use os procedimentos nesta seção para preparar o Lync Server 2013Servidores Front-End antes de mover o Lync Server 2010Servidor de Gerenciamento Central.

## Para preparar um Enterprise Edition Pool de Front-Ends

1.  No Lync Server 2013 Enterprise Edition Pool de Front-Ends onde você deseja realocar o Servidor de Gerenciamento Central: Faça o login no computador onde o Shell de Gerenciamento do Lync Server está instalado como um membro do grupo **RTCUniversalServerAdmins**. Você também deve ter direitos e permissões de usuário sysadmin do banco de dados do SQL Server no banco de dados onde deseja instalar o Repositório de Gerenciamento Central.

2.  Abra o Shell de Gerenciamento do Lync Server.

3.  Para criar o novo Repositório de Gerenciamento Central no banco de dados do SQL Server do Lync Server 2013, no Shell de Gerenciamento do Lync Server, digite:
    
        Install-CsDatabase -CentralManagementDatabase -SQLServerFQDN <FQDN of your SQL Server> -SQLInstanceName <name of instance>

4.  Confirme que o status do serviço do **Front-End do Lync Server** é **Iniciado** .

## Para preparar um Standard Edition Servidor Front-End

1.  No Lync Server 2013 Standard Edition Servidor Front-End onde você deseja realocar o Servidor de Gerenciamento Central: Faça o logon no computador onde o Shell de Gerenciamento do Lync Server está instalado como membro do grupo **RTCUniversalServerAdmins**.

2.  Abra o Assistente de Implantação do Lync Server.

3.  No Assistente de Implantação do Lync Server, clique em **Preparar o primeiro servidor do Standard Edition** .

4.  Na página **Executando comandos** , o SQL Server Express é instalado como o Servidor de Gerenciamento Central. Regras de firewall necessárias são criadas. Quando a instalação do banco de dados e software de pré-requisito estiver concluída, clique em **Finalizar** .
    
    > [!NOTE]  
    > A instalação inicial pode levar algum tempo sem nenhuma atualização visível na tela de resumo de saída do comando. Isto ocorre devido à instalação do SQL Server Express. Se você precisa monitorar a instalação do banco de dados, use o Gerenciador de Tarefas para monitorar a configuração.

5.  Para criar o novo Repositório de Gerenciamento Central no Lync Server 2013 Standard Edition Servidor Front-End, no Shell de Gerenciamento do Lync Server, digite:
    
        Install-CsDatabase -CentralManagementDatabase -SQLServerFQDN <FQDN of your Standard Edition Server> -SQLInstanceName <name of instance - RTC by default>

6.  Confirme que o status do serviço do **Front-End do Lync Server** é **Iniciado** .

## Para mover o Lync Server 2010Servidor de Gerenciamento Central para Lync Server 2013

1.  No servidor do Lync Server 2013 que será o Servidor de Gerenciamento Central: Faça o login no computador onde o Shell de Gerenciamento do Lync Server está instalado como membro do grupo **RTCUniversalServerAdmins**. Você também deve ter direitos e permissões de usuário administrador do banco de dados do SQL Server.

2.  Abrir o Shell de Gerenciamento do Lync Server.

3.  No Shell de Gerenciamento do Lync Server, digite:
    
        Enable-CsTopology
    

    > [!WARNING]
    > Se <CODE>Enable-CsTopology</CODE> não tem êxito, resolva o problema evitando que o comando conclua antes de continuar. Se <STRONG>Enable-CsTopology</STRONG> não tem êxito, a movimentação falhará e poderá deixar sua topologia em um estado onde não há Repositório de Gerenciamento Central.



4.  No Lync Server 2013Servidor Front-End ou Pool de Front-Ends, no Shell de Gerenciamento do Lync Server, digite:
    
        Move-CsManagementServer

5.  O Shell de Gerenciamento do Lync Server exibe os servidores, repositórios de arquivos, repositórios de bancos de dados e pontos de conexão do serviço do Estado Atual e do Estado Proposto. Leia as informações cuidadosamente e confirme que esta é a origem e o destino pretendido. Digite **Y** para continuar ou **N** para parar a movimentação.

6.  Revise qualquer aviso ou erro gerado pelo comando **Move-CsManagementServer** e resolva-os.

7.  No servidor do Lync Server 2013, abra o Assistente de Implantação do Lync Server.

8.  No Assistente de Implantação do Lync Server, clique em **Instalar ou atualizar o Lync Server System** , clique em **Etapa 2: Configurar ou remover os componentes do Lync Server** , clique em **Avançar** , revise o resumo e clique em **Concluir** .

9.  No servidor do Lync Server 2010, abra o Assistente de Implantação do Lync Server.

10. No Assistente de Implantação do Lync Server, clique em **Instalar ou atualizar o Lync Server System** , clique em **Etapa 2: Configurar ou remover os componentes do Lync Server** , clique em **Avançar** , revise o resumo e clique em **Concluir** .

11. Reinicie o servidor de Lync Server 2013. Isso é necessário devido a uma alteração de associação de grupo para acessar o banco de dados de Servidor de Gerenciamento Central.

12. Para confirmar que a replicação com o novo Repositório de Gerenciamento Central está ocorrendo, no Shell de Gerenciamento do Lync Server, digite:
    
        Get-CsManagementStoreReplicationStatus
    
    > [!NOTE]  
    > A replicação pode levar algum tempo para atualizar todas as réplicas atuais.

## Para remover os arquivos do Lync Server 2010Repositório de Gerenciamento Central após uma movimentação

1.  No servidor do Lync Server 2010: Faça o login no computador onde o Shell de Gerenciamento do Lync Server está instalado como um membro do grupo **RTCUniversalServerAdmins**. Você também deve ter direitos e permissões do usuário administrador do banco de dados do SQL Server.

2.  Abra o Shell de Gerenciamento do Lync Server
    

    > [!WARNING]
    > Não continue com a remoção dos arquivos do banco de dados anteriores até que a replicação esteja concluída e estável. Se você remover os arquivos antes de concluir a replicação, você irá interromper o processo de replicação e deixar o Servidor de Gerenciamento Central recentemente movido em um estado desconhecido. Use o cmdlet <STRONG>Get-CsManagementStoreReplicationStatus</STRONG> para confirmar o status da replicação.



3.  Para remover os arquivos do banco de dados do Repositório de Gerenciamento Central do Lync Server 2010Servidor de Gerenciamento Central, digite:
    
        Uninstall-CsDatabase -CentralManagementDatabase -SqlServerFqdn <FQDN of SQL Server> -SqlInstanceName <Name of source server>
    
    Por exemplo:
    
        Uninstall-CsDatabase -CentralManagementDatabase -SqlServerFqdn sql.contoso.net -SqlInstanceName rtc
    
    Onde o *\<FQDN do SQL Server\>* é o Servidor de Back-End do Lync Server 2010 em uma implantação do Enterprise Edition ou o FQDN do servidor Standard Edition.

