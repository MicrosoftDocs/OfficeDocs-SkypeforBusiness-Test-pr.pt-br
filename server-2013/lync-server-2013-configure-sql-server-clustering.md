---
title: Configurar Agrupamento do SQL Server para Lync Server 2013
TOCTitle: Configurar Agrupamento do SQL Server para Lync Server 2013
ms:assetid: d7b52ef1-573c-48ed-bb94-34e37b49645c
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Dn383982(v=OCS.15)
ms:contentKeyID: 56558973
ms.date: 12/10/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Configurar Agrupamento do SQL Server para Lync Server 2013

 

_**Tópico modificado em:** 2016-12-08_

O Microsoft Lync Server 2013 oferece suporte de agrupamento para o SQL Server 2012 e SQL Server 2008 R2. Para saber mais sobre suportes, veja [Suporte a software de banco de dados no Lync Server 2013](lync-server-2013-database-software-support.md).

O agrupamento do SQL Server deve ser criado e configurado antes da instalação e implantação do Servidor Front-End Enterprise Edition e da base de dados do servidor Back-End. Para saber mais sobre práticas recomendadas e instruções de criação para failover de agrupamento no SQL Server 2012, veja <http://technet.microsoft.com/pt-br/library/hh231721.aspx>. Para failover de agrupamento no SQL Server 2008, veja <http://technet.microsoft.com/pt-br/library/ms189134(v=sql.105).aspx>.

Ao instalar o SQL Server, o SQL Server Management Studio deve ser instalado para gerenciar os locais de bases de dados e arquivos de log. O SQL Server Management Studio é instalado como componente opcional quando da instalação do SQL Server.

> [!IMPORTANT]  
> Para instalar e implantar as bases de dados no servidor de SQL Server, é preciso ser um membro do grupo sysadmin do SQL Server no servidor de SQL Server onde os arquivos de bases de dados estão sendo instalados. Se você não é um membro do grupo sysadmin do SQL Server, é necessário solicitar ao grupo que lhe adicione até que os arquivos de base de dados sejam implantados. Se não for possível se tornar um membro do grupo sysadmin, forneça o script de configuração e implantação das bases de dados ao seu administrador de bases de dados do SQL Server. Para saber mais sobre direitos e permissões necessários para concluir procedimentos, veja <a href="lync-server-2013-deployment-permissions-for-sql-server.md">Permissões de implantação para Servidor SQL no Lync Server 2013</a>.

## Para configurar o agrupamento no SQL Server

1.  Depois de completar a instalação e configuração do agrupamento no SQL Server, defina o armazenamento do SQL Server no Construtor de Topologia usando uma instância de nome de cluster virtual no SQL Server (como configurado nas definições para agrupamento de SQL Server) e uma instância de nomes da base de dados do SQL Server. Diferentemente de um único Servidor SQL Server, você usará o nó do nome de domínio totalmente qualificado (FQDN) para um agrupamento de Servidor SQL Server.
    
    > [!NOTE]  
    > Os nós de cluster individuais do Windows Server não precisam ser configurados para o Construtor de Topologia. Você usará somente o nome de cluster virtual do SQL Server.

2.  Se estiver usando o Contrutor de Topologia para implantação das bases de dados, é preciso ser um membro do grupo sysadmin do SQL Server. Se você já é um membro do grupo sysadmin do SQL Server, mas ainda não tem privilégios neste domínio (por exemplo, função de administrador de bases de dados do SQL Server), então você tem direitos de criação de bases de dados mas não de leitura de informações necessárias no Lync Server. Para saber mais sobre direitos e permissões necessárias para implantar o Lync Server, veja [Permissões de implantação para Servidor SQL no Lync Server 2013](lync-server-2013-deployment-permissions-for-sql-server.md).

3.  Verifique se a pasta da base de dados e os arquivos de log padrão estão mapeadas corretamente nos discos compartilhados no cluster do SQL Server ao usar o SQL Server Management Studio. Esse procedimento é obrigatório para criar bases de dados usando o Contrutor de Topologias.
    
    > [!NOTE]  
    > Se você não instalou o SQL Server Management Studio, é possível fazê-lo ao executar novamente a instalação do SQL Server e selecionar a ferramenta de gerenciamento como recurso adicionado para a implantação do SQL Server existente.

4.  Instale as bases de dados para o Servidor SQL Server usando o Contrutor de Topologia ou os cmdlets do Windows PowerShell. Para usar o Contrutor de Topologia, siga as etapas a seguir. Para usar cmdlets Windows PowerShell, veja [Instalação de banco de dados usando o Shell de Gerenciamento do Lync Server no Lync Server 2013](lync-server-2013-database-installation-using-lync-server-management-shell.md).

## Para criar bases de dados usando o Contrutor de Topologia

1.  Inicie o Construtor de Topologias: clique em **Iniciar**, em **Todos os Programas**, em **Microsoft Lync Server 2013** e em **Construtor de Topologias do Lync Server**.
    

    > [!WARNING]
    > O procedimento a seguir pressupõe que a topologia no Construtor de Topologia já foram definidas e configuradas. Para saber mais sobre definições de topologia, veja<A href="lync-server-2013-defining-and-configuring-the-topology.md">Definindo e configurando a topologia no Lync Server 2013</A>. Para usar o Contrutor de Topologia para publicar uma topologia e configurar uma base de dados, você deve logar com direitos e permissões de usuário de grupo corretas. Para saber mais sobre direitos e permissões de grupo necessários, veja <A href="lync-server-2013-deployment-permissions-for-sql-server.md">Permissões de implantação para Servidor SQL no Lync Server 2013</A>.



2.  Em Construtor de Topologia, ao publicar a topologia, na página **Criar base de dados**, clique em **Avançado**.

3.  A página **Selecione a Localização do Arquivo da Base de dados** tem duas opções que determinam como os arquivos de bases de dados serão implementados no cluster do SQL Server. Selecione um dos seguintes:
    
      - **Determina automaticamente a localização do arquivo da base de dados.** Esta seleção usa um algoritmo para determinar o local do arquivo da base de dados e arquivos log baseados na configuração da unidade no Servidor SQL Server. Os arquivos serão distribuídos de modo a tentar oferecer desempenho otimizado.
    
      - Use a instância padrão do SQL Server. Ao selecionar esta opção, os arquivos de log e de dados serão instalados de acordo com as configurações de instância do SQL Server. Depois da implantação dos arquivos da base de dados no SQL Server, o seu administrador de base de dados do SQL Server poderá realocar os arquivos para otimizar o desempenho para os seus requisitos de configuração particular do SQL Server.

4.  Concluir a publicação desta topologia e confirmar que não houve erros durante a operação.

