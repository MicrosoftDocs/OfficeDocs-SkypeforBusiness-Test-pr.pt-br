---
title: 'Lync Server 2013: Instalação de banco de dados usando o Shell de Gerenciamento do Lync Server'
TOCTitle: Instalação de banco de dados usando o Shell de Gerenciamento do Lync Server
ms:assetid: c90a6449-4dd5-4b18-b21c-ea2c2a64dc3c
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398832(v=OCS.15)
ms:contentKeyID: 49308100
ms.date: 12/10/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Instalação de banco de dados usando o Shell de Gerenciamento do Lync Server no Lync Server 2013

 

_**Tópico modificado em:** 2016-12-08_

A separação de funções e responsabilidades entre administradores de servidor e administradores do SQL Server pode resultar em atrasos na implementação. O Lync Server 2013 usa o RBAC (controle de acesso baseado em função) para reduzir essas dificuldades. Em algumas instâncias, o administrador do SQL Server deverá gerenciar a instalação de bancos de dados no servidor baseado em SQL Server fora do RBAC. O Shell de Gerenciamento do Lync Server 2013 oferece uma maneira para que o administrador do SQL Server execute cmdlets do Windows PowerShell projetados para configurar os bancos de dados com os dados e os arquivos de log corretos. Para obter detalhes, consulte [Permissões de implantação para Servidor SQL no Lync Server 2013](lync-server-2013-deployment-permissions-for-sql-server.md).

> [!IMPORTANT]  
> O procedimento a seguir assume que como mínimo, o Lync Server 2013 OCSCore.msi, Objetos de Gerenciamento do SQL Server Native Client (sqlncli.msi) Microsoft SQL Server 2012, Tipos CLR para Microsoft SQL Server 2012 e Microsoft SQL Server 2012 ADOMD.NET estão instalados. O OCSCore.msi está localizado na mídia de instalação no diretório \Setup\AMD64\Setup. Os componentes restantes estão localizados em \Setup\amd64. Além disso, a preparação do Active Directory para o Lync Server 2013 foi concluída com sucesso.

**Install-CsDatabase** é o cmdlet do Windows PowerShell usado para instalar os bancos de dados. O cmdlet **Install-CsDatabase** tem muitos parâmetros, somente alguns deles são discutidos aqui. Para obter detalhes sobre os possíveis parâmetros, consulte a documentação do Shell de Gerenciamento do Lync Server 2013.


> [!WARNING]
> Para evitar possíveis problemas de tempo limite e de desempenho, sempre use os FQDNs (nomes de domínio totalmente qualificados) ao se referir aos servidores baseados no SQL Server. Evite usar referências somente ao nome do host. Por exemplo, use sqlbe01.contoso.net, mas evite usar SQLBE01.



Para instalar bancos de dados, o **Install-CsDatabase** usa os três métodos principais para colocar os bancos de dados no servidor baseado em SQL Server preparado:

  - Execute **Install-CsDatabase** sem DatabasePaths ou UseDefaultSqlPath. O cmdlet usa um algoritmo integrado para determinar o melhor posicionamento dos arquivos de log e de dados. O algoritmo funciona somente para implementações autônomas do SQL Server.

  - Execute **Install-CsDatabase** com o parâmetro DatabasePaths. O algoritmo integrado para otimizar os locais de arquivo de log e de dados não é usado se o parâmetro DatabasePaths for definido. O uso desse parâmetro permite que você defina os locais onde os arquivos de log e de dados serão implantados.

  - Execute **Install-CsDatabase** com UseDefaultSqlPaths. Esta opção não usa o algoritmo integrado para otimizar os locais do arquivo de dados e log. O arquivo de dados e log são implantados para as definições padrões pelo administrador do SQL Server. Estes caminhos são geralmente definidos para fins de administração automática dos arquivos de dados e log no SQL Server antecipadamente e não estão associados com a configuração do Lync Server 2013.

  - O parâmetro DatabasePathMap também pode ser usado para especificar explicitamente um local para cada banco de dados e seu respectivo arquivo de log.

## Para usar cmdlets do Windows PowerShell para configurar o SQL Server Repositório de Gerenciamento Central

1.  Em qualquer computador, faça logon com credenciais administrativas para a criação dos bancos de dados no servidor baseado em SQL Server. Para obter detalhes, consulte [Permissões de implantação para Servidor SQL no Lync Server 2013](lync-server-2013-deployment-permissions-for-sql-server.md).

