---
title: Modificando opções do banco de dados de arquivamento no Lync Server 2013
TOCTitle: Modificando opções do banco de dados de arquivamento no Lync Server 2013
ms:assetid: 3775f09d-65b0-48bc-8a4d-d97bd0c3423c
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ204814(v=OCS.15)
ms:contentKeyID: 49306380
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Modificando opções do banco de dados de arquivamento no Lync Server 2013

 

_**Tópico modificado em:** 2012-11-01_

Se você implantar o arquivamento usando o armazenamento do SQL Server para arquivar o armazenamento de qualquer um de seus usuários, poderá fazer as seguintes alterações no armazenamento do banco de dados:

  - Usar um banco de dados do SQL Server diferente para arquivar o armazenamento. Isso abrange o banco de dados de arquivamento primário e qualquer banco de dados usado para espelhamento do SQL Server.

  - Alternar para a integração do Microsoft Exchange para armazenar arquivos e dados de arquivamento nos servidores do Exchange 2013. Se todos os usuários estiverem hospedados nos servidores do Exchange 2013 e você desejar usar o armazenamento do Microsoft Exchange para todos os usuários de sua implantação, será preciso remover os bancos de dados de armazenamento do SQL Server de sua topologia.

Para fazer uma dessas alterações, é preciso executar o Construtor de Topologias, fazer as alterações e publicar a topologia novamente. É possível usar o Construtor de Topologias para isso. Não especifique as informações de **Armazenamento de arquivamento do SQL Server** ou **Habilitar espelhamento do armazenamento do SQL Server**, a menos que tenha usuários do Lync que não estão hospedados nos servidores do Exchange 2013.

## Par alterar a opção de banco de dados de arquivamento

1.  Em um computador que está executando o Lync Server 2013 ou no qual as ferramentas administrativas do Lync Server estejam instaladas, faça logon usando uma conta que seja membro do grupo de usuários local (ou uma conta com direitos de usuário equivalentes).
    
    > [!NOTE]  
    > É possível definir uma topologia usando uma conta que seja membro do grupo de usuários local, mas para publicar uma topologia, o que é obrigatório para adicionar um componente à topologia, é preciso usar uma conta que seja membro do grupo de <strong>Admins. do domínio</strong> e do grupo <strong>RTCUniversalServerAdmins</strong> e que tenha permissões totais de controle (isto é, ler, gravar e modificar) no compartilhamento de arquivos usado no armazenamento de arquivos do Lync Server 2013 (isto é, para que o Construtor de Topologias possa configurar as DCALs (listas de controle de acesso condicional)) ou uma conta com direitos equivalentes.

2.  Inicie o Construtor de Topologias.

3.  Na árvore de console, navegue até o pool de front-ends no qual o arquivamento foi implantado e clique no nome do pool de front-ends no qual deseja alterar as opções de banco de dados.

4.  No menu **Ação**, clique em **Editar Propriedades**.

5.  Na caixa de diálogo **Editar Propriedades**, clique em **Geral**.

6.  Role a tela para baixo até **Arquivamento**.

7.  Em **Arquivamento**, faça o seguinte:
    
      - Para alterar para um armazenamento existente diferente do SQL Server, em **Armazenamento de arquivamento do SQL Server**, na caixa de listagem suspensa, faça o seguinte:
        
          - Para usar um armazenamento existente do SQL Server, na caixa de listagem suspensa, clique no nome do armazenamento do SQL Server que deseja usar.
        
          - Para especificar um novo armazenamento do SQL Server, clique em **Novo** e, depois, na caixa de diálogo **Definir Novo Armazenamento do SQL Server**, faça o seguinte:
            
              - Para usar um armazenamento existente do SQL Server, na caixa de listagem suspensa, clique no nome do armazenamento do SQL Server que deseja usar.
            
              - Para especificar um novo armazenamento do SQL Server, clique em **Novo** e, depois, na caixa de diálogo **Definir Novo Armazenamento do SQL Server**, faça o seguinte:
                
                  - Em **FQDN do SQL Server**, especifique o FQDN do servidor no qual deseja criar o armazenamento do SQL Server.
                
                  - Clique em **Instância padrão** para usar a instância padrão ou, para especificar uma instância diferente, clique em **Instância nomeada** e especifique a instância que deseja usar.
                
                  - Na instância do SQL Server especificada em uma relação de espelhamento, marque a caixa de seleção **Esta instância do SQL está em relação de espelhamento** e, então, em **Número da porta espelho**, especifique o número da porta.
    
      - Para adicionar um armazenamento do SQL Server de espelhamento ou alteração a um armazenamento existente diferente do SQL Server, selecione **Habilitar espelhamento do armazenamento do SQL Server** e, em seguida, faça o seguinte:
        
          - Para usar um armazenamento existente do SQL Server para espelhamento, na caixa de listagem suspensa **Espelho do armazenamento do SQL Server de arquivamento**, clique no nome do armazenamento do SQL Server que deseja usar para espelhamento.
        
          - Para especificar um novo armazenamento do SQL Server para espelhamento, clique em **Novo**e, então, na caixa de diálogo **Definir Novo Armazenamento do SQL Server**, realize uma das seguintes ações:
            
            1.  Em **FQDN do SQL Server**, especifique o FQDN do SQL Server no qual deseja criar o armazenamento do SQL Server.
            
            2.  Clique em **Instância padrão** para usar a instância padrão ou, para especificar uma instância diferente, clique em **Instância nomeada** e especifique a instância que deseja usar.
            
            3.  Na instância do SQL Server especificada em uma relação de espelhamento, marque a caixa de seleção **Esta instância do SQL está em relação de espelhamento** e, então, em **Número da porta espelho**, especifique o número da porta.
        
          - Se você habilitar o espelhamento do SQL Server e quiser adicionar ou alterar uma testemunha de espelhamento do SQL Server (uma terceira instância do SQL Server separada, que possa detectar a integridade do servidor primário do SQL Server e as instâncias de espelho), marque a caixa de seleção **Usar testemunha de espelhamento do SQL Server para habilitar failover automático** e, depois, realize uma dessas ações:
            
            1.  Em **FQDN do SQL Server**, especifique o FQDN do servidor no qual deseja criar a testemunha de espelhamento do SQL Server.
            
            2.  Clique em **Instância padrão** para usar a instância padrão ou, para especificar uma instância diferente, clique em **Instância nomeada** e especifique a instância que deseja usar para a testemunha de espelhamento.
            
            3.  Na instância do SQL Server especificada em uma relação de espelhamento, marque a caixa de seleção **Esta instância do SQL está em relação de espelhamento** e, então, em **Número da porta espelho**, especifique o número da porta.
    
      - Para alternar para a integração do Microsoft Exchange a fim de armazenar arquivos e dados de arquivamento nos servidores do Exchange 2013 (se todos os usuários de sua implantação estiverem hospedados nos servidores do Exchange 2013), exclua todas as informações dos bancos de dados de arquivamento.
    
    > [!IMPORTANT]  
    > Se tiver qualquer usuário do Lync que não esteja hospedado nos servidores do Exchange 2013, não exclua as informações do armazenamento do SQL Server.

8.  Para salvar a configuração, clique em **OK**.
    
    > [!IMPORTANT]  
    > As alterações feitas no Construtor de Topologias só terão efeito depois que a nova topologia for publicada. Para obter detalhes, consulte <a href="lync-server-2013-publishing-the-updated-topology-to-add-archiving-databases.md">Publicando a topologia atualizada para adicionar ao arquivamento de bancos de dados</a> na documentação de planejamento.
