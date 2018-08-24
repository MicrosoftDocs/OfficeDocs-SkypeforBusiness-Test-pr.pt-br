---
title: 'Lync Server 2013: Adicionar Servidor de Chat Persistente à topologia'
TOCTitle: Adicionar Servidor de Chat Persistente à topologia
ms:assetid: 8389b307-8c17-4e45-b3b5-5dc9fcfc2ffb
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ205049(v=OCS.15)
ms:contentKeyID: 49307316
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Adicionar Servidor de Chat Persistente à topologia no Lync Server 2013

 

_**Tópico modificado em:** 2012-10-06_

Você deve incoporar o suporte a Lync Server 2013 e Servidor de Chat Persistente na topologia antes de configurara implantação para oferecer suporte a Servidor de Chat Persistente. As informações deste tópico descrevem como usar Construtor de Topologias para adicionar suporte Servidor de Chat Persistente à topologia existente.

## Para adicionar Servidor de Chat Persistente a uma topologia

Siga estas instruções para instalar um único Pool de Servidor de Chat Persistente sem configuração para recuperação de desastres. Para configurar Pool de Servidor de Chat Persistente estendido a fim de garantir alta disponibilidade e recuperação de desastres, consulte [Configurando o Servidor de Chat Persistente para alta disponibilidade e recuperação de desastre no Lync Server 2013](lync-server-2013-configuring-persistent-chat-server-for-high-availability-and-disaster-recovery.md) na documentação de implantação.

Para implantar diversos Pools de Servidor de Chat Persistente, repita o processo para todos os pools.

1.  Em um computado com Lync Server 2013 em execução ou em que as ferramentas administrativas Lync Server estejam instaladas, faça logon usando uma conta que faça parte do grupo de usuários local (ou uma conta com direitos de usuário equivalentes).
    
    > [!NOTE]  
    > É possível definir a topologia por meio de uma conta que faça parte do grupo de usuários local. Porém, para publicar a topologia, o que é necessário para instalar servidores Lync Server 2013, é necessário usar uma conta que faça parte dos grupos <strong>Admins. do domínio</strong> e <strong>RTCUniversalServerAdmins</strong> e que tenha permissões para controle total (ou seja, ler, gravar e modificar) no repositório de arquivos que será usado para o repositório de arquivos Servidor de Chat Persistente (ou seja, para que Construtor de Topologias possa configurar DACLs) ou uma conta com direitos equivalentes.

2.  Iniciar Construtor de Topologias.

3.  Na árvore do console, acesse o nó **Chat Persistente Pools** e expanda-o para selecionar um Pool de Servidor de Chat Persistente ou clique no nó com o botão direito e selecione **Novo Chat Persistente Pool** . Defina o nome de domínio totalmente qualificado (FQDN) do pool e indique se trata-se de implementação de pool com um só ou com diversos servidores.
    
    Você pode entre **Pool de múltiplos computadores** ou **Pool de único computador** . Escolha a primeira opção se planejar ter mais de um Servidor de Chat PersistenteServidor Front-End em seu Pool de Servidor de Chat Persistente. É possível escolher agora ou depois porque após a criação do pool de único computador não é possível adicionar outros servidores. Se optar pelo pool de múltiploscomputadores, insira o nome do Servidor de Chat PersistenteServidores Front-End que contém o pool.
    
    > [!IMPORTANT]  
    > Se a função Servidor de Chat Persistente estiver sendo instalada em um Lync Server 2013Servidor Standard Edition, é necessário que o FQDN corresponda ao FQDN de Servidor Standard Edition.

4.  Defina um **Nome de exibição** simples para Pool de Servidor de Chat Persistente. O nome de exibição pode serusado por clientes personalizados, principalmente quando há diversos Pools de Servidor de Chat Persistente, a fim de diferenciar a sala.

5.  Defina a porta usada por Servidor de Chat Persistente para comunicação com Lync ServerServidores Front-End. A porta padrão é 5041.

6.  Se sua organização requerer suporte à conformidade, marque a caixa de seleção **Habilitar conformidade** . Caso a caixa seja marcada, o serviço de conformidade Servidor de Chat Persistente será intalado no mesmo computador que o Servidor de Chat PersistenteServidor Front-End. O sistema solicitará que você selecione SQL ServerServidor Back-End para conformidade Servidor de Chat Persistente posterior.