2.  Abra o Shell de Gerenciamento do Lync Server 2013. Se você não tiver ajustado a política de execução para o Windows PowerShell, será necessário ajustá-la para permitir a execução de scripts do Windows PowerShell. Para obter detalhes, consulte “Examinando a diretiva de execução” em <http://go.microsoft.com/fwlink/?linkid=203093>.

3.  Use o cmdlet **Install-CsDatabase** para instalar o Repositório de Gerenciamento Central.
    
```
        Install-CsDatabase -CentralManagementDatabase -SqlServerFqdn <fully qualified domain name of SQL Server> 
        -SqlInstanceName <named instance> -DatabasePaths <logfile path>,<database file path> 
        -Report <path to report file>
```
```    
        Install-CsDatabase -CentralManagementDatabase -SqlServerFqdn sqlbe.contoso.net -SqlInstanceName rtc -DatabasePaths "C:\CSDB-Logs","C:\CSDB-CMS" -Report "C:\Logs\InstallDatabases.html"
```    

> [!TIP]
> O parâmetro Report é opcional, mas é útil se você estiver documentando o processo de instalação.



4.  O **Install-CsDatabase –DatabasePaths** pode usar até seis parâmetros de caminho, cada um definindo os caminhos para os drives conforme definido no Local do Arquivo de Log e Dados do SQL Server. Pelas regras lógicas da configuração do banco de dados no Lync Server 2013, os drives são analisados em dois grupos de dois, quatro ou seis. Dependendo da sua configuração do SQL Server e o número de grupos, você oferece dois caminhos, quatro caminhos ou seis caminhos.
    
    Se você possui três drives, o log tem prioridade e os arquivos de dados são distribuídos posteriormente. Um exemplo para um servidor baseado em SQL Server configurado com seis drives:
    
        Install-CsDatabase -ConfiguredDatases -SqlServerFqdn sqlbe.contoso.net -DatabasePaths "D:\CSDynLogs","E:\CSRtcLogs","F:\MonCdrArcLogs","G:\MonCdrArchData","H:\AbsAppLog","I:\DynRtcAbsAppData" -Report "C:\Logs\InstallDatabases.html"

5.  Após a conclusão da instalação do banco de dados, é possível fechar o Shell de Gerenciamento do Lync Server 2013 ou continuar com a instalação dos bancos de dados configurados pelo Lync Server 2013 definidos no Construtor de Topologias.

## Para usar cmdlets do Windows PowerShell para configurar os bancos de dados configurados da topologia do SQL Server

1.  Para instalar os bancos de dados configurados por Construtor de Topologias para Lync Server 2013, o administrador do Lync Server 2013 deve publicar a topologia. Para obter detalhes, consulte [Publicar a topologia no Lync Server 2013](lync-server-2013-publish-the-topology.md) na documentação Implantação.

2.  Em qualquer computador, faça o login com credenciais administrativas para criar os bancos de dados no servidor baseado em SQL Server. Consulte o tópico, [Permissões de implantação para Servidor SQL no Lync Server 2013](lync-server-2013-deployment-permissions-for-sql-server.md).
    
    > [!IMPORTANT]  
    > Para poder configurar os bancos de dados baseados em SQL Server, certifique-se de que a conta de administrador do SQL Server usada para executar as etapas descritas aqui também seja membro do grupo sysadmins (ou equivalente) no servidor que está executando o SQL Server e mantenha a função Servidor de Gerenciamento Central. Isso é especialmente importante para verificar a existência de quaisquer pools do Lync Server 2013 adicionais que exigem a instalação ou configuração do banco de dados do SQL Server. Por exemplo, se você está implantando um segundo pool (pool02), mas a função Servidor de Gerenciamento Central é mantida por pool01. O grupo sysadmin do SQL Server (ou equivalente) precisa ter permissões em ambos os bancos de dados baseados no SQL Server.

3.  Abra o Shell de Gerenciamento do Lync Server 2013, caso ainda não esteja aberto.

4.  Use o cmdlet **Install-CsDatabase** para instalar os bancos de dados configurados por Construtor de Topologias.
    
