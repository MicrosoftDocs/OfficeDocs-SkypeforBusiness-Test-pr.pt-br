---
title: Atribuir uma política de arquivamento por usuário
TOCTitle: Atribuir uma política de arquivamento por usuário
ms:assetid: a12ca483-b235-460f-b3fe-130fb3087264
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg182560(v=OCS.15)
ms:contentKeyID: 49307647
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Atribuir uma política de arquivamento por usuário

 

_**Tópico modificado em:** 2013-02-22_

A política de arquivamento é uma das configurações individuais de uma conta de usuário que você pode configurar no Painel de Controle do Lync Server 2013.

Implantar uma ou mais políticas de arquivamento é opcional. Você também pode implantar somente uma política de arquivamento de nível global ou de nível de site. Se você implantar políticas por usuário, deve atribui-las explicitamente a usuários, grupos ou objetos de contato. Requisitos de arquivamento são considerados com os valores padrão automaticamente para aqueles definidos na política de conferências de nível global, quando nenhuma política de nível de site ou por usuário estiver atribuída.

Depois de criar no mínimo uma política de arquivamento por usuário, use os procedimentos neste tópico para atribuir a política que especifica adequadamente se as comunicações internas, externas ou ambas de um usuário em particular serão arquivadas pelo servidor.

Para detalhes sobre como criar políticas de arquivamento por usuário, consulte [Criar uma Política de Arquivamento para Habilitar ou Desabilitar o Arquivamento de Comunicações Internos ou Externos para Sites ou Usuários Específicos](lync-server-2013-creating-an-archiving-policy-to-enable-or-disable-archiving-of-internal-or-external-communications-for-specific-sites-or-users.md).

## Para atribuir uma política de arquivamento por usuário

1.  Usando uma conta de usuário atribuída à função CsUserAdministrator ou CsAdministrator, faça logon em qualquer computador de sua implantação interna.

