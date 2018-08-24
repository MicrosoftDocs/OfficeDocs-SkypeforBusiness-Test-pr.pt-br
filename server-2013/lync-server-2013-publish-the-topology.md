---
title: 'Lync Server 2013: Publicar a topologia'
TOCTitle: Publicar a topologia
ms:assetid: 3b5a744b-b3a8-4538-a55e-e2e4f72dff47
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg425880(v=OCS.15)
ms:contentKeyID: 49306433
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Publicar a topologia no Lync Server 2013

 

_**Tópico modificado em:** 2013-10-01_

Para publicar, habilitar ou desabilitar com êxito uma topologia ao adicionar ou remover uma função de servidor, você deve estar conectado como um usuário membro dos grupos RTCUniversalServerAdmins e Administradores de Domínio. Também é possível delegar os direitos e permissões de administrador adequados. Para obter detalhes, consulte [Delegar permissões de configuração no Lync Server 2013](lync-server-2013-delegate-setup-permissions.md). Para fazer outras alterações na configuração, apenas a associação ao grupo RTCUniversalServerAdmins é necessária.

Depois de definir sua topologia no Construtor de Topologias, você deve publicar a topologia para o Repositório de Gerenciamento Central. O Repositório de Gerenciamento Central oferece um armazenamento robusto e esquematizado dos dados necessários para definir, configurar, manter, administrar, descrever e operar uma implantação do Lync Server 2013. Também valida os dados para garantir a consistência da configuração. Todas as alterações para estes dados de configuração acontecem no Repositório de Gerenciamento Central, eliminando os problemas “fora de sincronização”. As cópias somente leitura dos dados são replicadas para todos os servidores na topologia, incluindo os Servidores de Borda.

> [!NOTE]  
> O SQL Server precisa de um mínimo de 20 GB de espaço em disco livre para publicar a topologia inicial com êxito e criar o Servidor de Gerenciamento Central.

> [!NOTE]  
> Para o Enterprise Edition somente: para publicar a topologia, o Servidor Back-End baseado no SQL Server deve estar online e acessível com exceções de firewall no lugar. Para obter detalhes sobre a especificação de exceções de firewall, consulte <a href="lync-server-2013-understanding-firewall-requirements-for-sql-server.md">Compreendendo os requisitos de firewall para Servidor SQL com Lync Server 2013</a>. Para obter detalhes sobre a configuração do SQL Server, consulte <a href="lync-server-2013-configure-sql-server-for-lync-server.md">Configurar o SQL Server para Lync Server 2013</a>.

## Para publicar uma topologia

1.  Inicie o Construtor de Topologias: clique em **Iniciar**, em **Todos os Programas**, em **Microsoft Lync Server 2013** e em **Construtor de Topologias do Lync Server**.

2.  Selecione para abrir a topologia de um arquivo local. Se você estiver no computador onde definiu a topologia, este será o local onde você salvou nas etapas anteriores. Normalmente, será a pasta Documentos do usuário que configurou a topologia.

3.  Clique com o botão direito do mouse no nó **Lync Server 2013** e, depois, clique em **Publicar Topologia** .

4.  Na página **Publicar a topologia** , clique em **Avançar** .

5.  Na página **Criar bancos de dados** , selecione os bancos de dados que deseja publicar.
    
    > [!NOTE]  
    > Se não tiver os direitos apropriados para criar os bancos de dados, você poderá desmarcar as caixas de seleção ao lado desses bancos de dados e, posteriormente, alguém com os direitos apropriados poderá criar bancos de dados. Para obter detalhes, consulte <a href="lync-server-2013-deployment-permissions-for-sql-server.md">Permissões de implantação para Servidor SQL no Lync Server 2013</a>.

6.  Opcionalmente, clique em **Avançado** . As opções avançadas de posicionamento do arquivo de dados do SQL Server permitem que você selecione entre as seguintes opções:
    
      - **Determinar o local do arquivo de banco de dados automaticamente** - essa opção determinará o melhor desempenho operacional baseado na configuração do disco no servidor baseado em SQL Server distribuindo os arquivos de log e de dados para o melhor local.
    
      - **Usar padrões de instância SQL Server** - esta opção coloca arquivos de log e de dados no servidor de SQL Server usando as configurações de instância. Essa opção não usa a funcionalidade operacional do servidor de SQL Server para determinar locais ideais para logs e dados. O administrador do SQL Server normalmente moverá arquivos de log e de dados para locais que são apropriados para os procedimentos de gerenciamento de servidor e organização baseados no SQL Server.
    
    Clique em **OK** e, em seguida, clique em **Avançar** .

7.  Na página **Selecionar um Servidor de Gerenciamento Central** , selecione um Pool de Front-Ends.

8.  Opcionalmente, clique em **Avançado** . As opções avançadas de posicionamento do arquivo de dados do SQL Server permitem que você selecione entre as seguintes opções:
    
      - **Determinar o local do arquivo de banco de dados automaticamente** - essa opção determinará o melhor desempenho operacional baseado na configuração do disco no servidor baseado em SQL Server distribuindo os arquivos de log e de dados para o melhor local.
    
      - **Usar padrões de instância SQL Server** - esta opção coloca arquivos de log e de dados no servidor de SQL Server usando as configurações de instância. Essa opção não usa a funcionalidade operacional do servidor de SQL Server para determinar locais ideais para logs e dados. O administrador do SQL Server normalmente moverá arquivos de log e de dados para locais que são apropriados para os procedimentos de gerenciamento de servidor e organização baseados no SQL Server.
    
    Clique em **OK** .

9.  Clique em **Avançar** para concluir o processo de publicação.

10. Quando o processo de publicação for concluído, clique em **Finalizar** .
    
    Depois que a topologia for publicada com êxito, você poderá começar a instalar uma réplica local do Repositório de Gerenciamento Central em cada servidor com o Lync Server 2013 em execução em sua topologia. É recomendável começar com o primeiro Pool de Front-Ends.

## Consulte Também

#### Outros Recursos

[Configurand Servidores e pools Front-End para Lync Server 2013](lync-server-2013-setting-up-front-end-servers-and-front-end-pools.md)

