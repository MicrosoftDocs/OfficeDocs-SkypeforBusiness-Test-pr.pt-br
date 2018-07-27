---
title: Atribuir uma política de PIN por usuário
TOCTitle: Atribuir uma política de PIN por usuário
ms:assetid: d8211c64-0b63-4193-a074-673da7d14287
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg182594(v=OCS.15)
ms:contentKeyID: 49308275
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Atribuir uma política de PIN por usuário

 

_**Tópico modificado em:** 2013-02-22_

A política de PIN (número de identificação pessoal) de conferência discada é uma das configurações individuais de uma conta de usuário que podem ser definidas no Painel de Controle do Lync Server 2013.

A implantação de uma ou mais políticas de PIN por usuário é opcional. Também é possível implantar somente uma política de PIN de nível global ou política de PIN de nível de site. Se você implantar políticas por usuário, deverá atribui-las explicitamente aos usuários, grupos ou objeto de contato. Direitos e permissões do usuário relacionados ao uso de PINs para conferência discada assumem automaticamente o padrão daqueles definidos na política de PIN de nível global quando nenhuma política específica de nível de site ou por usuário é atribuída.

Após a criação de pelo menos uma política de PIN por usuário, use o procedimento neste tópico para atribuir a política que especifica as restrições que você deseja que o servidor imponha sobre os PINs criados e usados por um usuário específico.

Para obter detalhes sobre como criar políticas de PIN de conferência discada por usuário, consulte [Criar ou modificar as configurações de PIN de conferência discada no Lync Server 2013 para um site ou grupo de usuários](lync-server-2013-create-or-modify-dial-in-conferencing-pin-settings-for-a-site-or-group-of-users.md).

## Para atribuir uma política de PIN por usuário

1.  Usando uma conta de usuário atribuída à função CsUserAdministrator ou CsAdministrator, faça logon em qualquer computador de sua implantação interna.

2.  Abra uma janela do navegador e insira a URL do Administrador para abrir o Painel de Controle do Lync Server. Para obter detalhes sobre os diferentes métodos que você pode usar para iniciar o Painel de Controle do Lync Server, consulte [Abrir ferramentas administrativas do Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

3.  Na barra de navegação esquerda, clique em **Usuários**.

4.  Use um dos métodos a seguir para localizar um usuário:
    
      - Na caixa **Pesquisar usuários**, digite todo ou parte do nome de exibição, nome, sobrenome, nome de conta do SAM (Gerenciador de contas de segurança), endereço SIP ou URI (Uniform Resource Identifier) da linha da conta de usuário e clique em **Localizar**.
    
      - Se você tiver uma consulta salva, clique no ícone **Abrir consulta**, use a caixa de diálogo **Abrir** para recuperar a consulta (um arquivo .usf) e clique em **Localizar**.

5.  (Opcional) Especifique critérios de pesquisa adicionais para restringir os resultados:
    
    1.  Clique em **Adicionar Filtro**.
    
    2.  Insira a propriedade do usuário digitando ou clicando na seta na lista suspensa para selecionar a propriedade.
    
    3.  Na lista suspensa **Igual a**, clique no operador (por exemplo, **Igual a** ou **Diferente de**).
    
    4.  Dependendo da propriedade do usuário selecionada, insira os critérios que você deseja usar para filtrar os resultados da pesquisa digitando ou clicando na seta da lista suspensa.
        

        > [!TIP]
        > Para adicionar outras cláusulas de pesquisa à sua consulta, clique em <STRONG>Adicionar Filtro</STRONG>.

    
    5.  Clique em **Localizar**.

6.  Clique em um usuário nos resultados da pesquisa, clique em **Ação** e clique em **Atribuir políticas**.
    

    > [!TIP]
    > Se você quiser a mesma política de PIN por usuário aplicada a diversos usuários, selecione múltiplos usuários nos resultados da pesquisa e clique em <STRONG>Ações</STRONG> e em <STRONG>Atribuir políticas</STRONG>.



7.  Em **Atribuir Políticas**, em **Política de PIN**, execute uma das seguintes ações:
    
    > [!NOTE]  
    > Como há várias políticas que podem ser configuradas usando a caixa de diálogo <strong>Atribuir Políticas</strong>, <strong>&lt;Manter como está&gt;</strong> está selecionado por padrão para cada política na caixa de diálogo. Continue usando a política previamente atribuída ao usuário não fazendo alterações nessa configuração.    
      - Permita que o Lync Server 2013 escolha automaticamente a política de nível global ou, se estiver definida, a política de nível de site.
    
      - Clique no nome de uma política PIN por usuário definida anteriormente na página **Política de PIN**.
        

        > [!TIP]
        > Para ajudá-lo a decidir a política que você deseja atribuir, após clicar em um nome de política, clique em <STRONG>Exibir</STRONG> para exibir os direitos e permissões de usuário definidos na política.



8.  Quando terminar, clique em **OK**.

## Atribuir uma política de PIN por usuário utilizando cmdlets do Shell de Gerenciamento do Lync Server

É possível atribuir as políticas PIN por usuário utilizando o Shell de Gerenciamento do Lync Server e o cmdlet **Grant-CsPinPolicy**. É possível executar este cmdlet do Shell de Gerenciamento do Lync Server 2013 ou de uma sessão remota do Windows PowerShell. Para obter detalhes sobre como usar o Windows PowerShell remoto para conectar ao Lync Server, consulte o artigo de blog do Lync Server Windows PowerShell, "Quick Start: Managing Microsoft Lync Server 2010 Using Remote PowerShell" em [http://go.microsoft.com/fwlink/p/?linkId=255876 (em inglês)](http://go.microsoft.com/fwlink/p/?linkid=255876).

## Para atribuir uma política PIN por usuário para um único usuário

  - O seguinte comando atribui a política PIN por usuário RedmondPinPolicy para o usuário Ken Myer.
    
        Grant-CsPinPolicy -Identity "Ken Myer" -PolicyName "RedmondPinPolicy"

## Para atribuir uma política PIN por usuário a vários usuários

  - O seguinte comando atribui a política PIN por usuário RedmondUsersPinPolicy para todos os usuários que trabalham na cidade de Redmond. Para obter detalhes sobre o parâmetro LdapFilter usado neste comando, consulte [Get-CsUser](https://docs.microsoft.com/en-us/powershell/module/skype/Get-CsUser).
    
        Get-CsUser -LdapFilter "l=Redmond" | Grant-CsPinPolicy -PolicyName "RedmondUsersPinPolicy"

## Para retirar a atribuição de uma política PIN por usuário

  - O seguinte comando retira a atribuição de qualquer política PIN por usuário anteriormente atribuído ao Ken Myer. Após a política por usuário ser retirada, Ken irá automaticamente ser gerenciado usando a política global ou, se existir, sua política de site local. Uma política de site tem precedência sobre a política global.
    
        Grant-CsPinPolicy -Identity "Ken Myer" -PolicyName $Null

Para obter detalhes, consulte [Grant-CsPinPolicy](https://docs.microsoft.com/en-us/powershell/module/skype/Grant-CsPinPolicy).

## Consulte Também

#### Tarefas

[Criar uma nova política de PIN](lync-server-2013-create-a-new-pin-policy.md)  

#### Outros Recursos

[Atribuir políticas por usuário no Lync Server 2013](lync-server-2013-assigning-per-user-policies.md)

