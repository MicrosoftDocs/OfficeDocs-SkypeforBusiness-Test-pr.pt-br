---
title: Atribuir uma política de chat persistente por usuário
TOCTitle: Atribuir uma política de chat persistente por usuário
ms:assetid: e22168f2-fde1-4f0a-b194-1fc881436822
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ721908(v=OCS.15)
ms:contentKeyID: 49886441
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Atribuir uma política de chat persistente por usuário

 

_**Tópico modificado em:** 2013-02-22_

É possível atribuir uma política de chat persistente por usuário no Painel de Controle do Lync Server 2013 ou Shell de Gerenciamento do Lync Server 2013. Para obter detalhes sobre como criar políticas de usuário para o Servidor de Chat Persistente, consulte [Criar uma política de usuário para Chat Persistente no Lync Server 2013](lync-server-2013-create-a-user-policy-for-persistent-chat.md).

## Para atribuir uma política de chat persistente por usuário no Painel de Controle do Lync Server

1.  Usando uma conta de usuário atribuída à função CsUserAdministrator ou CsAdministrator, faça logon em qualquer computador de sua implantação interna.

2.  Abra uma janela do navegador e insira a URL do Administrador para abrir o Painel de Controle do Lync Server. Para obter detalhes sobre os diferentes métodos que você pode usar para iniciar o Painel de Controle do Lync Server, consulte [Abrir ferramentas administrativas do Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

3.  Na barra de navegação esquerda, clique em **Usuários**.

4.  Use um dos seguintes métodos para localizar um usuário:
    
      - Na caixa **Pesquisar usuários**, digite todo ou parte do nome de exibição, nome, sobrenome, nome da conta SAM, endereço SIP ou URI de linha da conta do usuário e clique em **Localizar**.
    
      - Se você salvou uma consulta, clique no ícone **Abrir consulta**, use a caixa de diálogo **Abrir** para recuperar a consulta (um arquivo .usf) e clique em **Localizar**.

5.  (Opcional) Especifique o critério de pesquisa adicional para reduzir os resultados:
    
    1.  Clique em **Adicionar filtro**.
    
    2.  Insira a propriedade do usuário digitando ou clicando na seta da lista suspensa para selecionar a propriedade.
    
    3.  Na lista suspensa **Igual a**, clique no operador (por exemplo, **Igual a** ou **Diferente de**).
    
    4.  Dependendo da propriedade do usuário selecionada, insira o critério que deseja usar para filtrar os resultados de pesquisa digitando ou clicando na seta da lista suspensa.
        

        > [!TIP]
        > Para adicionar cláusulas de pesquisa adicionais à sua consulta, clique em <STRONG>Adicionar filtro</STRONG>.

    
    5.  Clique em **Localizar**.

6.  Clique em um usuário nos resultados da pesquisa, clique em **Ação** e em **Atribuir políticas**.
    

    > [!TIP]
    > Se você deseja aplicar a mesma política de Chat persistente para usuários múltiplos, selecione os usuários nos resultados da pesquisa e clique em <STRONG>Ações</STRONG> e em <STRONG>Atribuir políticas</STRONG>.



7.  Em **Atribuir políticas**, em **Política de Chat persistente**, siga um destes procedimentos:
    
    > [!NOTE]  
    > Como há várias políticas que você pode configurar usando a caixa de diálogo <strong>Atribuir políticas</strong>, <strong>&lt;Manter como está&gt;</strong> é selecionado por padrão para cada política na caixa de diálogo. Continue usando a política atribuída anteriormente ao usuário para não realizar alterações desta configuração.    
      - Selecione **\<Automático\>** para permitir que o Lync Server 2013 escolha automaticamente a política a nível global ou, se definida, a política a nível de site.
    
      - Clique no nome de uma política de chat persistente por usuário definida anteriormente na página **Política de chat persistente**.
        

        > [!TIP]
        > Para ajudar a decidir a política que deseja atribuir, após clicar no nome da política, clique em <STRONG>Exibir</STRONG> para ver os direitos e permissões do usuário definidos na política.



8.  Ao concluir, clique em **OK**.

## Atribuir uma política de chat persistente por usuário utilizando cmdlets do Lync Server PowerShell

As políticas de chat persistente por usuário também pode ser atribuídas utilizando o Lync Server PowerShell e o cmdlet Grant-CsPersistentChatPolicy. Este cmdlet pode ser executado do Shell de Gerenciamento do Lync Server 2013 ou de uma sessão remota do Windows PowerShell. Para obter detalhes sobre como usar o Windows PowerShell remoto para conectar ao Lync Server, consulte o artigo de blog do Lync Server Windows PowerShell, "Quick Start: Managing Microsoft Lync Server 2010 Using Remote PowerShell" em [http://go.microsoft.com/fwlink/p/?linkId=255876 (em inglês)](http://go.microsoft.com/fwlink/p/?linkid=255876).

## Atribuir uma política de chat persistente por usuário a um único usuário

  - O seguinte comando atribui a política de Chat persistente RedmondPersistentChatPolicy para o usuário Ken Myer.
    
        Grant-CsPersistentChatPolicy -Identity "Ken Myer" -PolicyName "RedmondPersistentChatPolicy"

## Atribuir uma política de chat persistente por usuário a vários usuários

  - Este comando atribui a política de chat persistente por usuário RedmondUsersPersistentChatPolicy a todos os usuários que trabalham no departamento de TI. Para obter mais informações sobre o parâmetro LdapFilter usado neste comando, consulte a documentação para o cmdlet [Get-CsUser](https://docs.microsoft.com/en-us/powershell/module/skype/Get-CsUser).
    
        Get-CsUser -LdapFilter "Department=IT" | Grant-CsPersistentChatPolicy -PolicyName "RedmondUsersPersistentChatPolicy"

## Retirar atribuição de uma política de chat persistente por usuário

  - O seguinte comando retira a atribuição de qualquer política de chat persistente por usuário atribuída anteriormente à Ken Myer. Após a política por usuário ser retirada, Ken Myer irá automaticamente ser gerenciado utilizando a política global ou, se existir, sua política de site local. Uma política de site tem precedência sobre a política global.
    
        Grant-CsPersistentChatPolicy -Identity "Ken Myer" -PolicyName $Null

Para obter mais informações, consulte o tópico de ajuda para o cmdlet [Grant-CsPersistentChatPolicy](https://docs.microsoft.com/en-us/powershell/module/skype/Grant-CsPersistentChatPolicy).

## Consulte Também

#### Conceitos

[Criar uma política de usuário para Chat Persistente no Lync Server 2013](lync-server-2013-create-a-user-policy-for-persistent-chat.md)