2.  Abra uma janela do navegador e insira a URL do Administrador para abrir o Painel de Controle do Lync Server. Para obter detalhes sobre os diferentes métodos que você pode usar para iniciar o Painel de Controle do Lync Server, consulte [Abrir ferramentas administrativas do Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

3.  Na barra de navegação à esquerda, clique em **Usuários**.

4.  Use um dos métodos a seguir para localizar um usuário:
    
      - Na caixa **Pesquisar usuários** digite a primeira parte ou todo o nome de exibição, primeiro nome, sobrenome, nome de conta SAM, endereço SIP ou URI de linha da conta do usuário e clique em **Localizar**.
    
      - Se você tem uma consulta salva, clique no ícone **Abrir consulta**, use a caixa de diálogo **Abrir** para recuperar a consulta (um arquivo .usf) e clique em **Localizar**.

5.  (Opcional) Especifique critérios de pesquisa adicionais para restringir os resultados:
    
    1.  Clique em **Adicionar Filtro**.
    
    2.  Insira a propriedade de usuário digitando-a ou clicando na seta na lista suspensa para selecioná-la.
    
    3.  Na lista suspensa **Igual a**, clique no operador (por exemplo, **Igual a** ou **Diferente de**).
    
    4.  Dependendo da propriedade de usuário selecionada, insira o critério que deseja usar para filtrar os resultados da pesquisa digitando-o ou clicando na seta na lista suspensa.
        

        > [!TIP]
        > Para incluir cláusulas de pesquisa adicionais à sua consulta, clique em <STRONG>Adicionar Filtro</STRONG>.

    
    5.  Clique em **Localizar**.

6.  Clique em um usuário nos resultados da pesquisa, clique em **Ação** e em **Atribuir políticas**.
    

    > [!TIP]
    > Se você deseja que a mesma política de arquivamento por usuário se aplique a vários usuários, selecione-os nos resultados da pesquisa, clique em <STRONG>Ações</STRONG> e em <STRONG>Atribuir políticas</STRONG>.



7.  Na caixa de diálogo **Atribuir Políticas**, sob **Política de arquivamento**, execute um dos seguintes procedimentos:
    
    > [!NOTE]  
    > Como existem várias políticas que podem ser configuradas usando a caixa de diálogo <strong>Atribuir Políticas</strong>, a opção <strong>&lt;Manter como está&gt;</strong> está selecionada por padrão para todas as políticas na caixa de diálogo. Continue usando a política anteriormente atribuída ao usuário simplesmente não alterando esta configuração.    
      - Permita que o Lync Server 2013 automaticamente escolha entre a política de nível global ou, se estiver definida, a política de nível de site.
    
      - Clique no nome de uma política de arquivamento por usuário definida anteriormente na página **Política de Arquivamento**.
        

        > [!TIP]
        > Para ajudá-lo a decidir a política que deseja atribuir, depois de clicar no nome da política, clique em <STRONG>Exibir</STRONG> para visualizar os direitos e permissões de usuário definidos.



8.  Quando terminar, clique em **OK**.

## Atribuição de política de arquivamento por usuário usando cmdlets do Windows PowerShell

As políticas de arquivamento por usuário podem ser também atribuídas usando o Windows PowerShell e o cmdlet **Grant-CsArchivingPolicy**. Esse cmdlet pode ser executado tanto do Shell de Gerenciamento do Lync Server 2013 quanto de uma sessão remota do Windows PowerShell. Para obter detalhes sobre como usar o Windows PowerShell remoto para conectar ao Lync Server, consulte o artigo de blog do Lync Server Windows PowerShell, "Quick Start: Managing Microsoft Lync Server 2010 Using Remote PowerShell" em [http://go.microsoft.com/fwlink/p/?linkId=255876 (em inglês)](http://go.microsoft.com/fwlink/p/?linkid=255876).

## Atribuição de política de arquivamento por usuário a um único usuário

  - O comando a seguir atribui a política de arquivamento por usuário RedmondArchivingPolicy ao usuário Ken Myer.
    
        Grant-CsArchivingPolicy -Identity "Ken Myer" -PolicyName "RedmondArchivingPolicy"

## Atribuição de política de arquivamento por usuário a vários usuários

  - Esse comando atribui a política de arquivamento por usuário RedmondArchivingPolicy a todos os usuários que tenham contas hospedadas no pool do Registrador atl-cs-001.litwareinc.com. Para obter mais informações sobre o parâmetro Filtro usado neste comando, consulte a documentação do cmdlet [Get-CsUser](https://docs.microsoft.com/en-us/powershell/module/skype/Get-CsUser).
    
        Get-CsUser -Filter {RegistrarPool -eq "atl-cs-001.litwareinc.com"} | Grant-CsArchivingPolicy -PolicyName "RedmondArchivingPolicy"

## Desatribuição de uma política de arquivamento por usuário

  - O comando a seguir desatribui a política de arquivamento por usuário anteriormente atribuída a Ken Myer. Depois que a política de voz por usuário é desatribuida, Ken Myer será automaticamente gerenciado usando uma política global ou, se existir, a política do seu site local. A política de site tem precedência sobre a política global.
    
        Grant-CsarchivingPolicy -Identity "Ken Myer" -PolicyName $Null

Para obter mais informações, consulte o tópico de ajuda do cmdlet [Grant-CsArchivingPolicy](https://docs.microsoft.com/en-us/powershell/module/skype/Grant-CsArchivingPolicy).

## Consulte Também

#### Tarefas

[Criar uma Política de Arquivamento para Habilitar ou Desabilitar o Arquivamento de Comunicações Internos ou Externos para Sites ou Usuários Específicos](lync-server-2013-creating-an-archiving-policy-to-enable-or-disable-archiving-of-internal-or-external-communications-for-specific-sites-or-users.md)  

#### Outros Recursos

[Atribuir políticas por usuário no Lync Server 2013](lync-server-2013-assigning-per-user-policies.md)

