---
title: Adicionando o Arquivamento de Bancos de Dados à Topologia de Lync Server 2013
TOCTitle: Adicionando o Arquivamento de Bancos de Dados à Topologia de Lync Server 2013
ms:assetid: 089ab32f-1167-4bb8-a283-fdc6c9613072
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ204654(v=OCS.15)
ms:contentKeyID: 49305804
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Adicionando o Arquivamento de Bancos de Dados à Topologia de Lync Server 2013

 

_**Tópico modificado em:** 2012-10-10_

É necessário incorporar o arquivamento à sua topologia antes de poder configurar sua implantação para suportar o arquivamento. As informações neste tópico explicam como usar o Construtor de Topologias para adicionar o arquivamento à sua topologia existente.

> [!NOTE]  
> Se você quiser usar a integração do Microsoft Exchange para armazenar dados de arquivamento e arquivos nos servidores do Exchange 2013 para todos seus usuários em sua implantação, não especifique informações do <strong>Repositório do SQL Server de Arquivamento</strong> ou <strong>Usar espelhamento do SQL Server Store</strong>.

## Para adicionar suporte ao banco de dados de Arquivamento à sua topologia

1.  Em um computador que está executando o Lync Server 2013 ou no qual as ferramentas administrativas do Lync Server estão instaladas, faça logon usando uma conta membro do grupo local Usuários (ou uma conta com direitos de usuário equivalentes).
    
    > [!NOTE]  
    > Você pode definir uma topologia usando uma conta membro do grupo local Usuários, mas para publicar uma topologia, o que é necessário para adicionar um servidor à topologia, você precisa usar uma conta membro do grupo <strong>Admins. de Domínio</strong> e do grupo <strong>RTCUniversalServerAdmins</strong> e ter permissões de controle total (ou seja, leitura, gravação e modificação) no compartilhamento de arquivo que você está usando para o repositório de arquivos do Lync Server 2013 (ou seja, para que o Construtor de Topologias possa configurar as DACLs [lista de controle de acesso discricionário] necessárias), ou uma conta com direitos equivalentes.

2.  Inicie o Construtor de Topologias.

3.  Na árvore do console, navegue até o pool de Front-Ends no qual você deseja implantar o Arquivamento e clique no nome do pool.

4.  No menu **Ação**, clique em **Editar Propriedades**.

5.  Na caixa de diálogo **Editar Propriedades**, clique em **Geral**.

6.  Role a tela para baixo até **Arquivamento**.

7.  Marque a caixa de seleção **Arquivamento**.

8.  Em **Repositório do SQL Server de Arquivamento**, faça o seguinte:
    
      - Para usar um repositório existente do SQL Server, na caixa de listagem suspensa, clique no nome do repositório do SQL Server que você deseja usar. Se todos os seus usuários estiverem hospedados no Microsoft Exchange Server 2013 ou acima, você poderá arquivar as comunicações do Lync para todos os seus usuários no Exchange. Nesse caso, não é necessário configurar o repositório de Arquivamento do SQL Server.
    
      - Para especificar um novo repositório do SQL Server, clique em **Novo** e na caixa de diálogo **Definir Novo Repositório do SQL Server**, faça o seguinte:
        
          - Em **FQDN do SQL Server**, especifique o FQDN do servidor no qual você deseja criar o novo repositório do SQL Server.
        
          - Clique em **Instância Padrão** para usar a instância padrão, ou, para especificar uma instância diferente, clique em **Instância nomeada** e especifique a instância que você deseja usar.
        
          - Se a instância do SQL Server especificada estiver em um relacionamento de espelhamento, marque a caixa de seleção **Esta instância SQL está em uma relação de espelhamento** e, em **Número da porta de espelho**, especifique o número da porta.

9.  Se você quiser usar o espelhamento do repositório do SQL Server, selecione **Habilitar espelhamento do Repositório do SQL Server** e faça o seguinte:
    
      - Para usar um repositório existente do SQL Server para espelhamento, na caixa de listagem suspensa **Espelho do repositório do SQL Server de Arquivamento**, clique no nome do repositório do SQL Server que você deseja usar para espelhamento.
    
      - Para especificar um novo repositório do SQL Server para espelhamento, clique em **Novo** e na caixa de diálogo **Definir Novo Repositório do SQL Server**, execute uma das seguintes ações:
        
        1.  Em **FQDN do SQL Server**, especifique o FQDN do SQL Server no qual você deseja criar o novo repositório do SQL Server .
        
        2.  Clique em **Instância Padrão** para usar a instância padrão, ou, para especificar uma instância diferente, clique em **Instância Nomeada** e especifique a instância que você deseja usar.
        
        3.  Se a instância do SQL Server especificada estiver em um relacionamento de espelhamento, marque a caixa de seleção **Esta instância SQL está em uma relação de espelhamento** e, em **Número da porta de espelho**, especifique o número da porta.
    
      - Se você habilitar o espelhamento do SQL Server e quiser incluir uma testemunha de espelhamento do SQL Server (uma terceira instância separada do SQL Server que pode detectar a integridade do servidor primário e instâncias de espelho do SQL Server), marque a caixa de seleção **Usar testemunha de espelhamento do SQL Server para habilitar o failover automático** e execute uma das seguintes ações:
        
        1.  Em **FQDN do SQL Server**, especifique o FQDN do servidor no qual você deseja criar a nova testemunha de espelhamento do SQL Server.
        
        2.  Clique em **Instância Padrão** para usar a instância padrão, ou, para especificar uma instância diferente, clique em **Instância Nomeada** e especifique a instância que você deseja usar para a testemunha de espelhamento.
        
        3.  Se a instância do SQL Server especificada estiver em um relacionamento de espelhamento, marque a caixa de seleção **Esta instância SQL está em uma relação de espelhamento** e, em **Número da porta de espelho**, especifique o número da porta.

10. Para salvar a configuração, clique em **OK**.