```
        Install-CsDatabase -ConfiguredDatabases -SqlServerFqdn <fully qualified domain name of SQL Server> 
         -DatabasePaths <logfile path>,<database file path> -Report <path to report file>
```
```    
        Install-CsDatabase -ConfiguredDatabases -SqlServerFqdn sqlbe.contoso.net 
        -Report "C:\Logs\InstallDatabases.html"
    
```


> [!TIP]
> O parâmetro Report é opcional, mas é útil se você estiver documentando o processo de instalação.



5.  Após a conclusão da instalação do banco de dados, feche o Shell de Gerenciamento do Lync Server 2013.

## Para usar os cmdlets do Windows PowerShell para configurar a topologia do SQL Server usando o parâmetro DatabasePathMap

1.  Para instalar bancos de dados do Lync Server 2013, o administrador do Lync Server deve criar caminhos e implantar os arquivos do banco de dados e arquivos de log de acordo com um conjunto de regras predefinidas.

2.  Em qualquer computador, faça o login com credenciais administrativas para criar os bancos de dados no servidor baseado em SQL Server. Consulte o tópico, [Permissões de implantação para Servidor SQL no Lync Server 2013](lync-server-2013-deployment-permissions-for-sql-server.md).
    
    > [!IMPORTANT]  
    > Para poder configurar os bancos de dados baseados em SQL Server, certifique-se de que a conta de administrador do SQL Server usada para executar as etapas descritas aqui também seja membro do grupo sysadmins (ou equivalente) no servidor que está executando o SQL Server e mantenha a função Servidor de Gerenciamento Central. Isso é especialmente importante para verificar a existência de quaisquer pools do Lync Server adicionais que exigem a instalação ou configuração do banco de dados do SQL Server. Por exemplo, se você está implantando um segundo pool (pool02), mas a função Servidor de Gerenciamento Central é mantida por pool01. O grupo sysadmin do SQL Server (ou equivalente) precisa ter permissões em ambos os bancos de dados baseados no SQL Server.

3.  Abra o Shell de Gerenciamento do Lync Server, caso ainda não esteja aberto.

4.  Use o cmdlet **Install-CsDatabase** com o parâmetro DatabasePathMap e uma tabela de hash PowerShell para instalar os bancos de dados configurados do Construtor de Topologias.

5.  No código de exemplo, os caminhos para os bancos de dados podem ser determinados de forma granular usando o parâmetro –DatabasePathsMap e uma tabela de hash definida como a seguir (o exemplo usa “C:\\CSData” para todos os arquivos (.mdf) do banco de dados, e “C:\\CSLogFiles” para todos os arquivos (.ldf) de log. A pasta será criada conforme necessário por Install-CsDatabase):
    
        $pathmap = @{
        "BackendStore:BlobStore:DbPath"="C:\CsData";"BackendStore:BlobStore:LogPath"="C:\CsLogFiles"
        "BackendStore:RtcSharedDatabase:DbPath"="C:\CsData";"BackendStore:RtcSharedDatabase:LogPath"="C:\CsLogFiles"
        "ABSStore:AbsDatabase:DbPath"="C:\CsData";"ABSStore:AbsDatabase:LogPath"="C:\CsLogFiles"
        "ApplicationStore:RgsConfigDatabase:DbPath"="C:\CsData";"ApplicationStore:RgsConfigDatabase:LogPath"="C:\CsLogFiles"
        "ApplicationStore:RgsDynDatabase:DbPath"="C:\CsData";"ApplicationStore:RgsDynDatabase:LogPath"="C:\CsLogFiles"
        "ApplicationStore:CpsDynDatabase:DbPath"="C:\CsData";"ApplicationStore:CpsDynDatabase:LogPath"="C:\CsLogFiles"
        "ArchivingStore:ArchivingDatabase:DbPath"="C:\CsData";"ArchivingStore:ArchivingDatabase:LogPath"="C:\CsLogFiles"
        "MonitoringStore:MonitoringDatabase:DbPath"="C:\CsData";"MonitoringStore:MonitoringDatabase:LogPath"="C:\CsLogFiles"
        "MonitoringStore:QoEMetricsDatabase:DbPath"="C:\CsData";"MonitoringStore:QoEMetricsDatabase:LogPath"="C:\CsLogFiles"
        }
        Install-CsDatabase -ConfigureDatabases -SqlServerFqdn sqlbe01.contoso.net -DatabasePathsMap $pathmap

