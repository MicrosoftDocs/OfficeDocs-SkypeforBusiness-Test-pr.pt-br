---
title: 'Lync Server 2013: Configurar categorias'
TOCTitle: Configurar categorias
ms:assetid: 4547f514-f0c0-404d-890f-092ddeeac852
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ204859(v=OCS.15)
ms:contentKeyID: 49306554
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Configurar categorias no Lync Server 2013

 

_**Tópico modificado em:** 2012-10-06_

No Painel de Controle do Lync Server 2013, você pode utilizar a seção **Categoria** da página **Chat Persistente** para configurar categorias. Uma categoria de sala Chat Persistente é uma estrutura lógica para organizar salas de bate-papo. Uma categoria define um conjunto padrão de listas de controle de acesso (ACLs) para controlar os usuários e grupos de usuário que possam criar ou participar de salas de bate-papo. Você pode utilizar categorias para reforçar paredes éticas entre diferentes subdivisões dentro das organizações.

As categorias de sala de bate-papo podem conter salas de bate-papo, mas nenhuma outra categoria. Cada categoria descreve o conteúdo com metadados, como *Nome* e *Descrição* . Além disso, a categoria possui propriedades as quais podem ser definidas para controlar o comportamento das salas de bate-papo pertencentes, como se as salas de bate-papo permitissem *Convites* ou *Envio de arquivo* ou contém *Histórico de bate-papo* .

## Para configurar categorias salas de bate-papo

1.  A partir de uma conta de usuário com a função CsPersistentChatAdministrator ou CsAdministrator atribuída, faça o logon em qualquer computador na sua implementação interna.

2.  Do menu **Iniciar**, selecione o Painel de Controle do Lync Server ou abra uma janela de navegador e, então, insira o Admin URL. Para detalhes sobre diferentes métodos que podem ser usados para iniciar o Painel de Controle do Lync Server, consulte [Abrir ferramentas administrativas do Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).
    
    > [!IMPORTANT]  
    > Você também pode usar o cmdlets Windows PowerShell. Para obter detalhes, consulte <a href="configuring-persistent-chat-server-by-using-windows-powershell-cmdlets.md">Configurando Servidor de Chat Persistente usando cmdlets do Windows PowerShell</a> na documentação de Implantação.

3.  Na barra de navegação à esquerda, clique em **Chat Persistente** e, então, em **Categoria**.
    
    Para múltiplas implantações Pool de Servidor de Chat Persistente, selecione o pool apropriado na lista suspensa.

4.  Na página **Categoria**, clique em **Novo** ou **Editar**.

5.  Em **Selecionar um serviço**, selecione o serviço correspondente ao Pool de Servidor de Chat Persistente na categoria que precisa ser criada. O serviço é o pool Servidor de Chat Persistente em que o Chat Persistente (cliente) utiliza para identificar qual pool a categoria pertence. Uma categoria pode pertencer apenas a um Pool de Servidor de Chat Persistente e não pode ser movido para outro ou compartilhado com outro pool.

6.  Em **Nova categoria**, faça o seguinte:
    
    1.  Em **Nome**, especifique um nome para a nova categoria de sala.
    
    2.  Em **Descrição**, forneça uma descrição detalhada para a categoria da sala (por exemplo, uma categoria de sala para Contoso).
    
    3.  Para controlar se os convites podem ser ativados por salas de bate-papo que pertencem a tal categoria, selecione ou limpe a caixa de marcação **Habilitar convites**. Se marcado, as salas nesta categoria poderão ter convites ativados ou desativados; em caso de não marcado, as salas nessa categoria não podem ter convite. Se uma sala possui convites ativados, quando um novo membro for adicionado à sala, ele ou ela recebe uma notificação da nova sala no cliente Chat Persistente.
    
    4.  Para controlar o envio de arquivo nas salas de bate-papo pertencentes a esta categoria, selecione ou limpe a caixa de marcação **Ativar envio de arquivo**. Se selecionado, as salas desta categoria podem ativar ou desativar o envio de arquivos; se não marcado, as salas nesta categoria não podem ter arquivos enviados.
        
        > [!IMPORTANT]  
        > Esta configuração é reforçada no servidor porque aplicativos personalizados ou clientes Chat de Grupo anteriores que utilizam Office Communications Server 2007 R2Servidor de Chat de Grupo ou Lync Server 2010, Chat de Grupo podem postar arquivos para uma sala. O cliente Lync 2013 não tem a capacidade de envio/download de arquivo, então, caso você tenha uma implantação Lync 2013 pura ou cliente Lync 2013, não é possível postar arquivos em uma sala de bate-papo Servidor de Chat Persistente.    
    5.  Para controlar o histórico do bate-papo, selecione ou limpe a caixa de marcação **Ativar histórico de bate-papo**. Se selecionado, as salas de bate-papo se tornam persistentes; caso contrário, as mensagens de bate-papo não são persistentes. Se a conformidade estiver ativada, as salas de bate-papo serão salvas em conformidade, mas os usuários não poderão acessar mensagens antigas. Essa opção pode ser utilizada para salas designadas para colaborações em tempo real e ad hoc que não precisam do histórico de bate-papo persistente.

7.  Em **Editar categoria**, faça o seguinte:
    
      - Em **Associação**, na seção **Membros permitidos**, adicione ou remova usuários e outras entidades Serviços de Domínio Active Directory (usuários, grupos de distribuição, unidades organizacionais e assim por diante) que são permitidos a serem adicionados como membros de uma sala de bate-papo pertencente à categoria. As entidades permitidas por uma categoria podem pesquisar por salas na categoria (a menos que uma sala esteja oculta, caso o qual apenas membros da sala podem pesquisar por ela no diretório).
    
      - Em **Associação**, na seção **Membros negados**, adicione ou remova usuários e outras entidades Active Directory associadas aos membros sendo negados da sala.
    
      - Em **Associação**, na seção **Criadores**, adicione ou remova usuários e outras entidades Active Directory associadas aos criadores para a categoria. Um criador é um usuário que possui permissões de criar salas de bate-papo e atribuir gerentes e membros de sala de bate-papo.

8.  Clique em **Confirmar**.

