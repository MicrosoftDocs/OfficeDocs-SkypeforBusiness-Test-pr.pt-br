---
title: Atribuir uma política de versão de cliente por usuário
TOCTitle: Atribuir uma política de versão de cliente por usuário
ms:assetid: f7e8ba2f-62dc-4e7d-8b63-682986f10240
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg182607(v=OCS.15)
ms:contentKeyID: 49308650
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Atribuir uma política de versão de cliente por usuário

 

_**Tópico modificado em:** 2013-02-22_

A política de versão do cliente é uma das configurações individuais de uma conta do usuário que você pode configurar no Painel de Controle do Lync Server.

Implantar uma ou mais políticas de versão do cliente por usuário é opcional. Também é possível implantar apenas uma política de versão do cliente a nível global ou políticas de versão do cliente a nível do pool ou a nível do site. Se você implantar políticas por usuário, deve atribui-las explicitamente aos usuários, grupos ou objeto de contato. Quando nenhuma política por usuário, por site ou por pool é atribuída, os clientes padrões permitidos a se registrar com o Lync Server 2013 são aqueles definidos na política de versão do cliente a nível global.

Após criar pelo menos uma política de versão do cliente por usuário, use os procedimentos neste tópico para atribuir a política que especifica as versões do cliente que deseja permitir o registro com o Lync Server.

Para obter detalhes sobre a criação de políticas de versão do cliente por usuário, consulte [Especificando aplicativos de client que podem ser usados para fazer logon no Lync Server 2013](lync-server-2013-specifying-the-client-applications-that-can-be-used-to-log-on-to-lync-server-2013.md).

## Para atribuir uma política de versão do cliente por usuário

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
    > Se você deseja que a mesma política de versão do cliente por usuário seja aplicada a vários usuários, selecione vários usuários nos resultados da pesquisa, clique em <STRONG>Ações</STRONG> e em <STRONG>Atribuir políticas</STRONG>.



7.  Em **Atribuir políticas**, em **Política de versão do cliente**, faça um dos seguintes:
    
    > [!NOTE]  
    > Como há várias políticas que você pode configurar usando a caixa de diálogo <strong>Atribuir políticas</strong>, <strong>&lt;Manter como está&gt;</strong> é selecionado por padrão para cada política na caixa de diálogo. Continue usando a política atribuída anteriormente ao usuário para não realizar alterações desta configuração.    
      - Permita que o Lync Server escolha automaticamente a política a nível global ou, se definida, a política a nível local ou a nível do pool.
    
      - Clique no nome de uma política de versão do cliente por usuário definida anteriormente na página **Política de versão do cliente**.
        

        > [!TIP]
        > Para ajudar a decidir a política que deseja atribuir, após clicar no nome da política, clique em <STRONG>Exibir</STRONG> para ver os direitos e permissões do usuário definidos na política.



8.  Ao concluir, clique em **OK**.

## Para atribuir uma política de versão do cliente específica do usuário usando o Shell de Gerenciamento do Lync Server

Também é possível atribuir políticas de versão do cliente específicas do usuário usando o cmdlet Grant-CsClientVersionPolicy. É possível executar este cmdlet do Shell de Gerenciamento do Lync Server 2013 ou de uma sessão remota do Windows PowerShell. Para obter detalhes sobre como usar o Windows PowerShell remoto para conectar ao Lync Server, consulte o artigo de blog do Lync Server Windows PowerShell, "Quick Start: Managing Microsoft Lync Server 2010 Using Remote PowerShell" em [http://go.microsoft.com/fwlink/p/?linkId=255876 (em inglês)](http://go.microsoft.com/fwlink/p/?linkid=255876)..

## Para atribuir uma política de versão do cliente específica do usuário

  - O comando a seguir atribui a política de versão do cliente RedmondClientVersionPolicy ao usuário Ken Myer.
    
        Grant-CsClientVersionPolicy -Identity "Ken Myer" -PolicyName "RedmondClientVersionPolicy"

## Para atribuir uma política de versão do cliente específica do usuário a vários usuários

  - Este comando atribui a política de versão do cliente RedmondClientVersionPolicy a todos os usuários aos quais a política de voz RedmondVoicePolicy tiver sido anteriormente atribuída. Para obter mais informações sobre os parâmetros de filtro usados neste comando, consulte a documentação do cmdlet [Get-CsUser](https://docs.microsoft.com/en-us/powershell/module/skype/Get-CsUser).
    
        Get-CsUser -Filter {VoicePolicy -eq "RedmondVoicePolicy"} | Grant-CsClientVersionPolicy -PolicyName "RedmondClientVersionPolicy"

## Para cancelar a atribuição de uma política de versão do cliente específica do usuário

  - O comando a seguir cancela a atribuição de uma política de versão do cliente específica do usuário atribuída anteriormente a Ken Myer. Após cancelar a atribuição de uma política específica do usuário, o Ken Myer será automaticamente gerenciado usando a política global, sua política do site local (se existir) ou a política de escopo de serviço atribuída ao seu Registrar. Uma política de escopo de serviço tem precedência sobre qualquer política de site e a política de site tem precedência sobre a política global.
    
        Grant-CsClientVersionPolicy -Identity "Ken Myer" -PolicyName $Null

Para obter mais informações, consulte o tópico do cmdlet [Grant-CsClientVersionPolicy](https://docs.microsoft.com/en-us/powershell/module/skype/Grant-CsClientVersionPolicy).

## Consulte Também

#### Outros Recursos

[Atribuir políticas por usuário no Lync Server 2013](lync-server-2013-assigning-per-user-policies.md)  
[Gerenciando dispositivos, telefones e aplicativos do cliente no Lync Server 2013](lync-server-2013-managing-devices-phones-and-client-applications.md)