7.  Designe a afinidade de site para Pool de Servidor de Chat Persistente. Marque a caixa de seleção **Usar este pool como padrão para o site \<Nomedosite\>** ou **Usar este pool como padrão para todos os sites** para designar este Pool de Servidor de Chat Persistente como o pool padrão para o site atual ou para todos os sites. Quando o cliente Lync 2013 for usado para criar e gerenciar salas, o poolpadrão associado ao site do usuário é usado pela experiência de criação e gerenciamento de salas para que seja possível encaminhar as operações de criação e gerenciamento de salas para o pool em questão. Isso aplica-sesomente quando há diversos Pools de Servidor de Chat Persistente implantados e você deseja usar os recursos de criação e gerenciamento de sala de Servidor de Chat Persistente.
    
    > [!IMPORTANT]  
    > É possível personalizar os recursos de criação e gerenciamento de sala por meio do Software Development Kit (SDK) do Servidor de Chat Persistente.<br />    Para obter detalhes sobre como configurar bancos de dados de backup SQL Server para recuperação de desastres, consulte <a href="lync-server-2013-configuring-persistent-chat-server-for-high-availability-and-disaster-recovery.md">Configurando o Servidor de Chat Persistente para alta disponibilidade e recuperação de desastre no Lync Server 2013</a> na documentação de implantação.

8.  Defina o **repositório SQL para back-end Servidor de Chat Persistente (em que o conteúdo da sala de chat é armazenado)** seguindo estas instruções:
    
      - Para usar um banco de dados SQL Server existente, clique no nome do banco de dados SQL Server, exibido na lista suspensa, que deseja usar.
    
      - Para especificar um novo banco de dados SQL Server, clique em **Novo** e em **Definir novo repositório SQL** e siga estas instruções:
    
    <!-- end list -->
    
      - Em **FQDN do SQL Server** , especifique o FQDN do SQL Server em que deseja criar o novo banco de dados SQL Server.
    
      - Selecione **Instância padrão** para usar a instância padrão ou **Instância nomeada** e especifique a instância que deseja usar para especificar outra instância.

9.  Defina o banco de dados de conformidade SQL Server caso a conformidade esteja ativa.
    
    > [!IMPORTANT]  
    > Para obter mais detalhes sobre como configurar espelhos SQL Server para alta disponibilidadepara o banco de dados Servidor de Chat Persistente e o banco de dados de conformidade Servidor de Chat Persistente, consulte <a href="lync-server-2013-configuring-persistent-chat-server-for-high-availability-and-disaster-recovery.md">Configurando o Servidor de Chat Persistente para alta disponibilidade e recuperação de desastre no Lync Server 2013</a> na documentação de implantação.

10. Defina o reposítório do arquivo. Repositórios de arquivos são pastas em que são armazenadas cópidas de todos os arquivos enviados para o repositório de arquivos (por exemplo, para armazenar anexos postados em salas de chat). No caso de topologia Servidor de Chat Persistente com diversos servidores, o reositório deve ser um caminho UNC; no caso de topologia Servidor de Chat Persistente com um único servidor, pode ser o caminho de um arquivo local.
    
    Para usar repositórios de arquivos existentes, siga estas instruções:
    
      - No **FQDN do servidor de arquivos** , especifique o FQDN do repositório de arquivos em que deseja criar um novo repositório.
    
      - Em **Compartilhamento de arquivos** , especifique o repositório que deseja usar.
    
    > [!IMPORTANT]  
    > Você pode definir o repositório de arquivos em Construtor de Topologias antes de criar o repositório de arquivos, mas deve criar o repositório de arquivos no local definido por você antes de publicar a topologia.

11. Selecione o pool Servidor Front-End a ser usado como próximo salto para este Pool de Servidor de Chat Persistente. Este é o pool Servidor Front-End que será usado para encaminhar solicitações Servidor de Chat Persistente ao pool em questão.

12. Para salvar a configuração, clique em **Concluir** . Pool de Servidor de Chat Persistente é exibidoem Construtor de Topologias juntamente com as configurações do pool específico.
    
    Para publicar a topologia atualizada em que agora consta Servidor de Chat Persistente, consulte [Postar a topologia atualizada no Lync Server 2013](lync-server-2013-publish-the-updated-topology.md) na documentação de implantação.
    
    > [!NOTE]  
    > Com o Construtor de Topologias aberto, siga para a etapa 3 em <a href="lync-server-2013-publish-the-updated-topology.md">Postar a topologia atualizada no Lync Server 2013</a> para dar início à publicação da topologia atualizada.