6.  Como os arquivos de log e o banco de dados são nomeados explicitamente com seu local no servidor do banco de dados de destino, é possível definir locais específicos para cada banco de dados atual do tipo de serviço e local de log. O exemplo a seguir coloca bancos de dados para cada tipo de serviço específico em discos separados e arquivos de log associados em outro. Por exemplo:
    
      - Todos os bancos de dados RTC para “D:\\RTCDatabase”
    
      - Todos os arquivos de log do RTC para “E:\\RTCLogs”
    
      - Todos os bancos de dados de repositório do aplicativo para “F:\\CPSDatabases”
    
      - Todos os logs do repositório de aplicativos para “G:\\CPSLogs”
    
      - Todos os bancos de dados do repositório do grupo de resposta para “H:\\RGSDatabases”
    
      - Todos os logs do repositório do grupo de resposta para “I:\\RGSLogs”
    
      - Todos os bancos de dados do repositório do catálogo de endereços para “J:\\ABSDatabases”
    
      - Todos os arquivos de log do repositório de catálogo de endereços para “K:\\ABSLogs”
    
      - Todos os bancos de dados do repositório de arquivamento para “L:\\ArchivingDatabases”
    
      - Todos os logs do repositório de arquivamento para “M:\\ArchivingLogs”
    
      - Todos os bancos de dados do repositório de monitoramento para “N:\\MonitoringDatabases”
    
      - Todos os arquivos de log do repositório de monitoramento para “O:\\MonitoringLogfiles”
    
    <!-- end list -->
    
    ``` 
    
    $pathmap = @{
    "BackendStore:BlobStore:DbPath"="D:\RTCDatabase";"BackendStore:BlobStore:LogPath"="E:\RTCLogs"
    "BackendStore:RtcSharedDatabase:DbPath"="D:\RTCDatabase";"BackendStore:RtcSharedDatabase:LogPath"="E:\RTCLogs"
    "ABSStore:AbsDatabase:DbPath"="J:\ABSDatabases";"ABSStore:AbsDatabase:LogPath"="K:\ABSLogs"
    "ApplicationStore:RgsConfigDatabase:DbPath"="H:\RGSDatabases";"ApplicationStore:RgsConfigDatabase:LogPath"="G:\CPSLogs"
    "ApplicationStore:RgsDynDatabase:DbPath"="H:\RGSDatabases";"ApplicationStore:RgsDynDatabase:LogPath"="I:\RGSLogs"
    "ApplicationStore:CpsDynDatabase:DbPath"="F:\CPSDatabases";"ApplicationStore:CpsDynDatabase:LogPath"="G:\CsLogFiles"
    "ArchivingStore:ArchivingDatabase:DbPath"="M:\ArchivingLogs";"ArchivingStore:ArchivingDatabase:LogPath"="N:\MonitoringDatabases"
    "MonitoringStore:MonitoringDatabase:DbPath"="N:\MonitoringDatabases";"MonitoringStore:MonitoringDatabase:LogPath"="O:\MonitoringLogfiles"
    "MonitoringStore:QoEMetricsDatabase:DbPath"="N:\MonitoringDatabases";"MonitoringStore:QoEMetricsDatabase:LogPath"="O:\MonitoringLogfiles"
    }
    
    Install-CsDatabase -ConfiguredDatabases -SqlServerFqdn sqlbe01.contoso.net -DatabasePathMap $pathmap
    ```
    
    Usando o parâmetro –DatabasePathMap, é possível definir qualquer combinação de mapeamento da letra de unidade lógica que oferece a melhor solução para seus requisitos de posicionamento e desempenho do SQL Server.

Se você configurar seus arquivos de dados do banco de dados e arquivos de log usando o método **DatabasePathMap**, precisará realizar uma pequena mudança em seu processo normal ao usar o Construtor de Topologias. Geralmente, você define suas escolhas de topologia e escolhe implantar as seleções do banco de dados.

Se você usou o **DatabasePathMap**, já realizou a terceira parte do processo do Construtor de Topologias. Em caso de ter um servidor do banco de dados configurado completamente antes de executar o Construtor de Topologias, você ainda deve definir todas as suas funções e opções do servidor, mas desmarcar a opção para criar bancos de dados.

