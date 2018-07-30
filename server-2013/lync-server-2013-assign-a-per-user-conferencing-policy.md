---
title: Atribuir uma política de conferência por usuário
TOCTitle: Atribuir uma política de conferência por usuário
ms:assetid: 72f12c72-65f7-44fe-ab81-0f57cb2f87d1
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg521015(v=OCS.15)
ms:contentKeyID: 49307099
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Atribuir uma política de conferência por usuário

 

_**Tópico modificado em:** 2013-02-22_

A política de conferência é uma das configurações individuais de uma conta de usuário que você pode definir no Painel de Controle do Lync Server.

A implantação de uma ou mais políticas de conferência por usuário é opcional. Você também pode implantar somente uma política de conferência a nível global ou política de conferência a nível de site. Se você implantar políticas por usuário, deverá explicitamente atribuí-las a usuários, grupos ou objetos de contato. As permissões e direitos de usuário de conferência são automaticamente padrão para os que estão definidos na política de conferência a nível global, quando nenhuma política específica a nível de site ou por usuário é atribuída.

Depois de criar pelo menos uma política de conferência por usuário, use os procedimentos neste tópico para atribuir a política que especifica os direitos e permissões que você deseja que o servidor conceda a reuniões organizadas por um determinado usuário.

Para uma lista de todas as configurações da política de conferência disponíveis, consulte [Referência das configurações da política de conferência para Lync Server 2013](lync-server-2013-conferencing-policy-settings-reference.md).

Para obter detalhes sobre a criação de políticas de conferência, consulte [Criar ou Modificar uma Política de Conferência no Lync Server 2013](lync-server-2013-create-or-modify-a-conferencing-policy.md).

## Para atribuir uma plítica de conferência por usuário

1.  Usando uma conta de usuário atribuída à função CsUserAdministrator ou CsAdministrator, faça logon em qualquer computador de sua implantação interna.

2.  Abra uma janela do navegador e insira a URL do Administrador para abrir o Painel de Controle do Lync Server. Para obter detalhes sobre os diferentes métodos que você pode usar para iniciar o Painel de Controle do Lync Server, consulte [Abrir ferramentas administrativas do Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

3.  Na barra de navegação esquerda, clique em **Usuários**.

4.  Use um dos seguintes métodos para localizar um usuário:
    
      - Na caixa **Pesquisar usuários**, digite todo ou a primeira parte do nome de exibição, do nome, do sobrenome, do nome da conta do Gerenciador de Contas de Segurança (SAM), do endereço SIP ou da linha do Identificador de Recursos Uniforme (URI) da conta do usuário e clique em **Localizar**.
    
      - Se você possui uma consulta salva, clique no ícone **Abrir consulta**, use a caixa de diálogo **Abrir** para recuperar a consulta (um arquivo .usf) e clique em **Localizar**.

5.  (Opcional) Especifique o critério de pesquisa adicional para reduzir os resultados:
    
    1.  Clique em **Adicionar Filtro**.
    
    2.  Insira a propriedade do usuário digitando ou clicando na seta da lista suspensa para selecionar a propriedade.
    
    3.  Na lista suspensa **Igual a**, clique no operador (por exemplo, **Igual a** ou **Diferente de**).
    
    4.  Dependendo da propriedade do usuário selecionada, insira o critério que você deseja usar para filtrar os resultados da pesquisa digitando ou clicando na seta da lista suspensa.
        

        > [!TIP]
        > Para adicionar as cláusulas de pesquisa adicionais na sua consulta, clique em <STRONG>Adicionar Filtro</STRONG>.

    
    5.  Clique em **Localizar**.

6.  Clique em um usuário nos resultados da pesquisa, em **Ação** e em **Atribuir políticas**.
    

    > [!TIP]
    > Se deseja que a mesma política de conferência por usuário seja aplicada a vários usuários, selecione vários usuários nos resultados da pesquisa e clique em <STRONG>Ações</STRONG> e em <STRONG>Atribuir políticas</STRONG>.



7.  Em **Atribuir políticas**, na **Política de conferência**, faça o seguinte procedimento:
    
    > [!NOTE]  
    > Como há várias políticas que você pode configurar em <strong>Atribuir políticas</strong>, <strong>&lt;Manter&gt;</strong> é selecionado por padrão para cada política na caixa de diálogo. Continue a usar a política atribuída anteriormente ao usuário sem realizar alterações nesta configuração.    
      - Selecione **\<Automático\>** para permitir que o Lync Server 2013 escolha automaticamente a política a nível global ou, se definida, a política a nível de site.
    
      - Clique no nome de uma política de conferência por usuário previamente definida na página **Política de conferência**.
        

        > [!TIP]
        > Para ajudar você a decidir a política que deseja atribuir, após clicar no nome da política, clique em <STRONG>Exibir</STRONG> para exibir os direitos e permissões do usuário definidos na política.



8.  Quando terminar, clique em **OK**.

## Atribuindo uma política de conferência por usuário usando os cmdlets de PowerShell do Lync Server

As políticas de conferência por usuário também podem ser atribuídas usando o PowerShell do Lync Server e o cmdlet Grant-CsConferencingPolicy. Esse cmdlet pode ser executado no Shell de Gerenciamento do Lync Server 2013 ou em uma sessão remota do Windows PowerShell. Para obter detalhes sobre como usar o Windows PowerShell remoto para conectar ao Lync Server, consulte o artigo de blog do Lync Server Windows PowerShell, "Quick Start: Managing Microsoft Lync Server 2010 Using Remote PowerShell" em [http://go.microsoft.com/fwlink/p/?linkId=255876 (em inglês)](http://go.microsoft.com/fwlink/p/?linkid=255876).

## Atribuindo uma política de conferência por usuário a um único usuário

  - O comando a seguir atribui a política de conferência por usuário RedmondConferencingPolicy ao usuário Ken Myer.
    
        Grant-CsConferencingPolicy -Identity "Ken Myer" -PolicyName "RedmondConferencingPolicy"

## Atribuindo uma política de conferência por usuário a vários usuários

  - Este comando atribui a política de conferência por usuário HRConferencingPolicy a todos os usuários que trabalham para o departamento de Recursos Humanos. Para obter mais informações sobre o parâmetro LdapFilter usado neste comando, consulte a documentação do cmdlet [Get-CsUser](https://docs.microsoft.com/en-us/powershell/module/skype/Get-CsUser).
    
        Get-CsUser -LdapFilter "Department=Human Resources" | Grant-CsConferencingPolicy -PolicyName "HRConferencingPolicy"

## Cancelando a atribuição de uma política de conferência por usuário

  - O comando a seguir cancela a atribuição de qualquer política de conferência por usuário atribuída a Ken Myer. Após o cancelamento da atribuição da política por usuário, Ken Myer será automaticamente gerenciado usando a política global ou a política de site local (se houver). Um política de site tem prioridade sobre a política global.
    
        Grant-CsConferencingPolicy -Identity "Ken Myer" -PolicyName $Null

Para obter mais informações, consulte o tópico de ajuda do cmdlet [Grant-CsConferencingPolicy](https://docs.microsoft.com/en-us/powershell/module/skype/Grant-CsConferencingPolicy).

## Consulte Também

#### Tarefas

[Criar ou Modificar uma Política de Conferência no Lync Server 2013](lync-server-2013-create-or-modify-a-conferencing-policy.md)  

#### Outros Recursos

[Atribuir políticas por usuário no Lync Server 2013](lync-server-2013-assigning-per-user-policies.md)

