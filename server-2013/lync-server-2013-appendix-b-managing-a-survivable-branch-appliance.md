---
title: 'Lync Server 2013: Anexo B: Gerenciando um Aplicativo de Filial Persistente'
TOCTitle: 'Anexo B: Gerenciando um Aplicativo de Filial Persistente'
ms:assetid: 2ec9d505-6d39-491c-9524-8cf36866b855
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg425797(v=OCS.15)
ms:contentKeyID: 49306265
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Anexo B: Gerenciando um Aplicativo de Filial Persistente no Lync Server 2013

 

_**Tópico modificado em:** 2012-10-18_

Este tópico inclui procedimentos sobre o gerenciamento do Aparelho de Filial Persistente. Especificamente, como substituir e renomear um Aparelho de Filial Persistente e como alterar o pool de Front-End do Lync Server 2013 que o Aparelho de Filial Persistente está associado.

## Para substituir um aplicativo de filial persistente

1.  Pare todos os serviços do Lync Server 2013 no Aparelho de Filial Persistente. (Consulte a documentação do fornecedor do Aparelho de Filial Persistente.)

2.  (Recomendado) Remova o Aparelho de Filial Persistente do domínio.

3.  Exclua o objeto de computador do Aparelho de Filial Persistente no Serviços de Domínio Active Directory, executando estas etapas:
    
      - Faça logon em um servidor membro como um membro do grupo Administração de Empresa.
    
      - Clique em **Iniciar** , depois em **Ferramentas Administrativas** e, em seguida, clique em **Usuários e Computadores do Active Directory** .
    
      - Clique com o botão direito do mouse no objeto Aparelho de Filial Persistente e clique em **Excluir** .

4.  Adicione o objeto de computador Aparelho de Filial Persistente novamente. (Consulte [Adicionar um Aplicativo de Filial Persistente ao Active Directory no Lync Server 2013](lync-server-2013-add-a-survivable-branch-appliance-to-active-directory.md).)

5.  Aguarde a replicação do Active Directory ocorrer.

6.  Abra o Shell de Gerenciamento do Lync Server e digite **Enable-CSTopology** .

7.  Conecte o novo Aparelho de Filial Persistente à rede e execute as etapas em [Implantando um servidor ou aparelho de filial persistente com o Lync Server 2013 - Tarefas do site central](lync-server-2013-deploying-a-survivable-branch-appliance-or-server-central-site-tasks.md) e [Implantar Servidor ou Aparelho de Filial Persistente com Lync Server 2013 - tarefa de site de filial](lync-server-2013-deploy-a-survivable-branch-appliance-or-server-branch-site-task.md).

## Para renomear um aplicativo de filial persistente

1.  Mova os usuários para o site central. Para obter detalhes, consulte [Mover usuários para outro pool](lync-server-2013-move-users-to-another-pool.md).

2.  Pare todos os serviços do Lync Server 2013 no Aparelho de Filial Persistente. (Consulte a documentação do fornecedor do Aparelho de Filial Persistente.)

3.  Remova a Aparelho de Filial Persistente da topologia, executando estas etapas:
    
      - Clique em **Iniciar** , **Todos os programas** , **Microsoft Lync Server** e em **Construtor de topologias do Lync Server** .
    
      - Na árvore de console, expanda **Sites locais** , clique em Aparelho de Filial Persistente e em **Excluir** no painel Ações.

4.  Remova o Aparelho de Filial Persistente do domínio.

5.  Exclua o objeto de computador do Aparelho de Filial Persistente no Active Directory, executando estas etapas:
    
      - Faça logon no controlador de domínio como membro do grupo Administradores de Empresa.
    
      - Clique em **Iniciar** , depois em **Ferramentas Administrativas** e, em seguida, clique em **Usuários e Computadores do Active Directory** .
    
      - Clique com o botão direito do mouse no objeto Aparelho de Filial Persistente e clique em **Excluir** .

6.  Restaure o Aparelho de Filial Persistente para os padrões de fábrica. (Consulte a documentação do fornecedor do Aparelho de Filial Persistente.)

7.  Execute as etapas em [Implantando um servidor ou aparelho de filial persistente com o Lync Server 2013 - Tarefas do site central](lync-server-2013-deploying-a-survivable-branch-appliance-or-server-central-site-tasks.md) e em [Implantar Servidor ou Aparelho de Filial Persistente com Lync Server 2013 - tarefa de site de filial](lync-server-2013-deploy-a-survivable-branch-appliance-or-server-branch-site-task.md).

8.  Mova os usuários para o Aparelho de Filial Persistente renomeado. Para obter detalhes, consulte [Mover usuários para outro pool](lync-server-2013-move-users-to-another-pool.md).

## Para alterar o pool de front-end do Lync Server que o aplicativo de filial persistente está associado

1.  Mova os usuários do Aparelho de Filial Persistente para o pool de Front-End do Lync Server no site central. Para obter detalhes, consulte [Mover usuários para outro pool](lync-server-2013-move-users-to-another-pool.md).

2.  Pare todos os serviços do Lync Server no Aparelho de Filial Persistente. (Consulte a documentação de fornecedor do Aparelho de Filial Persistente).

3.  Atualize o pool de Front-end do Lync Server que o Aparelho de Filial Persistente está associado seguindo estas etapas:
    
      - Clique em **Iniciar** , **Todos os programas** , **Microsoft Lync Server** e em **Construtor de topologias do Lync Server** .
    
      - Expanda **Sites de filial** .
    
      - Clique com o botão direito no objeto do Aparelho de Filial Persistente a modificar e clique em **Editar propriedades**
    
      - Em Resiliência, selecione o novo Pool de Front-Ends que o Aparelho de Filial Persistente deve ser associado e clique em **Avançar** .
    
      - Na árvore do console, clique com o botão direito do mouse no novo Aparelho de Filial Persistente, clique em **Topologia** e clique em **Publicar** .

4.  Reinicie todos os Serviços do Lync Server no Aparelho de Filial Persistente.

5.  Teste o Aparelho de Filial Persistente. Para obter detalhes, consulte [Usuários domésticos em um Home users on a Aparelho de Filial Persistente ou Servidor no Lync Server 2013](lync-server-2013-home-users-on-a-survivable-branch-appliance-or-server.md).

6.  Mova os usuários do pool de Front-end do Lync Server no site central para o Aparelho de Filial Persistente.

