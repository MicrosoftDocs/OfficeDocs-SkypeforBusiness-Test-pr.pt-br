---
title: 'Lync Server 2013: Implantando espelhamento SQL para alta disponibilidade de Servidor Back-End'
TOCTitle: Implantando espelhamento SQL para alta disponibilidade de Servidor Back-End
ms:assetid: 70224520-b5c8-4940-a08e-7fb9b1adde8d
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ204992(v=OCS.15)
ms:contentKeyID: 49307069
ms.date: 12/10/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Implantando espelhamento SQL para alta disponibilidade de Servidor Back-End no Lync Server 2013

 

_**Tópico modificado em:** 2016-12-08_

Para que seja possível implantar o espelhamento SQL, os servidores devem executar no mínimo o SQL Server 2008 R2. Essa versão deve ser executada em todos os servidores envolvidos: principal, espelho e testemunha. Para obter detalhes, consulte [http://go.microsoft.com/fwlink/?linkid=3052\&clcid=0x416](http://go.microsoft.com/fwlink/?linkid=3052%26clcid=0x416).

Em geral, a configuração do espelhamento SQL entre os dois servidores back-end com uma testemunha requer:

  - Que a versão do SQL Server do servidor principal ofereça suporte a espelhamento SQL.

  - Que o principal, o espelho e a testemunha (se implantada) tenham a mesma versão do SQL Server.

  - Que o principal e o espelho tenham a mesma edição do SQL Server. A testemunha pode ter uma edição diferente.

Para conhecer as práticas recomendadas de SQL em termos de quais versões são compatíveis com uma função Testemunha, consulte "Testemunha de espelhamento de banco de dados" na biblioteca do MSDN, em [http://go.microsoft.com/fwlink/?linkid=247345\&clcid=0x416](http://go.microsoft.com/fwlink/?linkid=247345%26clcid=0x416).

Use Construtor de Topologias para implantar espelhamento SQL. Selecione uma opção no Construtor de Topologias para espelhar os bancos de dados; o Construtor de Topologia configurará o espelhamento (inclusive a testemunha, se desejado) quando você publicar a topologia. Observe que a testemunha é configurada ou removida ao mesmo tempo que o espelho. Não há um comando separado para implantar ou remover somente a testemunha.

Para configurar o espelhamento do servidor, primeiro você deve configurar as permissões do banco de dados SQL corretamente. Para obter os detalhes, consulte "Configurar contas de logon para espelhamento de banco de dados ou para grupos de disponibilidade AlwaysOn (SQL Server)" em [http://go.microsoft.com/fwlink/?linkid=268454\&clcid=0x416](http://go.microsoft.com/fwlink/?linkid=268454%26clcid=0x416).

Com o espelhamento SQL, o modo de recuperação de banco de dados fica sempre definido como **Completo**, o que significa que você deve monitorar de perto o tamanho dos logs de transações, fazendo backup regular deles para evitar o esgotamento do espaço em disco dos servidores back-end. A frequência dos backups dos logs de transações depende da taxa de expansão dos logs, que, por sua vez, depende das transações do banco de dados provenientes de atividades de usuários no pool front-end. Recomendamos que você determine a expansão dos logs de transação esperada para a carga de trabalho de implantação do Lync, de modo que seja possível realizar um planejamento adequado. Os artigos a seguir fornecem mais informações sobre o gerenciamento de logs e backups do SQL:

  - Modelos de recuperação de banco de dados: "Modelos de recuperação (SQL Server)" em [http://go.microsoft.com/fwlink/?linkid=268446\&clcid=0x416](http://go.microsoft.com/fwlink/?linkid=268446%26clcid=0x416)

  - Visão geral de backup: "Visão geral de backup (SQL Server)" em [http://go.microsoft.com/fwlink/?linkid=268449\&clcid=0x416](http://go.microsoft.com/fwlink/?linkid=268449%26clcid=0x416)

  - Backup de logs de transações: "Fazer backup de um log de transações (SQL Server)" em [http://go.microsoft.com/fwlink/?linkid=268452\&clcid=0x416](http://go.microsoft.com/fwlink/?linkid=268452%26clcid=0x416)

Com o espelhamento SQL, você pode configurar a topologia do espelhamento no momento da criação dos pools ou após isso.

> [!IMPORTANT]  
> O uso do Construtor de Topologias ou cmdlets para configurar e remover o espelhamento SQL é suportado somente quando os servidores principal, espelho e testemunha (se desejado) pertencem ao mesmo domínio. Caso deseje configurar o espelhamento SQL entre servidores de domínios diferentes, consulte a documentação do SQL Server.

> [!IMPORTANT]  
> Sempre que fizer uma alteração em um relacionamento de espelhamento de banco de dados back-end, você deverá reiniciar todos os servidores front-end do pool.<br />Para uma alteração de espelhamento (como alteração do local de um espelho), use Construtor de Topologias para executar estas três etapas:<ol>
> <li><p>Remova o espelhamento do servidor espelho antigo.</p></li>
> 
> <li><p>Adicione espelhamento ao novo servidor espelho.</p></li>
> 
> 
> <li><p>Publique a topologia.</p></li></ol>


> [!NOTE]  
> Um compartilhamento de arquivos deve ser criado para os arquivos espelho a serem gravados, e o serviço que o SQL Server e o SQL Agent estão executando precisam de acesso de leitura/gravação. Se o serviço SQL Server estiver executando no Serviço de Rede, você pode adicionar &lt;Domain&gt;\&lt;SQLSERVERNAME&gt;$ dos Servidores Principal and SQL Espelhos para compartilhar as permissões. O $ é importante para identificar uma conta de computador.

## Para configurar o espelhamento SQL no momento da criação de um pool no Construtor de Topologias

1.  Na página **Definir o Repositório do SQL**, clique em **Novo** ao lado da caixa **Repositório do SQL**.

2.  Na página **Definir Novo Repositório do SQL**, especifique o repositório principal, selecione **Esta instância SQL está em relação de espelhamento**, especifique o número da porta de espelhamento SQL (o padrão é 5022) e clique em **OK**.

3.  De volta à página **Definir o Repositório do SQL**, selecione **Habilitar Espelhamento do Repositório do SQL**.

4.  Na página **Definir Novo Repositório do SQL**, especifique o repositório do SQL a ser usado como espelho, selecione **Esta instância SQL está em relação de espelhamento**, especifique o número da porta de espelhamento SQL (o padrão é 5022) e clique em **OK**.

5.  Caso deseje uma testemunha para este espelho, faça o seguinte:
    
    1.  Selecione **Usar testemunha de espelhamento do SQL para habilitar failover automático**.
    
    2.  Na página **Definir o Repositório do SQL**, selecione **Usar testemunha de espelhamento do SQL para habilitar failover automático** e especifique o repositório do SQL a ser usado como testemunha.
    
    3.  Especifique o número da porta (o padrão é 7022) e clique em **OK**.

6.  Após concluir a definição do pool front-end e de todas as outras funções na topologia, use o Construtor de Topologias para publicá-la. Após a publicação da topologia, se o pool front-end que hospeda o Repositório de Gerenciamento Central tiver o espelhamento SQL habilitado, você verá uma opção para criar os bancos de dados principal e espelho do repositório SQL.
    
    Clique em **Configurações** e digite o caminho que será usado como compartilhamento de arquivos para o backup de espelhamento.
    
    Clique em **OK** e em **Avançar** para criar os bancos de dados e publicar a topologia. O espelhamento e a testemunha (se especificada) serão implantados.

Você pode usar o Construtor de Topologias para editar as propriedades de um pool já existente a fim de habilitar o espelhamento SQL.

## Para adicionar o espelhamento SQL a um pool front-end existente no Construtor de Topologias

1.  No Construtor de Topologias, clique com o botão direito do mouse no pool e em **Editar Propriedades**.

2.  Selecione **Habilitar Espelhamento do Repositório do SQL** e clique em **Novo** ao lado de **Repositório do SQL de Espelhamento**.

3.  Especifique o repositório do SQL que deseja usar como espelho.

4.  Selecione **Esta instância SQL está em relação de espelhamento**, especifique o número da porta de espelhamento (o padrão é 5022) e clique em **OK**.

5.  Caso deseje configurar uma testemunha, selecione **Usar testemunha de espelhamento do SQL para habilitar failover automático** e clique em **Novo**.

6.  Especifique o repositório do SQL que deseja usar como testemunha.

7.  Selecione **Esta instância SQL está em relação de espelhamento**, especifique o número da porta de espelhamento (o padrão é 7022) e clique em **OK**.

8.  Clique em **OK**.

9.  Publique a topologia. Quando você fizer isso, o sistema solicitará a instalação do banco de dados.
    
    Durante o processo de publicação da topologia, você deverá definir um caminho de compartilhamento de arquivos. Os Servidores SQL que participam do espelhamento devem acesso de leitura/gravação a esse compartilhamento de arquivos para que o espelhamento seja estabelecido.

Instale o banco de dados antes de ir para o próximo procedimento.

Lembre-se disto ao configurar o espelhamento SQL:

  - Caso já exista um ponto de extremidade de espelhamento, ele será reutilizado usando as portas definidas nele e irá ignorar aquelas especificadas na topologia.

  - Todas as portas já alocadas a outros aplicativos no mesmo servidor (inclusive de outras instâncias do SQL) não serão usadas com as instâncias do SQL instaladas atualmente. Isso significa que, se você tiver mais de uma instância do SQL instalada no mesmo servidor, elas não poderão usar a mesma porta para espalhamento. Para obter detalhes, consulte os seguintes artigos:
    
      - "Especificar um endereço de rede do servidor (Espelhamento de banco de dados)" na biblioteca do MSDN, em [http://go.microsoft.com/fwlink/?linkid=247346\&clcid=0x416](http://go.microsoft.com/fwlink/?linkid=247346%26clcid=0x416)
    
      - "O ponto de extremidade de espelhamento de banco de dados (SQL Server)" em [http://go.microsoft.com/fwlink/?linkid=247347\&clcid=0x416](http://go.microsoft.com/fwlink/?linkid=247347%26clcid=0x416)

## Usando cmdlets do Shell de Gerenciamento do Lync Server para configurar o espelhamento SQL

O modo mais fácil de configurar o espelhamento é usar o Construtor de Topologias, mas também é possível usar cmdlets.

1.  Abra uma janela do Shell de Gerenciamento do Lync Server e execute o seguinte cmdlet:
    
        Install-CsMirrorDatabase [-ConfiguredDatabases] [-ForInstance] [-ForDefaultInstance] [-DatabaseType <Application | Archiving | CentralMgmt | Monitoring | User | BIStaging | PersistentChat | PersistentChatCompliance >] -FileShare <fileshare> -SqlServerFqdn <primarySqlserverFqdn> [-SqlInstanceName] [-DatabasePathMap] [-ExcludeDatabaseList] [-DropExistingDatabasesOnMirror] -Verbose 
    
    Por exemplo:
    
        Install-CsMirrorDatabase -ConfiguredDatabases -FileShare \\PRIMARYBE\csdatabackup -SqlServerFqdn primaryBE.contoso.com -DropExistingDatabasesOnMirror -Verbose 
    
    Você verá:
    
        Database Name:rtcxds 
                Data File:D:\CsData\BackendStore\rtc\DbPath\rtcxds.mdf 
                 Log File:D:\CsData\BackendStore\rtc\LogPath\rtcxds.ldf 
              Primary SQL: e04-ocs.los_a.lsipt.local\rtc 
                  Account: LOS_A\e04-ocs$ 
               Mirror SQL: K16-ocs.los_a.lsipt.local\rtc 
                  Account: LOS_A\K16-ocs$ 
             Witness SQL : AB14-lct.los_a.lsipt.local\rtc 
                  Account: LOS_A\AB14-lct$ 
            Database Name:rtcshared 
                Data File:D:\CsData\BackendStore\rtc\DbPath\rtcshared.mdf 
                 Log File:D:\CsData\BackendStore\rtc\LogPath\rtcshared.ldf 
              Primary SQL: e04-ocs.los_a.lsipt.local\rtc 
                  Account: LOS_A\e04-ocs$ 
               Mirror SQL: K16-ocs.los_a.lsipt.local\rtc 
                  Account: LOS_A\K16-ocs$ 
             Witness SQL : AB14-lct.los_a.lsipt.local\rtc 
                  Account: LOS_A\AB14-lct$ 
            Database Name:rtcab 
                Data File:D:\CsData\ABSStore\rtc\DbPath\rtcab.mdf 
                 Log File:D:\CsData\ABSStore\rtc\LogPath\rtcab.ldf 
              Primary SQL: e04-ocs.los_a.lsipt.local\rtc 
                  Account: LOS_A\e04-ocs$ 
               Mirror SQL: K16-ocs.los_a.lsipt.local\rtc 
                  Account: LOS_A\K16-ocs$ 
             Witness SQL : AB14-lct.los_a.lsipt.local\rtc 
                  Account: LOS_A\AB14-lct$ 
            Database Name:rgsconfig 
                Data File:D:\CsData\ApplicationStore\rtc\DbPath\rgsconfig.mdf 
                 Log File:D:\CsData\ApplicationStore\rtc\LogPath\rgsconfig.ldf 
              Primary SQL: e04-ocs.los_a.lsipt.local\rtc 
                  Account: LOS_A\e04-ocs$ 
               Mirror SQL: K16-ocs.los_a.lsipt.local\rtc 
                  Account: LOS_A\K16-ocs$ 
             Witness SQL : AB14-lct.los_a.lsipt.local\rtc 
                  Account: LOS_A\AB14-lct$ 
            Database Name:rgsdyn 
                Data File:D:\CsData\ApplicationStore\rtc\DbPath\rgsdyn.mdf 
                 Log File:D:\CsData\ApplicationStore\rtc\LogPath\rgsdyn.ldf 
              Primary SQL: e04-ocs.los_a.lsipt.local\rtc 
                  Account: LOS_A\e04-ocs$ 
               Mirror SQL: K16-ocs.los_a.lsipt.local\rtc 
                  Account: LOS_A\K16-ocs$ 
             Witness SQL : AB14-lct.los_a.lsipt.local\rtc 
                  Account: LOS_A\AB14-lct$ 
            Database Name:cpsdyn 
                Data File:D:\CsData\ApplicationStore\rtc\DbPath\cpsdyn.mdf 
                 Log File:D:\CsData\ApplicationStore\rtc\LogPath\cpsdyn.ldf 
              Primary SQL: e04-ocs.los_a.lsipt.local\rtc 
                  Account: LOS_A\e04-ocs$ 
               Mirror SQL: K16-ocs.los_a.lsipt.local\rtc 
                  Account: LOS_A\K16-ocs$ 
             Witness SQL : AB14-lct.los_a.lsipt.local\rtc 
                  Account: LOS_A\AB14-lct$ 
            Database Name:xds 
                Data File:D:\CsData\CentralMgmtStore\rtc\DbPath\xds.mdf 
                 Log File:D:\CsData\CentralMgmtStore\rtc\LogPath\xds.ldf 
              Primary SQL: e04-ocs.los_a.lsipt.local\rtc 
                  Account: LOS_A\e04-ocs$ 
               Mirror SQL: K16-ocs.los_a.lsipt.local\rtc 
                  Account: LOS_A\K16-ocs$ 
             Witness SQL : AB14-lct.los_a.lsipt.local\rtc 
                  Account: LOS_A\AB14-lct$ 
            Database Name:lis 
                Data File:D:\CsData\CentralMgmtStore\rtc\DbPath\lis.mdf 
                 Log File:D:\CsData\CentralMgmtStore\rtc\LogPath\lis.ldf 
              Primary SQL: e04-ocs.los_a.lsipt.local\rtc 
                  Account: LOS_A\e04-ocs$ 
               Mirror SQL: K16-ocs.los_a.lsipt.local\rtc 
                  Account: LOS_A\K16-ocs$ 
             Witness SQL : AB14-lct.los_a.lsipt.local\rtc 
                  Account: LOS_A\AB14-lct$
        [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): 

2.  Verifique se:
    
      - A porta 5022 pode ser acessada pelo firewall quando o Firewall do Windows está habilitado no SQL Server principal e04-ocs.los\_a.lsipt.local\\rtc.
    
      - A porta 5022 pode ser acessada pelo firewall quando o Firewall do Windows está habilitado no SQL Server espelho K16-ocs.los\_a.lsipt.local\\rtc.
    
      - A porta 7022 pode ser acessada pelo firewall quando o Firewall do Windows está habilitado no SQL Server testemunha AB14-lct.los\_a.lsipt.local\\rtc.
    
      - As contas executando todos os SQL Servers principais e espelhos têm permissão de leitura/gravação do compartilhamento de arquivos \\\\E04-OCS\\csdatabackup
    
      - Verifique se o provedor WMI (Instrumentação de Gerenciamento do Windows) está em execução em todos esses servidores. O cmdlet usa esse provedor para encontrar informações da conta relativas aos serviços do SQL Server em execução em todos os servidores principais, espelho e testemunha.
    
      - Verifique se a conta que executa esse cmdlet tem permissão de criação das pastas dos dados e arquivos de log para todos os servidores espelho.
    
      - Observe que a conta de usuário usada pela instância do SQL para execução deve ter permissão de leitura/gravação do compartilhamento de arquivos. Se o compartilhamento de arquivos estiver em um servidor diferente e a instância do SQL for executada em uma conta do sistema local, você deverá conceder permissões de compartilhamento de arquivos ao servidor que hospeda a instância do SQL.

3.  Digite A e pressione ENTER.
    
    O espelhamento será configurado.

**Install-CsMirrorDatabase** instala o espelho e configura o espelhamento para todos os bancos de dados presentes no repositório SQL principal. Caso deseje configurar o espelhamento somente para bancos de dados específicos, você poderá usar a opção -DatabaseType. Ou, caso deseje configurar o espelhamento para todos os bancos de dados, exceto alguns, use a opção -ExcludeDatabaseList, juntamente com uma lista separada por vírgulas com os nomes dos bancos de dados que devem ser excluídos.

Por exemplo, caso adicione a opção a seguir a **Install-CsMirrorDatabase**, todos os bancos de dados serão espelhados, com exceção de rtcab e rtcxds.

`-ExcludeDatabaseList rtcab,rtcxds`

Por exemplo, caso adicione a opção a seguir a **Install-CsMirrorDatabase**, somente os bancos de dados rtcab, rtcshared e rtcxds databases serão espelhados.

`-DatabaseType User`

## Removendo ou alterando o espelhamento SQL

Para remover o espelhamento SQL de um pool no Construtor de Topologias, primeiro use um cmdlet para remover o espelho no SQL Server. Em seguida, você poderá usar o Construtor de Topologias para remover o espelho da topologia. Para remover o espelho no SQL Server, use o cmdlet a seguir:

    Uninstall-CsMirrorDatabase -SqlServerFqdn <SQLServer FQDN> [-SqlInstanceName <SQLServer instance name>] -DatabaseType <Application | Archiving | CentralMgmt | Monitoring | User | BIStaging | PersistentChat | PersistentChatCompliance> [-DropExistingDatabasesOnMirror] [-Verbose]

Por exemplo, para remover o espelhamento e descartar os bancos de dados de usuários, digite:

    Uninstall-CsMirrorDatabase -SqlServerFqdn primaryBE.contoso.com -SqlInstanceName rtc -Verbose -DatabaseType User -DropExistingDatabasesOnMirror

A opção `-DropExistingDatabasesOnMirror` faz com que os bancos de dados afetados sejam excluídos do espelho.

Depois, para remover o espelho da topologia, faça o seguinte:

1.  No Construtor de Topologias, clique com o botão direito do mouse no pool e em **Editar Propriedades**

2.  Desmarque **Habilitar Espelhamento do Repositório do SQL** e clique em **OK**.

3.  Publique a topologia.

## Removendo a testemunha de espelhamento

Use este procedimento caso deseje remover a testemunha de uma configuração de espelhamento do Servidor Back-End.

1.  Em Construtor de Topologias, clique com o botão direito no pool e clique em **Editar Propriedades**.

2.  Desmarque **Usar testemunha de espelhamento do SQL Server para habilitar failover automático** e clique em **OK**.

3.  Publique a topologia.
    
    Após publicar a topologia, Construtor de Topologias você verá uma mensagem que inclui o seguinte
    
        Run the Uninstall-CsMirrorDatabase cmdlet to remove databases that are paired with following primary databases.
    
    Porém, não siga essa etapa e não digite `Uninstall-CsMirrorDatabase`, pois isso fará a desinstalação de toda a configuração de espelhamento.

4.  Para remover apenas a testemunha da configuração do SQL Server, siga as instruções em "Remover a testemunha de uma sessão de espelhamento de banco de dados (SQL Server)", em [http://go.microsoft.com/fwlink/?linkid=268456\&clcid=0x416](http://go.microsoft.com/fwlink/?linkid=268456%26clcid=0x416).

